---
layout: default
title: Storms Leaderboard
description:
---

<table id="stormsTable"></table>

<link rel="stylesheet" href="/assets/css/sortable.min.css" />
<script src="/assets/js/sortable.min.js"></script>
<script>
    function createHeader() {
        var table = document.getElementById("stormsTable");
        table.classList.add("sortable")
        var header = table.createTHead(table);
        var row = header.insertRow(0);
        var head = ["User", "Wins", "Net Rewards", "Starts", "Single Guess", "Two Guesses", "Three Guesses", "Four Guesses"];
        for (let i = 0; i < head.length; i++) {
            let cell = document.createElement("th");
            cell.innerText = head[i];
            row.append(cell);
        }
    }
    function populateBody(json) {
        var table = document.getElementById("stormsTable");
        var tbody = table.createTBody(table);
        var i = 0;
        for (key in json) {
            var row = tbody.insertRow(i);
            var username = json[key].username
            var numStormWins = json[key].numStormWins
            if (numStormWins == undefined) {
                numStormWins = "0"
            }
            var numNetStormRewards = json[key].numNetStormRewards
            if (numNetStormRewards == undefined) {
                numNetStormRewards = "0.00"
            }
            var numStormStarts = json[key].numStormStarts
            if (numStormStarts == undefined) {
                numStormStarts = "0"
            }
            var numStormTier1Multi = json[key].numStormTier1Multi
            if (numStormTier1Multi == undefined) {
                numStormTier1Multi = "0"
            }
            var numStormTier2Multi = json[key].numStormTier2Multi
            if (numStormTier2Multi == undefined) {
                numStormTier2Multi = "0"
            }
            var numStormTier3Multi = json[key].numStormTier3Multi
            if (numStormTier3Multi == undefined) {
                numStormTier3Multi = "0"
            }
            var numStormTier4Multi = json[key].numStormTier4Multi
            if (numStormTier4Multi == undefined) {
                numStormTier4Multi = "0"
            }
            row.innerHTML = `
            <td>${username}</td>
            <td>${numStormWins}</td>
            <td>${numNetStormRewards}</td>
            <td>${numStormStarts}</td>
            <td>${numStormTier1Multi}</td>
            <td>${numStormTier2Multi}</td>
            <td>${numStormTier3Multi}</td>
            <td>${numStormTier4Multi}</td>
            `;
            i++;
        }
        var headerCells = table.getElementsByTagName("th");
        headerCells[1].click()
    }
    function generateTable() {
        fetch("{{site.gbot_host}}/GBot/public/leaderboard")
            .then((response) => response.json())
            .then(json => {
                createHeader();
                populateBody(json);
            });
    }
    generateTable()
</script>

---
layout: default
title: "'Who Dis?' Leaderboard"
description:
---

<table id="whoDisTable"></table>

<link rel="stylesheet" href="/assets/css/sortable.min.css" />
<script src="/assets/js/sortable.min.js"></script>
<script>
    function createHeader() {
        var table = document.getElementById("whoDisTable");
        table.classList.add("sortable")
        var header = table.createTHead(table);
        var row = header.insertRow(0);
        var head = ["User", "Wins", "Total Rewards"];
        for (let i = 0; i < head.length; i++) {
            let cell = document.createElement("th");
            cell.innerText = head[i];
            row.append(cell);
        }
    }
    function populateBody(json) {
        var table = document.getElementById("whoDisTable");
        var tbody = table.createTBody(table);
        var i = 0;
        for (key in json) {
            var row = tbody.insertRow(i);
            var username = json[key].username
            var numWhoDisWins = json[key].numWhoDisWins
            if (numWhoDisWins == undefined) {
                numWhoDisWins = "0"
            }
            var numWhoDisRewards = json[key].numWhoDisRewards
            if (numWhoDisRewards == undefined) {
                numWhoDisRewards = "0.00"
            }
            row.innerHTML = `
            <td>${username}</td>
            <td>${numWhoDisWins}</td>
            <td>${numWhoDisRewards}</td>
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

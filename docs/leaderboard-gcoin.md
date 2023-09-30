---
layout: default
title: GCoin Leaderboard
description:
---

<table id="gcoinTable"></table>

<link rel="stylesheet" href="/assets/css/sortable.min.css" />
<script src="/assets/js/sortable.min.js"></script>
<script>
    function createHeader() {
        var table = document.getElementById("gcoinTable");
        table.classList.add("sortable")
        var header = table.createTHead(table);
        var row = header.insertRow(0);
        var head = ["User", "GCoin"];
        for (let i = 0; i < head.length; i++) {
            let cell = document.createElement("th");
            cell.innerText = head[i];
            row.append(cell);
        }
    }
    function populateBody(json) {
        var table = document.getElementById("gcoinTable");
        var tbody = table.createTBody(table);
        var i = 0;
        for (key in json) {
            var row = tbody.insertRow(i);
            var username = json[key].username
            var balance = json[key].balance
            if (balance == undefined) {
                balance = "0.00"
            }
            row.innerHTML = `
            <td>${username}</td>
            <td>${balance}</td>
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

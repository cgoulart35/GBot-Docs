---
layout: default
title: Storms Leaderboard
description:
---

<table id="stormsTable"></table>

<script>
    function createHeader() {
        var table = document.getElementById("stormsTable");
        var header = table.createTHead(table);
        var row = header.insertRow(0);
        var head = ["User", "Wins", "Total Rewards", "Single Guess", "Two Guesses", "Three Guesses", "Four Guesses"];
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
            row.innerHTML = `
            <td>${json[key].username}</td>
            <td>${json[key].numWins}</td>
            <td>${json[key].numRewards}</td>
            <td>${json[key].numX10Multi}</td>
            <td>${json[key].numX5Multi}</td>
            <td>${json[key].numX2d5Multi}</td>
            <td>${json[key].numX1d25Multi}</td>
            `;
            i++;
        }
    }
    function setupSorting(colToClick) {
        var excludedColumns = ["User"];
        const getCellValue = (tr, idx) => tr.children[idx].innerText || tr.children[idx].textContent;
        const comparer = (idx, asc) => (a, b) => ((v1, v2) => 
            v1 !== '' && v2 !== '' && !isNaN(v1) && !isNaN(v2) ? v1 - v2 : v1.toString().localeCompare(v2)
            )(getCellValue(asc ? a : b, idx), getCellValue(asc ? b : a, idx));
        var allHeaders = document.querySelectorAll('th')
        var thToClick;
        for (i = 0; i < allHeaders.length; i++) {
            var th = allHeaders[i];
            if (!excludedColumns.includes(th.innerText)) {
                if (colToClick === th.innerText) {
                    thToClick = th;
                }
                th.addEventListener('click', (() => {
                    const table = th.closest('table');
                    const tbody = table.querySelector('tbody');
                    Array.from(tbody.querySelectorAll('tr'))
                        .sort(comparer(Array.from(th.parentNode.children).indexOf(th), this.asc = !this.asc))
                        .forEach(tr => tbody.appendChild(tr) );
                }))
            }
        }
        if (thToClick != undefined) {
            thToClick.click();
            thToClick.click();
        }
    }
    fetch("{{site.gbot_host}}/GBot/public/storms/leaderboard")
        .then((response) => response.json())
        .then(json => {
            createHeader();
            populateBody(json);
            setupSorting("Wins");
        });
</script>

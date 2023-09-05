---
layout: default
title: "'Who Dis?' Leaderboard"
description: "Users with the most 'Who Dis?' wins."
---

<table id="gcoinTable"></table>

<script>
    function createHeader() {
        var table = document.getElementById("gcoinTable");
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
            row.innerHTML = `
            <td>${key}</td>
            <td>${json[key].balance}</td>
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
    fetch("https://gbot-database-default-rtdb.firebaseio.com/gcoin.json")
        .then((response) => response.json())
        .then(json => {
            createHeader();
            populateBody(json);
            setupSorting("GCoin");
        });
</script>

[back](./)

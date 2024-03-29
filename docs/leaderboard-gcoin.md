---
layout: default
title: GCoin Leaderboard
description:
---

<table id="gcoinTable"></table>

<script>
    function setupSorting() {
        // extracted JS
        document.addEventListener("click", function(c) {
            try {
                function h(b, a) {
                    return b.nodeName === a ? b : h(b.parentNode, a)
                }
                var w = c.shiftKey || c.altKey,
                    d = h(c.target, "TH"),
                    m = d.parentNode,
                    n = m.parentNode,
                    g = n.parentNode;
                function p(b, a) {
                    b.classList.remove("dir-d");
                    b.classList.remove("dir-u");
                    a && b.classList.add(a)
                }
                function q(b) {
                    var a;
                    return w ? b.dataset.sortAlt : null !== (a = b.dataset.sort) && void 0 !== a ? a : b.textContent
                }
                if ("THEAD" === n.nodeName && g.classList.contains("sortable") && !d.classList.contains("no-sort")) {
                    var r, f = m.cells,
                        t = parseInt(d.dataset.sortTbr);
                    for (c = 0; c < f.length; c++) f[c] === d ? r = parseInt(d.dataset.sortCol) || c : p(f[c], "");
                    f = "dir-d";
                    if (d.classList.contains("dir-d") || g.classList.contains("asc") && !d.classList.contains("dir-u")) f = "dir-u";
                    p(d, f);
                    var x = "dir-u" === f,
                        y = g.classList.contains("n-last"),
                        u = function(b, a, e) {
                            a = q(a.cells[e]);
                            b = q(b.cells[e]);
                            if (y) {
                                if ("" === a && "" !== b) return -1;
                                if ("" === b && "" !== a) return 1
                            }
                            e = Number(a) - Number(b);
                            a = isNaN(e) ? a.localeCompare(b) : e;
                            return x ? -a : a
                        };
                    for (c = 0; c < g.tBodies.length; c++) {
                        var k = g.tBodies[c],
                            v = [].slice.call(k.rows, 0);
                        v.sort(function(b, a) {
                            var e = u(b, a, r);
                            return 0 !== e || isNaN(t) ? e : u(b, a, t)
                        });
                        var l = k.cloneNode();
                        l.append.apply(l, v);
                        g.replaceChild(l, k)
                    }
                }
            } catch (h) {}
        });
    }
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
        function prettyNumber(numStr) {
            return numStr.replace(/\B(?<!\.\d*)(?=(\d{3})+(?!\d))/g, ",");
        }
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
            <td data-sort="${balance}">${prettyNumber(balance)}</td>
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
                setupSorting();
                createHeader();
                populateBody(json);
            });
    }
    generateTable()
</script>

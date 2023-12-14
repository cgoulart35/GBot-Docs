---
layout: default
title: Storms Leaderboard
description:
---

<table id="stormsTable"></table>

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
        function prettyNumber(numStr) {
            return numStr.replace(/\B(?<!\.\d*)(?=(\d{3})+(?!\d))/g, ",");
        }
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
            <td data-sort="${numStormWins}">${prettyNumber(numStormWins)}</td>
            <td data-sort="${numNetStormRewards}">${prettyNumber(numNetStormRewards)}</td>
            <td data-sort="${numStormStarts}">${prettyNumber(numStormStarts)}</td>
            <td data-sort="${numStormTier1Multi}">${prettyNumber(numStormTier1Multi)}</td>
            <td data-sort="${numStormTier2Multi}">${prettyNumber(numStormTier2Multi)}</td>
            <td data-sort="${numStormTier3Multi}">${prettyNumber(numStormTier3Multi)}</td>
            <td data-sort="${numStormTier4Multi}">${prettyNumber(numStormTier4Multi)}</td>
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

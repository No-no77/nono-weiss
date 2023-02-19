---
published: draft
subtitle:
date: 2023-02-19
tags:
foam_template:
  filepath: '_journal/2023-02-graphviz-game-cycle-danganronpa.md'
  name: Journal Entry
---

# Test


{% graphviz Prototype of a Game Cycle for a Danganronpa-themed TTRPG %}
digraph G {
  node [shape=box]
  edge [color = "#aaaaaa"]
  overlap = "false"
  nodesep = 1

  sda2 [label="sda2", color="#ffd44f"]
  sdb2 [label="sdb2", color="#ffd44f"]

  md1 [label="mdraid mirror (md1)", color="#ffd44f"]

  sda2, sdb2 -> md1
}
{% endgraphviz %}




---
published: draft
subtitle:
date: 2023-02-19
tags:
foam_template:
  filepath: '_journal/2023-02-graphviz-game-cycle-danganronpa.md'
  name: Journal Entry
---

# Prototype of a Game Cycle for a Danganronpa-themed TTRP

{% graphviz Test %}
digraph trial {
    rankdir=TB;
    node [shape=rectangle]

    // Daytime block
    subgraph cluster_daytime {
        label="Daily Life Block";
        style=filled;
        node [style=rounded];
        d0 [label="Early Morning [2A]", style=filled, fillcolor=white];
        d1 [label="Breakfast [3A]", style=filled, fillcolor=white];
        d2 [label="Morning [4A]", style=filled, fillcolor=white];
        d3 [label="Lunch [2A]", style=filled, fillcolor=white];
        n0 [label="Afternoon [Work + 2A]", style=filled, fillcolor=white];
        n1 [label="Dinner [2A]", style=filled, fillcolor=white];
        n2 [label="Night [2A]", style=filled, fillcolor=white];
        n3 [label="Overtime [2A]", style=filled, fillcolor=orange];
        n4 [label="Blue Hour [1A]", style=filled, fillcolor=lightblue];
        n5 [label="Staying up until \nBlue Hour makes you \nsleepy for the \nentire next day", style=filled, fillcolor=white]
        n6 [label="Going overtime \nmakes you sleepy \nin the next morning", style=filled, fillcolor=white]
        
        {rank=same; d0; d1; d2; d3;}
        {rank=same; n4; n5}               
        {rank=same; n3; n6}   

    }
    // Daytime connections
    d0 -> d1;
    d1 -> d2;
    d2 -> d3;
    d3 -> n0;
    
    // Daytime connections
    n0 -> n1;
    n1 -> n2;
    n2 -> n3;
    n3 -> n4;
    n3 -> n6;
    n4 -> n5;
    n4 -> d0;
    n2 -> a1;
    a1 -> a2;
    a2 -> n4;
    
    a0 [label="A = Action"]
    a1 [label="Given n ammount of days have passed"]
    a2 [label="Start an Event"]
    a3 [label="An action block \nmight take 1 to 2 hours\n to be completed"]
    a4 [label="Physical Challenge"]
    a5 [label="Puzzle"]
    a6 [label="Annnouncement"]
    a7 [label="Inciting Despair"]
    
    a0 -> a3;
    a2 -> a4;
    a2 -> a5;
    a2 -> a6;
    a2 -> a7;
    
     // Investigation block
    subgraph cluster_inv {
        label="Investigation Block";
        style=filled;
        e0 [label="3 or more people find a body", style=filled, fillcolor=white]
        e1 [label="Gather evidence and information", style=filled, fillcolor=white];
        e2 [label="Talk to witnesses and suspects", style=filled, fillcolor=white];
        e3 [label="Examine crime scene and clues", style=filled, fillcolor=white];
    }

    // Trial block
    subgraph cluster_trial {
        label="Trial Block";
        t0 [label="Opening Statements"];
        t1 [label="Witness Testimonies"];
        t2 [label="Cross-Examination"];
        t3 [label="Closing Arguments"];
        t4 [label="Verdict Deliberation"];
        t5 [label="Verdict Announcement"];
    }

    // Events leading up to the trial
    e0 -> e1;
    e1 -> e2;
    e1 -> e3;

    // Trial events
    e2 -> t0;
    e3 -> t0;
    t0 -> t1;
    t1 -> t2;
    t2 -> t1;
    t2 -> t3;
    t3 -> t4;
    t4 -> t5;

    // Verdict
    t5 -> verdict;
    verdict [shape=ellipse, style=filled, fillcolor=gray, label="Verdict\n(Not Guilty or Guilty)"];
    

    // Results
    verdict -> r1
    verdict -> r2
    
    r1 [label="Wrong"]
    r2 [label="Right"]
    
    c1 [label="Assassin survives"]
    c2 [label="Everyone is Executed"]
    c3 [label="Assassin is Executed"]
    c4 [label="Game continues."]
    c5 [label="Game ends."]
    
    r1 -> c1
    r1 -> c2
    c2 -> c5
    c1 -> c5
    
    r2 -> c3
    c3 -> c4
}

{% endgraphviz %}




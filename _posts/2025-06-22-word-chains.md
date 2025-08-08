---
layout: post
title: "Word Chains"
author: "Petar"
---

<head>
    <script type="text/javascript" src="https://unpkg.com/vis-network/standalone/umd/vis-network.min.js"></script>
    <style type="text/css">
        .network {
            /* width: 600px; */
            height: 600px;
        }
        #loadingBar {
            display: flex;
            justify-content: center;
            align-items: center;
            width: 100%;
        }
    </style>
</head>

<img loading="lazy" src="/assets/images/word-chains/cover.png" />

When I look up a word in the dictionary, I get unusually annoyed when I see the word itself used in its definition.

> **redundancy** /rĭ-dŭn′dən-sē/
> noun
>
> - The state of being **redundant**.
> - Something **redundant** or excessive; a superfluity.
> - Repetition of linguistic information inherent in the structure of a language...
>
> _The American Heritage® Dictionary of the English Language, 5th Edition_

Yeah, ok, it's not the _exact_ same word and the definition makes sense, but I'd rather not have to look up the definition of _"redundant"_ to understand what the _"state of being redundant"_ is. The 3rd definition given above gets it.

So that got me thinking, how often does that happen and does it form a chain of words? Let's define every word in the dictionary as a _node_ and draw lines to every word that appears in its definition.

For simplicity I:

- used the English 2024 `WordNet` [dictionary](https://wn.readthedocs.io/en/latest/#)
- ignored entries with spaces in them
- filtered out punctuation and stop words (e.g: `a, of, us, but, they...`) in definitions
- aimed not to spend more than a day on this **_(spoiler alert: this took way too long and I couldn't even get it to work 100%)_**

Some of the filtered words include `Salpiglossis sinuata`, `sea snake`, `polling booth`, `occipital protuberance` and my favourite, `beefsteak geranium`.

There were 67,780 such entries out of a total of 161,705. Initially I was also getting errors for around 12k words but that's because the `.words()` method was returning all adjectives tagged as `a` but their internal tag elsewhere in the wordnet was `s`.

As for the actual word chains, I just straight up brute-forced it. No fancy data structures or clever algorithms. I just looped over the `word: definition` map twice and checked for matches. Yeah, it's dumb, but ~~it's~~ was a Sunday morning. It took about 2hrs to process on my M1. Let's plot the results!

<img src="/assets/images/word-chains/initial_results.png" width="600"/> _Ah yes, as expected._

I am using the [vis.js](https://visjs.github.io/vis-network/docs/network/index.html) library for this (first time). Whilst the code is working, the visualisation is simply too dense. I needed to do some more filtering. I removed words with 0 chains and made sure I am not double counting things. Oh and I need to turn on the `physics` setting!

Let's check out how things look on a random sample of ~1000 words.

> Note: it's interactive! 🕹️

<div id="loadingBar">
        <progress id="bar" value="0" max="100">0</progress>
</div>
<div class="network" id="small-network"></div>
<script type="text/javascript">
        fetch('/assets/data/smallNetwork.json')
            .then(res => res.json())
            .then(({ nodes, edges }) => {
                const container = document.getElementById('small-network');
                const data = {
                    nodes: new vis.DataSet(nodes),
                    edges: new vis.DataSet(edges)
                };
                const options = {
                    interaction: {
                        dragNodes: true,
                        dragView: false,
                        zoomView: true
                    },
                    layout: {improvedLayout: true},
                    physics: {
                        enabled: true,
                        solver: 'forceAtlas2Based',
                        stabilization: { iterations: 150 }
                    },
                    nodes: {
                    shape: 'dot',
                    scaling: {
                    min: 5,
                    max: 30,
                    },
                    font: {
                        color: '#000',
                        size: 18,
                        face: 'arial'
                        },
                    color: {
                        border: '#5b5b5b',
                        background: '#000',
                        highlight: {
                            border: '#000',
                            background: '#c20000'
                        },
                    }}
                };
                const network = new vis.Network(container, data, options);
                network.on("stabilizationProgress", function (params) {
                    let progress = 100 * (params.iterations / params.total);
                    document.getElementById("bar").value = progress
                    document.getElementById("bar").innerHTML = progress
                });
                network.once("stabilizationIterationsDone", function () {
                    document.getElementById("loadingBar").style.opacity = 0;
                    setTimeout(function () {
                        document.getElementById("loadingBar").style.display = "none";
                    }, 500);
                });
            });

</script>

Great! We're starting to see some clusters emerge! The arrows indicate who appears in whose definition:

<center><code>twisting</code> ⟹ <code>worm</code></center>
<br>
This means _"twisting"_ appears in the definition of _"worm"_.

I pre-computed the above graph so that it loads faster, which will come in handy for the full results below.

### A month later: optimising, hacking & crying

Future Petar here. On that beautiful Sunday morning everything indicated that I was going to finish this before noon, just in time to go out and enjoy a nice day at the beach. What a fool I was. Apparently, visualising 85441 nodes and 384717 edges is more computationally expensive than landing on the moon. I spent a few more Sundays trying to render this giant network...

**TLDR**

❌ What didn't work:

- loading everything at once (23MB of nodes and edges) crashes the server
- loading in batches also crashes the server
- waiting for the network to stabilise before adding a new batch takes an "infinite" amount of time since it gets slower with each batch
- tuning the physics parameters (this did result in some improvement but not enough to solve the problem)

I wish the batched approach worked because it resulted in some cool behaviour. See the below (sped up) video:

<video controls preload="none" style="width:100%;height:auto;display:block;">
  <source src="/assets/videos/word-chains.mp4" type="video/mp4">
</video>
<br>

✅ What (kind of) worked:

- loading the most heavily connected nodes first **with physics off**, then letting the network stabilise
- zooming out the canvas before turning on physics

Unfortunately this approach also immediately starts to chug, even with just ~7% of all nodes and ~3% of all edges, but if you wait ~2 minutes you get a semi-usable network. Interactivity is choppy but, hey, it works.

## Final results

Here's the precomputed network for 5839 most-connected words (10000 edges) after a few minutes of stabilisation. Give it a sec to load.
This one is also interactive, but you'll notice it's not as "floaty" as the sample earlier; that's because `physics` have been turned off.

<div class="network" id="largeNetwork"></div>
<script type="text/javascript">
        fetch('/assets/data/largeNetwork.json')
            .then(res => res.json())
            .then(data => {
                const nodes = new vis.DataSet(data.nodes);
                const edges = new vis.DataSet(data.edges);
                const container = document.getElementById('largeNetwork');
                const networkData = { nodes, edges };
                const options = {
                    physics: { enabled: false },
                    layout: { improvedLayout: false },
                    nodes: {
                        shape: 'dot',
                        scaling: {
                            min: 1,
                            max: 10,
                            label: {
                                min: 10,
                                max: 18,
                                drawThreshold: 1,
                                maxVisible: 20
                            },
                        },
                        color: {
                            border: '#5b5b5b',
                            background: '#000',
                            highlight: {
                                border: '#000',
                                background: '#c20000'
                            },
                        },
                        shadow: false
                    }
                }; // your options here
                network = new vis.Network(container, networkData, options);
            });

</script>
<br>
I am disappointed I didn't get to load the entire network but I am kind of tired (and bored) of this side project -- I first jotted this idea down back in 2021 -- better to publish it now rather than never.
With a bit more tinkering I think I could get this to work and also look into some questions such as "what's the longest chain?". If anyone has any ideas on how to improve the performance, here's the Github [repo](https://github.com/petargyurov/word-chains).
Thanks for reading!

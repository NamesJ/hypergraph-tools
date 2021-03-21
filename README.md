# hypergraph-tools
A collection of tools for working with hypergraph data structures


# Summary
| Name | Last Active | Described Purpose | Language(s) | Link |
| ---- | ----------- | ----------------- | ----------- | ---- |
| yamafaktory / hypergraph | 4 months | hypergraph data structure library | Rust | [repo](https://github.com/yamafaktory/hypergraph) |
| jinhuang / hyperx | 6 years | scalable framework for hypergraph processing and learning algorithms | Scala | [repo](https://github.com/jinhuang/hyperx) |
| isislab-unisa / hypergraphs-plot | 2 years | hypergraph visualization library | JavaScript | [repo](https://github.com/isislab-unisa/hypergraphs-plot) |
| bnolan / hypergraph.js | 10 years | hypergraph library as part of some work on an AI chatbot, attempts to mimick the API of hypergraphdb | JavaScript, CofeeScript | [repo](https://github.com/bnolan/hypergraph.js) |
| hypergraphdb | 3 years | general purpose open-source data storage mechanism with several application components implemented | Java* | [website](http://www.hypergraphdb.org/)

---

# yamafaktory / hypergraph

Hypergraph is data structure library to create a directed hypergraph in which an hyperedge can join any number of vertices.

This library allows you to:

-   represent **non-simple** hypergraphs with two or more hyperedges containing the same set of vertices with different weights
-   represent **self-loops** —i.e., hyperedges containing vertices directed to themselves one or more times
-   represent **unaries** —i.e., hyperedges containing a set with a unique vertex
-   output a representation of a hypergraph using the [Graphviz dot format](https://graphviz.org/doc/info/lang.html)

---

# jinhuang / hyperx

A scalable framework for hypergraph processing and learning algorithms. HyperX is built upon Apache Spark and inspired by its graph counterpart, GraphX.

When processing a hypergraph (where an edge contains arbitrary number of vertices), instead of converting the hypergraph to a bipartite and employing GraphX to do the tricks, HyperX directly operates on a distributed hypergraph representation. By carefully optimizing the hypergraph partitioning strategies, the preliminary exprimental results show that HyperX is able to achieve a 49 speedup factor on the hypergraph random walks upon the bipartite GraphX solution.

A paper describing the details is now under review for ICDM 2015. A technical report can be found at [iojin.com | Hyperx Report](http://iojin.com/resources/hyperx_report.pdf).

---

# isislab-unisa / hypergraphs-plot

hypergraphs-plot is a js library to visual hypergraphs.

## Usage

To visualize a simple hypergraph, just define the nodes, the hyperlinks and the weight of each node in their respective hyperlinks.

```
var graph={}
graph.nodes= [
    {"id":"1" , "links":["1","2","3"]},
    {"id":"2" , "links":["1","2"]},
    {"id":"3" , "links":["2"]},
    {"id":"4" , "links":["2"]},
    {"id":"5" , "links":["2"]}
];
graph.links= [
    {"id":"1", "nodes": ["1","2"]},
    {"id":"2", "nodes": ["1","2","3","4","5"]},
    {"id":"3", "nodes": ["1"]}
];
graph.nodelinks= [
                {"node":"1","link":"1","value":"1"},
                {"node":"1","link":"2","value":"1"},
                {"node":"1","link":"3","value":"1"},
                {"node":"2","link":"1","value":"1"},
                {"node":"2","link":"2","value":"1"},
                {"node":"3","link":"2","value":"1"},
                {"node":"4","link":"2","value":"1"},
                {"node":"5","link":"2","value":"1"}
];
```

Then plot the hypergraph with one of the following functions, based on the type of visualization you want.

```
hgColorEdgePlot(graph: graph)

hgRadalPlot(graph: graph)

hgVennNodesPlot(graph: graph)
```

### with Julia

You can also use this library with Julia on Jupyter Notebook, thanks to the simple integration with the library [SimpleHypergraphs.jl](https://github.com/pszufe/SimpleHypergraphs.jl).

Check the [example\_notebook](https://nbviewer.jupyter.org/github/isislab-unisa/hypergraphs-plot/blob/master/example_notebook.ipynb) for more details.

---

# bnolan / hypergraph.js

A [hypergraph](http://en.wikipedia.org/wiki/Hypergraph) library in Javascript, part of some work on an AI chatbot. I've tried to copy the API of [hypergraphdb](http://www.hypergraphdb.org/). The graph has tests in Jasmine.

## Usage

```
graph = new HyperGraph

dog = graph.add(new Vertex("dog"))
cat = graph.add(new Vertex("cat"))
animal = graph.add(new Vertex("animal"))

edge = graph.addEdge(new Edge([dog, animal]));
edge = graph.addEdge(new Edge([cat, animal]));

graph.getEdgesForVertex('animal') => [Edge([animal, cat]), Edge([animal, dog])]

graph.getVertex("dog") => Vertex(...)
```

---

# HyperGraphDB

**HyperGraphDB** is a general purpose, open-source data storage mechanism based on a powerful knowledge management formalism known as _directed hypergraphs_. While a persistent memory model designed mostly for knowledge management, AI and semantic web projects, it can also be used as an embedded object-oriented database for Java projects of all sizes. Or a graph database. Or a (non-SQL) relational database.

Read Alex Popescu's [HyperGraphDB interview](http://nosql.mypopescu.com/post/942594519/what-is-hypergraphdb) with Borislav Iordanov for a high-level overview.

Watch Borislav Iordanov's [HyperGraphDB Presentation at StrangeLoop 2010](http://www.infoq.com/br/presentations/hypergraphdb-nosql-grafos).

Watch a presentation by Victor Puente (in Portuguese) given at Sao Paulo TDC conference: [http://www.infoq.com/presentations/HyperGraphDB](http://www.infoq.com/presentations/HyperGraphDB)

### Feature Summary

-   Powerful data modeling and knowledge representation.
-   Graph-oriented storage.
-   N-ary, higher order relationships (edges) between graph nodes.
-   Graph traversals and relational-style queries.
-   Customizable indexing.
-   Customizable storage management.
-   Extensible, dynamic DB schema through custom typing.
-   Out of the box Java OO database.
-   Fully transactional and multi-threaded, MVCC/STM. Non-blocking concurrent writes and reads!
-   P2P framework for data distribution.

### Application Components

Besides covering persistence of Java objects, the core database engine targets exclusively the implementation of generalized, typed, directed hypergraphs. As a meta-model those are pretty powerful and subsume most data models. But practical applications are built within a specific domain and sometimes follow an existing industry standard.

HyperGraphDB application components implement various domain models, standards, algorithms and domain-specific tools, taking advantage of its generality. Every entity in those components is ultimately a HyperGraphDB atom, which makes it possible to integrate and compose them naturally.

| Component | Description |
| --------- | ----------- |
| [JSON](http://www.hypergraphdb.org/?page=Json&project=hypergraphdb) | Implementation of [JSON](http://json.org) storage as a hypergraph - JSON structures as graphs rather than blobs as commonly implemented in so called "document-oriented" database. |
| [WordNet](http://www.hypergraphdb.org/?page=WordNet&project=hypergraphdb) | Representation of the lexical WordNet database from Princeton. |
| [TopicMaps](http://www.hypergraphdb.org/?page=TopicMaps&project=hypergraphdb) | Implementation of the Topic Maps 1.0 standard. |
| [RDF via Sail](http://www.hypergraphdb.org/?page=SesameSail&project=hypergraphdb) | Implementation of the RDF standard using the [openRDF.org](http://www.openrdf.org) Sesame framework. |
| [OWL 2.0](http://www.hypergraphdb.org/?page=Home&project=owl) | Full implementation of the OWL 2.0 standard with distributed versioning and a [Protege](http://protege.stanford.edu) plugin. |
| [Protege Plugin](http://www.hypergraphdb.org/?page=ProtegePlugin&project=hypergraphdb) | Integration of HyperGraphDB backed ontology storage into the popular [Protege](http://protege.stanford.edu) ontology editor. Full GUI support for the distributed version control management with pull, push, commit, revision graph, history and everything you would expect from a modern version control system. |
| [TuProlog](http://www.hypergraphdb.org/?page=TuProlog&project=hypergraphdb) | Integration with the TuProlog interpreter for reasoning over hypergraphs through Prolog. |
| [XmlSchema](http://www.hypergraphdb.org/?page=XmlSchema&project=hypergraphdb) | Implementation of the XML Schema standard within the HyperGraphDB type system._\[incomplete\]_ |
| [Feedforward Neural Nets](http://www.hypergraphdb.org/?page=NeuralNets&project=hypergraphdb) | Implementation for a feed-forward 3-layer neural net as a hypergraph |
| [Distributed Dataflow](http://www.hypergraphdb.org/?page=DataFlow&project=hypergraphdb) | Flow-based programming in Java based on a HyperGraphDB representation and using its P2P framework._\[unreleased\]_ |

*All those components are implemented as [HyperGraphDB Applications](http://www.hypergraphdb.org/?page=HyperGraphDBApplications&project=hypergraphdb)*

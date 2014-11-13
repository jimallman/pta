pta
===

A phylogeny-taxonomy alignment service for the Open Tree project.

The general idea is that the service receives a tree with leaves
mapped to Open Tree Taxonomy (OTT) ids, and returns json data required
for rendering the alignment of the tree as an interactive d3 graphic,
e.g.:

http://reelab.net/phylografter/graph/view_ott/1

# Installing

**pta** is a [web2py](www.web2py.com) app. This repo can be cloned
directly into web2py's `applications` directory.

## Requirements

* [graph-tool](graph-tool.skewed.de) and its dependencies
* [ivy](github.com/rhr/ivy) and its dependencies

(These may be tricky to install if you are not using Ubuntu.)

# Usage

Start the server, which will listen on localhost port 8000 by default:

```
python ./web2py.py
```

Currently the service expects an entire study nexson file to be POSTed
in a `data` parameter. For example to submit a file called `ot_20.json`:

```
curl --data-urlencode data@ot_20.json http://localhost:8000/pta/default/index.json
```

The response will be json data object with a key `treeids` mapping to
a list (possibly empty) of tree id values corresponding to trees in
the nexson file that were processed. The phylogeny-taxonomy alignment
data can be retrieved from the json object using these tree ids as
keys.

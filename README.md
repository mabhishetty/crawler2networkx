# crawler2networkx
A module that represents an instance of the Crawler class as a 'NetworkX' digraph
These objects (instances of Crawler class) are generated by the 'crawler_f1.py' script, accessible here: https://github.com/mabhishetty/CrawlerFirstRelease

## Motivation:

Although instances of class Crawler contain all the information necessary to understand the network, reading the text alone is not very illustrative.
Particularly when visiting large numbers of websites, you might be interested in seeing which links are common between visited sites.
Working this out by reading the lists of links from each visited site would be cumbersome - this is why we need a graphical representation.
This has been included as a separate repository because the function stands alone. If other scripts generate instances of Crawler then they too may use this module to draw the graphs.

## Structure:

A very simple script, a summary of the structure is:
- Begin loop
  - Take a visited site
  - Add a node for this site
  - Add nodes for each of the other sites in the links, with appropriate colour, shapes and tooltip links
  - Add directed edges between the visited site and each of those links
- Repeat loop

## Usage:

To use this script, just: `import crawler_operations ` and run the function: `crawler_operations.crawler2networkx(crawler)`.
The function takes an instance of class Crawler and returns nothing - but does save a '.svg' file which contains the digraph.

In addition: a number of modules are required for the operation of this script.
They are:
* matplotlib.pyplot : on which NetworkX operates
* networkx : creates an empty Digraph and provides some operations for the graph
* math : from which we use a 'floor' function to round down division
* numpy : element-wise multiplication
* networkx.drawing.nx_agraph -> to_agraph : convert our networkx representation to a graph
* pygraphviz : helps with visualising graph

To install these, I ran:
* `python3.6 -m pip install matplotlib`
* `python3.6 -m pip install networkx`
For pygraphviz, install: homebrew -> graphviz -> pygraphviz. I ran:
* `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"` (installing homebrew)
* `brew install graphviz`
* `python3.6 -m pip install pygraphviz`

and if you are using Jupyter Notebook

* `sudo ipython -m pip install pygraphviz`

## Example:

Here is an example of the current output of the function:

![Image of example output](https://github.com/mabhishetty/crawler_operations/blob/main/new_test.png?raw=true)

## Known Issues/To do:

* There seems to be a problem with the colours of the node fillings: they are being overwritten when nodes have multiple connections
* The same problem is occurring with node labels - resulting in some odd numbering
* Want to add a key to explain the symbols
* Ideally there will be some interactivity in the plot where edges could be highlighted for easier understanding of the data.

## Contact:
By email: mailto:manojabhishetty@gmail.com

## Further reading:

* NetworkX documentation: 
* Graphviz documentation: https://www.graphviz.org/doc/info/attrs.html
* Very helpful stackoverflow post for the .svg code: https://stackoverflow.com/questions/39657395/how-to-draw-properly-networkx-graphs

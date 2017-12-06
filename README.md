# PyNode: Graph Theory Visualizer
<a href="http://www.alexsocha.com/pynode"><img src="http://www.alexsocha.com/images/pynode/logo.png" align="left" hspace="10" vspace="6" width="100px" height="100px"></a>
**PyNode** is a Python library for visualizing Graph Theory. It can be used to develop algorithm prototypes, or to demonstrate how algorithms work in a visual, interactive way. This is source for the online version, originally published <a href="http://www.alexsocha.com/pynode">here</a>.
<br><br>

## How it works
* When the 'Play' button is pressed, the Python code written in the editor (provided by <a href="https://ace.c9.io/#nav=about">Ace</a>) is transpiled to JavaScript (using <a href="https://github.com/mauriciopoppe/greuler">Brython</a>).
* The code is then executed instantaneously, and all API calls are added to a queue, ready to be executed sequentially.
* The API calls trigger visual animations (using a modified version of <a href="https://github.com/maurizzzio/greuler">Greuler</a>, built on <a href="https://github.com/d3/d3">D3</a> and <a href="https://github.com/tgdwyer/WebCola">WebCola</a>).

## Project structure
* **pynode_graphlib.py** - The entry point for the PyNode Graphlib API, which references all Graph Theory-related functions. These are implemented in graph_api.js.
* **pynode_core.py** - Handles the internal functions of the API, and acts as a bridge between pynode_graphlib.py and graph_api.js, allowing the API to be compatible with both the online and offline versions of PyNode.

* **/css** - Contains custom fonts and the main style sheet.
* **/images** - Contains all icons used in the interface.
* **/js** - Contains all JavaScript code.
    * **graph_api.js** - Contains all functions referenced by pynode_graphlib.py, and handles all updates made to the graph. Also communicates information back to C++ (and hence to Python) through the JavaScript console.
    * **d3_controls.js** - Handles interface events such as panning and zooming.
    * **resize.js** - Handles resizing of the window, and includes functions which manage node layout/positioning.
    * **/greuler** - The (modified) <a href="https://github.com/maurizzzio/greuler">Greuler API</a>.
    * **/cola** - The <a href="https://github.com/tgdwyer/WebCola">WebCola API</a>.
    * **/d3** - The <a href="https://github.com/d3/d3">D3 API</a>.

# BPMN_RPA
Robotic Process Automation in Windows by using Driagrams.net BPMN diagrams.

With this Framework you can draw Business Process Model Notation based Diagrams and run those diagrams with a WorkflowEngine.
It is based on the mxGraph model notation of https://app.diagrams.net/.

<h3>Content:</h3>
* [Quick Start](#Quick start)
* [Allowed Shapes](#Allowed)
* [Example](#Example)


<h4 id="Quick start">Quick start:</h4>
- Open the diagram.net (or DrawIO desktop) app
- Import the BPMN RPA Shapes ( file -> import from -> device)
- Create your Diagram in https://app.diagrams.net/ or in the Desktop application by using the BPMN_RPA Shape-set
- Set the right mappings for each shape
- Save your diagram as XML
- Run your workflow by using the WorkflowEngine

<h4 id="Allowed">Allowed Shapes:</h5>
For the Workflow engine to recognize the flow, you are restricted to use the following Shapes:
* Tasks.
Each Task must contain the following Data attributes:
** Module: This is the full path to the Python file that contains your Class and/or function.
** Class: for reference to the Class to use in the Module.
** Function: The name of the Function to Call.
** Mapping: The mapping of the input parameters to the output of the previous task.
* GateWays:
** For now you can only use the Exclusive Gateway. This Gateway has to have a Data attribute named 'Type' with the value 'Exclusive Gateway'.
* Sequence flow arrow. If the Sequence flow arrow is originating from an Exclusive Gateway, the Sequence flow arrow must have a value of 'True' or 'False'.


<h4 id="Example">Example:</h4>

```Python
engine = WorkflowEngine("c:\\\python\\\python.exe")
doc = engine.open("test.xml")
steps = engine.get_flow(doc)
engine.run_flow(steps)
```

You can download the DrawIO desktop version [here](https://github.com/jgraph/drawio-desktop/releases)

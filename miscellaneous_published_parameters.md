# Miscellaneous Published Parameters

Self-Serve parameters can include any regular parameters, not just ones that are specific only to a Data Download setup

Any parameter in FME can be published and presented to the user as a choice to be made when running a workspace. They don’t have to be specifically related to the Data Download service.

**Finding a Parameter**

Parameters are located in the Navigator window (usually on the left-hand side of FME Workbench).

As you can see, there are parameters for the source data location (1) and the destination data dataset (2), which is the one that the Data Download service overrides. There are also general Reader and Writer parameters (3) and parameters for transformers (4)

**Publishing a Parameter**

Parameters are published by right-clicking on them and choosing “Create User Parameter”.

For example, here a workspace author is about to publish a parameter on the LabelPointReplacer transformer.

When the workspace is run the end-user will now be able to decide what size they want labels to appear as.

The author gets to choose the type of parameter (in this case a floating point number), the user prompt, and the default value.

**Using a Parameter**

A User Parameter that is published becomes available to the end-user at run-time.

In FME Workbench, you would select Run > Prompt and Run from the menubar, to see these parameters. There is also a toolbar button and a keyboard shortcut (Ctrl+R).

In FME Server, these parameters become available on the Configuration page of a service, as seen in the Chapter 2 exercises.

**Key Parameter Types**

Two key parameter types for a self-serve setup are “Choice with Alias” and “Scripted”.

Choice with Alias parameters are where the user is presented with a choice, each of which returns a different value to FME.

For example, here the author wishes the user to select the height of labels to be created in the output dataset.

The user is presented with the list of (more intuitive) options on the right, but the value returned to FME will be the (more useful) number on the left.

This parameter type is also very useful for some Data Download specific tasks, as we’ll see shortly.

Scripted parameters are a way to incorporate a Python or Tcl script into the generation of a parameter value.

This script can include references to other user parameters, meaning one parameter value can be calculated based on the value of another. Parameters referred to in the scripts are generally published parameters that accept input from the user.

So, user input can be accepted from one parameter, and this input processed using a script, in order to produce the actual information required by the workspace.
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
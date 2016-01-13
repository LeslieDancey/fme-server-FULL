# Layer Selection and Handling

Layer (Feature Type) flexibility can be achieved through the Feature Types to Read parameter.

There is no single method by which users might wish to select data or features. Every organization implementing FME Server lets users select data in different ways.

However, spatial data is often organized in layers (groups, classes, categories, feature types) and a common way that users will wish to choose data is on a layer-basis.

**Selecting Layers**

Allowing users to select data by layer is the simplest solution available in an FME Workspace, although in many situations users will wish to select data not just by layer, but by a mix of criteria.

Allowing choice by layer alone can be handled easily if the layers correspond to Feature Types in the source data.

Each reader in FME has a parameter called Feature Types to Read. When this parameter is published, the workspace will accept a list of layers to read from the user.

The publishing dialog for Feature Types to Read is different because FME can automatically scan the workspace and provide a list of available feature types.

Additionally, the Use Alternate Display Name allows the author to publish alternate names (for example Road Centrelines instead of RdCtrLns) in a similar way to the “Choice with Alias” parameter.
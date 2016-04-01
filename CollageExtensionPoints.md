## Introduction ##

Collage is based on Eclipse [GEF](http://www.eclipse.org/gef/gef_mvc/index.php), a Model-View-Controller framework for developing graphical editors. To extend Collage, clients can contribute new types of shapes to the Collage model, together with controllers ("edit parts", in GEF terminology) that handle a shape's presentation in the view and respond to modification requests. Clients can also extend Collage with GEF tools that allow the user to create and manipulate elements in Collage layers.

**Note that Collage is currently in an early stage of development; extension points and public APIs are subject to change.**

## Model contributions (`org.eclipselabs.collage.model`) ##

The `org.eclipselabs.collage.model` extension point allows you to contribute shape elements (subclasses of <a href='http://code.google.com/a/eclipselabs.org/p/collage/source/browse/org.eclipselabs.collage/src/org/eclipselabs/collage/model/Shape.java'><code>org.eclipselabs.collage.model.Shape</code></a>) to Collage's model. The contributed elements can be added to Collage's layers. Implementers of contributed shape elements should ensure that the classes they create can be serialized and deserialized using [JAXB](http://java.sun.com/xml/downloads/jaxb.html); Collage model elements are serialized when Collage exports layers and when Collage saves its model state upon Eclipse shutdown, and deserialized when Collage imports layers and when Collage loads its model state during Eclipse startup. Contributed shape elements should be accompanied by a GEF graphical edit part that handles the shape element in the editor view, and optionally by a GEF tree edit part that handles the shape element in the Collage Layers tree view.

Clients using the `org.eclipselabs.collage.model` extension point should provide:

  * One `modelValue` element, the `value` attribute of which should be a valid [OSGi version identifier](http://www.osgi.org/javadoc/r4v43/core/org/osgi/framework/Version.html) giving the current version of the contributed model. (This is not necessarily the same as the current version of the client plugin, and should only be updated when the contributed model actually changes.)
  * One or more `shape` elements, with the following attributes:
    * `name`: Optional string giving a human-readable name for the model element.
    * `modelClass`: The model element class (must extend <a href='http://code.google.com/a/eclipselabs.org/p/collage/source/browse/org.eclipselabs.collage/src/org/eclipselabs/collage/model/Shape.java'><code>org.eclipselabs.collage.model.Shape</code></a>)
    * `controllerClass`: The controller class (GEF edit part) for this type of model element (must implement <a href='http://help.eclipse.org/galileo/index.jsp?topic=/org.eclipse.gef.doc.isv/reference/api/org/eclipse/gef/EditPart.html'><code>org.eclipse.gef.EditPart</code></a>)
    * `treeControllerClass`: Optional tree controller class (GEF tree edit part) for this type of model element (must implement <a href='http://help.eclipse.org/galileo/index.jsp?topic=/org.eclipse.gef.doc.isv/reference/api/org/eclipse/gef/TreeEditPart.html'><code>org.eclipse.gef.TreeEditPart</code></a>)

### Usage example ###

```
   <extension
         point="org.eclipselabs.collage.model">
      <modelVersion
            value="0.1.0">
      </modelVersion>
      <shape
            controllerClass="org.eclipselabs.collage.text.parts.TextNoteEditPart"
            modelClass="org.eclipselabs.collage.text.model.TextNoteShape"
            name="Text"
            treeControllerClass="org.eclipselabs.collage.colourpicker.parts.tree.ColouredShapeTreeEditPart">
      </shape>
   </extension>
```

## Tool contributions (`org.eclipselabs.collage.tools`) ##

The `org.eclipselabs.collage.tools` extension point allows you to contribute GEF tools (classes which implement <a href='http://help.eclipse.org/galileo/index.jsp?topic=/org.eclipse.gef.doc.isv/reference/api/org/eclipse/gef/Tool.html'><code>org.eclipse.gef.Tool</code></a>) to Collage. Tools let the user create and manipulate Collage GEF shapes. A tool contributed via this extension point will automatically be given a button in the Collage toolbar which activates the tool.

Clients using the `org.eclipselabs.collage.tools` extension point should provide:

  * One or more `tool` elements, with the following attributes:
    * `name`: Description of the tool (will be used for toolbar button tooltip)
    * `icon`: Path to an icon for the tool (will be used for toolbar button image)
    * `class`: Tool class (must implement <a href='http://help.eclipse.org/galileo/index.jsp?topic=/org.eclipse.gef.doc.isv/reference/api/org/eclipse/gef/Tool.html'><code>org.eclipse.gef.Tool</code></a>)

### Usage example ###

```
   <extension
         point="org.eclipselabs.collage.tools">
      <tool
            class="org.eclipselabs.collage.text.tools.TextShapeCreationTool"
            icon="icons/text.gif"
            name="Add a text note">
      </tool>
   </extension>
```

## Toolbar contributions (`org.eclipselabs.collage.toolbar`) ##

The `org.eclipselabs.collage.toolbar` extension point allows you to contribute buttons and other widgets to the Collage toolbar. This extension point is intended to allow clients to provide toolbar elements that do not activate a GEF tool (e.g., a colour picker).

Clients using the `org.eclipselabs.collage.toolbar` extension point should provide:

  * One or more `contribution` elements, with the following attributes:
    * `name`: Optional description of the contribution.
    * `class`: Contribution class (must implement <a href='http://code.google.com/a/eclipselabs.org/p/collage/source/browse/org.eclipselabs.collage/src/org/eclipselabs/collage/ui/ICollageToolBarContributor.java'><code>org.eclipselabs.collage.ui.ICollageToolBarContributor</code></a>)
    * `position`: Optional integer hint for where this widget should be positioned in the toolbar section allocated to `org.eclipselabs.collage.toolbar` extension point contributions. Higher values place the widget further to the right.

### Usage example ###

```
   <extension
         point="org.eclipselabs.collage.toolbar">
      <contribution
            class="org.eclipselabs.collage.draw.toolbar.LineWidthToolBarContribution"
            name="Line width widget"
            position="99">
      </contribution>
   </extension>
```
**As Google Code is shutting down, Collage will be moving to GitHub: https://github.com/abradley/collage**


---


<img src='http://collage.eclipselabs.org.codespot.com/files/collage-rectangle-markup-430-padded.png' align='right' width='440' alt='Screenshot of Collage text, freehand sketch, rectangle and ellipse markup tools used to highlight a bug' height='309' />

## About Collage ##

Collage is a framework that lets you **create and edit layers of graphical shapes on top of your code** in an Eclipse editor. Collage is based on the powerful Eclipse [Graphical Editing Framework](http://www.eclipse.org/gef/), and its features include the following:

  * Your original source code is **not modified** in any way. Collage data is stored separately in the workspace's plugin state location.
  * Shapes can be moved, resized and deleted; shape operations can be undone and redone.
  * As in graphics software like Adobe Photoshop or GIMP, layers can be moved above and below other layers and hidden from view. They can also be exported to and imported from XML files.
  * Shape properties can be viewed and edited in the Eclipse Properties view.
  * Shapes are positioned based on code line numbers, so their rendering can be adjusted when code blocks are expanded and collapsed. Collage also attempts to reposition shapes when lines are added to or removed from the code underneath.

The Collage framework allows developers to contribute new shapes and tools through its [extension points](CollageExtensionPoints.md).

### Code Markup Tools ###

Have you ever wanted to write or draw on your code - perhaps to comment on problematic areas during a code review, or to plan out a large refactoring, or to figure out how an algorithm is supposed to work? Do you use Eclipse to teach classes or give presentations that involve coding, and wish you had some way to mark up the code on the fly? The **Collage Code Markup Tools** let you annotate code in your Eclipse editor with ink drawings, text notes and basic geometric shapes (see the screenshot above.)

**For a more detailed look at the user interface for Collage and the Code Markup Tools, as well as some usage tips, see the "[Using Collage](UsingCollage.md)" wiki page.**

## Installation ##

The Collage framework and code markup tools can be installed from Eclipse Marketplace by dragging this button into a running Eclipse workspace:

<a href='http://marketplace.eclipse.org/marketplace-client-intro?mpc_install=378587' title='Drag and drop into a running Eclipse Indigo or Juno workspace to install Collage Framework and Code Markup Tools'><img src='http://marketplace.eclipse.org/misc/installbutton.png' /></a>

They can also be installed from the following Eclipse update site:

> http://collage.eclipselabs.org.codespot.com/git/updates-release/

Collage has been tested on Eclipse 3.7 (Indigo) and 4.2 (Juno) on Ubuntu Linux 12.04 and Windows 7; on Eclipse 4.2 on Mac OS X; on Eclipse 4.3 (Kepler) on Ubuntu Linux 12.04; and on Eclipse 4.4 (Luna) on Ubuntu Linux 14.04.

Bug reports, suggestions, and general feedback are very welcome. Bugs can be reported using the "Issues" tab above, and other feedback can be directed to the author, Alex Bradley (`a.bradley at alumni dot cs dot ubc dot ca`).

<wiki:gadget title="" url="http://eclipse-marketplace-gadgets.googlecode.com/svn/files/favorite/v1/gadget.xml" width="200" height="70" up\_nodeNo="378587" border="0" />
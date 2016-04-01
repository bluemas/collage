## Version 0.1.1 (August 16, 2012) ##

  * Bug fixes:
    * Text note text colour should always be black. Using the tooltip foreground colour gave white text on white background in Ubuntu 12.04's default theme. ([63f25e6b74c2](http://code.google.com/a/eclipselabs.org/p/collage/source/detail?r=63f25e6b74c2330926bef63945903cff8e21d3c3))
    * Adding/removing lines in the underlying code was only shifting shapes in the active layer. ([b501e52502f4](http://code.google.com/a/eclipselabs.org/p/collage/source/detail?r=b501e52502f40897432efc7130991c5d2abd08d5))
    * Disallow undo/redo of shape create/delete/move/resize commands unless shape's parent layer has been created and has not been deleted. ([2fdc37435d1f](http://code.google.com/a/eclipselabs.org/p/collage/source/detail?r=2fdc37435d1f8d843f29acd835ed71f5a5cbbd23))
    * Properties view didn't pick up Collage element selections correctly in Eclipse Juno. ([issue 1](https://code.google.com/p/collage/issues/detail?id=1), [29db9bc1750d](http://code.google.com/a/eclipselabs.org/p/collage/source/detail?r=29db9bc1750d9c62df2a6bffbcea5b6a58a71435))

## Version 0.1.0 (June 11, 2012) ##

  * Initial release.
# Glyph

**[Original code/repository, on google code](https://code.google.com/p/glyph/), by: Chandler Armstrong (omnirizon)**

**Code on this git, with changes, by me: Lucas de Morais Siqueira (LukeMS)**

##Description##

Glyph is a library for manipulating text and printing it to a pygame window.

So what? there are about a million pygame libraries to do that already.

Glyph is different for a few reasons:

1. glyph provides a within string literal mini-language for text manipulation. you can use the mini-language to indicate what you want exactly where you want it, all right within the string literal.

2. glyph provides typesetting like functionality: positioning text, wrapping text, justifying text, scrolling text, switching font, text color, background color, even inserting images into text

3. glyph provides 'linked' text: text that returns a value whenever the mouse is hovering over it. this can be used to route the user around your program, or provide tooltips.

One simple object, the Glyph object, provides all this functionality. How? because Glyph interprets a mini-language, provided in string literals, that indicates how the Glyph object should treat text.

##Changes##

Glyph mark-up language: glyph accepts special commands given through markup in the text. the language can be used to change font, size, color, background color, and denote text as 'linked'.

The commands given in the mark-up language are called 'environments'. all text inside of an environment is treated according to the environemnt type. for example, text can be italicized by starting an italics environment, and all text inside the environment will be blitted to the screen as italicized.

Environments are started with a left curly bracket '{', and terminated with a right curly bracket '}'. the first text following the left curly bracket is the type of the environment. currently, the following types are available:

* font - tells glyph that this font should be used in this environment
* color - tells glyph that this color should be used in this environment
* bkg - tells glyph that this background color should be used in this environment
* link - tells glyph that this text is 'linked'

Environments can be nested. when two environments of the same type are nested (e.g. two font environments), the most recent will take precedence.

Immediately following the environment type are the arguments. the arguments specify what the environment will do to the text within it. arguments must be seperated with commas and terminated with a semi-colon. below are the environments and the arguments they expect:

* font - file, size
file is the path to the directory containing the font file
size will be the size of the font

* color - R, G, B
R, G, B are the red, green, blue values, respectively.

* bkg R, G, B
R, G, B are the red, green, blue values, respectively.

Below are some example environments:

* glyph can {font fonts\\silkscreen_bold, 8;bold} text for you.
* it can also {color (255, 0, 0);color} text for you.
* it can even {font fonts\\silkscreen_bold, 8;nest these {color (255, 0, 0);features} for you}.

The environments and arguments can become cumbersome to type out. fortunately, glyph can store macros that will allow long rules to be abbreviated. to do this, simply add an entry to the glyph.Macro dictionary, with the key being the abbreviation, and the value being the environment type and environment:

* glyph.Macro['b'] = ('font', Font(silkscreen_bold, 8))
* glyph.Macro['red'] = ('color', (255, 0, 0))

With macros set, simply use the abbreviation at the start of environments rather than the name and argument list:

Glyph can {b;bold} text for you.
It can also {red;color} text for you.
It can even {b;nest these {red;features} for you}.

##Links##
* [Pygame project page](http://www.pygame.org/project-Glyph-1002-2817.html)
* [Google code old repository](https://sourceforge.net/projects/pyglyph/files/)
* [Screenshot](http://www.pygame.org/shots/1002.png)

# scala-mode2 -- A new scala-mode for emacs

This is a new scala major mode for emacs. It is a complete rewrite based on scala language specification 2.9.

The mode intends to provide the basic emacs support, including
- indenting of code, comments and multi-line strings
- motion commands
- highlighting

Currently the indenting of code has been finalized. Highlighting is
under work. No scala specific motion commands have been added, but
standard emacs motions work ofcourse.

## Setting the mode up for use

1. Download the files to a local directory, you can use the 'git'
command. This will create a directory called scala-mode2.
```
> git git://github.com/hvesalai/scala-mode2.git
```

2. Include the following in your '.emacs'  file
```
(add-to-list 'load-path "/path/to/scala-mode2/")
(require 'scala-mode)
```

3. That's it. Next you can start emacs and take look at the
customization menu for scala-mode.

Free emacs tip: if you are using emacs from a text terminal and you
are having trouble with colors, try setting the customization variable
'frame-background-mode' to 'dark' (use M-x customize-variable).

## Indenting modes

The indenting engine has three modes for handling run-on lines. The
'reluctant' (default) mode is geared toward a general style of coding
and the 'eager' for strictly functional style. A third mode called
'operators' is between the two.  You can configure the mode from the
mode customization menu (use M-x customize-mode when in scala-mode).

The difference between the modes is how they treat run-on lines. For
example, the 'eager' mode will indent 'map' in the following code

```
val x = List(1, 2, 3)
  map(x => x + 1)
```

The 'operators' and 'eager' modes will indent the second row in the
following code:

```
val x = 20 
  + 21
```

The 'reluctant' mode (default) will not indent the line in either
case. 

You can use empty lines in 'eager' mode to stop it from indenting a
line. For example

```
val x = foo("bar")
           ("zot", "kala") // indented as curry

val y = foo("bar")

("zot", "kala")
```

However, in all three modes pressing tab repeatedly on a line
will toggle between the modes.

## Motion

Basic emacs motion will work, including movement over expressions (M-C-f, M-C-b).

## Code highlighting

Highlighting code is still a work in progress. Feedback on how it
should work is welcomed as issues to this github project.

## Other features
- supports multi-line strings
- highlights only properly formatted string and character constants
- fills scaladoc comments properly (TODO row comments)

## Future work

- indent scaladoc left margin correctly
- indenting a row should remove trailing whitespace and converts tabs to spaces
- indent and fill multi-line strings with margin correctly
- movement commands to move to previous or next definition (val,
  var, def, class, trait, object)
- highlight headings and annotations inside scaladoc specially (use underline for headings)
- highlight variables in string interpolation (scala 2.10)

All suggestions and especially pull requests are welcomed in github
https://github.com/hvesalai/scala-mode2

## Credit

Mode development: Heikki Vesalainen

Contributors and valuable feedback:
- Ray Racine
- Eiríkr Åsheim (aka Erik Osheim)
- Seth Tisue
# sgrtab
Display standard/custom table of SGR combinations (terminal colors)

https://github.com/avih/sgrtab

`sgrtab` is a small shell script(1) which renders a standard or custom table of
SGR combinations - _Select Graphic Rendition_ terminal codes.

By default it renders the standard table with ` gYw ` using all the colors,
i.e. columns (X) are the different background colors, rows (Y) are different
foregrounds, and each row is displayed twice (Z): normal or bold.

However, all the values are fully customizable: the values of each axis,
the sample text at the cells, and it's also possible to use global modifiers
which affect all table cells, for instance adding "2" which is the SGR code for
"dim", or even 2 and 7 to make all cells dim and inverted.

But it's not limited to the normal colors. You could use 256-colors values
at the axes, or true colors, or even not use colors and instead display
combinations of different attributes (bold, dim, underline, etc).

All this while keeping the table nicely aligned and being reasonably quick.

```
Usage: sgrtab [[-t] txt [-w W]] [-g g1 g2..] [-[xXyYzZ] s1 s2..] ...
Display standard/custom table of SGR combinations (terminal colors).
- The Z axis repeats each row with the different z values.
- Default: X: 40-47 (bg colors), Y: 30-37 (fg), Z: -/1 (normal/bold).

txt   : Sample text. The default is ' gYw '.
W     : On-screen width of txt (work around locale/alignment issues).
g1..  : Global individual SGR modifiers added to all table cells.
s1..  : Axis SGR sequences. Use '-' as an empty sequence.
-[xyz]: s1 s2 ... are added to the axis. -[XYZ]: replace axis values.
Each cell uses an SGR sequence of: [x-seq][y-seq][z-seq][g1;g2...] .
Example: sgrtab -g 3 -y 7 '33;7' -X '- 2 4 48;5;40'
         > global italic (3), two extra rows (-y), four columns (-X).
```

(1) Other than the use of `local` for function variables, it should also be
POSIX compliant.

# Screenshots

![sgrtab screenshots using xterm](https://raw.githubusercontent.com/avih/auxiliary/master/images/sgrtab/sgrtab-examples.png)
# sgrtab
Display standard/custom table of SGR combinations (terminal colors)

https://github.com/avih/sgrtab

`sgrtab` is a POSIX-compliant shell script which renders a standard or custom
table of SGR combinations - _Select Graphic Rendition_ terminal codes.

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
Usage: sgrtab [[-g] G1..] [-m MODE] [-t TXT [-w W]] [-[xXyYzZ] S1..] ...
Display terminal colors (SGR sequences) in various modes.
  MODE : table(default)/256/true/info
  G1.. : Global individual SGR modifiers added to all table cells.

-m MODE or --MODE:
  256  : 256 colors indexed palette (accepts -g, ignores others).
  true : true-colors surface (accepts -[gt], ignores others).
  info : attributes and their SGR codes (accepts -[gty], ignores others).
  table: (default) display standard/custom table of terminal colors:
   - The Z axis repeats each row with the different z values.
   - Default: X: 40-47 (bg colors), Y: 30-37 (fg), Z: -/1 (normal/bold).

TXT   : Sample text. The default is ' gYw ', or ' ' with mode 'true'.
W     : On-screen width of txt (work around locale/alignment issues).
S1..  : Axis SGR sequences. Use '-' as an empty sequence.
-[xyz]: S1 S2 ... are added to the axis. -[XYZ]: replace axis values.
Each cell uses an SGR sequence of: [x-seq][y-seq][z-seq][G1;G2...] .
Example: sgrtab -g 3 -y 7 '33;7' -X '- 2 4 48;5;40'
         > global italic (3), two extra rows (-y), four columns (-X).
```


# Screenshots

## Default mode (`table`)
![sgrtab screenshots using xterm](https://raw.githubusercontent.com/avih/auxiliary/master/images/sgrtab/sgrtab-examples.png)

## Other modes: `--info`, `--256`, `--true`
![sgrtab screenshots using xterm](https://raw.githubusercontent.com/avih/auxiliary/master/images/sgrtab/sgrtab-info-256-true.png)

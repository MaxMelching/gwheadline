# gwheadline

A gravitational-wave headline template for LaTeX documents.

## Usage

Import the package via

```tex
\usepackage{gwheadline}
```

to get access to the `\gwheadline[]{}` command. This can be used in various
ways, which are shown in the accompanying examples folder. The simplest way is
to include it as

```tex
\ihead{\gwheadline{}Other Header Text}
```

(in files that use a KOMA-script documentclass). The `fancyhdr` package can be
used in a similar way. When testing this package, this turned out to be the
most versatile (and natural) way of providing the aspired functionality.

For such an inclusion to work, the `.sty` and `.txt` files in this repository
have to be either in the same directory as the corresponding LaTeX file or in a
directory where your LaTeX distribution finds them. The location of the `.txt`
can also be given as an argument to the package (called `templatefile`).

It is possible to use any waveform you want in the headline. The only
requirement for the displaying to work properly is that the values are
between $-1$ and $+1$, and that the times are between $0$ and $1$. If you
have some GWPy ``TimeSeries`` on hand, this preparation can be done using
`signal_export` function in the accompanying python script.

***Note:*** in case the line looks misaligned in some compiler like Overleaf,
this will typically disappear in the exported pdf. I do not know why this
happens, but I have experienced it several times. You can confirm that
everything is calculated correctly by zooming in on the transitions.

### Arguments

Options can be provided both to the package and to the command itself, but
arguments given to command itself take precedence over arguments given to package.
Since there are not too many, we list them here and not in a separate pdf:

- `templatefile`: the file used for plotting. Must adhere the TikZ requirements
  on the `plot file` function: two colums of equal length, with the first one
  representing x-data and second one representing y-data. As mentioned in the
  text, for proper displaying there are constraints on the values in this file.

- `leftpadding`: how much space is left between signal start and headline start.
  Defaults to `0.45\textwidth`.

- `rightpadding`: how much space is left between signal end and headline end.
  Defaults to `0.05\textwidth`.

- `signalheight`: height of the signal (measured from zero, i.e. the total
  signal height is twice of this). Defaults to `\headheight`.

- `signalshift`: shifts the line up or down. Defaults to `-0.5em`.

- `headwidth`: width of the header. Defaults to `\textwidth`, but might be
  changed manually and in that case, the package needs to know this. Unfortunately,
  I could not find a robust manual way of getting this length (due to the many
  different possible classes and packages that could be used to control is).

- Styling: albeit not being a direct option that can be passed, it is possible
  to change the appearance of the line by editing the corresponding TikZ style:

  ```tex
  \tikzset{gwline/.style={<style options>}}
  ```

  (cf. the `examples/style_example` file).

### Examples

To see how this beamertemplate looks like and how it can be used, have
a look at the `examples` folder in this repository.

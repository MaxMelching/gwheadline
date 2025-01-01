# gwheadline

## Usage

Idea for package: provide command that can be inserted, then we are safe with different classes (KOMA can use chead, others use fancyhdr for example)

Arguments given to command take precedence over arguments given to package

for styling options, edit the `gwline` TikZ style:

```tex
\tikzset{
    gwline/.style={
		smooth,
		line width=0.42pt,
	}
}
```

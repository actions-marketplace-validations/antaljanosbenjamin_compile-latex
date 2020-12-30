# Compile latex action
This action can be used to compile latex documents with `latexmk`. The action uses an ubuntu based [docker image](https://github.com/antaljanosbenjamin/latex-extra-docker).

It calls `latexmk` in the working directory on a single tex file.
## Inputs

### `file` (required)
The LaTeX file to be compiled.

### `output-directory`
The directory for output files, relative to the root of the repository. Defaulted to `.`.
### `args`
Additional arguments to pass over to `latexmk`.

## Example usage


```
name: test
on: [push]
jobs:
  test-example:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: antaljanosbenjamin/compile-latex@master
        with:
          file: test.tex
          args: -pdf
      - run: '(test -f test.pdf && echo PDF exists) || (echo PDF does not exist && exit 1)'
```

For further examples check the [test workflow](.github/workflows/test.yml).
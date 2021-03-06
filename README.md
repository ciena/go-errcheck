# Go `errcheck` tool

## Usage

_Example using the oftee application_

```
docker run -ti --rm -v $(pwd)/src/github.com/ciena/oftee:/go/src/github.com/ciena/oftee ciena/go-errcheck
```

Any flags specified at the end of the run command will be passed to the `errcheck`
binary.

## Package specification

This container uses the following bash hack to _guess_ the packages on which
`errcheck` should be run.

```
find /go/src -name "*.go" | grep -v "\/vendor\/" | grep -v "\/\.git\/" | sed -e 's/\/[^\/]*\.go$//g' -e 's/\/go\/src\///g' | sort -u
```


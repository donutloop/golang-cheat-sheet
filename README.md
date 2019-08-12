# golang-cheat-sheet

## Go tools 

### Debugging:

Debug test files and viewing of variables possible per following command:  

```bash 
go test -c -gcflags "-N -l"
```
### Testing

The command below will create a coverage profile and open the results page in the browser.

```bash
go test -coverprofile=c.out && go tool cover -html=c.out
```

Go’s race detector is available from the Go tools via -race. go test also supports this flag and reports races.

```bash
go test -race
```
How to separate go tests by build tag

Mark your _test.go files with [**build constraints**][0]:

For instance:
```go
// +build integration

package logger_test

```
Now you can execute your integration tests with the tags flag (When you don't pass tags only all other tests will be executed!)

```bash
go test --tags=integration
```

### Benchmarking


The command below will trigger all benchmarks in your project.

```bash

go test -bench=.

```

The command below will trigger just one benchmark in your project.

```bash

go test -bench={{Name of Benchmark}}

```

### Go Mod 

#### Replace package online with local path

Example:

```go
module github.com/acme/foo

go 1.12

require (
	github.com/acme/bar v1.0.0
)

replace github.com/acme/bar => /path/to/local/bar
```

Command:

```bash
go mod edit -replace github.com/acme/bar=/path/to/local/bar
```


### GO 1.8 Features

You can build a plugin with that command below which will give you a shared object (.so) file`

```bash
go build -buildmode=plugin
```

[0]: https://golang.org/pkg/go/build/#hdr-Build_Constraints

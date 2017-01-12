# golang-cheat-sheet

## Go tools 

### Debugging:

Debug test files and viewing of varibles possible per following command:  

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

### Benchmarking


The command below will trigger all benchmarks in your project.

```bash

go test -bench=.

```

The command below will trigger just one benchmark in your project.

```bash

go test -bench={{Name of Benchmark}}

```

### GO 1.8 Features

You can build a plugin with that command below which will give you a shared object (.so) file`

```bash
go build -buildmode=plugin
```


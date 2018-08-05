Source of this tool: https://github.com/kubernetes/perf-tests/tree/master/network/benchmarks/netperf

Why created this repo:

1. Rebuild nptest Image: image from girishkalele/netperf-latest has a stepsize as 1, so it takes extremely long to finish all testcases. Now it's modified as 64.

2. Fix a bug while using MacOS: 'standard_init_linux.go:175: exec user process caused "exec format error"' is fixed by adding "env GOOS=linux GOARCH=386" in front of "go build" while compiling nptest.go.

Usage:

1. Install Go & godep
2. Clone this project under $GOPATH/src
3. Run `godep restore` in the project directory to install required libs
4. Start benchmark by run command `go run benchmarks/netperf/launch.go --iterations 1 --kubeConfig $HOME/.kube/config --image liwang0513/netperf-latest`

* Will take some time to get final results. Can speed it up by changing `mssStepSize` param under `benchmarks/netperf/nptest/nptest.go`

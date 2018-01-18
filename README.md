Source of this tool: https://github.com/kubernetes/perf-tests/tree/master/network/benchmarks/netperf

Why created this repo:

1. Rebuild nptest Image: image from girishkalele/netperf-latest has a stepsize as 1, so it takes extremely long to finish all testcases.

2. Fix a bug while using MacOS: 'standard_init_linux.go:175: exec user process caused "exec format error"' is fixed by adding "env GOOS=linux GOARCH=386" in front of "go build" while compiling nptest.go.

Usage:

$ go run ./launch.go --iterations 1 --kubeConfig $HOME/.kube/config --image liwang0513/netperf-latest

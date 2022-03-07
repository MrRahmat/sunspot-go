# sunspot-go

Sample malicious program that emulates the SolarWinds attack on build process.

1. Listen for processes that use the go compiler
2. Wait for a syscall to open a main.go file
3. Pause compiler process.
4. Modify contents of main.go, cache legitimate copy.
5. Start compiler
6. Replace contents of trojanized file with the original.

## How to use

1.  compile program
`go build .`
2.  Run app as root
3.  In another terminal compile a Go program that includes a file name of `main.go`
4.  It will inject the following `init function`
```
func init() {
	fmt.Println("Malicious code is injected by SNE!!")
}
```

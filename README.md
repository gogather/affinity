# Affinity 

Affinity is a tool for goroutine cpu core affinity binding.

## Example

```golang
func processUnit(cpuID int) chan *string {
	ch := make(chan *string, 1000)
	go func() {
		affinity.SetAffinity(cpuID)
		proc := poly.NewProcessor()
		for {
			proc.Process(<-ch)
		}
	}()
	return ch
}
```

calling `affinity.SetAffinity` in an goroutine could bind the goroutine on operation system thread (M) and binding the thread on specific cpu core.

## License

MIT License

这一节就讲了 What is  compiling? What are packages?
还有下面这些，东西其实很少，主要看下 line by line 就行了

# Hello World code line by line
```go
package main // this file belongs to package main

import "fmt" // this package contains the `PrintLn()`

func main() { // this is where the execution starts(we need to name i `main` as this is where the code starts)
  fmt.Println("Hello #90DaysOfDevOps")
}
```
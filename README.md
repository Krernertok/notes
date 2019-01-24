
# Notes for Learning Programming


## Inspiration

[Peter Norvig's Learn Programming in 10 Years](http://norvig.com/21-days.html)


## Book Notes

### Think Like A Programmer

Planning against design weaknesses:
- convoluted designs
- can'get started
- fails to test (e.g. special cases)
- overconfident
- weak area

Planning for your strengths:
- eye for detail
- fast learner
- fast coder
- never gives up
- super problem-solver
- tinkerer

Learning new languages
- take the time to learn
- start with what you know
- investigate what is different
- study well-written code


### Go in Action

Importing:
- Remote import
- Named import
    - Using blank identifier (_) so that init() functions are called

Go tools:
- go vet
- go fmt
- go get
- go test (-run="regex" - bench -benchmem)
- go doc
- godoc

Vendoring:
- Look into modules (part of go 1.11)

Slices:
- Initializing slices of slices, e.g.
    ```go
    var xxi [][]int
    xxi := [][]int{
        {1, 2, 3},
        {4, 5, 6},
    }
    ```

Types:
- Unnamed types (might be useful testing JSON), i.e.
    ```go
    t := struct{
        Name string
        Age int
    }{"Bob Brewer", 40}
    ```
- Pointers or values as receivers?
    - Think about the nature of the type!
        - "Does adding or removing something from a value of this type need to create a new value or mutate the existing one?
        - Is it primitive, i.e. like an int or string or slices?
        - Is it non-primitive like a file?

Concurrency:
- Goroutines vs. parallelism
    - Go runtime schedules goroutines against logical processors
    - 1 logical processor per OS thread
    - X threads per physical processor
    - Parallelism == at least 2 logical processors that are running on 
        separate physical processors    
- Locking
    - functions in atomic, e.g. atomic.AddInt64(*pointer, value)
    - sync.Mutex
- Channels
    - Unbuffered
    - Buffered
- The book provided three concurrency patterns

Logging:
- Custom loggers
- Flags for logging
    
Testing:
- Logging, i.e. t.Log(), with go test -v
- Mocking HTTP calls with net/http/httptest
    

## Technology-specific Notes

### PostgreSQL

You can start the database server with:
    /usr/lib/postgresql/11/bin/pg_ctl -D /var/lib/postgresql/11/main -l logfile start

## Self-reflection

- When reading new code:
    1. Don't read through it in order!
        - You don't need to understand the internals of every function in the beginning (or ever)
        - You won't remember the internals of every function (ever)
    2. It's more important to understand the bigger picture before understanding the finer details
        - Q: How do you understand the big picture as quickly as possible?
        - A: -- Ask the senior devs --

- When dealing with a technology you aren't particularly interested in (e.g. front end web):
    - Try to look deeper into the problem, past the technology
    - Try to understand what the problem is irrespective of the technology and the tech details

- When starting a new project/assignment:
    - Don't fall into the waterfall-thinking trap, i.e. trying to understand and define everything up front
    - Instead:
        1. Understand the goal
            - Why do we need this? (This should be clear.)
            - Who needs it?
            - What we need is often not clear!
        2. Plan intermediate outcomes:
            - What is the smallest/simplest task that you can do to move things forward?
            - What's the smallest/simplest task after that?
            - Etc.
        3. Plan a course of action for the simplest task
        4. Execute
        5. Repeat planning and execution for intermediate outcomes
        
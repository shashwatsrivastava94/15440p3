p3
==

This repository contains the starter code for project 3 (15-440, Fall 2015).
These instructions assume you have set your `GOPATH` to point to the repository's
root `p3/` directory.

## Starter Code

The starter code for this project is organized roughly as follows:

```
bin/                               Student-compiled binaries

src/github.com/cmu440-F15/        
  paxos/                           implement Paxos

  tests/                           Source code for official tests
    paxostest/                     Tests your paxos implementation
  
  rpc/
    paxosrpc/                      Paxos RPC helpers/constants
    
tests/                             Shell scripts to run the tests
    paxostest.sh                   Script for checkpoint tests
```

## Instructions

### Compiling your code

To and compile your code, execute one or more of the following commands (the
resulting binaries will be located in the `$GOPATH/bin` directory):

```bash
go install github.com/cmu440/runners/prunner
```

To simply check that your code compiles (i.e. without creating the binaries),
you can use the `go build` subcommand to compile an individual package as shown below:

```bash
# Build/compile the "paxos" package.
go build path/to/paxos

# A different way to build/compile the "paxos" package.
go build github.com/cmu440-F15/paxos
```

##### How to Write Go Code

If at any point you have any trouble with building, installing, or testing your code, the article
titled [How to Write Go Code](http://golang.org/doc/code.html) is a great resource for understanding
how Go workspaces are built and organized. You might also find the documentation for the
[`go` command](http://golang.org/cmd/go/) to be helpful. As always, feel free to post your questions
on Piazza.

##### The `prunner` program

The `prunner` program creates and runs an instance of your
`PaxosNode` implementation. Some example usage is provided below:

```bash
# Start a ring of three paxos nodes, where node 0 has prot 9009, node 1 has port 9010, and so on.
./prunner -ports=9009,9010,9011 -N=3 -id=0 -retries=5
./prunner -ports=9009,9010,9011 -N=3 -id=1 -retries=5
./prunner -ports=9009,9010,9011 -N=3 -id=2 -retries=5
```

You can read further descriptions of these flags by running 
```bash
./prunner -h
```

### Executing the official tests

#### 1. Checkpoint
The tests for checkpoint are provided as bash shell scripts in the `p3/tests` directory.
The scripts may be run from anywhere on your system (assuming your `GOPATH` has been set and
they are being executed on a 64-bit Mac OS X or Linux machine). Simply execute the following:

```bash
$GOPATH/tests/paxostest.sh
```

#### 2. Full test

The tests for the whole project are not provided for this project. You should develop your own
ways of testing your code. After the checkpoint is due, we will open up submissions for the final
version and run the full suite of tests.

If you have other questions about the testing policy please don't hesitate to ask us a question on Piazza!

### Submitting to Autolab

To submit your code to Autolab, create a `p3.tar` file containing your implementation as follows:

```sh
cd $GOPATH
tar -cvf p3.tar src/
```

In order for us to test your Paxos implementation, you should maintain the same directory structure and
API for RPC calls as in the handout. However, you can add additional packages as part of your application
component.

## Miscellaneous

### Using Go on AFS

For those students who wish to write their Go code on AFS (either in a cluster or remotely), you will
need to set the `GOROOT` environment variable as follows (this is required because Go is installed
in a custom location on AFS machines):

```bash
export GOROOT=/usr/local/depot/go
```

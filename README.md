# task-lib-example

An example app making use of the task-lib tasks

This example uses library tasks defined in [github.com/campbel/task-lib](https://github.com/campbel/task-lib) and a _hacky_ task file to implement dynamic task fetching.

First step is a `pre-flight` check that will download necessary dependencies. This example uses `go-getter`, but any tool would work.

Second step is a generic `run` task that recurisvely calls task with the desired task. This allows task the opportunity to re-load the newly downloaded libraries, since they would otherwise not be available on the initial load. We use the `optional` flag for the dependencies to enable this.

## Result

Calling this task file in the form `task run -- setup` will execute the `pre-flight` task, downloading the dependencies. Then run the `run` task, which will call `task setup`. When `task setup` is called the libraries are available and the task can load and call the dependencies.
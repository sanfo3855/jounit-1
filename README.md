# JoUnit
Tool used for Unit Test of Jolie Microservices

## Requirement

1. Microservice to test (re)named as "main.ol"

1. Directory "test_suite" in the project to test's repository.
    Within this directory you must put every file needed for the test:
    - init.ol (needed) -> here you will write tests in the format explained below
    - dependencies.ol.test (facultative) -> here you will write variables needed for the test
    - every other file needed for the test (such for example as a JSON with some structured data needed for an operations)

1. Format of "init.ol":

    If you need dependencies.ol.test file, you must include it in init.ol

    ```jolie
    include "./test_suite/dependencies.ol.test"
    ```

    Format of "dependencies.ol.test":
    
    ```jolie
    constants {
      <nameConst1>=<valueConst1>,
      <nameConst2>=<valueConst2>,
      ...
    }
    ```

    If your microservice has dependencies, you must include every of it.

    The syntax for importing a dependency is:
    
    ```jolie
    include <outputPortName>.depservice
    ```
    For dependency we mean an external microservice connected with an output port with our microservice to test.

    For example if you have two dependencies connected with 2 outputPort named "firstDependency" and "secondoDependency", you have to write like this at the top fo init.ol
    
    >include "firstDependency.depservice"
    
    >include "secondDependency.depservice"
    

> efficiency in execution and expressiveness  - 1

"By concurrence we mean the potentially parallel execution of desired actions." - 3

> There is little interaction between the various "jobs" or "processes' that are executed concurrently. Indeed, the correctness of an operating system is dependent on making sure that none of the numerous (user-defined) processes affect each other.


Actor Model Theory about concurrency.
- Better suited for natural models


# Design Choices

- Nature of computer elements
- Global synchrony versus asynchronous elements
- Mode of interaction between computing elements
- Degree of Fairness
- Reconfigurability and extensibility


# Nature of Computer elements

1. Sequential processes
2. Functions transforming data values
3. Actors


## Sequential processes

The operational notion of a sequential process is that it performs a sequence of transformations on states, where a state is a map from locations to values such as integers.
These transformations might require certain inputs and produce outputs, which means there is a possibility for deadlock. Each process is sequential but they can execute in parallel.

## Functions Transforming Data values


## Actors
Actors are computational agents which map each incoming communication to a 3-tuple consisting of:
1. a finite set of communication sent to other Actors
2. a new behavior (which will govern the response to the next communication processed)
3. a finite set of new actors created


"Creation of new actors guarantees the ability to abstractly increase the distributivity of the computation as it evolves." - 14

## Interaction Between agents

## Degree of Fairness

>...a realistic model must assume that the arrival order of communications sent is both arbitrary and entirely unknown. In particular, the use of the arbiter as the hard- ware element for serialization implies that the arrival order is physically indeterminate.

### Guarantee of Delivery

> There are, realistically, no un-bounded buffers in the physically realizable universe.

> There is, however, no general limit on buffers: the size of any real buffer will be specific to any particular implementation and 'its limitations. The point of building a semantic model is to abstract away from such details 'inherent 'in any implementation.

The guarantee of delivery does not assume that each message is "meaningfully" processed.  An Actor could ignore a message on delivery or indefinitely buffer some communications.

The guarantee of delivery is one form of *fairness*.  A strong requirement for fairness is that all messages sent are received in a random order no matter their properties.  A weaker one would be that a system delivers 3 "short" messages for each "long" it delivers.

## Reconfigurability and Extensibility
If a process only communicates with a set of processes throughout its lifetime, its *interconnection topology* is said to be *static*.  If in the course of its lifetime a process communicates to a new process it is *dynamic*.  A static topology is easier to reason about at compile time, however, it has severe limitations in representing the behavior of a real system.

Consider the example of a *resoure-manager* for two printers.  We can assume that the printers are identical and are interchangeable.  This resource-manager can:
1. Send the print requests to the __first available__ printer
2. When a print request has been processed, to send a *receipt* to the user requesting the printing.
If the *resource-manager* were static then it must either communicate with both printers or neither.  While in reality we want it to pick which printer to send the request based on its availability.  You can imagine this graphically.  If we make this system dynamic then the edges connecting the resource-manager and the printers represents possible communication.

# Defining an Actor system
> Computation in a system of actors is in response to communications sent to the system communications are contained in Tasks.  

Computing a task can result in new tasks and new actors.  Processed tasks and actors no longer "useful" can be removed safely from the system.  Thus the configuration of an actor system is defined by its actors and the set of all unprocessed tasks.

# Tasks
"a future 'is a communication that can be sent a communication to evaluate itself" - 34


# Description of actors
- mail address to a sufficiently large mail queue
- It's behavior, which is a function of the communication accepted.


Thus we can imagine an actor having both a queue for messages as they arrive and an *actor machine* that points to the message being processed.

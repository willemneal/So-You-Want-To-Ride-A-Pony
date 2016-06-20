"efficiency in execution and expressiveness"  - 1

"By concurrence we mean the potentially parallel execution of desired actions." - 3

"there is little interaction between the various "jobs" or "processes' that are executed concurrently. Indeed, the correctness of an operating system is dependent on making sure that none of the numerous (user-defined) processes affect each other."


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


# Defining an Actor system
"Computation in a system of actors is in response to communications sent to the system"
communications are contained in Tasks.  Computing a task can result in new tasks and new actors.  Processed tasks and actors no longer "useful" can be removed safely from the system.  Thus the configuration of an actor system is defined by its actors and the set of all unprocessed tasks.

# Tasks
"a future 'is a communication that can be sent a communication to evaluate itself" - 34


# Description of actors
- mail address to a sufficiently large mail queue
- It's behavior, which is a function of the communication accepted.


Thus we can imagine an actor having both a queue for messages as they arrive and an *actor machine* that points to the message being processed.

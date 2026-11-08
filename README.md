# Queue Management Simulator

A multithreaded Java application that simulates clients arriving at a service system with multiple queues (like checkout lanes in a supermarket) and distributes them in real time according to a selectable scheduling strategy.

## Tech Stack
- **Language:** Java (Maven)
- **GUI:** Java Swing
- **Concurrency:** `ExecutorService`, `BlockingQueue` (`LinkedBlockingQueue`), `AtomicInteger`, `synchronized`
- **Design patterns:** Strategy

## How It Works
- Clients are randomly generated with an **arrival time** and a **service time**, within user-defined intervals.
- Each queue (`Server`) runs on **its own thread** and processes its clients concurrently with the other queues.
- A `Scheduler` dispatches each arriving client to a queue using one of two strategies (Strategy pattern):
  - **SHORTEST_QUEUE**: the queue with the fewest clients
  - **SHORTEST_TIME**: the queue with the smallest total waiting time
- The `SimulationManager` advances the simulation clock and updates the GUI in real time.

## Features
- Configurable simulation: number of clients, number of queues, min/max arrival time, min/max service time, time limit
- Live visualization of every queue and the clients waiting in it
- Statistics at the end of the simulation: **average waiting time**, **average service time** and **peak hour**
- Full simulation log written to `log.txt`

## Architecture
```
src/main/java
├── Model/          Task (client), Server (queue running on its own thread)
├── BusinessLogic/  SimulationManager, Scheduler, Strategy, ShortestQueueStrategy,
│                   ShortestTimeStrategy, SelectionPolicy
└── GUI/            SimulationFrame (Swing interface)
```
A UML class diagram is included in the repository (`.drawio` file).

## How to Run
**Prerequisites:** Java (JDK 25), Maven

1. Clone the repository: `git clone https://github.com/daniilban01/queue-management-simulator.git`
2. Open it as a Maven project in IntelliJ IDEA (or another IDE).
3. Run `BusinessLogic.SimulationManager` (contains the `main` method).
4. Set the simulation parameters in the GUI, choose a strategy and start the simulation.

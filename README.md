# 🎫 clsQueueLine — Queue Line Management System

A C++ class that simulates a real-world queue line system with ticket issuing, client serving, and expected wait time calculation.

---

## 📖 Overview

`clsQueueLine` is a C++ class that models a physical queue line (like in a bank or government office). It issues numbered tickets with a prefix, tracks waiting clients, calculates expected serve time, and supports serving clients one by one. It uses a nested `clsTicket` class and depends on `clsDate` for timestamping tickets.

---

## ✨ Features

- **Ticket Issuing**: Generate sequentially numbered tickets with a custom prefix
- **Expected Wait Time**: Each ticket shows the estimated wait time based on average serve time and number of waiting clients
- **Ticket Timestamping**: Every ticket records the exact time it was issued using `clsDate`
- **Serve Next Client**: Remove the front client from the queue
- **Who Is Next**: Preview the next client's ticket number
- **Queue Info**: Display total, served, and waiting client counts
- **Print Tickets RTL/LTR**: Visualize the queue in both right-to-left and left-to-right directions
- **Print All Tickets**: Display full details of all tickets currently in the queue

---

## 🚀 How to Use

```cpp
#include "clsQueueLine.h"
```

### Basic Usage
```cpp
clsQueueLine line("A", 5); // Prefix "A", 5 min average serve time

line.IssueTicket(); // A1
line.IssueTicket(); // A2
line.IssueTicket(); // A3

cout << line.WhoIsNext();      // "A1"
cout << line.WaitingClients(); // 3

line.PrintInfo();
line.PrintTicketsLineRTL();    //  A1 <-- A2 <-- A3 <--
line.PrintTicketsLineLTR();    //  A3 --> A2 --> A1 -->
line.PrintAllTickets();

line.ServeNextClient();
cout << line.WhoIsNext();      // "A2"
cout << line.ServedClients();  // 1
```

---

## 🧠 Concepts Used

- **OOP** — Encapsulation of queue line behavior inside a class with a nested `clsTicket` class
- **Nested Class** — `clsTicket` defined privately inside `clsQueueLine` for clean encapsulation
- **STL Queue** — `std::queue<clsTicket>` used as the underlying line storage
- **STL Stack** — `std::stack<clsTicket>` used to reverse ticket order for LTR printing
- **Queue Copy** — Queue is copied before printing to preserve the original order
- **Dependency** — Uses `clsDate::GetSystemDateTimeString()` for ticket timestamping
- **Encapsulation** — Private prefix, ticket count, and serve time with public methods only

---

## 🔑 Key Methods

| Method | Description |
|---|---|
| `IssueTicket()` | Creates and adds a new numbered ticket to the queue |
| `WhoIsNext()` | Returns the ticket number of the next client to be served |
| `ServeNextClient()` | Removes the front client from the queue |
| `WaitingClients()` | Returns the number of clients currently in the queue |
| `ServedClients()` | Returns the number of clients already served |
| `AverageServeTime()` | Returns the average serve time per client |
| `PrintInfo()` | Displays total, served, and waiting client counts |
| `PrintTicketsLineRTL()` | Prints the queue left-to-right with `<--` arrows |
| `PrintTicketsLineLTR()` | Prints the queue right-to-left with `-->` arrows using a stack |
| `PrintAllTickets()` | Prints full details of all tickets in the queue |

---

## 🔗 Dependency

This class depends on [`clsDate`](../clsDate/) for ticket timestamp generation.

---

## 📄 License

This project is open source and free to use for educational purposes.

---

## 👤 Author

👤 **Mahmoud Abd El-Sattar**  
📧 mahmoud.abdelsattar.dev@gmail.com  
💼 [linkedin.com/in/mahmoud-abd-el-sattar](https://www.linkedin.com/in/mahmoud-abd-el-sattar-1b227522a)

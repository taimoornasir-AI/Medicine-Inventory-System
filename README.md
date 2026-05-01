# 💊 Medicine Management System

A console-based **Medicine Management System** written in C++ that demonstrates and compares three classic data structure implementations — **Doubly Linked List**, **Stack**, and **Queue** — for managing pharmacy inventory data.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Data Structures](#data-structures)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Algorithms](#algorithms)
- [Input Format](#input-format)

---

## Overview

This project was built as a **Data Structures course assignment** to explore how different linear data structures behave when performing common operations such as insertion, search, sorting, and deletion. All three implementations expose the same set of operations, making it easy to observe structural and behavioral differences side by side.

---

## Features

| Feature | Description |
|---|---|
| ➕ Add Medicine | Insert a new medicine record with unique ID validation |
| 🔍 Search | Look up medicines by Name, ID, or Expiry Date |
| 🔃 Sort | Sort records by Name, ID, or Expiry Date |
| ✏️ Update | Edit an existing medicine's details |
| 🗑️ Auto-Delete Expired | Automatically remove records past their expiry date |
| 📋 Display All | Print all stored medicine records in a formatted table |

---

## Data Structures

### 🔗 Doubly Linked List (`linkedlist.cpp`)
Each node holds `prev` and `next` pointers, enabling bidirectional traversal. Sorting uses **QuickSort** adapted for doubly linked lists by swapping node data in-place.

### 📚 Stack (`stack.cpp`)
A singly linked list operating in **LIFO** (Last In, First Out) order. New medicines are pushed to the top. Sorting uses **QuickSort** on a singly linked list, where finding the node before the pivot requires a linear scan.

### 🚶 Queue (`queue.cpp`)
A singly linked list operating in **FIFO** (First In, First Out) order, with separate `front` and `rear` pointers. Sorting uses **Bubble Sort** optimized with an early-exit flag.

---

## Project Structure

```
medicine-management-system/
│
├── main.cpp          # Entry point; menu-driven interface for all three DSes
├── head.cpp          # Shared Medicine struct, color macros, input validators
├── linkedlist.cpp    # MedicineListLinkedList — doubly linked list implementation
├── stack.cpp         # MedicineListStack — stack-based implementation
├── queue.cpp         # MedicineListQueue — queue-based implementation
└── compare.cpp       # Execution time measurement utilities (in progress)
```

---

## Getting Started

### Prerequisites

- A C++11 (or later) compiler: `g++`, `clang++`, or MSVC

### Compile

```bash
g++ -std=c++11 main.cpp -o medicine_system
```

> **Note:** `main.cpp` includes the other `.cpp` files directly via `#include`, so only `main.cpp` needs to be passed to the compiler.

### Run

```bash
./medicine_system        # Linux / macOS
medicine_system.exe      # Windows
```

---

## Usage

On launch, you select a data structure to work with:

```
1. Linked List
2. Stack
3. Queue
4. Exit
```

Each mode presents the same operation menu:

```
1.  Add Medicine
2.  Search by Name
3.  Search by ID
4.  Search by Expiry Date
5.  Sort by Name
6.  Sort by ID
7.  Sort by Expiry Date
8.  Display All Medicines
9.  Update Medicine
10. Auto-Delete Expired
0.  Back
```

---

## Algorithms

| Operation | Linked List | Stack | Queue |
|---|---|---|---|
| Insert | O(1) tail append | O(1) push to top | O(1) enqueue to rear |
| Search | O(n) linear scan | O(n) linear scan | O(n) linear scan |
| Sort by Name | QuickSort O(n log n) avg | QuickSort O(n log n) avg | Bubble Sort O(n²) |
| Sort by ID | QuickSort O(n log n) avg | QuickSort O(n log n) avg | Bubble Sort O(n²) |
| Sort by Expiry | QuickSort O(n log n) avg | QuickSort O(n log n) avg | Bubble Sort O(n²) |
| Delete Expired | O(n) | O(n) rebuild | O(n) |

---

## Input Format

### Medicine Fields

| Field | Type | Example |
|---|---|---|
| ID | Integer (unique) | `101` |
| Name | String | `Paracetamol` |
| Price | Double | `12.50` |
| Quantity | Integer | `200` |
| Expiry Date | `MM/YYYY` | `06/2026` |

### Expiry Date Validation
- Format must be exactly `MM/YYYY`
- Month must be between `01` and `12`
- Year must be between `2000` and `9999`

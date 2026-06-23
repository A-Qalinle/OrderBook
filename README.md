# Order Book Matching Engine (C++)

A simple order book written in C++. It stores buy and sell orders, matches them against each other, and supports four order types: market, limit, good-till-canceled (GTC) and fill-or-kill (FOK).

## Features

- Add orders, and cancel them by ID
- Match buy orders against sell orders:
  - A buy order matches a sell order priced at or below the buy price.
  - A sell order matches a buy order priced at or above the sell price.
  - A trade executes at the price of the order it matched against.
- Print every order in the book before and after matching

Orders are matched by type, in this order:

| Order type | How it is handled |
| --- | --- |
| Market | Matched first |
| Good-till-canceled | Matched second; stays in the book if nothing matches |
| Fill-or-kill | Filled only if one opposite order covers the whole quantity; otherwise canceled straight away |
| Limit | Matched last; stays in the book if nothing matches |

## Project structure

```
order-book/
├── include/
│   └── OrderBook.hpp   OrderBook class: orders, matching, cancelling, printing
├── src/
│   └── main.cpp        Example: adds 8 sample orders, matches them, prints the book
└── README.md
```


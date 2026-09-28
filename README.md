# Swift Collection Methods

A Swift practice project focused on working with collections, dictionaries, optionals, and higher-order functions.

The project uses an array of book dictionaries to demonstrate how Swift collection methods can be applied to transform, filter, flatten, and aggregate data.

## 🎯 Objective

The main objective is to practice Swift's collection operations using real-world-style book data.

The exercise demonstrates how to:

* Transform collection elements with `map`
* Filter elements using `filter`
* Flatten nested collections with `flatMap`
* Safely extract optional values with `compactMap`
* Aggregate values using `reduce`
* Perform conditional type casting with `as?`
* Work with `Optional` values and nil-coalescing (`??`)
* Use `Set` to store unique values

## 📚 Data Model

The project uses an array of dictionaries representing books.

Each book contains:

* `title` — Book title
* `author` — Author name
* `year` — Publication year
* `price` — Book price
* `genre` — Array of genres

Example:

```swift
[
    "title": "Swift Fundamentals",
    "author": "John Doe",
    "year": 2015,
    "price": 40,
    "genre": ["Programming", "Education"]
]
```

## 🔧 Operations Implemented

### 1. Discounted Prices — `map`

Calculates the price of every book after applying a 10% discount.

```swift
let discountedPrices: [Double] = books.map {
    Double($0["price"] as? Int ?? 0) * 0.9
}
```

Result:

```text
[36.0, 13.5, 27.0, 22.5, 18.0]
```

### 2. Books Published After 2000 — `filter` + `map`

Filters books published after the year 2000 and extracts their titles.

```swift
let booksPostedAfter2000: [String] = books
    .filter {
        ($0["year"] as? Int ?? 0) > 2000
    }
    .map {
        $0["title"] as? String ?? ""
    }
```

The `filter` operation determines which books meet the condition, while `map` extracts only the required title.

### 3. Unique Genres — `flatMap` + `Set`

Each book contains an array of genres. `flatMap` combines these nested arrays into a single collection, while `Set` removes duplicate genres.

```swift
let allGenres: Set<String> = Set(
    books.flatMap {
        $0["genre"] as? [String] ?? []
    }
)
```

Result:

```text
Programming
Education
Classic
Drama
Fantasy
Epic
Technology
Non-Fiction
```

### 4. Total Cost — `reduce`

Calculates the total price required to purchase one copy of every book.

```swift
let totalCost: Int = books
    .map {
        $0["price"] as? Int ?? 0
    }
    .reduce(0, +)
```

Result:

```text
130
```

## 🧠 Swift Concepts Practiced

This exercise focuses on several fundamental Swift concepts:

| Concept      | Purpose                                           |
| ------------ | ------------------------------------------------- |
| `map`        | Transform every element in a collection           |
| `filter`     | Keep elements that satisfy a condition            |
| `flatMap`    | Flatten nested collections                        |
| `compactMap` | Transform values while removing `nil` results     |
| `reduce`     | Combine multiple values into a single result      |
| `as?`        | Perform a safe type cast                          |
| `??`         | Provide a default value when an Optional is `nil` |
| `Set`        | Store unique values                               |

## 🛠️ Technologies

* **Swift**
* **Xcode**
* **Git / GitHub**

## ▶️ How to Run

1. Clone the repository.
2. Open the project in Xcode.
3. Build and run the project.
4. Review the console output to see the results of each collection operation.

## 📌 Learning Outcome

This project demonstrates practical use of Swift's higher-order collection functions and provides a foundation for writing concise, expressive, and type-safe collection-processing code.

The exercise is intentionally implemented using dictionaries and `Any` to practice type casting and optionals. In production applications, strongly typed models such as Swift `struct` types would generally be preferred for better type safety and maintainability.

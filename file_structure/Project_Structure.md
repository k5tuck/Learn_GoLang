# Structure Types

## Table of Contents

1. [Flat](#flat) \*Small Projects
2. [Layered (MVC)](#layered)
3. [Modular](#modular)
4. [Data Driven Domain (DDD)](<#data-driven-domain-(ddd)>) \*Large Projects
5. [DDD-Hexagonal](#ddd-hexagonal)

<center>For our file structure examples, we will use Reviews of Books as an example. As well as two storage types: JSON and Database samples.</center>

`* - ideal`

### [Flat](#table-of-contents)

```
/
├── main.go
├── storage.go
├── storage_json.go
├── storage_mem.go
├── data.go
├── model.go
└── handlers.go
```

**Flat Structure**

Pros

1. Easy to Navigate
2. Can avoid circular dependencies a little easier
3. Sweet and Simple

Cons

1. Easy to use global state
2. Not really scalable

### [Layered](#table-of-contents)

```
/
├── handlers
│   ├── review.go
│   └── books.go
├── models
│   ├── review.go
│   ├── storage.go
│   └── books.go
├── storage
│   └── json.go
├── main.go
└── data.go - Sample Data
```

**_Group by functionality_**

1. Presentation
2. Business Logic
3. Ext Dependencies / Infrastructure

Pros

1. Familiar - Classic MVC
2. Easy to Decide where to put things
3. What the app does is a **little** clearer

Cons

1. Biggest Con is possible circular dependencies
2. Global state could be problematic
3. Naming Delimmas (single vs. plural)
4. Hard to scale over time

### [Modular](#table-of-contents)

```
/
├── books
│   ├── book.go
│   └── handler.go
├── reviews
│   ├── review.go
│   └── handler.go
├── storage
│   ├── storage.go
│   ├── data.go
│   └── json.go
└── main.go
```

**_Group by module_**

Pros

Cons

1. Naming Convention is not good
2. Circular Dependencies
3. Confusion caused by naming of files in separate folders

## What is DDD?

Data Driven Domain, or DDD, is a technique for how to think of organization, structure, and functionality of your app.

- Define business logic and domain
- Define Terminology
- Categorize the Building Blocks of your System:
  - Context - App Context
  - Language - Terminology/Language that will be used in App
  - Entities - single identifiable object
  - Value Objects - Properties to Entities
  - Aggregates - Combine entities together
  - Service - Stateless Operations performed by multiple entities in App
  - Events - Anything that can effect state of your app
  - Repositories
  - Factory

### [Data Driven Domain (DDD)](#table-of-contents)

```
/
├── adding
│   ├── endpoint.go
│   └── service.go
├── books
│   ├── book.go
│   └── samples.go
├── reviewing
│   ├── endpoint.go
│   └── service.go
├── reviews
│   ├── review.go
│   └── sample.go
├── listing
│   ├── endpoint.go
│   └── service.go
├── storage
│   ├── storage.go
│   ├── json.go
│   └── data.go
└── main.go
```

**_Group by context_**

Pros

1. Little easier to avoid circular dependencies

Cons

1. Integration of New features is difficult
2. Sample data is not **_necessarily_** in an **ideal** palce

### [DDD-Hexagonal](#table-of-contents)

```
/
├── cmd (Binaries)
│   ├── server (I/O) Interface
│   │   └── main.go
│   └── sample_data  (I/O) Interface
│       ├── main.go
│       ├── books_sample.go (Could also place in top-level "resources" directory)
│       └── reviews_sample.go (Could also place in top-level "resources" directory)
└── pkg (Packages)
    ├── adding
    │   ├── book.go
    │   └── service.go
    ├── reviewing
    │   ├── review.go
    │   └── service.go
    ├── listing
    │   ├── book.go
    │   ├── review.go
    │   └── service.go
    ├── http (I/O) Interface
    │   └── rest
    │       └── handler.go
    └── storage (I/O) Interface
        ├── identity_generator.go
        ├── json
        │   ├── main.go
        │   ├── book.go
        │   └── review.go
        └── memory
            ├── main.go
            ├── book.go
            └── review.go
```

<center>OR</center>
<br />

```
/
├── cmd (Binaries)
│   ├── data
│   │   └── main.go
│   └── server
│       └── main.go
├── pkg (Packages)
│   ├── adding
│   │   └── service.go
│   │   ├── book.go
│   ├── reviewing
│   │   ├── review.go
│   │   └── service.go
│   ├── listing
│   │   ├── book.go
│   │   ├── review.go
│   │   └── service.go
│   ├── http
│   │   └── rest
│   │       └── handler.go
│   └── storage
│       ├── json
│       │   ├── main.go
│       │   ├── book.go
│       │   └── review.go
│       └── memory
│           ├── main.go
│           ├── book.go
│           └── review.go
├── docker
├── docs
└── resources
    ├── books_sample.go
    └── reviews_sample.go
```

Pros

1. Core Domain is in center
2. Dependencies are Layered
3. External I/O's surround your Application
4. Changes to one Domain of the app should only effect that specific Domain
5. Dependencies **only point inwards**.

<br />
<h5>
Notes, Samples, and Architecture Taken from:

[Kat Zien](https://github.com/katzien/go-structure-examples) - Github |
[How Do You Structure Your Go Apps?](https://www.youtube.com/watch?v=Qtk9FFOoT5M&t=11s) - Youtube

[Marcus Olsson's (GoDDD App)](https://github.com/marcusolsson/goddd) - Github

</h5>

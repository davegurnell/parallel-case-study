# Three levels of understanding

Conceptual
Theoretical
Craft

# Conceptual level

Properties of good code:

- Readable
- Scalable
- Modular
- Maintainable / Testable
- Composable / Closure
- Predictable / Statically typed

# Big theory patterns

1. ADTs
   - Sum types     -- sealed traits
   - Product types -- case classes
2. Sequencing methods:
   - map
   - flatMap
   - foldLeft/Right
3. Type classes
   - A definition of some
     functionality that we want to
     implement for a wide range of
     data types

# Introductions

- Name
- How much Scala
- How much Cats
- What do you want to get out of
  the course

# Parts of this course

- Toolbox
  - Type classes
    - Semigroup and Monoid
    - Functor, Monad, and MonadError
    - Semigroupal, Applicative
    - Parallel
    - Foldable and Traverse
  - Data types
    - Option, Either, Future, Try
    - Monad transformers
    - Eval
    - Validated
    - (maybe Reader, Writer, and State)
- Intepreter pattern
  - Tagless final encoding
  - aka Finally tagless encoding
  - (maybe natural transformations)
- Workshop

# Setup

```bash
open https://underscore.io/books/scala-with-cats

sbt new underscoreio/cats-seed.g8
# We're using:
# - Scala 2.12
# - Cats 1.4
# - Kind projector

git clone https://github.com/typelevel/cats.git
```

(We'll be looking at the code to find out how things work!)

# Type classes






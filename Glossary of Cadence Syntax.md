Started 06/08/2022

# Formats
  
**Format of an empty contract** - 
```cadence
pub contract [contract name] {

  init () {
  }
}
```

**Format of an empty transaction** - 
```cadence
import [contract name] from [address of that contract]

transaction (...) {
  prepare (signer ...) {
  }
  
  execute {
  }
}
```

**Format of an empty script** - 
```cadence
import [contract name] from [address of that contract]

pub fun main (): [return type] {
  return [...]
}

```

**Format of declaring a variable** - `[access modifier] [var/let] [variable name]: [Type]`

**Format of writing a function** - `[access modifier] fun [function name](parameter1: Type, parameter2: Type,...): [return Type] {...}`

**Format of calling a function** - 


# Syntax

**`log`** - the most basic function in Cadence, which means, "Print this to the screen so I can read it."

**Type** - a broader representation of what kind of thing something is
  `Int` = Integer = 5
  `String` = String = " " = "Hello idiot"
  `UInt64` = a positive number between 0 and 18,446,744,073,709,551,615
  
`AuthAccount` - 


# Vocabulary

**Function** - executes a piece of code/logic when it's called/run

**Arguments/Parameters** - functions always take these in, & they get put into the function so it knows what to do

**Variable** - something that stores/hold a piece of data inside of it at a certain point in time

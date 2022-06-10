## Quest Chapter 5 Day 2

**1. Explain why standards can be beneficial to the Flow ecosystem.**

Standards can be beneficial to the FLOW ecosystem because it helps us rationalize that a Smart Contract we're looking at is meant to be an "NFT Contract" without having to read all of its code line by line. It also helps clients, like a marketplace DApp, understand what they're looking at and not have to implement different functionality for every NFT contract.

It's also helpful to developers because they have an NFT contract outline to look at to make sure they include what's necessary (and so they don't make a poopy NFT contract).

**2. What is YOUR favourite food?**

It's a tie between a good corned beef sandwich (2nd Ave Deli is THE place to go) and nigiri/sashimi sushi.

**3. Please fix this code (Hint: There are two things wrong):**

The contract interface:

```CADENCE
pub contract interface ITest {
  pub var number: Int
  
  pub fun updateNumber(newNumber: Int) {
    pre {
      newNumber >= 0: "We don't like negative numbers for some reason. We're mean."
    }
    post {
      self.number == newNumber: "Didn't update the number to be the new number."
    }
  }

  pub resource interface IStuff {
    pub var favouriteActivity: String
  }

  pub resource Stuff {
    pub var favouriteActivity: String
  }
}
```

The implementing contract:

```CADENCE
pub contract Test {
  pub var number: Int
  
  pub fun updateNumber(newNumber: Int) {
    self.number = 5
  }

  pub resource interface IStuff {
    pub var favouriteActivity: String
  }

  pub resource Stuff: IStuff {
    pub var favouriteActivity: String

    init() {
      self.favouriteActivity = "Playing League of Legends."
    }
  }

  init() {
    self.number = 0
  }
}
```

_THE NEW ANSWER_:

There are no mistakes in the contract interface.

The implementing contract:

```CADENCE
pub contract Test {
  pub var number: Int
  
  pub fun updateNumber(newNumber: Int) {
    newNumber = 5 //Mistake #1 was here
  }

  pub resource interface IStuff {
    pub var favouriteActivity: String
  }

  pub resource Stuff: ITest.IStuff { //Mistake #2 was here
    pub var favouriteActivity: String

    init() {
      self.favouriteActivity = "Playing League of Legends."
    }
  }

  init() {
    self.number = 0
  }
}
```

_THE OLD ANSWER_:

The contract interface:
```CADENCE
pub contract interface ITest {
  pub var number: Int
  
  pub fun updateNumber(newNumber: Int) {
    pre {
      newNumber >= 0: "We don't like negative numbers for some reason. We're mean."
    }
    post {
      self.number == newNumber: "Didn't update the number to be the new number."
    }
  }

  pub resource interface IStuff {
    pub var favouriteActivity: String
  }

  pub resource Stuff: IStuff { //Mistake #1 was here
    pub var favouriteActivity: String
  }
}
```

The implementing contract:

```CADENCE
pub contract Test  {
  pub var number: Int
  
  pub fun updateNumber(newNumber: Int) {
    self.number = 5
  }

  pub resource interface IStuff {
    pub var favouriteActivity: String
  }

  pub resource Stuff: ITest.IStuff { //Mistake #2 was here
    pub var favouriteActivity: String

    init() {
      self.favouriteActivity = "Playing League of Legends."
    }
  }

  init() {
    self.number = 0
  }
}
```

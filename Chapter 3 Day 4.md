## Quest Chapter 3 Day 4 🆗

**1. Explain, in your own words, the 2 things resource interfaces can be used for (we went over both in today's content)**

Two things resource interfaces can be used for are
- Specifying a set of requirements for something to implement
- Allowing a developer to only expose certain things to certain people

**2. Define your own contract. Make your own resource interface and a resource that implements the interface. Create 2 functions. In the 1st function, show an example of not restricting the type of the resource and accessing its content. In the 2nd function, show an example of restricting the type of the resource and NOT being able to access its content.**

```cadence
pub contract IAmGoodLooking {

    pub resource interface IBreakHearts {
        pub var phraseOne: String
        pub var phraseTwo: String
        pub fun updatePhraseTwo(newPhraseTwo: String): String
    }
    
    pub resource BreakHearts: IBreakHearts {
        pub var phraseOne: String
        pub var phraseTwo: String
        
        pub fun updatePhraseTwo(newPhraseTwo: String): String {
            self.phraseTwo = newPhraseTwo
            return self.phraseTwo
        }
        
        init () {
            self.phraseOne = "If you look good,"
            self.phraseTwo = "you feel good."
        }
    }
    
    pub fun notTopSecret() {
        let breakHearts: @BreakHearts <- create BreakHearts()
        breakHearts.updatePhraseTwo(newPhraseTwo: "the mirror won't crack.")
        log(breakHearts.phraseTwo)
        
        destroy breakHearts
    }
    
    pub fun topSecret() {
        let breakHearts: @BreakHearts{IBreakHearts} <- create BreakHearts()
        let newPhraseTwo = breakHearts.updatePhraseTwo(newPhraseTwo: "the mirror won't crack.")
        log(newPhraseTwo)
        
        destroy breakHearts
    }
}
```

**3. How would we fix this code?**

```Cadence
pub contract Stuff {

    pub struct interface ITest {
      pub var greeting: String
      pub var favouriteFruit: String
    }

    // ERROR:
    // `structure Stuff.Test does not conform 
    // to structure interface Stuff.ITest`
    pub struct Test: ITest {
      pub var greeting: String

      pub fun changeGreeting(newGreeting: String): String {
        self.greeting = newGreeting
        return self.greeting // returns the new greeting
      }

      init() {
        self.greeting = "Hello!"
      }
    }

    pub fun fixThis() {
      let test: Test{ITest} = Test()
      let newGreeting = test.changeGreeting(newGreeting: "Bonjour!") // ERROR HERE: `member of restricted type is not accessible: changeGreeting`
      log(newGreeting)
    }
}
```

THE OLD ANSWER
```Cadence
pub contract Stuff {

    pub struct interface ITest {
      pub var greeting: String
      pub var favouriteFruit: String
      pub fun changeGreeting(newGreeting: String): String 
    }
    
    // ERROR:
    // `structure Stuff.Test does not conform 
    // to structure interface Stuff.ITest`
    pub struct Test: ITest {
      pub var greeting: String
      init() {
        self.greeting = "Hello!"
      }

      pub fun changeGreeting(newGreeting: String): String {
        self.greeting = newGreeting
        return self.greeting // returns the new greeting
      }
    }

    pub fun fixThis() {
      let test: Test{ITest} = Test()
      let newGreeting = test.changeGreeting(newGreeting: "Bonjour!")
      log(newGreeting)
    }
}
```

I'm still getting the first error message, I thought I fixed it, but now I don't know what to do.

![image](https://user-images.githubusercontent.com/104703860/172021199-1bd0bb2e-ce4d-48a0-98de-dccdb388c21a.png)


THE NEW ANSWER
```cadence
pub contract Stuff {

    pub struct interface ITest {
      pub var greeting: String
      pub var favouriteFruit: String
      pub fun changeGreeting(newGreeting: String): String 
    }
    
    // ERROR:
    // `structure Stuff.Test does not conform 
    // to structure interface Stuff.ITest`
    pub struct Test: ITest {
      pub var greeting: String
      pub var favouriteFruit: String
      init() {
        self.greeting = "Hello!"
        self.favouriteFruit = "Cherry"
      }

      pub fun changeGreeting(newGreeting: String): String {
        self.greeting = newGreeting
        return self.greeting // returns the new greeting
      }
    }

    pub fun fixThis() {
      let test: Test{ITest} = Test()
      let newGreeting = test.changeGreeting(newGreeting: "Bonjour!")
      log(newGreeting)
    }
}
```

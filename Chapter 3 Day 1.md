## Quest Chapter 3 Day 1 ✅

**1. In words, list 3 reasons why structs are different from resources.**

Structs are different from resources because:

- Structs can be lost (or overwritten), but resources cannot
- Structs can be created at any point in time, but resources cannot
- Structs can be copied, but resources cannot

Basically, recources are much more difficult than structs to deal with.

**2. Describe a situation where a resource might be better to use than a struct.**

A situation where a resource wuld be better to use than a struct would be in the case of a developer moving an NFT worth millions of dollars to another account. THe million dollar NFT couldn't be accidentally destroyed in the process because the developer has to explicitly command the NFT to be destroyed since it is a resource type.

**3. What is the keyword to make a new resource?**

`create` is the keyword to make a new resource. 

**4. Can a resource be created in a script or transaction (assuming there isn't a public function to create one)?**

A resource CANNOT be created in a script or transaction because they can only be created inside a smart contract. That is, the `create` keyword can only be used inside a contract. 

**5. What is the type of the resource below?**

_NEW ANSWER_: @Jacob, which is the declared name of the resource Jacob.

_OLD ANSWER_: This is a `string` type resource. 

```Cadence

pub resource Jacob {

}
```

**6. Let's play the "I Spy" game from when we were kids. I Spy 4 things wrong with this code. Please fix them.**
pub contract Test {

```Cadence

  pub contract Test {

    // Hint: There's nothing wrong here ;)
    pub resource Jacob {
        pub let rocks: Bool
        init() {
            self.rocks = true
        }
    }

    pub fun createJacob(): Jacob { // there is 1 here
        let myJacob = Jacob() // there are 2 here
        return myJacob // there is 1 here
    }
}
```

THE FIXED CODE:

```Cadence

  pub contract Test {

    // Hint: There's nothing wrong here ;)
    pub resource Jacob {
        pub let rocks: Bool
        init() {
            self.rocks = true
        }
    }

    pub fun createJacob(): @Jacob { 
        let myJacob <- create Jacob() 
        return <- myJacob 
    }
}
```

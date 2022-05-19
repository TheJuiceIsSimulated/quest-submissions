# FLOW Testnet Address:
0x8442e312e8a9534e


## Quest Chapter 1 Day 1 ✅
  
  **1. Explain what the Blockchain is in your own words.**

   A blockchain is a decentralized digital public ledger. Broken down, that means the blockchain is a record of all transactions made on a specific network, no single entity has control over the blockchain, the blockchain exists solely in the digital realm, and anyone can view, make changes to, or store data on the blockchain at any time (it's an open and transparent network).
  
  **2. Explain what a Smart Contract is.**

  A Smart Contract is a program, or "rulebook," that a developer makes on a blockchain so that users can interact with it. 

  **3. Explain the difference between a script and a transaction.**

  A transaction changes data on a blockchain and costs money, whereas scripts view data on a blockchain and are free. 
  

## Quest Chapter 1 Day 2 

  **1. What are the 5 Cadence Programming Language Pillars?**
  
  The five Cadence Programing Language Pillars are Safety and Security, Clarity, Approachability, Developer Experience, and Resource Oriented Programming.
  
  **2. In your opinion, even without knowing anything about the Blockchain or coding, why could the 5 Pillars be useful (you don't have to answer this for #5)?**
  
  Safety and Security could be useful because the more secure a Smart Contract is, 
  Clarity could be useful
  Approachability could be useful
  Developer Experience could be useful


## Quest Chapter 2 Day 1

**1. Deploy a contract to account 0x03 called "JacobTucker". Inside that contract, declare a constant variable named is, and make it have type String. Initialize it to "the best" when your contract gets deployed.**



**2. Check that your variable is actually equals "the best" by executing a script to read that variable. Include a screenshot of the output.** 






## Quest Chapter 2 Day 2

**1. Explain why we wouldn't call changeGreeting in a script.**



**2. What does the AuthAccount mean in the prepare phase of the transaction?**



**3. What is the difference between the prepare phase and the execute phase in the transaction?**



**4. This is the hardest quest so far, so if it takes you some time, do not worry! I can help you in the Discord if you have questions.**

**Add two new things inside your contract:**

**A variable named myNumber that has type Int (set it to 0 when the contract is deployed)
A function named updateMyNumber that takes in a new number named newNumber as a parameter that has type Int and updates myNumber to be newNumber
Add a script that reads myNumber from the contract**

**Add a transaction that takes in a parameter named myNewNumber and passes it into the updateMyNumber function. Verify that your number changed by running the script again.**






## Quest Chapter 2 Day 3

1. In a script, initialize an array (that has length == 3) of your favourite people, represented as Strings, and log it.

2. In a script, initialize a dictionary that maps the Strings Facebook, Instagram, Twitter, YouTube, Reddit, and LinkedIn to a UInt64 that represents the order in which you use them from most to least. For example, YouTube --> 1, Reddit --> 2, etc. If you've never used one before, map it to 0!

3. Explain what the force unwrap operator ! does, with an example different from the one I showed you (you can just change the type).

4. Using this picture below, explain...

What the error message means

Why we're getting this error

How to fix it

![image](https://user-images.githubusercontent.com/104703860/169172973-6b7551c6-9d9b-4616-a3e9-0a5f01c16b55.png)


## Quest Chapter 2 Day 4

1. Deploy a new contract that has a Struct of your choosing inside of it (must be different than Profile).

2. Create a dictionary or array that contains the Struct you defined.

3. Create a function to add to that array/dictionary.

4. Add a transaction to call that function in step 3.

5. Add a script to read the Struct you defined.


## Quest Chapter 3 Day 1

1. In words, list 3 reasons why structs are different from resources.

2. Describe a situation where a resource might be better to use than a struct.

3. What is the keyword to make a new resource?

4. Can a resource be created in a script or transaction (assuming there isn't a public function to create one)?

5. What is the type of the resource below?

pub resource Jacob {

}
6. Let's play the "I Spy" game from when we were kids. I Spy 4 things wrong with this code. Please fix them.
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

## Quest Chapter 3 Day 2

1. Write your own smart contract that contains two state variables: an array of resources, and a dictionary of resources. Add functions to remove and add to each of them. They must be different from the examples above.


## Quest Chapter 3 Day 3

1. Define your own contract that stores a dictionary of resources. Add a function to get a reference to one of the resources in the dictionary.

2. Create a script that reads information from that resource using the reference from the function you defined in part 1.

3. Explain, in your own words, why references can be useful in Cadence.


## Quest Chapter 3 Day 4

1. Explain, in your own words, the 2 things resource interfaces can be used for (we went over both in today's content)

2. Define your own contract. Make your own resource interface and a resource that implements the interface. Create 2 functions. In the 1st function, show an example of not restricting the type of the resource and accessing its content. In the 2nd function, show an example of restricting the type of the resource and NOT being able to access its content.

3. How would we fix this code?

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


## Quest Chapter 3 Day 5

1. For today's quest, you will be looking at a contract and a script. You will be looking at 4 variables (a, b, c, d) and 3 functions (publicFunc, contractFunc, privateFunc) defined in SomeContract. In each AREA (1, 2, 3, and 4), I want you to do the following: for each variable (a, b, c, and d), tell me in which areas they can be read (read scope) and which areas they can be modified (write scope). For each function (publicFunc, contractFunc, and privateFunc), simply tell me where they can be called.

access(all) contract SomeContract {
    pub var testStruct: SomeStruct

    pub struct SomeStruct {

        //
        // 4 Variables
        //

        pub(set) var a: String

        pub var b: String

        access(contract) var c: String

        access(self) var d: String

        //
        // 3 Functions
        //

        pub fun publicFunc() {}

        access(contract) fun contractFunc() {}

        access(self) fun privateFunc() {}


        pub fun structFunc() {
            /**************/
            /*** AREA 1 ***/
            /**************/
        }

        init() {
            self.a = "a"
            self.b = "b"
            self.c = "c"
            self.d = "d"
        }
    }

    pub resource SomeResource {
        pub var e: Int

        pub fun resourceFunc() {
            /**************/
            /*** AREA 2 ***/
            /**************/
        }

        init() {
            self.e = 17
        }
    }

    pub fun createSomeResource(): @SomeResource {
        return <- create SomeResource()
    }

    pub fun questsAreFun() {
        /**************/
        /*** AREA 3 ****/
        /**************/
    }

    init() {
        self.testStruct = SomeStruct()
    }
}
This is a script that imports the contract above:

import SomeContract from 0x01

pub fun main() {
  /**************/
  /*** AREA 4 ***/
  /**************/
}


## Quest Chapter 4 Day 1

1. Explain what lives inside of an account.

2. What is the difference between the /storage/, /public/, and /private/ paths?

3. What does .save() do? What does .load() do? What does .borrow() do?

4. Explain why we couldn't save something to our account storage inside of a script.

5. Explain why I couldn't save something to your account.

6. Define a contract that returns a resource that has at least 1 field in it. Then, write 2 transactions:

  i. A transaction that first saves the resource to account storage, then loads it out of account storage, logs a field inside the resource, and destroys it.

  ii.A transaction that first saves the resource to account storage, then borrows a reference to it, and logs a field inside the resource.


## Quest Chapter 4 Day 2

1. What does .link() do?

2. In your own words (no code), explain how we can use resource interfaces to only expose certain things to the /public/ path.

3. Deploy a contract that contains a resource that implements a resource interface. Then, do the following:

  i. In a transaction, save the resource to storage and link it to the public with the restrictive interface.

  ii. Run a script that tries to access a non-exposed field in the resource interface, and see the error pop up.

  iii. Run the script and access something you CAN read from. Return it from the script.


## Quest Chapter 4 Day 3

1. Why did we add a Collection to this contract? List the two main reasons.

2. What do you have to do if you have resources "nested" inside of another resource? ("Nested resources")

3. Brainstorm some extra things we may want to add to this contract. Think about what might be problematic with this contract and how we could fix it.

  Idea #1: Do we really want everyone to be able to mint an NFT? 🤔.

  Idea #2: If we want to read information about our NFTs inside our Collection, right now we have to take it out of the Collection to do so. Is this good?


## Quest Chapter 4 Day 4

1. Because we had a LOT to talk about during this Chapter, I want you to do the following:

Take our NFT contract so far and add comments to every single resource or function explaining what it's doing in your own words. Something like this:

pub contract CryptoPoops {
  pub var totalSupply: UInt64

  // This is an NFT resource that contains a name,
  // favouriteFood, and luckyNumber
  pub resource NFT {
    pub let id: UInt64

    pub let name: String
    pub let favouriteFood: String
    pub let luckyNumber: Int

    init(_name: String, _favouriteFood: String, _luckyNumber: Int) {
      self.id = self.uuid

      self.name = _name
      self.favouriteFood = _favouriteFood
      self.luckyNumber = _luckyNumber
    }
  }

  // This is a resource interface that allows us to... you get the point.
  pub resource interface CollectionPublic {
    pub fun deposit(token: @NFT)
    pub fun getIDs(): [UInt64]
    pub fun borrowNFT(id: UInt64): &NFT
  }

  pub resource Collection: CollectionPublic {
    pub var ownedNFTs: @{UInt64: NFT}

    pub fun deposit(token: @NFT) {
      self.ownedNFTs[token.id] <-! token
    }

    pub fun withdraw(withdrawID: UInt64): @NFT {
      let nft <- self.ownedNFTs.remove(key: withdrawID) 
              ?? panic("This NFT does not exist in this Collection.")
      return <- nft
    }

    pub fun getIDs(): [UInt64] {
      return self.ownedNFTs.keys
    }

    pub fun borrowNFT(id: UInt64): &NFT {
      return &self.ownedNFTs[id] as &NFT
    }

    init() {
      self.ownedNFTs <- {}
    }

    destroy() {
      destroy self.ownedNFTs
    }
  }

  pub fun createEmptyCollection(): @Collection {
    return <- create Collection()
  }

  pub resource Minter {

    pub fun createNFT(name: String, favouriteFood: String, luckyNumber: Int): @NFT {
      return <- create NFT(_name: name, _favouriteFood: favouriteFood, _luckyNumber: luckyNumber)
    }

    pub fun createMinter(): @Minter {
      return <- create Minter()
    }

  }

  init() {
    self.totalSupply = 0
    self.account.save(<- create Minter(), to: /storage/Minter)
  }
}

## Quest Chapter 5 Day 1


## Quest Chapter 5 Day 2


## Quest Chapter 5 Day 3

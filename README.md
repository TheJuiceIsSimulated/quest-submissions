# FLOW Testnet Address:
0x8442e312e8a9534e


## Quest Chapter 1 Day 1 ✅
  
  **1. Explain what the Blockchain is in your own words.**

   A blockchain is a decentralized digital public ledger. Broken down, that means the blockchain is a record of all transactions made on a specific network, no single entity has control over the blockchain, the blockchain exists solely in the digital realm, and anyone can view, make changes to, or store data on the blockchain at any time (it's an open and transparent network).
  
  **2. Explain what a Smart Contract is.**

  A Smart Contract is a program (kind of like a middleman), or "rulebook," that a developer makes on a blockchain so that users can interact with/do certain things on the blockchain. 

  **3. Explain the difference between a script and a transaction.**

  A transaction modifies data on a blockchain and costs money (gas), whereas scripts read data from a blockchain and are free. 
  
  
  

## Quest Chapter 1 Day 2 ✅

  **1. What are the 5 Cadence Programming Language Pillars?**
  
  The five Cadence Programing Language Pillars are Safety and Security, Clarity, Approachability, Developer Experience, and Resource Oriented Programming.
  
  **2. In your opinion, even without knowing anything about the Blockchain or coding, why could the 5 Pillars be useful (you don't have to answer this for #5)?**
  
  Safety and Security is useful on Cadence because the more secure a Smart Contract is, it's really hard to be hack if a developer codes the Cadence contract well. The safer and more secure a Cadence Smart Contract is, the better it will be (developers would be able to read it easier, and because they can read it easier, they can understand what's being executed in the code and can more easily identify any bugs, which will help the user's experience/interaction with the smart contract).

  Clarity is useful on Cadence because its code is very easy to read compared to other languages (like Ethereum's Solidity), which is helpful. If a dev is ever minting NFTs or interacting with a DApp, the ability to read the smart contract code is really important so the dev knows that they're not going to be hacked/so the dev knows the contract isn't malicious in any other way. Clarity of the smart contract is also hugely helpful in ensuring that the code is human readable to prevent making any REALLY BAD AND PERMANENT coding errors.
  
  Approachability and Developer Experience are useful on Cadence because since Cadence is very easy to read in comparison to other programming languages, it's a great onboarding programming language for people to get into the Web3 space as developers. Cadence also offers approachability in that it offers a good coding environment for learning. (But LOL PlayGround reeeally needs to be fixed ASAP 😂)


## Quest Chapter 2 Day 1 ✅

**1. Deploy a contract to account `0x03` called "JacobTucker". Inside that contract, declare a constant variable named `is`, and make it have type `String`. Initialize it to "the best" when your contract gets deployed.**

![image](https://user-images.githubusercontent.com/104703860/170118126-f9f99f99-76da-4254-a318-651a7700d064.png)

**2. Check that your variable `is` actually equals "the best" by executing a script to read that variable. Include a screenshot of the output.** 

![image](https://user-images.githubusercontent.com/104703860/170118192-7f44532e-965c-426d-b919-35c691d40f32.png)




## Quest Chapter 2 Day 2 ✅

**1. Explain why we wouldn't call `changeGreeting` in a script.** 

You can't call changeGreeting in a script because the script tab is only for reading the contract, not for modifying the contract. Calling functions (making the function run) that modify the code in the contract are done in the transactions tab.

**2. What does the `AuthAccount` mean in the `prepare` phase of the transaction?**

In the prepare phase of the transaction, AuthAccount means that it's allowing the smart contract to access data/information in a user's account/address. This occurs when a user signs a transaction in their FLOW wallet.  

**3. What is the difference between the `prepare` phase and the `execute` phase in the transaction?**

The prepare phase (1st phase) of the transaction allows the smart contract ot access information and data in a user's account, and the execute phase (2nd phase) of the transaction calls functions to change data in a user's account/address on the blockchain.


**4. This is the hardest quest so far, so if it takes you some time, do not worry! I can help you in the Discord if you have questions.**

- Add two new things inside your contract:

  - A variable named `myNumber` that has type `Int` (set it to 0 when the contract is deployed)
  - A function named `updateMyNumber` that takes in a new number named `newNumber` as a parameter that has type `Int` and updates `myNumber` to be `newNumber`

![image](https://user-images.githubusercontent.com/104703860/170653422-9f7bde07-f03e-46f8-88d3-5db9d1868300.png)

```cadence
pub contract HelloWorld {

    pub var myNumber: Int
    
    pub fun updateMyNumber(newNumber: Int) {
      self.myNumber = newNumber
    }

    init() {
    self.myNumber = 0
    }
}
```
  
- Add a script that reads `myNumber` from the contract

![script 1](https://user-images.githubusercontent.com/104703860/170653501-cfa062db-c072-4acf-8b27-f725391f7390.png)

```cadence
import HelloWorld from 0x01

pub fun main (): Int {
    return HelloWorld.myNumber
}
```

- Add a transaction that takes in a parameter named `myNewNumber` and passes it into the `updateMyNumber` function. Verify that your number changed by running the script again.

![transaction ch2d2](https://user-images.githubusercontent.com/104703860/170653595-088d434a-796b-4020-9017-faf41dab8d61.png)

```cadence
import HelloWorld from 0x01

transaction(myNewNumber: Int) {

  prepare(signer: AuthAccount) {}

  execute {
    HelloWorld.updateMyNumber(newNumber: myNewNumber)
  }
}
```

![script 2](https://user-images.githubusercontent.com/104703860/170653696-200b4303-386f-4a38-a7e2-d30797e78a73.png)




## Quest Chapter 2 Day 3 ✅

**1. In a script, initialize an array (that has length == 3) of your favourite people, represented as `String`s, and `log` it.**

In the third line of code, I tried to do 'log(favoritePeople)' instead of 'return(favoritePeople)' but I got the error message "Missing return statement" in the Playground & couldn't execute the code. I don't know what I was doing wrong. 

![image](https://user-images.githubusercontent.com/104703860/171033861-8a1f3d8a-44fc-485f-a7cc-a9fce3e256a3.png)

```cadence
pub fun main (): [String] {
 var favoritePeople: [String] = ["myReflection", "myMother", "myCat"]
 return(favoritePeople)
}
```

**2. In a script, initialize a dictionary that maps the `String`s Facebook, Instagram, Twitter, YouTube, Reddit, and LinkedIn to a `UInt64` that represents the order in which you use them from most to least. For example, YouTube --> 1, Reddit --> 2, etc. If you've never used one before, map it to 0!**

![image](https://user-images.githubusercontent.com/104703860/171033683-3eafecac-7acc-4f69-8d04-ee65391ba9b5.png)

```cadence
pub fun main (): {String: UInt64} {
 var socialMedia: {String: UInt64} = {"Facebook": 0, "YouTube": 1, "Twitter": 2, "Reddit": 3, "LinkedIn": 4, "Instagram": 5}
 return(socialMedia)
}
```

**3. Explain what the force unwrap operator `!` does, with an example different from the one I showed you (you can just change the type).**

The force upwarap operator `!` makes it so that we can get the actual value that is mapped (matched) to an existing dictionary key in a dictionary.

![image](https://user-images.githubusercontent.com/104703860/171033529-6d3a42ed-ff72-480f-bea5-f4d675235446.png)

```cadence
pub fun main(): String {
 let hotOrNot: {String: String} = {"Tania": "Hot", "Maserati": "So-So", "Okra": "Not"}
 return hotOrNot["Tania"]!
}
```

**4. Using this picture below, explain...**

  **◦ What the error message means**

  **◦ Why we're getting this error**

  **◦ How to fix it**

![image](https://user-images.githubusercontent.com/104703860/169172973-6b7551c6-9d9b-4616-a3e9-0a5f01c16b55.png)

The error message means that because `string` is the variable declared in the statement, the program is expecting you to return a string. However, every value returned from a dictionary will be an optional type, represented by `?`, so that is why "got String?" is in the error message. You can fix this in two ways. 

First, you can include the force unwrap operator `!` at the end of `return thing[0x03]`. 

```cadence
pub fun main (): String {
 let thing: {Address: String} = {0x01: "One", 0x02: "Two", 0x03, "Three"}
 return thing[0x03]!
 ]
```

The second way to fix it is by declaring an optional variable type `String?` instead of just a `String` type. In this way, you're able to get an actual value returned to you instead of the error message.

```cadence
pub fun main (): String? {
 let thing: {Address: String} = {0x01: "One", 0x02: "Two", 0x03, "Three"}
 return thing[0x03]
 ]
```




## Quest Chapter 2 Day 4 ✅

**1. Deploy a new contract that has a Struct of your choosing inside of it (must be different than `Profile`).**

**2. Create a dictionary or array that contains the Struct you defined.**

**3. Create a function to add to that array/dictionary.**

![image](https://user-images.githubusercontent.com/104703860/171067400-5b566378-24b8-4908-944c-5cdd38ac3a3a.png)

```cadence
pub contract carSpecs {

    pub var autos: {String: Auto}

    pub struct Auto {
        pub let make: String
        pub let model: String
        pub let exteriorColor: String
        pub let interiorColor: String

        init(_make: String, _model: String, _exteriorColor: String, _interiorColor: String) {
            self.make = _make
            self.model = _model 
            self.exteriorColor = _exteriorColor
            self.interiorColor = _interiorColor
        }
    }
    pub fun addAuto(make: String, model: String, exteriorColor: String, interiorColor: String) {
        let newAuto = Auto(_make:make, _model: model, _exteriorColor: exteriorColor, _interiorColor: interiorColor)
        self.autos[make] = newAuto
    }
    init () {
        self.autos = {}
    }
}
```

**4. Add a transaction to call that function in step 3.**

![image](https://user-images.githubusercontent.com/104703860/171067505-ddcf5a47-ed87-455c-a2d9-f26747b970f7.png)

```cadence
import carSpecs from 0x01

transaction(make: String, model: String, exteriorColor: String, interiorColor: String) {

  prepare(signer: AuthAccount) {}
  
  execute {
    carSpecs.addAuto(make: make, model: model, exteriorColor: exteriorColor, interiorColor: interiorColor)
    log("Get that money, hunny.")
  }
}
```

**5. Add a script to read the Struct you defined.**

![image](https://user-images.githubusercontent.com/104703860/171067564-22f0c01c-958a-4be1-af4f-da7d734a277f.png)

```cadence
import carSpecs from 0x01

pub fun main(make:String): carSpecs.Auto {
  return carSpecs.autos [make]!
}
```




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

This is a `string` type resource. 

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




## Quest Chapter 3 Day 2 🆗

**1. Write your own smart contract that contains two state variables: an array of resources, and a dictionary of resources. Add functions to remove and add to each of them. They must be different from the examples above.**

```cadence
pub contract Cars {

  pub var arrayOfAutos: @[Auto]

  pub var dictionaryOfAutos: @{String: Auto}

  pub resource Auto {
    pub let makeAndModel: String
    init () {
      self.makeAndModel = "Lotus Exige"
    }
  }

  pub fun addAuto(auto: @Auto) {
    self.arrayOfAutos.append(<- auto)
  }
  
  pub fun removeAuto(index: Int): @Auto {
    return <- self.arrayOfAutos.remove(at: index)
  }

  pub fun addAuto (auto: @Auto) {
    let key = auto.makeAndModel
    
    let oldAuto <- self.dictionaryOfAutos[key] <- auto
    destroy oldAuto
  }
  
  pub fun removeAuto(key: String): @Auto {
    let auto <- self.dictionaryofAutos.remove(key: key) ?? panic("Auto not found!")
    return <- auto
  }

 init () {
    self.arrayOfAutos <- []
  }

 init () {
    self.dictionaryOfAutos <- {}
  }

}
```

I got the following error messages and don't know how to fix them - I tried moving some lines of code around already, but it just made the error messages worse. I definitely need some help here.

![image](https://user-images.githubusercontent.com/104703860/171969044-9e92ff69-0389-4b4c-9dd5-712b0c8f901e.png)




## Quest Chapter 3 Day 3 🆗

**1. Define your own contract that stores a dictionary of resources. Add a function to get a reference to one of the resources in the dictionary.**

![image](https://user-images.githubusercontent.com/104703860/172017743-f0f1aba8-2507-4ceb-9d06-0f783a9054a8.png)

```cadence
pub contract AmericanFootball {

  pub var dictionaryOfTeams: @{String: Team}
  
  pub resource Team {
    pub let division: String
    init (_division: String) {
      self.division = _division
    }
  }
  
  pub fun getReference(key: String): &Team {
    return &self.dictionaryOfTeams[key] as &Team
  }
  
  init () {
    self.dictionaryOfTeams <- {
      "Philadelphia Eagles": <- create Team(_division: "NFC East"),
      "Denver Broncos": <- create Team(_division: "AFC West")
    }
  }
}
```

**2. Create a script that reads information from that resource using the reference from the function you defined in part 1.**

![image](https://user-images.githubusercontent.com/104703860/172017778-60607958-004a-479e-9238-657fd36a38c9.png)

```cadence
import AmericanFootball from 0x01

pub fun main(): String {
  let ref = AmericanFootball.getReference(key: "Philadelphia Eagles")
  return ref.division
}
```

**3. Explain, in your own words, why references can be useful in Cadence.**

References can be very, very useful in Cadence because it allows a developer to interact with a struct or a resource (typically) without having to type out however many lines of code that struct or resource has. In other words, a developer doesn't have to move a struct or resource around in order to look at or update its fields. 




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

THE FIXED CODE
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




## Quest Chapter 3 Day 5

**1. For today's quest, you will be looking at a contract and a script. You will be looking at 4 variables (a, b, c, d) and 3 functions (publicFunc, contractFunc, privateFunc) defined in `SomeContract`. In each AREA (1, 2, 3, and 4), I want you to do the following: for each variable (a, b, c, and d), tell me in which areas they can be read (read scope) and which areas they can be modified (write scope). For each function (publicFunc, contractFunc, and privateFunc), simply tell me where they can be called.**

```CADENCE
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
```

This is a script that imports the contract above:

```CADENCE
import SomeContract from 0x01

pub fun main() {
  /**************/
  /*** AREA 4 ***/
  /**************/
}
```

AREA 1

Read Scope: a, b, c, d

Write Scope: a, b, c, d

publicFunc, contractFunc, privateFunc can be called here


AREA 2:

Read Scope: a, b, c

Write Scope: a, b, c

publicFunc, contractFunc can be called here


AREA 3:

Read Scope: a, b, c

Write Scope: a, b, c

publicFunc, contractFunc can be called here


AREA 4:

Read Scope: a, b

Write Scope: a

publicFunc can be called here




## Quest Chapter 4 Day 1 🆗

**1. Explain what lives inside of an account.**

There are two things that live inside accounts on Flow:

 - Contract Code
 
   - Once a developer deploys a contract to an account to put on Mainnet, it lives inside that account. Multiple contract scan be deployed to and live inside an account
   
 - Account Storage
 
   - All the data of an account gets stored in account storage

**2. What is the difference between the  `/storage/`, `/public/`, and `/private/` paths?**

The difference between these three paths is that each path allows a developer to get to certain data. The `/storage/` path can only be accessed by the account owner (otherwise, someone malicious could steal all of your data) and ALL of the account's data lives here. Data in the `/public/` path is available to everyone. Data in the `/private/` path is available to the account owner and people who the account owner gives access to. 

**3. What does `.save()` do? What does `.load()` do? What does `.borrow()` do?**

`.save()` saves something to the `/storage/` path. 

`.load()` takes something out of `/storage/`. 

`.borrow()` lets us only look at something in `/storage/`. 

**4. Explain why we couldn't save something to our account storage inside of a script.**

We couldn't save something to account storage inside of a script because in order to access `/storage/`, we need to use our `AuthAccount` type. We can only use our `AUthAccount` type by signing a transaction in the `prepare` phase. 

**5. Explain why I couldn't save something to your account.**

You couldn't save something to my account because only I, the account owner, can access my own `/storage/` path. The only way you would be able to save something to my account is if I give you permission through the `/private/` path. 

**6. Define a contract that returns a resource that has at least 1 field in it. Then, write 2 transactions:**

![image](https://user-images.githubusercontent.com/104703860/172037279-efb53508-17df-4e63-ac39-2b8b22237df6.png)

```cadence
pub contract SportsCars {

 pub resource Hardtops {
  pub var auto: String 
  init () {
   self.auto = "Lotus Exige"
  }
 }
 
 pub fun createHardtops(): @Hardtops {
  return <- create Hardtops()
 }
 
}
```

  **i. A transaction that first saves the resource to account storage, then loads it out of account storage, logs a field inside the resource, and destroys it.**
  
  I didn't know how to combine the two into one transaction, I tried different ways of combining but kept getting errors.
  
  ![image](https://user-images.githubusercontent.com/104703860/172037286-98915095-bb27-4f72-82da-6f86c9cd411b.png)
  
  ```cadence
import SportsCars from 0x01
transaction() {
   prepare(signer: AuthAccount) {
     let testDrive <- SportsCars.createHardtops()
     signer.save(<- testDrive, to: /storage/MyTestDrive)
    
   }
    
   execute {
    
   }
}
  ```
  
  ![image](https://user-images.githubusercontent.com/104703860/172037301-85eb6630-0a4e-4c78-b394-d3b8c9fd93fe.png)
  
  ```cadence
import SportsCars from 0x01
transaction() {
    prepare(signer: AuthAccount) {
        let testDrive <- signer.load<@SportsCars.Hardtops>(from: /storage/MyTestDrive)
                      ?? panic("A `@SportsCars.Hardtops` resource does not live here.")
        log(testDrive.auto)
    
        destroy testDrive
    }

    execute {

    }
}
  ```

  **ii.A transaction that first saves the resource to account storage, then borrows a reference to it, and logs a field inside the resource.**
  
  ![image](https://user-images.githubusercontent.com/104703860/172037311-f0255df0-c249-4bcb-b674-a28c8519d054.png)
  
  ```cadence
import SportsCars from 0x01
transaction() {
    prepare(signer: AuthAccount) {
        let testDrive = signer.borrow<&SportsCars.Hardtops>(from: /storage/MyTestDrive)
                      ?? panic("A `@SportsCars.Hardtops` resource does not live here.")
    log(testDrive.auto)
  
    }

    execute {

    }
}
  ```
  
 I don't know why the program is panicking and not logging the value here, all of the other transactions worked fine.





## Quest Chapter 4 Day 2 🆗

**1. What does `.link()` do?**

`.link()` allows a developer to "link" resources in the `/storage/` path to the `/public/` or `/private/` paths so the resource can be publically accessible or viewable in the case of `/public/` OR accessible/viewable to whoever the developer wants to give access to `/storage/` in the case of `/private/`.

**2. In your own words (no code), explain how we can use resource interfaces to only expose certain things to the `/public/` path.**

We can use resource interfaces to only expose certain things to the `/public/` path by only exposing the fields we want to expose to the pubic and then by linking that resource interface to the `/public/` path using `.link()`. That will restrict that reference to only use the resource interface that we defined and make it secure from any hackers that want to change our info. 

**3. Deploy a contract that contains a resource that implements a resource interface. Then, do the following:**

![image](https://user-images.githubusercontent.com/104703860/172054744-2f73347d-5e1a-444e-8b3a-2402f05c01af.png)

```cadence
pub contract SportsCars {

    pub resource interface IDrive {
        pub var auto: String
    }

    pub resource Drive: IDrive {
        pub var auto: String

        pub fun changeAuto(newAuto: String) {
            self.auto = newAuto
        }

        init () {
            self.auto = "Lotus Exige"
        }
    }

    pub fun createDrive(): @Drive {
        return <- create Drive()
    }

}
```

  **i. In a transaction, save the resource to storage and link it to the public with the restrictive interface.**
  
  ![image](https://user-images.githubusercontent.com/104703860/172054763-eaf8d6ca-a4cd-4dd9-9891-27ec1ca5e76a.png)
  
  ```cadence
import SportsCars from 0x01
transaction () {
  prepare(signer: AuthAccount) {

    signer.save(<- SportsCars.createDrive(), to: /storage/MyScenicDriveResource)
  
    signer.link<&SportsCars.Drive{SportsCars.IDrive}>(/public/MyScenicDriveResource, target: /storage/MyScenicDriveResource)
  }
  
  execute {

  }
}
  ```

  **ii. Run a script that tries to access a non-exposed field in the resource interface, and see the error pop up.**
  
  I ran a transaction instead of a script here, I think there's a typo.
  
  ![image](https://user-images.githubusercontent.com/104703860/172054773-528e52e4-6d3f-4b79-81a1-ec99e1731424.png)
  
  ```cadence
  import SportsCars from 0x01
transaction(address: Address) {
    prepare(signer: AuthAccount) {

    }

    execute {
        let publicCapability: Capability<&SportsCars.Drive> = 
            getAccount(address).getCapability<&SportsCars.Drive>(/public/MyScenicDriveResource)

        let driveResource: &SportsCars.Drive = publicCapability.borrow() ?? panic("The capability does not exist or you did not specify the right type when you got the capability.")

        driveResource.changeAuto(newAuto: "Ferrari Enzo")
    }
}
  ```

  **iii. Run the script and access something you CAN read from. Return it from the script.**
  
  ![image](https://user-images.githubusercontent.com/104703860/172054787-3373992d-166e-4266-88f2-c5393d631c61.png)
  
```cadence
import SportsCars from 0x01
pub fun main(address: Address): String {
  let publicCapability: Capability<&SportsCars.Drive{SportsCars.IDrive}> =
      getAccount(address).getCapability<&SportsCars.Drive{SportsCars.IDrive}>(/public/MyScenicDriveResource)

  let driveResource: &SportsCars.Drive{SportsCars.IDrive} = publicCapability.borrow() ?? panic("The capability does not exist or you did not specify the right type when you got the capability.")

  return driveResource.auto 
}
```





## Quest Chapter 4 Day 3 🆗

**1. Why did we add a Collection to this contract? List the two main reasons.**

We added a Collection to this contract because

- 1. If we wanted to have multiple NFTs, we would have to remember each individual storage path we gave to each NFT, which is vey inefficient and annoying. 
- 2. No one can give us any NFTs because only the account owner can store an NFT in `/storage/` directly, so no one can mint us an NFT.

**2. What do you have to do if you have resources "nested" inside of another resource? ("Nested resources")**

If you have resources "nested" inside of another resource, you must declare a `destroy` function that manually destroys the "nested" resources with the `destroy` keyword.

**3. Brainstorm some extra things we may want to add to this contract. Think about what might be problematic with this contract and how we could fix it.**

  **◦ Idea #1: Do we really want everyone to be able to mint an NFT? 🤔.**
  
  **◦ Idea #2: If we want to read information about our NFTs inside our Collection, right now we have to take it out of the Collection to do so. Is this good?**

No, we don't want everyone to be able to mint an NFT. Sometimes, we only want specific addresses to be able to mint, like in a White List/Allow List scenario. So, we need to add a resource that mints NFTs. In that way, only an address that owns that resource has to ability to mint an NFT. 

Taking our NFTs out of our Collection in order to read something about it isn't good because we only want to have one "container" for all our NFTs to hang out in for ease of access and functionality. In order to read our NFTs without taking them out of the collection, we need to add a `.borrow()` function to our NFT Contract because the `.borrow()` function allows us to look at data in `/storage/`.




## Quest Chapter 4 Day 4 🆗

**1. Because we had a LOT to talk about during this Chapter, I want you to do the following:**

**Take our NFT contract so far and add comments to every single resource or function explaining what it's doing in your own words. Something like this:**

```CADENCE
pub contract CryptoPoops {
  pub var totalSupply: UInt64

// This is an NFT resource that contains a name, favouriteFood, and luckyNumber
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

// This is a resource interface that allows us to only expose `deposit` and `getIDs` to the public
  pub resource interface CollectionPublic {
//This function allows us to deposit NFTs
    pub fun deposit(token: @NFT)
This function allows us to get a list of all of the NFT IDs in our collection.
    pub fun getIDs(): [UInt64]
//This borrowNFT function allows the metadata fields to be accessible to the public
    pub fun borrowNFT(id: UInt64): &NFT
  }

//This resource makes it so that `Collection` implements `CollectionPublic`
  pub resource Collection: CollectionPublic {
    pub var ownedNFTs: @{UInt64: NFT}

//This function allows us to deposit an NFT to our Collection
    pub fun deposit(token: @NFT) {
      self.ownedNFTs[token.id] <-! token
    }
//This function allows us to withdraw an NFT from our Collection. If the NFT doesn't exist, it panics and aborts the program.
    pub fun withdraw(withdrawID: UInt64): @NFT {
      let nft <- self.ownedNFTs.remove(key: withdrawID) 
              ?? panic("This NFT does not exist in this Collection.")
      return <- nft
    }

//This function returns an array of all of the NFTs in our Collection.
    pub fun getIDs(): [UInt64] {
      return self.ownedNFTs.keys
    }

//This function allows us to read our NFTs without taking them out of the Collection
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

//This function allows us to save a `Collection` to our account storage so we can manage our NFTs better. 
  pub fun createEmptyCollection(): @Collection {
    return <- create Collection()
  }

//This resource Minter allows anyone who holds it to mint NFTs
  pub resource Minter {

//This function mints a new NFT resource and `createNFT` function is moved into the `Minter` resource
    pub fun createNFT(name: String, favouriteFood: String, luckyNumber: Int): @NFT {
      return <- create NFT(_name: name, _favouriteFood: favouriteFood, _luckyNumber: luckyNumber)
    }

//This function creates a new Minter resource
    pub fun createMinter(): @Minter {
      return <- create Minter()
    }

  }

//This `init` function saves the `Minter` resource to account storage
  init() {
    self.totalSupply = 0
    self.account.save(<- create Minter(), to: /storage/Minter)
  }
}
```




## Quest Chapter 5 Day 1

**1. Describe what an event is, and why it might be useful to a client.**

**2. Deploy a contract with an event in it, and emit the event somewhere else in the contract indicating that it happened.**

**3. Using the contract in step 2), add some pre conditions and post conditions to your contract to get used to writing them out.**

**4. For each of the functions below (numberOne, numberTwo, numberThree), follow the instructions.**

```CADENCE
pub contract Test {

  // TODO
  // Tell me whether or not this function will log the name.
  // name: 'Jacob'
  pub fun numberOne(name: String) {
    pre {
      name.length == 5: "This name is not cool enough."
    }
    log(name)
  }

  // TODO
  // Tell me whether or not this function will return a value.
  // name: 'Jacob'
  pub fun numberTwo(name: String): String {
    pre {
      name.length >= 0: "You must input a valid name."
    }
    post {
      result == "Jacob Tucker"
    }
    return name.concat(" Tucker")
  }

  pub resource TestResource {
    pub var number: Int

    // TODO
    // Tell me whether or not this function will log the updated number.
    // Also, tell me the value of `self.number` after it's run.
    pub fun numberThree(): Int {
      post {
        before(self.number) == result + 1
      }
      self.number = self.number + 1
      return self.number
    }

    init() {
      self.number = 0
    }

  }

}
```




## Quest Chapter 5 Day 2

**1. Explain why standards can be beneficial to the Flow ecosystem.**

**2. What is YOUR favourite food?**

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




## Quest Chapter 5 Day 3

**1. What does "force casting" with `as!` do? Why is it useful in our Collection?**

**2. What does `auth do?` When do we use it?**

**3. This last quest will be your most difficult yet. Take this contract:**

```CADENCE
import NonFungibleToken from 0x02
pub contract CryptoPoops: NonFungibleToken {
  pub var totalSupply: UInt64

  pub event ContractInitialized()
  pub event Withdraw(id: UInt64, from: Address?)
  pub event Deposit(id: UInt64, to: Address?)

  pub resource NFT: NonFungibleToken.INFT {
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

  pub resource Collection: NonFungibleToken.Provider, NonFungibleToken.Receiver, NonFungibleToken.CollectionPublic {
    pub var ownedNFTs: @{UInt64: NonFungibleToken.NFT}

    pub fun withdraw(withdrawID: UInt64): @NonFungibleToken.NFT {
      let nft <- self.ownedNFTs.remove(key: withdrawID) 
            ?? panic("This NFT does not exist in this Collection.")
      emit Withdraw(id: nft.id, from: self.owner?.address)
      return <- nft
    }

    pub fun deposit(token: @NonFungibleToken.NFT) {
      let nft <- token as! @NFT
      emit Deposit(id: nft.id, to: self.owner?.address)
      self.ownedNFTs[nft.id] <-! nft
    }

    pub fun getIDs(): [UInt64] {
      return self.ownedNFTs.keys
    }

    pub fun borrowNFT(id: UInt64): &NonFungibleToken.NFT {
      return &self.ownedNFTs[id] as &NonFungibleToken.NFT
    }

    init() {
      self.ownedNFTs <- {}
    }

    destroy() {
      destroy self.ownedNFTs
    }
  }

  pub fun createEmptyCollection(): @NonFungibleToken.Collection {
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
    emit ContractInitialized()
    self.account.save(<- create Minter(), to: /storage/Minter)
  }
}
```

and add a function called `borrowAuthNFT` just like we did in the section called "The Problem" above. Then, find a way to make it publically accessible to other people so they can read our NFT's metadata. Then, run a script to display the NFTs metadata for a certain `id`.

You will have to write all the transactions to set up the accounts, mint the NFTs, and then the scripts to read the NFT's metadata. We have done most of this in the chapters up to this point, so you can look for help there :)

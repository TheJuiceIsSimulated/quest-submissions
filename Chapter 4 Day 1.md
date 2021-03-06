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
  
_THE NEW TRANSACTION ANSWER_:
![image](https://user-images.githubusercontent.com/104703860/172977781-eb32a0a2-b8ca-446a-b2c0-c3856d470fdb.png)
  
  
_THE OLD TRANSACTION ANSWER_:
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

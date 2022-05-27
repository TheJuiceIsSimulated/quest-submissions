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



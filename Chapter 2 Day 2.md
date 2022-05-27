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

![image](https://user-images.githubusercontent.com/104703860/170615918-fe5f45e5-2ee4-4652-a6bb-58b88ef491f4.png)

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

![image](https://user-images.githubusercontent.com/104703860/170615983-48dd2e0d-f6c4-4c19-b401-d69abaa35326.png)

```cadence
import HelloWorld from 0x01

pub fun main (): Int {
    return HelloWorld.myNumber
}
```

- Add a transaction that takes in a parameter named `myNewNumber` and passes it into the `updateMyNumber` function. Verify that your number changed by running the script again.

![image](https://user-images.githubusercontent.com/104703860/170616076-de28d9a7-6634-4375-89f8-26971b02713c.png)

```cadence
import HelloWorld from 0x01

transaction(myNewNumber: Int) {

  prepare(signer: AuthAccount) {}

  execute {
    HelloWorld.updateMyNumber(newNumber: myNewNumber)
  }
}
```

![image](https://user-images.githubusercontent.com/104703860/170616112-b267dfa6-edfa-4ddb-9712-08cbb95fc246.png)

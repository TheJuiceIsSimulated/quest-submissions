## Quest Chapter 5 Day 1 🆗

**1. Describe what an event is, and why it might be useful to a client.**

An event is a smart contract's way of communicating to the outside world that something happened, like if an NFT was minted. Events could be useful to clients for two reasons:

1. So clients can update thier code accordingly, like the live claim feed on floats.city that shows every time a FLOAT is minted and claimed by an address
2. So clients can avoid constantly checking the smart contract to check if an event occurred, which is inefficient and annoying

**2. Deploy a contract with an event in it, and emit the event somewhere else in the contract indicating that it happened.**

```cadence
pub contract YouMintedAnNFT {
  
  pub event MintedNFT(id: UInt64)
  
  pub resource NFT {
    pub let id: UInt64
    
    init() {
      self.id = self.uuid
      
      emit MintedNFT(id: self.id)
    }
  }
}
```

**3. Using the contract in step 2), add some pre conditions and post conditions to your contract to get used to writing them out.**

```cadence
pub contract YouMintedAnNFT {
  
  pub fun logMoney(money: String) {
    pre {
      money.length > 5: "You don't have enough FLOW to mint this NFT."
    }
    log(money)
  }
  
  pub fun updateMoney() {
    post {
      before(self.number) ==self.number - 1
    }
      self.number = self.number + 1
  
  pub event MintedNFT(id: UInt64)
  
  pub resource NFT {
    pub let id: UInt64
    
    init() {
      self.id = self.uuid
      
      emit MintedNFT(id: self.id)
    }
  }
}
```

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
    return name.concat("Tucker")
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
_THE NEW ANSWER_:
numberOne: Yes, the function will log the name "Jacob" (I didn't know what == meant before, so that's why I got confused.)

numberTwo: Yes, the function will return a value.

numberThree: No, the function won't run because the pre-condition of 5 isn't met


_THE OLD ANSWER_: 

numberOne: No, the function will not log the name "Jacob"

numberTwo: Yes, the function will return a value.

numberThree: Yes, the function will log the updated number. After it's run, the value of `self.number` will be 2.

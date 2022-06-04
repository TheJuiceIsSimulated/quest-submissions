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

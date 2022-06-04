## Quest Chapter 3 Day 3

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

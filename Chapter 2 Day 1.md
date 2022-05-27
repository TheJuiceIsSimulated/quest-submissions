## Quest Chapter 2 Day 1 ✅

**1. Deploy a contract to account `0x03` called "JacobTucker". Inside that contract, declare a constant variable named `is`, and make it have type `String`. Initialize it to "the best" when your contract gets deployed.**

![image](https://user-images.githubusercontent.com/104703860/170118126-f9f99f99-76da-4254-a318-651a7700d064.png)

```Cadence
pub contract JacobTucker {

    pub let is: String

    init() {
    self.is = "the best"
    }
}
```


**2. Check that your variable `is` actually equals "the best" by executing a script to read that variable. Include a screenshot of the output.** 

![image](https://user-images.githubusercontent.com/104703860/170118192-7f44532e-965c-426d-b919-35c691d40f32.png)

```Cadence
import JacobTucker from 0x03

pub fun main (): String {
return JacobTucker.is
}
```

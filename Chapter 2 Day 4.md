## Quest Chapter 2 Day 4

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

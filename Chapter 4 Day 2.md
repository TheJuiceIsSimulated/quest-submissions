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

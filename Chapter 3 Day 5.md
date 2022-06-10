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

THE NEW ANSWER:

AREA 1

Read Scope: a, b, c, d

Write Scope: a, b, c, d

publicFunc, contractFunc, privateFunc can be called here


AREA 2:

Read Scope: a, b, c

Write Scope: a

publicFunc, contractFunc can be called here


AREA 3:

Read Scope: a, b, c

Write Scope: a

publicFunc, contractFunc can be called here


AREA 4:

Read Scope: a, b

Write Scope: None of the variables are in the write scope of Area 4 because no data that's already on the blockchain can be changed inside a script.

publicFunc can be called here

.
THE OLD ANSWER:

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

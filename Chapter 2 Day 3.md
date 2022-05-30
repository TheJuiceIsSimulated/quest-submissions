## Quest Chapter 2 Day 3 ✅

**1. In a script, initialize an array (that has length == 3) of your favourite people, represented as `String`s, and `log` it.**

In the third line of code, I tried to do 'log(favoritePeople)' instead of 'return(favoritePeople)' but I got the error message "Missing return statement" in the Playground & couldn't execute the code. I don't know what I was doing wrong. 

![image](https://user-images.githubusercontent.com/104703860/171033861-8a1f3d8a-44fc-485f-a7cc-a9fce3e256a3.png)

```cadence
pub fun main (): [String] {
 var favoritePeople: [String] = ["myReflection", "myMother", "myCat"]
 return(favoritePeople)
}
```

**2. In a script, initialize a dictionary that maps the `String`s Facebook, Instagram, Twitter, YouTube, Reddit, and LinkedIn to a `UInt64` that represents the order in which you use them from most to least. For example, YouTube --> 1, Reddit --> 2, etc. If you've never used one before, map it to 0!**

![image](https://user-images.githubusercontent.com/104703860/171033683-3eafecac-7acc-4f69-8d04-ee65391ba9b5.png)

```cadence
pub fun main (): {String: UInt64} {
 var socialMedia: {String: UInt64} = {"Facebook": 0, "YouTube": 1, "Twitter": 2, "Reddit": 3, "LinkedIn": 4, "Instagram": 5}
 return(socialMedia)
}
```

**3. Explain what the force unwrap operator `!` does, with an example different from the one I showed you (you can just change the type).**

The force upwarap operator `!` makes it so that we can get the actual value that is mapped (matched) to an existing dictionary key in a dictionary.

![image](https://user-images.githubusercontent.com/104703860/171033529-6d3a42ed-ff72-480f-bea5-f4d675235446.png)

```cadence
pub fun main(): String {
 let hotOrNot: {String: String} = {"Tania": "Hot", "Maserati": "So-So", "Okra": "Not"}
 return hotOrNot["Tania"]!
}
```

**4. Using this picture below, explain...**

  **◦ What the error message means**

  **◦ Why we're getting this error**

  **◦ How to fix it**

![image](https://user-images.githubusercontent.com/104703860/169172973-6b7551c6-9d9b-4616-a3e9-0a5f01c16b55.png)

The error message means that because `string` is the variable declared in the statement, the program is expecting you to return a string. However, every value returned from a dictionary will be an optional type, represented by `?`, so that is why "got String?" is in the error message. You can fix this in two ways. 

First, you can include the force unwrap operator `!` at the end of `return thing[0x03]`. 

```cadence
pub fun main (): String {
 let thing: {Address: String} = {0x01: "One", 0x02: "Two", 0x03, "Three"}
 return thing[0x03]!
 ]
```

The second way to fix it is by declaring an optional variable type `String?` instead of just a `String` type. In this way, you're able to get an actual value returned to you instead of the error message.

```cadence
pub fun main (): String? {
 let thing: {Address: String} = {0x01: "One", 0x02: "Two", 0x03, "Three"}
 return thing[0x03]
 ]
```

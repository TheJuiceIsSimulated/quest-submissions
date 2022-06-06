## Quest Chapter 4 Day 3 🆗

**1. Why did we add a Collection to this contract? List the two main reasons.**

We added a Collection to this contract because

- 1. If we wanted to have multiple NFTs, we would have to remember each individual storage path we gave to each NFT, which is very inefficient and annoying. 
- 2. No one can give us any NFTs because only the account owner can store an NFT in `/storage/` directly, so no one can mint us an NFT.

**2. What do you have to do if you have resources "nested" inside of another resource? ("Nested resources")**

If you have resources "nested" inside of another resource, you must declare a `destroy` function that manually destroys the "nested" resources with the `destroy` keyword.

**3. Brainstorm some extra things we may want to add to this contract. Think about what might be problematic with this contract and how we could fix it.**

  **◦ Idea #1: Do we really want everyone to be able to mint an NFT? 🤔.**
  
  **◦ Idea #2: If we want to read information about our NFTs inside our Collection, right now we have to take it out of the Collection to do so. Is this good?**

No, we don't want everyone to be able to mint an NFT. Sometimes, we only want specific addresses to be able to mint, like in a White List/Allow List scenario. So, we need to add a resource that mints NFTs. In that way, only an address that owns that resource has to ability to mint an NFT. 

Taking our NFTs out of our Collection in order to read something about it isn't good because we only want to have one "container" for all our NFTs to hang out in for ease of access and functionality. In order to read our NFTs without taking them out of the collection, we need to add a `.borrow()` function to our NFT Contract because the `.borrow()` function allows us to look at data in `/storage/`.

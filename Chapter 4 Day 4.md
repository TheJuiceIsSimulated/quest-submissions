## Quest Chapter 4 Day 4 🆗

**1. Because we had a LOT to talk about during this Chapter, I want you to do the following:**

**Take our NFT contract so far and add comments to every single resource or function explaining what it's doing in your own words. Something like this:**

```CADENCE
pub contract CryptoPoops {
  pub var totalSupply: UInt64

// This is an NFT resource that contains a name,favouriteFood, and luckyNumber
  pub resource NFT {
    pub let id: UInt64

    pub let name: String
    pub let favouriteFood: String
    pub let luckyNumber: Int

    init(_name: String, _favouriteFood: String, _luckyNumber: Int) {
      self.id = self.uuid

      self.name = _name
      self.favouriteFood = _favouriteFood
      self.luckyNumber = _luckyNumber
    }
  }

// This is a resource interface that allows us to only expose `deposit` and `getIDs` to the public
  pub resource interface CollectionPublic {
//This function allows us to deposit NFTs
    pub fun deposit(token: @NFT)
This function allows us to get a list of all of the NFT IDs in our collection.
    pub fun getIDs(): [UInt64]
//This borrowNFT function allows the metadata fields to be accessible to the public
    pub fun borrowNFT(id: UInt64): &NFT
  }

//This resource makes it so that `Collection` implements `CollectionPublic`
  pub resource Collection: CollectionPublic {
    pub var ownedNFTs: @{UInt64: NFT}

//This function allows us to deposit an NFT to our Collection
    pub fun deposit(token: @NFT) {
      self.ownedNFTs[token.id] <-! token
    }
//This function allows us to withdraw an NFT from our Collection. If the NFT doesn't exist, it panics and aborts the program.
    pub fun withdraw(withdrawID: UInt64): @NFT {
      let nft <- self.ownedNFTs.remove(key: withdrawID) 
              ?? panic("This NFT does not exist in this Collection.")
      return <- nft
    }

//This function returns an array of all of the NFTs in our Collection.
    pub fun getIDs(): [UInt64] {
      return self.ownedNFTs.keys
    }

//This function allows us to read our NFTs without taking them out of the Collection
    pub fun borrowNFT(id: UInt64): &NFT {
      return &self.ownedNFTs[id] as &NFT
    }

    init() {
      self.ownedNFTs <- {}
    }

    destroy() {
      destroy self.ownedNFTs
    }
  }

//This function allows us to save a `Collection` to our account storage so we can manage our NFTs better. 
  pub fun createEmptyCollection(): @Collection {
    return <- create Collection()
  }

//This resource Minter allows anyone who holds it to mint NFTs
  pub resource Minter {

//This function mints a new NFT resource and `createNFT` function is moved into the `Minter` resource
    pub fun createNFT(name: String, favouriteFood: String, luckyNumber: Int): @NFT {
      return <- create NFT(_name: name, _favouriteFood: favouriteFood, _luckyNumber: luckyNumber)
    }

//This function creates a new Minter resource
    pub fun createMinter(): @Minter {
      return <- create Minter()
    }

  }

//This `init` function saves the `Minter` resource to account storage
  init() {
    self.totalSupply = 0
    self.account.save(<- create Minter(), to: /storage/Minter)
  }
}
```

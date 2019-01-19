---
Smart Contract: Ñíguez Randomity Engine
Contract Address: '0x031eaE8a8105217ab64359D4361022d0947f4572'
Contract Type: Closed Source
Original Author(s): Scheich R. Ahmed
---

# A Guide for using the Ñíguez Randomity Engine

## On-Chain Usage
- Import Ethereum API into your project | Use the following in Remix IDE (Other platforms may not support GitHub)

  ```
  pragma solidity ^0.5.0;
  import "https://github.com/niguezrandomityengine/ethereumAPI/blob/master/nreAPI.sol";
  ```
  
- Create a Smart Contract as follow:
   ```
  contract Randomness is usingNRE {
  
  }
  ```
  
- Code function to use sequence and set slots, there are 24 sequences i.e **ra()**, **rb()**, **rc()** upto **rx()**.

Example 1
   ```
  contract Randomness is usingNRE {
  
  }
  ```

## Off-Chain Usage


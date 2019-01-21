---
Smart Contract: Ñíguez Randomity Engine
Contract Address: '0x031eaE8a8105217ab64359D4361022d0947f4572'
Block Number: 7097983
Date Deployed: 20 January 2019
Original Author(s): Scheich R. Ahmed
---

# A Guide for using the Ñíguez Randomity Engine

## On-Chain Usage
- Import Ethereum API into your project | Use the following in Remix IDE (Other platforms may not support GitHub)

  ```
  pragma solidity ^0.5.0;
  
  import "https://github.com/niguezrandomityengine/ethereumAPI/nreAPI.sol";  
  ```
  
- Create a Smart Contract as follow:
   ```
  pragma solidity ^0.5.0;
  
  import "https://github.com/niguezrandomityengine/ethereumAPI/nreAPI.sol";
  
  contract Randomness is usingNRE {
  
  }
  ```
  
- Code function to use sequences and set slots, there are 24 sequences i.e **ra()**, **rb()**, **rc()** upto **rx()**.

  **Example 1: Using the explicit sequence to get a 10 digits random number.**
   ```
  pragma solidity ^0.5.0;
  
  import "https://github.com/niguezrandomityengine/ethereumAPI/nreAPI.sol";
  
  contract Randomness is usingNRE {
  
      function randomNumber() public view returns (uint256){
          return (ra()%(10**10));
      }
    
  }
  ```
  
   **Example 2: Using multiple sequences to generate 3 digits random number ranging from 0 to 999.**
   
   This type of random number generation can be used to randomly select validators in a Proof of Stake (PoS) network.
   
   ```
  pragma solidity ^0.5.0;
  
  import "https://github.com/niguezrandomityengine/ethereumAPI/nreAPI.sol";
  
  contract Randomness is usingNRE {
  
      function randomNumber() public view returns (uint256){
          return (((rf()%10)*100)+((rx()%10)*10)+(rm()%10));
      }
    
  }
  ```
  
  **Example 3: Transaction of random numbers into state or local variable.**
   
   The below transaction will consume gas, approximately (40k - 120k) gas per sequence.
   
   ```
  pragma solidity ^0.5.0;
  
  import import "https://github.com/niguezrandomityengine/ethereumAPI/nreAPI.sol";
  
  contract Randomness is usingNRE {

  uint256 public randomNumber;
  
  event rNum(uint256 theNumber);
 
          /**State Variable. */
      function stateRandomNumber() public {
          randomNumber = (((ru()%10)*100)+((re()%10)*10)+(rq()%10));
      }
     
          /**Local Variable. */
      function localRandomNumber() public {
          uint256 randomGame = (((rj()%10)*100)+((rg()%10)*10)+(ri()%10));
          emit rNum(randomGame);
      }
 
   }
  ```
  
  **Example 4: Using the slot of numbers from between the sequence and hashing it for distinct random sequence**
   ```
  pragma solidity ^0.5.0;
  
  import "https://github.com/niguezrandomityengine/ethereumAPI/nreAPI.sol";
  
  contract Randomness is usingNRE {
  
      function randomNumber() public view returns (uint256){
          return (uint256(keccak256((rw()/(10**20))%(10**12))));
      }
    
  }
  ```
- These are merely 4 instances of generating a pseudo-random number, the user could use this numbers in infinite possibilities by using   dynamic slot selections, cross stitching sequences and using them as a salt to hash with user's address or nonce.

## Off-Chain Usage
- For off-chain application use web3.js library, Javascript and the contract (application binary interface) ABI.
- Contract | [ABI](https://github.com/niguezrandomityengine/ethereumAPI/blob/master/ABI.json)

## Conclusion
- Website | [Ñíguez Randomity Engine](https://niguezrandomityengine.github.io/)
- Whitepaper | [ResearchGate](https://www.researchgate.net/publication/330513989_Niguez_Randomity_Engine_Secure_generation_and_usage_of_pseudo-random_numbers_on_the_Ethereum_Blockchain) | [GitHub](https://github.com/niguezrandomityengine/niguezrandomityengine.github.io/blob/master/Niguez%20Randomity%20Engine%20Whitepaper.pdf)
- How to use guide for API | [Guide](https://github.com/niguezrandomityengine/guide/blob/master/guide.md)

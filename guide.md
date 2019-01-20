---
Smart Contract: Ñíguez Randomity Engine
Core Contract Address: '0x031eaE8a8105217ab64359D4361022d0947f4572'
Block Number: 7097983
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
   pragma solidity ^0.5.0;
  
  import "https://github.com/niguezrandomityengine/ethereumAPI/blob/master/nreAPI.sol";
  
  contract Randomness is usingNRE {
  
  }
  ```
  
- Code function to use sequence and set slots, there are 24 sequences i.e **ra()**, **rb()**, **rc()** upto **rx()**.

  **Example 1: Using the explicit sequence to get 10 digit random number.**
   ```
   pragma solidity ^0.5.0;
  
  import "https://github.com/niguezrandomityengine/ethereumAPI/blob/master/nreAPI.sol";
  
  contract Randomness is usingNRE {
  
        function randomNumber() public view returns (uint256){
             return (ra()%(10**10));
        }
    
  }
  ```
  
   **Example 2: Using multple sequence to generate 3 digit random number from 0 to 999.**
   
   This type of random number generation can be used to randomly select validators in Proof of Stake (PoS) network.
   
   ```
   pragma solidity ^0.5.0;
  
  import "https://github.com/niguezrandomityengine/ethereumAPI/blob/master/nreAPI.sol";
  
  contract Randomness is usingNRE {
  
        function randomNumber() public view returns (uint256){
             return (((rf()%10)*100)+((rx()%10)*10)+(rm()%10));
        }
    
  }
  ```
  
  **Example 3: Transaction of random number into state or local variable.**
   
   The below transaction will cost gas, approx. (40k - 120k) gas per sequence.
   
   ```
   pragma solidity ^0.5.0;
  
  import "https://github.com/niguezrandomityengine/ethereumAPI/blob/master/nreAPI.sol";
  
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
  
  **Example 4: Using the slot of numbers between the sequence and hashing it for distinctive random sequence**
   ```
   pragma solidity ^0.5.0;
  
  import "https://github.com/niguezrandomityengine/ethereumAPI/blob/master/nreAPI.sol";
  
  contract Randomness is usingNRE {
  
        function randomNumber() public view returns (uint256){
             return (uint256(keccak256((rw()/(10**20))%(10**12))));
        }
    
  }
  ```
- These are merely 4 instances of genarating pseudo-random number, the user could use this numbers in infinite possiblities by using dynamic slot selection, cross stitching sequence and using as a salt to hash with user's address, nounce.
       
## Off-Chain Usage


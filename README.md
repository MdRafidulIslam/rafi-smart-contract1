## Rafidul_Smart_Contract
### Basic with data types
"The Ethereum Virtual Machine, known as EVM, operates on the Ethereum blockchain and executes smart contracts written in Solidity. Its significance lies in providing a secure and trustworthy environment for decentralized applications (dapps) to run on the blockchain, making it an essential component of the Ethereum ecosystem.<br>"

We are using ```https://remix.ethereum.org/``` for our solidity smart contracts<br> 
We have created a file ```rafiSimpleStorage.sol``` where ```.sol``` means that it is a solidity file. Solidity is the priamary coding language of smart contract.<br>
Solidity is constantly changing and updating language.<br>
Here in the code below some basic data type of solidity
```

//SPDX-License-Identifier: MIT
//"SPDX" stands for "Software Package Data Exchange", which is a standard for sharing information about software licenses. 
//It provides a common way for developers, lawyers, and other stakeholders to identify and understand the terms of a software license
//"License-Identifier" is a keyword that identifies the license that applies to the code. It is used to uniquely identify the license terms and make them easily accessible
//"MIT" is the name of the license that applies to the code. The MIT License is a permissive open-source license that allows anyone to use, modify, and distribute the code, as long as they include a copy of the license in their distribution.
//at the top of our code we use licensing to make our code sharing and licensing easier and MIT which is the least restrictive license
pragma solidity ^0.8.7;
//we have to tell our code which version of solidity we need to use 
//we can add version by doing pragma,solidity and version we want to use.
//we have use here a caret to tell the code any version of 0.8.7 and above is okay for this contract.
//to define our contract we write contract that tells that next piece of our code will be contract
//contract can be think of like class in OOP and and anything within the curly bracket can be content of the contract
contract rafiSimplestorage {
  // basic data types: boolean, uint,int,address,bytes
  //uint(unsigned integer only positive),int both pos and neg
  //address is the address of the account
  //string are secretly byte objects only for text
  //bytes32 is a bytes objects whre 32 represent how many bytes we want them to be
  //byte objects look like 0xsdsysydggt
  //unint256 here 256 is bit (8,16,32 upto 256 we can use)
  bool hasGoodNumber= true;
  uint256 goodNumberU=689;
  int256 goodNumberI=689;
  string goodNumberS="Six hundred eighty nine";
}

```
<br><br>

### Basic Function
Function and method executes a subset of code when called<br>
There is a deploy and run transaction tab at remix that contain a ton of configuration pieces to deploy our contract<br>
Here our environment is a fake local blockchain environment where we can simulate transaction really quickly without having to wait for them to go through on a testnet<br>
When we run our fake local blockchain environment we are given a whole bunch of fake accounts from where to deploy from and we are given 100 ether<br>
Smart contracts have addresses like our wallet accounts<br>

Example of basic function
```
//SPDX-License-Identifier: MIT
pragma solidity ^0.8.7;

contract rafiSimplestorage {
  // basic data types: boolean, uint,int,address,bytes
  //uint(unsigned integer only positive),int both pos and neg
  //address is the address of the account
  //string are secretly byte objects only for text
  //bytes32 is a bytes objects whre 32 represent how many bytes we want them to be,max size is 32
  //byte objects look like 0xsdsysydggt
  //unint256 here 256 is bit (8,16,32 upto 256 we can use)
  uint256 public goodNumber;//this gets initialized to zero,
  //this 'uint256 public goodNumber' is a global scope means anything inside the curly brackets of contract akrkSimplestorage can access it.       
//pasing parameter of type uint256 and made the function public
//anything created within this function below can't be access by other functions or anything inside the curly brackets of contract akrkSimplestorage  
  function store(uint256 goodNumber) public{
    goodNumber = goodNumber;
    goodNumber = goodNumber +5;
  }
  
  
}



```
After compiling when we will deploy our contract we will see the following informations about deployment shown in the picture below:<br> 
![c1](https://user-images.githubusercontent.com/86659473/236888199-5313b207-890c-4089-b529-e86aee1ab4a5.JPG)

Figure 1 : Here orange color store button is created due to gas calling function store and blue color goodNumber button is created due to  uint256 public goodNumber; where we dont have to pay gas
![c2](https://user-images.githubusercontent.com/86659473/236889558-3def61b3-fa2d-40a6-a685-aecc247d38e6.JPG)

Figure 2 : here tranction details after clicking store button 

<br>

When we deploy a contract it is actually the same as sending a transaction. We have to remember when we do anything on blockchain,we modify any value we are actually sending transaction.<br>
Deploying a contract is modifying the blockchain to have this contract,it is modifying the state of blockchain.

When we run the above code we will see the following image at deploy and transaction tab:
![c3](https://user-images.githubusercontent.com/86659473/236892263-105a7265-642b-4341-8314-0459982575e4.JPG)

<br>

Here,<br>
In the above image the orange color store button appers due to the store function and the blue color prefferednumber button appears because we have made the visibility of preferred number to public.
When we typed a number ```765``` and hit the the store button we are actually making a transaction and then we hit the preferrednumber button we see that preferrednumber gets stored as ```770```<br>

To understand more about functions we rewrite the code again:
```
//SPDX-License-Identifier: MIT
pragma solidity ^0.8.7;

contract rafiSimplestorage {
  // basic data types: boolean, uint,int,address,bytes
  //uint(unsigned integer only positive),int both pos and neg
  //address is the address of the account
  //string are secretly byte objects only for text
  //bytes32 is a bytes objects whre 32 represent how many bytes we want them to be,max size is 32
  //byte objects look like 0xsdsysydggt
  //unint256 here 256 is bit (8,16,32 upto 256 we can use)
  uint256 public preferredNumber;//this gets initialized to zero

//pasing parameter of type uint256 and made the function public
  function store(uint256 _goodNumber) public{
    goodNumber = _goodNumber;
    goodNumber = _goodNumber +1;


  }
  function retrieve() public view returns(uint256){
    return goodNumber;
  }
  
}


```

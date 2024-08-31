Exam Paper Distribution Smart Contract
Overview
This project is a Solidity-based smart contract system for distributing exam papers securely. The ExamDistribution contract allows for the creation of exams, specifying their release time, and authorizing centers to access them.

Features
Create Exam: Allows creation of an exam with an IPFS hash, a release time, and a list of authorized centers.
Retrieve Exam Details: Fetch details of an exam including IPFS hash, release time, and authorized centers.
Authorized Centers: Manage and query the list of authorized centers for a specific exam.
Prerequisites
Node.js (v14.x or higher)
Truffle (v5.x or higher)
Ganache for local Ethereum blockchain simulation
Installation
Clone the Repository

git clone https://github.com/yourusername/exam-paper-distribution.git

cd exam-paper-distribution

Install Dependencies

**npm install**

Compile Contracts

**truffle compile**

Migrate Contracts

Ensure Ganache is running and migrate the contracts:

**truffle migrate --network development**

Usage
Interacting with the Contract
Open Truffle Console

**truffle console --network development**


Create an Exam


const examContract = await ExamDistribution.deployed();
await examContract.createExam(
    "QmExampleIPFSHash",
    Math.floor(Date.now() / 1000) + 3600,
    ["0xaAB38CbA067d5f92ecAc1F1D03B1A077e3bBaf3f", "0x8D6f702f30Ed8986bF02265576b7a00655ee83a4"]
);
Retrieve Exam Details


const examCount = await examContract.examCount();
console.log(`Exam Count: ${examCount.toString()}`);

const exam = await examContract.exams(1);
console.log(`Exam IPFS Hash: ${exam.ipfsHash}`);
console.log(`Release Time: ${new Date(exam.releaseTime * 1000).toLocaleString()}`);

const authorizedCenters = await examContract.getAuthorizedCenters(1);
console.log(`Authorized Centers: ${authorizedCenters}`);
Testing
Run the tests to ensure everything is functioning correctly:

truffle test



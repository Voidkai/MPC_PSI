# ABY： A Framework for Two-Party Computation

> A means **A**rithmetic, B means **B**oolean and Y means **Y**ao

## Overview

- The protocols are represented as **arithmetic or Boolean *circuits***.
  - Which can be evaluated privately using arithmetic sharing, Boolean sharing or Yao's Garbled circuits.
- Two primitive gate operations:
  - linear gates(Addition in arithmetic circuits, XOR in Boolean circuits), without communication using simple operations.
  - non-linear gates(Multiplication in arithmetic circuits, AND in Boolean circuits), require communication and the evaluation of cryptographic operations.
- ABY includes:
  - various gates for secret sharing inputs
  - reconstruction outputs
  - high-level operations
- In order to use the framework, An instance of the class ` ABYParty` has to be generated.
  - **role**: the SERVER listens for an open connection and acts as circuit garbler in Yao’s garbled circuits while the CLIENT connects and acts as circuit evaluator in Yao’s garbled circuits.
  - **Address and port**: If the party acts as server, it opens a socket on this IP address, whereas if the party acts as client, it tries to connect to this IP address.
  - **seclvl**: specifies the security level.
  - **bitlen**: specifies the bit-length of variables in the arithmetic sharing and can be{8,16,32,64}. The default value is 32 bits.

```c++
ABYParty ( e_role pid , char * addr = ( char *) " 127.0.0.1 ", uint16_t port = 7766 , seclvl seclvl = LT, uint32_t bitlen = 32, uint32_t nthreads = 2, e_mt_gen_alg mg_algo = MT_OT , uint32_t maxgates = 4000000) ;
```

### GetSharings

Sharing is a secure computation protocol which can be used to define and evaluate a Given circuit.

The currently supported sharing are:

1. Arithmetic sharing
2. Boolean sharing
3. Yao sharing

```c++
vector<Sharing*>& ABYParty::GetSharings();
vector<Sharing*>& sharings = party->GetSharings();
```

return a vector of all the supported sharings by the framework.

## Main components of ABY


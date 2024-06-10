# Foundry installation

```
~ via 🅒 base 
➜ curl -L https://foundry.paradigm.xyz | bash
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   167  100   167    0     0    852      0 --:--:-- --:--:-- --:--:--   852
100  2189  100  2189    0     0   3318      0 --:--:-- --:--:-- --:--:--  3318
Installing foundryup...

Detected your preferred shell is zsh and added foundryup to PATH.
Run 'source /Users/ju/.zshenv' or start a new terminal session to use foundryup.
Then, simply run 'foundryup' to install Foundry.

~ via 🅒 base 
➜ source /Users/ju/.zshenv

~ via 🅒 base 
➜ foundryup


.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx

 ╔═╗ ╔═╗ ╦ ╦ ╔╗╔ ╔╦╗ ╦═╗ ╦ ╦         Portable and modular toolkit
 ╠╣  ║ ║ ║ ║ ║║║  ║║ ╠╦╝ ╚╦╝    for Ethereum Application Development
 ╚   ╚═╝ ╚═╝ ╝╚╝ ═╩╝ ╩╚═  ╩                 written in Rust.

.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx

Repo       : https://github.com/foundry-rs/
Book       : https://book.getfoundry.sh/
Chat       : https://t.me/foundry_rs/
Support    : https://t.me/foundry_support/
Contribute : https://github.com/orgs/foundry-rs/projects/2/

.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx

foundryup: installing foundry (version nightly, tag nightly)
foundryup: downloading latest forge, cast, anvil, and chisel
########################################################################################################################################################################################## 100.0%
foundryup: downloading manpages
########################################################################################################################################################################################## 100.0%
foundryup: installed - forge 0.2.0 (6179312 2024-06-10T00:18:46.177980000Z)
foundryup: installed - cast 0.2.0 (6179312 2024-06-10T00:18:46.303058000Z)
foundryup: installed - anvil 0.2.0 (6179312 2024-06-10T00:18:46.313806000Z)
foundryup: installed - chisel 0.2.0 (6179312 2024-06-10T00:18:46.052417000Z)
foundryup: done!

~ via 🅒 base took 16s 
➜ forge init foundry-create2
Initializing /Users/ju/foundry-create2...
Installing forge-std in /Users/ju/foundry-create2/lib/forge-std (url: Some("https://github.com/foundry-rs/forge-std"), tag: None)
Cloning into '/Users/ju/foundry-create2/lib/forge-std'...
remote: Enumerating objects: 2321, done.
remote: Counting objects: 100% (2316/2316), done.
remote: Compressing objects: 100% (815/815), done.
remote: Total 2321 (delta 1542), reused 2149 (delta 1429), pack-reused 5
Receiving objects: 100% (2321/2321), 664.87 KiB | 2.39 MiB/s, done.
Resolving deltas: 100% (1542/1542), done.
    Installed forge-std v1.8.2
    Initialized forge project

```

# Test output

```
➜ forge test --match-path test/Create2.t.sol -vvvv
[⠊] Compiling...
[⠃] Compiling 26 files with Solc 0.8.26
[⠊] Solc 0.8.26 finished in 1.84s
Compiler run successful!

Ran 1 test for test/Create2.t.sol:Create2Test
[PASS] testDeterministicDeploy() (gas: 94510)
Traces:
  [94510] Create2Test::testDeterministicDeploy()
    ├─ [0] VM::deal(0x0000000000000000000000000000000000000001, 100000000000000000000 [1e20])
    │   └─ ← [Return] 
    ├─ [0] VM::startPrank(0x0000000000000000000000000000000000000001)
    │   └─ ← [Return] 
    ├─ [439] Create2::computeAddress(0x3132333435000000000000000000000000000000000000000000000000000000, 0xec497b02fb824271806e241abbd311178e40ff6a19da982be9b475c871302d71) [staticcall]
    │   └─ ← [Return] Counter: [0x9D84c2D69F91Da2deB3b45200729A12d4F1a22f8]
    ├─ [82286] Create2::deploy(0x3132333435000000000000000000000000000000000000000000000000000000, 0x6080604052348015600f57600080fd5b5060f78061001e6000396000f3fe6080604052348015600f57600080fd5b5060043610603c5760003560e01c80633fb5c1cb1460415780638381f58a146053578063d09de08a14606d575b600080fd5b6051604c3660046083565b600055565b005b605b60005481565b60405190815260200160405180910390f35b6051600080549080607c83609b565b9190505550565b600060208284031215609457600080fd5b5035919050565b60006001820160ba57634e487b7160e01b600052601160045260246000fd5b506001019056fea2646970667358221220380554e236eca25e41ce3f83305e720d4442aaad4e06b3f2ca8b7900b823776c64736f6c634300081a0033)
    │   ├─ [49499] → new Counter@0x9D84c2D69F91Da2deB3b45200729A12d4F1a22f8
    │   │   └─ ← [Return] 247 bytes of code
    │   └─ ← [Return] Counter: [0x9D84c2D69F91Da2deB3b45200729A12d4F1a22f8]
    ├─ [0] VM::stopPrank()
    │   └─ ← [Return] 
    ├─ [0] VM::assertEq(Counter: [0x9D84c2D69F91Da2deB3b45200729A12d4F1a22f8], Counter: [0x9D84c2D69F91Da2deB3b45200729A12d4F1a22f8]) [staticcall]
    │   └─ ← [Return] 
    └─ ← [Stop] 

Suite result: ok. 1 passed; 0 failed; 0 skipped; finished in 5.54ms (471.46µs CPU time)

Ran 1 test suite in 1.25s (5.54ms CPU time): 1 tests passed, 0 failed, 0 skipped (1 total tests)

```

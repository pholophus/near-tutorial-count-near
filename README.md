Count on NEAR
=============

Our counter example is a friendly decentralized app that stores a number and exposes methods to `increment`, `decrement`, and `reset` it.

![img](https://docs.near.org/assets/images/count-on-near-banner-2df2978ef988be400aafd5e0f99878be.png)

* * *

Starting the Counter[​](#starting-the-counter "Direct link to heading")
-----------------------------------------------------------------------

You have two options to start the Counter:

1.  **Recommended:** use the app through Gitpod (a web-based interactive environment)
2.  Clone the project locally .

*   🌐 JavaScript
*   🦀 Rust
*   🚀 AssemblyScript

Gitpod

Clone locally

[![Open in Gitpod](https://gitpod.io/button/open-in-gitpod.svg)](https://gitpod.io/#https://github.com/near-examples/js-counter.git)

🌐 `https://github.com/near-examples/js-counter.git`

Gitpod

Clone locally

[![Open in Gitpod](https://gitpod.io/button/open-in-gitpod.svg)](https://gitpod.io/#https://github.com/near-examples/rust-counter.git)

🦀 `https://github.com/near-examples/rust-counter.git`

Gitpod

Clone locally

[![Open in Gitpod](https://gitpod.io/button/open-in-gitpod.svg)](https://gitpod.io/#https://github.com/near-examples/counter.git)

🚀 `https://github.com/near-examples/counter.git`

If you choose Gitpod, a new browser window will open automatically with the code. Give it a minute, and the frontend will pop up (ensure the pop-up window is not blocked).

If you are running the app locally, enter the directory where you cloned it and use `yarn` to install dependencies, and `yarn start` to start it.

    cd counteryarnyarn deployyarn start

Your contract will then be **compiled** and **deployed** to an **account** in the `testnet` network. When done, a browser window should open.

* * *

Interacting With the Counter[​](#interacting-with-the-counter "Direct link to heading")
---------------------------------------------------------------------------------------

Go ahead and login with your NEAR account. If you don't have one, you will be able to create one in the moment. Once logged in, use the `+` and `-` buttons to increase and decrease the counter. Then, use the Gameboy buttons to reset it and make the counter blink an eye!

![img](https://docs.near.org/assets/images/count-on-near-4c3bca89fb498ba9e02547eeb320d02a.png) _Frontend of the Counter_

* * *

Structure of a dApp[​](#structure-of-a-dapp "Direct link to heading")
---------------------------------------------------------------------

Now that you understand what the dApp does, let us take a closer look to its structure:

1.  The frontend code lives in the `/frontend` folder.
2.  The smart contract code is in the `/contract` folder.

### Contract[​](#contract "Direct link to heading")

The contract presents 4 methods: `get_num`, `increment`, `decrement`, and `reset`. The method `get_num` retrieves the current value, and the rest modify it.

*   🌐 JavaScript
*   🦀 Rust
*   🚀 AssemblyScript

contract/src/contract.ts

    loading...

[See full example on GitHub](https://github.com/near-examples/js-counter/blob/master/contract/src/contract.ts#L3-L29#)

contract/src/lib.rs

    loading...

[See full example on GitHub](https://github.com/near-examples/rust-counter/blob/master/contract/src/lib.rs#L5-L36#)

contract/assembly/index.ts

    loading...

[See full example on GitHub](https://github.com/near-examples/counter/blob/master/contract/assembly/index.ts#)

### Frontend[​](#frontend "Direct link to heading")

The frontend is composed by a single HTML file (`/index.html`). This file defines the components displayed in the screen.

The website's logic lives in `/assets/js/index.js`, which communicates with the contract through `/near-interface.js`. You will notice in `/assets/js/index.js` the following code:

*   🌐 JavaScript

frontend/index.js

    loading...

[See full example on GitHub](https://github.com/near-examples/js-counter/blob/master/frontend/index.js#L10-L21#)

It indicates our app, when it starts, to check if the user is already logged in and execute either `signedInFlow()` or `signedOutFlow()`.

* * *

Testing[​](#testing "Direct link to heading")
---------------------------------------------

When writing smart contracts it is very important to test all methods exhaustively. In this project you have two types of tests: unit and integration. Before digging in them, go ahead and perform the tests present in the dApp through the command `yarn test`.

### Unit test[​](#unit-test "Direct link to heading")

Unit tests check individual functions in the smart contract. Right now only Rust implements unit testing.

*   🦀 Rust
*   🚀 AssemblyScript

contract/src/lib.rs

    loading...

[See full example on GitHub](https://github.com/near-examples/rust-counter/blob/master/contract/src/lib.rs#L48-L69#)

contract/assembly/\_\_tests\_\_/main.spec.ts

    loading...

[See full example on GitHub](https://github.com/near-examples/counter/blob/master/contract/assembly/__tests__/main.spec.ts#L5-L44#)

### Integration test[​](#integration-test "Direct link to heading")

Integration tests are generally written in javascript. They automatically deploy a new contract and execute methods on it. In this way, integration tests simulate interactions from users in a realistic scenario. You will find the integration tests for the `counter` in `tests/integration-tests`.

*   🌐 JavaScript

integration-tests/src/main.ava.ts

    loading...

[See full example on GitHub](https://github.com/near-examples/js-counter/blob/master/integration-tests/src/main.ava.ts#L37-L61#)

* * *

Moving Forward[​](#moving-forward "Direct link to heading")
-----------------------------------------------------------

A nice way to learn is by trying to expand the contract. Modify it by adding a parameter to `increment` and `decrement`, so the user can choose by how much to change the value. For this, you will need to use knowledge from the [anatomy](/develop/contracts/anatomy) and [storage](/develop/contracts/storage) sections.

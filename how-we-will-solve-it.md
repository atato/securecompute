# How we will solve it

## We need to be humble

Blockchain, cryptography, cryptosystems, all these technologies are attracting a lot of attention and interest as people have come to realize that there is something very important going on. And while what we’re all building is important, it is not yet very impactful. Almost no-one uses a blockchain daily today. Even the most popular services have a limited feature set. The ecosystem overall offers a poor user experience. We need to acknowledge these issues first if we want to address them.

The amount of effort, expertise, and capital required to build blockchain applications today is quite large. And while [some companies are very successful](https://www.kaleido.io/) in bringing these costs down, in many ways what is being built is comparable to what IBM was building for NASA in the 60s. We now have t-shirts instead of dress shirts, and laptop stickers instead of pocket protectors. We still need dozens of highly skilled engineers to build and operate these new and exciting machines. dApps have replaced the room-sized computers of the sixties, even if they hold the same revolutionary importance.

Some figures can help put things in perspective. The Ethereum blockchain has roughly the processing power of a CPU clocking in at roughly 10 kHz \(that’s a k for kilo\). In 1971, [Intel’s first CPU](https://en.wikipedia.org/wiki/Intel_4004) was already an order of magnitude faster than this. Storing 1kB of data on Ethereum costs a whopping 50 USD today \(again a k for kilo\). This is comparable to the [cost of RAM 50 years ago](https://en.wikipedia.org/wiki/Altair_8800#The_launch). Therefore, the Ethereum blockchain has basically the same performance as a 50 years old computer, but one with vastly superior security properties. One could argue that we’re comparing apples to oranges, and that’s true, we’re comparing the performance of computers that are limited by the size and number of transistors with the performance of secure computers with different bottlenecks. Still, we aren’t anywhere near being able to use secure computing everywhere, like we use computing today. And that’s a reality we need to acknowledge if we want to make progress.

{% hint style="info" %}
10 kHz is a quick estimate based on a [single contract](https://etherscan.io/tx/0x8f0612a3a643a4af720ea2aa74247a5eefcce34ca82eff30ae17307502d85ff2) average opcode price of 500, a block gas limit of 15M on mainnet in July 2021, a block time of 15seconds. Equivalent to ~2,000 instructions/second. Or [a 3 kHz CPU](https://en.wikipedia.org/wiki/Cycles_per_instruction#Example_2).

50 USD **is** based on executing [32 SSTORE](https://ethervm.io/#55) opcodes each [costing 20,000 gas](https://github.com/ethereum/go-ethereum/blob/master/params/protocol_params.go#L56) with a gas price of 28 and an Ethereum price of USD 2,600 as of writing.
{% endhint %}

## Gather the building blocks

While we’ve got a long way ahead of us, we also have an amazing arsenal of tools built by the blockchain, cryptography, and computer science communities. If we go back to the fundamental security properties that we require, we can pretty much map them one to one to some of the recent information technology innovations.

* Integrity, just like blockchain records can represent ownership they can also represent arbitrary data. And when coupled with distributed file systems, we can now enable guaranteed data integrity. A number of companies have been doing this, including [atato back in 2018](https://www.ledgerinsights.com/swiss-blockchain-tuna-food-traceability/). Yes this is a shameless plug.
* Availability, secure computers have very high availability guarantees, by being widely distributed. While this [isn’t true for all blockchains](https://bscscan.com/validators), the Ethereum network is [distributed across 9,214 computers](https://etherscan.io/nodetracker) as of writing this article. In 2017 Joseph Lubin stated [“we’ve built an unstoppable, uncensorable world computer”](https://twitter.com/consensys/status/845673911115231232).
* Confidentiality, we can perform computations while keeping the inputs and outputs private. This is done using fully homomorphic encryption and zero-knowledge-proofs, with companies like [Aztec](https://github.com/noir-lang/noir), [Zama](https://zama.ai/) and [NuCypher](https://www.nucypher.com/fully-homomorphic-encryption) demonstrating how this can be used already today for securing AI, or sharing secret information.
* Authenticity, we know how to build [verifiable decentralized identities](https://www.w3.org/TR/did-core/) too. They can be used to securely make and prove claims of authorship of information, and the covid-19 crisis demonstrates how a global identity system could allow global [proofs of vaccine or test claims](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7983450/), for example. 
* Possession, we can now maintain distributed records of ownership and guarantee the security of transfers as no central authority can modify someone else’s records. Blockchains have been doing this for years with both fungible and [non-fungible tokens](https://en.wikipedia.org/wiki/Non-fungible_token).
* Utility, we have created a machine which allows us to store and retrieve information anytime, anywhere using common standards, the internet. The information itself is increasingly standardized as well, and we have built ways to decouple the schema of information from its computer representation.

While individually, these security properties can be guaranteed, there is no consensus today on 1\) how to enable all the properties of secure computers at the same time, and 2\) the direction to take so that the secure computing capacity grows with demand for it. I believe that these two problems are the fundamental problems that we need to focus on right now, if we want secure computing to succeed. 

## And put them together

If we go back to the first question, how to enable the properties of secure computing all at the same time, a lot of work has been done in this area, and the architecture of a ‘proof of concept’ secure computer is reasonably simple. Broadly speaking, we can think of this architecture in terms of layers. A lower layer enables certain core functions, which become automatically available to the higher layers who themselves enable more complex functions, just like this was done [to build the internet](https://en.wikipedia.org/wiki/OSI_model), arguably the biggest ‘computer’ that exists. One approach I would like to propose when discussing the architecture of secure computers is to try and map the different layers of their architecture to the individual security properties required. 

Then introduces the following questions: What are the interfaces between these layers? What is the order of the different layers? I would like to propose the following model for discussion with the community.

<table>
  <thead>
    <tr>
      <th style="text-align:left"></th>
      <th style="text-align:left">Layer Name</th>
      <th style="text-align:left">Information Guarantees</th>
      <th style="text-align:left">Interfaces</th>
      <th style="text-align:left">Protocols / example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">1</td>
      <td style="text-align:left">Integrity</td>
      <td style="text-align:left">
        <p>State consensus</p>
        <p>Past immutability</p>
        <p>Changes authorization</p>
      </td>
      <td style="text-align:left">
        <p>Agree on state</p>
        <p>Change state</p>
      </td>
      <td style="text-align:left">
        <p>Blockchain consensus</p>
        <p>Ethereum PoS</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">Availability</td>
      <td style="text-align:left">
        <p>Retrieval</p>
        <p>Addition</p>
      </td>
      <td style="text-align:left">
        <p>Read information</p>
        <p>Add information</p>
      </td>
      <td style="text-align:left">
        <p>Blockchain nodes</p>
        <p>Ethereum RPC</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">3</td>
      <td style="text-align:left">Confidentiality</td>
      <td style="text-align:left">Access control</td>
      <td style="text-align:left">
        <p>Hide information</p>
        <p>Disclose information</p>
      </td>
      <td style="text-align:left">
        <p>Zero-knowledge proofs</p>
        <p>Aztec Noir</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">4</td>
      <td style="text-align:left">Authenticity</td>
      <td style="text-align:left">
        <p>Authorship</p>
        <p>Attribution</p>
      </td>
      <td style="text-align:left">
        <p>Sign information</p>
        <p>Verify signature</p>
      </td>
      <td style="text-align:left">
        <p>Blockchain wallets</p>
        <p>Metamask</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">5</td>
      <td style="text-align:left">Possession</td>
      <td style="text-align:left">
        <p>Ownership</p>
        <p>Transferability</p>
      </td>
      <td style="text-align:left">
        <p>Own information</p>
        <p>Transfer information</p>
      </td>
      <td style="text-align:left">
        <p>Token protocols</p>
        <p>ERC20</p>
      </td>
    </tr>
  </tbody>
</table>

And since the overall goal of this exercise is to enable the use of secure software on secure computers, there are computing properties that are required in addition to the security properties.

<table>
  <thead>
    <tr>
      <th style="text-align:left"></th>
      <th style="text-align:left">Layer Name</th>
      <th style="text-align:left">Computing Guarantees</th>
      <th style="text-align:left">Interfaces</th>
      <th style="text-align:left">Protocols / example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">6</td>
      <td style="text-align:left">Computation</td>
      <td style="text-align:left">Computation execution</td>
      <td style="text-align:left">
        <p>Store program</p>
        <p>Execute program</p>
        <p>Store results</p>
      </td>
      <td style="text-align:left">
        <p>Blockchain consensus</p>
        <p>Ethereum PoS</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">7</td>
      <td style="text-align:left">Composition</td>
      <td style="text-align:left">Computation extensibility</td>
      <td style="text-align:left">
        <p>Call results</p>
        <p>Call program</p>
      </td>
      <td style="text-align:left">
        <p>Blockchain nodes</p>
        <p>Ethereum RPC</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">8</td>
      <td style="text-align:left">Interaction</td>
      <td style="text-align:left">Exchange with user</td>
      <td style="text-align:left">
        <p>Sequence calls</p>
        <p>Select next call</p>
      </td>
      <td style="text-align:left">
        <p>2 phase commits</p>
        <p>&#x2018;Transaction groups&#x2019;?</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">9</td>
      <td style="text-align:left">Utility</td>
      <td style="text-align:left">Usefulness</td>
      <td style="text-align:left">
        <p>Use computer</p>
        <p>Use information</p>
      </td>
      <td style="text-align:left">
        <p>Recovery protocols</p>
        <p>Metadata standards</p>
      </td>
    </tr>
  </tbody>
</table>

If we want secure computers to scale, and become prevalent, we need our “PC revolution”. Personal computers suddenly allowed most people to use software in their daily lives. We need a revolution that’ll allow most people to use secure computers in their daily lives. And we have a huge advantage: almost everyone has a computer already. We should also acknowledge that there are still large unsolved problems. 

## Practically

I would like to propose three actionable tracks to get to secure computers. While this is a generational change, and it will take a while for secure computing to become prevalent, we need to get the ball rolling. For this, we could 1\) build a proof of concept, 2\) work on the long term problems, and 3\) assemble a sustainable community.

We need to build a proof of concept secure computer. It must enable all security, and computing properties in the model that we have established. Its speed, or the user experience do not matter at this point. There are two goals for it. First is to demonstrate that secure applications can be built and used. Second is to learn along the way, refine the layered model proposed, and progress towards an accepted standard architecture for secure computers.

We need to solve the big problems and that requires an agreement on what they are. First big problem, we need our version of [Moore’s law](https://en.wikipedia.org/wiki/Moore's_law). The computing capacity growth has been enormous arguably for two reasons. We figured out early that transistor density was the factor with the highest impact on performance, and sold computers in a way where capacity grew along with demand as everyone bought CPUs, adding to the total capacity. For blockchains and secure computers, there’s no consensus today on how to bring a [20 orders of magnitude](https://aiimpacts.org/global-computing-capacity/) increase to their capacity, or even if it’s feasible. How do we grow blockchains’ capacity along with the demand for them? 

Second big problem, composition of computation and privacy of information are conflicting requirements. How do we allow one program to make use of another program in a computer where everything is private? If everyone is lending and borrowing privately, and the interest rate charged by the program is public, an observer could derive information about loans by carefully watching the interest rate evolve over time. Perhaps information will in the future not always be absolutely accurate, and we would sometimes accept the tradeoff of a decrease in accuracy to maintain a higher privacy. 

Third big problem, the security of information and computation will only be guaranteed within secure computers. And we as humans can’t interact directly with integrated circuits \([yet](https://neuralink.com/)\). We also have billions of non-secure computers around the world today. Just like a spectrum of information security will likely exist in the future, a spectrum of computation security will. Designing ways to interact with secure computers, while making the right trade-offs between usability and security will be a difficult task which will span from user interfaces and operating systems of the future, all the way to designing new silicon and hardware.

Lastly, and this should be obvious by now, the amount of knowledge, education, effort, and capital needed to achieve these goals is enormous. And just like security is a team effort, secure computing must be open and transparent. No single organization can claim to drive secure computing as that would defeat its very purpose. For this reason, one of the very first steps we should take as a community is to assemble ourselves and get everyone to participate.  



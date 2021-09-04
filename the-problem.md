# The problem

## **Computing is now everywhere**

Cisco estimates that there are between 20 and 30 billion connected devices across the world today and that in 2023 there will be more than 5 billion internet users. Computers, smartphones, IoT devices, and ‘the cloud’ can be found anywhere on Earth, and even on its neighboring planets.

All these devices are built on the same fundamental design. Central processing units are given computation instructions, they retrieve the input data required for the computation, execute the computation, and then store the output data. This cycle is repeated billions of times each second, and this allows your smartphone to connect to the internet, a server to send you this article, and your screen to display its contents.

Subtle variations exist, for example in the way in which instructions are executed, or how data is accessed and stored, or on the number and arrangement of processing units. But it is important to understand that these 20 billion connected devices were all built for one purpose: process as quickly as possible any instructions they’re given on any data they’re given.

## **But running a 50-year-old design**

Fundamental parts of computer design and objectives are much older than some people realize. It is generally accepted that modern computer architecture was created in the late 1970s with Intel’s 8000 series of microprocessors, and later the first IBM PC in 1981. We could even argue that computers still use the same architecture as the IBM Harvard Mark 1, released in 1944.

Performance, however, cannot be compared. An interesting metric is the dollar cost per GFLOPS or billions of floating-point operations per second, it measures the cost of a unit of performance as computer hardware evolves. Since 1984, when Bill Gates was first featured on the cover of TIME magazine, this cost has gone down from $46 million to 3 cents. That’s a staggering 99.9999999% reduction over 40 years. The success in processing as fast as possible any instructions on any data is undeniable.

The question is, should computing any instructions on any data still be the objective of tomorrow’s computers? Is it what we want of 20 billion devices that constantly exchange data and instructions with one another? We aren’t living in a world where personal computers sit on a desk at home with its floppy disks in a drawer anymore.

## **Security wasn’t part of the specs**

The geniuses who designed and built modern computers were living in a world that was different from ours. While Alan Turing and his bombe electromechanical computer were designed to defeat the Enigma machine and break its encryption, it is not until the late 70s that the modern concept of encryption using public-private key cryptosystem was born. While CPUs were being designed, and the first motherboards were built to architecture how computers would receive, store and process information, these primitives that are everywhere in security today didn’t exist. And it took another 20 years before encryption became widely used. 

Today, there are several properties that we expect from a system to be considered secure. For example, the ‘CIA triad’. Confidentiality: being able to limit who has access to information. Integrity: that the original information remains complete and unaltered.  Availability: being always able to retrieve information on time. These three are sometimes extended to include possession, authenticity, and utility.  Possession: being able to tell who currently owns a piece of information. Authenticity: the ability to verify claims of authorship. Utility: remaining able to use a piece of information over time.

It is important to understand that computers, on their own, are unable to provide any of these six properties. To achieve any of them, we must carefully design, build and operate additional hardware and software systems that enable these fundamental security properties. In the 1970s, security was not a part of the specs sheet. A CPU must execute whatever instruction arrives on its pipeline. RAM must store whatever data shows up on the memory bus. Peripherals must deal with whatever data is given to them. Computers were built to be personal, and compute personal information.

## **Everyone is impacted today**

The complexity, and intricacies of building computer systems that provide information confidentiality, integrity, availability, possession, authenticity, and utility should not be underestimated. Enabling some basic confidentiality requires software that can provide encryption, hardware that can securely store private keys, systems that share identities and public keys, purpose-built applications, and people who understand how to securely use all of this. Because of this, less than 10 million people are using[ secure email worldwide today](https://keyserver.ubuntu.com/pks/lookup?op=stats), meaning that 99.75% of the planet uses email without true confidentiality.

Security is not a common area of interest, and only really understood by a few technology experts. Despite the industry’s best efforts, we often see spectacular failures. Just 3 years ago, a vulnerability was found in[ the vast majority of microprocessors](https://en.wikipedia.org/wiki/Meltdown_%28security_vulnerability%29) in the world that was considered ‘catastrophic’ by experts; it allowed malicious software to steal information from other software running on the same computer. A more recent example occurred in Ireland where the Health Service’s information system was[ targeted by a ransomware attack](https://www.theguardian.com/world/2021/may/14/ransomware-attack-disrupts-irish-health-services), things were so bad that some hospitals were forced to shut down all computer systems and cancel all outpatient visits.

And a month rarely passes without a major confidential data breach. In 2021, Facebook revealed that data of its users, including phone numbers, had leaked. That[ leak affected 533 million Facebook users](https://www.npr.org/2021/04/09/986005820/after-data-breach-exposes-530-million-facebook-says-it-will-not-notify-users), and barely made the news. Many of us will also not remember the[ 2017 Equifax data leak](https://en.wikipedia.org/wiki/2017_Equifax_data_breach), where private records of 160 million people that included social security numbers, addresses, and other confidential information leaked because the company failed to follow its own security procedures.  
****


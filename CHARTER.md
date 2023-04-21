# Runtime Integrity SIG Charter
The goal of this SIG is to discuss strategy and gaps in ISA and non-ISA
mechanisms for program safety and execution integrity for software running on
RISC-V platforms. Over the past couple of years, RISC-V has seen significant
adoption in embedded usages (including security-processor usages). Looking
ahead there are a significant number of community members breaking ground for
high performance computing targeting server and data-center workloads. As the
RISC-V ecosystem and software evolves, new security requirements are appearing.
To address these security concerns, and meet the overarching goal of program
safety, the Runtime Integrity SIG expects to operate in the following areas: 

- Mechanisms for TCB reduction for existing workloads
Existing use cases have untrusted 3rd party software components running with
high privilege and need mechanisms to de-privilege such 3rd party software
without needing a significant refactor of the software. Thus mechanisms for
reducing trusted computing base (TCB) are required. One such usage is to
mutually isolate software components at all privilege levels using domain
isolation mechanisms.

- Preventing classes of exploit vectors
A large number of workloads for general high performance computing are highly
multithreaded and written in unsafe languages. This has resulted in memory
safety (corruption) issues which can be exploited by attackers to perform
malicious execution (via data-flow/control-flow subversion), information
disclosures (like heartbleed) or denial of service issues. Hence, the SIG will
address mechanisms to enforce control flow integrity of the program to prevent
remote code execution attacks or memory safety technologies to prevent /
mitigate corruption issues altogether.

- Scalable Isolation mechanisms for evolving workloads
Software is constantly evolving and in some cases faster than hardware / CPU
ISA can respond to it.  One particular vehicle driving such evolution is large
address space available in 64 bit operating environments. As an example sv48
(and equivalent on other architectures) paging provides 128TiB of address space
in a process. One particular software model exploiting this large address space
is FaaS (or functions on the edge) model. Such evolving workloads require
finer-grain isolation mechanisms than available today in the RISC-V ISA.

- Platform mechanisms to support program safety
Certain use cases require software to be tamper resistant and analysis proof to
maintain their runtime integrity. Software can be analyzed or tampered with
using debug mechanisms provided by hardware, devices (peripherals) operating
system and debugging tools. ISA or software mechanisms are required using which
software can be made tamper proof and provides certain guarantees against
analysis.

The SIG will work within the larger Security HC, Trusted Computing SIG TGs and
Priv IC to pursue the common required ISA capabilities, and co-ordinate with
Priv software and tools TGs to evaluate impact on programming tools.

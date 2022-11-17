# Runtime Integrity SIG Charter

For the past couple of years the RISC-V community has used the TEE TG as a vehicle for exploring security mechanisms and ideas, and working towards creating ISA specifications for improving the security capabilities of RISC-V. From ePMP to IOPMP, SMPU, M-mode isolation, CFI and the IOMMU (which was also first proposed within the TEE TG), we had very productive discussions and the work we started there is still ongoing. Within the new organization the Runtime Integrity SIG aims to play a similar role, this time more focused on ISA specifications and specific mechanisms than whole frameworks, and with a better structure with multiple TGs under the SIG for better coordination and efficiency.

The idea is to explore security mechanisms that will allow us to provide strong security guarantees, under well defined conditions, and let vendors and users pick the combination of mechanisms/guarantees that suits their needs. Right now RISC-V has basically three ratified mechanisms for providing memory isolation (PMP/ePMP and the first and second stage of translation of virtual memory), everything else is a work in progress, we have a long way to go in order to cover other possible threat models and different system configurations.

 * PMP/ePMP is great but it has its limitations, it&apos;s there to protect a small and mostly static set of (physical) memory regions, configured at boot time, rather than allow us to dynamically manage a large set of regions at runtime. Instead of overloading ePMP we need a new mechanism and there are already discussions on AP-TEE TG and the IOMMU TG on the subject. The idea is to have a structure similar to a page table, managed by M-mode and shared with the IOMMU, that will allow us to dynamically add and remove regions/pages to the set of secure/trusted regions, accessible only by the TEEs and their secure monitor/hypervisor. In the future we may decide to extend this mechanism to also support assignment of memory regions to specific security domains or guests / privilege modes etc. It's a very interesting area to explore.
 * The forward and backward edge CFI proposals that the CFI TG is working on are evolving and will hopefully get ratified next year, however there may be other CFI techniques to consider, or future enhancements to those proposals.
 * M-mode isolation is gaining attention again, various use cases have come up that require running code on M-mode, alongside an isolated/protected trusted firmware. Same goes for SMPU which is also gaining attention as it continues to evolve.
 * There are also other areas that came up during our discussions, a few examples:
   * Anti-debugging
   * Memory tagging (on top of pointer masking)
   * Protection keys
   * Anomaly detection / gadget detection
   * Information flow tracking
   * Capability-based integrity (as in CHERI)

Now that we have Confidential Computing SIG handle Secure Boot, attestation, software architecture and other non-ISA items, the SoC HC handle IOMMU and IOPMP, and the Microarchitectural Side Channel Attack SIG, the Runtime Integrity SIG is the last piece of the puzzle.

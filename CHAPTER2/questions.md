# TOC
- [TOC](#toc)
  - [(5) What is the idea behind a CISC architecture?](#5-what-is-the-idea-behind-a-cisc-architecture)
  - [(6) What is the disadvantage of a CISC architecture?](#6-what-is-the-disadvantage-of-a-cisc-architecture)
  - [(7) What is the idea behind a RISC architecture?](#7-what-is-the-idea-behind-a-risc-architecture)
  - [(8) Why is the instruction set limited in RISC?](#8-why-is-the-instruction-set-limited-in-risc)
  - [(9) How is backward compatibility achieved between CISC and RISC?](#9-how-is-backward-compatibility-achieved-between-cisc-and-risc)
  - [(10) What rules are imposed on RISC instructions?](#10-what-rules-are-imposed-on-risc-instructions)
  - [(11) What is a superscalar architecture? How does the pipeline look and why were changes made?](#11-what-is-a-superscalar-architecture-how-does-the-pipeline-look-and-why-were-changes-made)
  - [(12) On what principle does a GPU work and how is this done in a vector processor?](#12-on-what-principle-does-a-gpu-work-and-how-is-this-done-in-a-vector-processor)
  - [(13) Representation of variable p in little endian vs big endian and the problem during conversion](#13-representation-of-variable-p-in-little-endian-vs-big-endian-and-the-problem-during-conversion)
    - [Struct definition](#struct-definition)
    - [Memory layout (assuming 32-bit int, ASCII, no padding)](#memory-layout-assuming-32-bit-int-ascii-no-padding)
      - [Big Endian](#big-endian)
      - [Little Endian](#little-endian)
    - [Problem during conversion](#problem-during-conversion)
  - [(14) On what principle do cache memories work?](#14-on-what-principle-do-cache-memories-work)
    - [Types of locality](#types-of-locality)
    - [Examples proving locality](#examples-proving-locality)
    - [Result](#result)
  - [(15) Why was RAID invented? What is the idea behind RAID?](#15-why-was-raid-invented-what-is-the-idea-behind-raid)
  - [(16) Why is there a need for a redundant disk in RAID?](#16-why-is-there-a-need-for-a-redundant-disk-in-raid)
  - [(17) What is the impact of stripe size on performance?](#17-what-is-the-impact-of-stripe-size-on-performance)
  - [(18) Why does RAID-4 have a write penalty? Proof with 4 I/O operations](#18-why-does-raid-4-have-a-write-penalty-proof-with-4-io-operations)
  - [(19) What does mechanically synchronized mean in RAID-2 and why is RAID-2 more reliable than RAID-3?](#19-what-does-mechanically-synchronized-mean-in-raid-2-and-why-is-raid-2-more-reliable-than-raid-3)
  - [(20) Why do solid-state drives have write amplification but hard disks do not?](#20-why-do-solid-state-drives-have-write-amplification-but-hard-disks-do-not)

## (5) What is the idea behind a CISC architecture?
- Provide `many complex` instructions that can `perform multiple` low-level `operations` in a `single instruction`
- `Reduce the number of instructions per program`, even if each instruction is more complex

---

## (6) What is the disadvantage of a CISC architecture?
- More `complex hardware` and `control logic`
- Harder to pipeline and optimize
- Potentially slower clock speeds

---

## (7) What is the idea behind a RISC architecture?
- Use a `small`, `simple`, and `highly optimized instruction set`
- Each instruction performs `one simple operation`
- Focus on `high clock speeds` and `efficient pipelining`
- Shift complexity from `hardware` to the `compiler`

---

## (8) Why is the instruction set limited in RISC?
- Simpler instructions allow:
  - `Faster decoding`
  - `Uniform execution time`
- Enables:
  - `Efficient pipelining`
  - `Simpler hardware design`
- Makes `compiler optimizations` easier and more effective

---

## (9) How is backward compatibility achieved between CISC and RISC?
- By using:
  - `Microcode` or `translation layers`
  - `Dynamic instruction translation`
- Complex `CISC instructions` are internally broken down into:
  - `RISC-like micro-operations`
- Example:
  - Modern `x86 CPUs` internally execute `RISC-style uops`

---

## (10) What rules are imposed on RISC instructions?
- Instructions are:
  - `Fixed length`
  - `Simple and atomic`
- Memory access is restricted to:
  - `Load` and `store` instructions only
- Most operations work only on:
  - `Registers`
- Typically:
  - `One clock cycle per instruction`

---

## (11) What is a superscalar architecture? How does the pipeline look and why were changes made?
- A `superscalar architecture` executes `multiple instructions per clock cycle`
- Uses:
  - `Multiple execution units` (ALU, FPU, Load/Store)
- Pipeline characteristics:
  - `Instruction fetch` → `decode` → `dispatch` → `parallel execution` → `commit`
- Key adaptations:
  - `Out-of-order execution`
  - `Instruction-level parallelism (ILP)`
  - `Register renaming`
- Goal:
  - Increase `throughput` without increasing clock speed

---

## (12) On what principle does a GPU work and how is this done in a vector processor?
- GPU works on:
  - `SIMT` (Single Instruction, Multiple Threads)
- Many threads execute:
  - The `same instruction` on `different data`
- Optimized for:
  - `Massive data parallelism`
- Vector processor works on:
  - `SIMD` (Single Instruction, Multiple Data)
- Difference:
  - GPU: many `lightweight threads`
  - Vector processor: operates on `vector registers` directly

---

## (13) Representation of variable p in little endian vs big endian and the problem during conversion

### Struct definition
```C
typedef struct {
    char str[4];
    int leeftijd;
} persoon;

persoon p = {"Wim", 50};
```
### Memory layout (assuming 32-bit int, ASCII, no padding)

#### Big Endian
> Address → +0 +1 +2 +3 +4 +5 +6 +7
> 
> Data | 'W' | 'i' | 'm' | '\0' | 00 | 00 | 00 | 32 |


#### Little Endian
> Address → +0 +1 +2 +3 +4 +5 +6 +7
> 
> Data | 'W' | 'i' | 'm' | '\0' | 32 | 00 | 00 | 00 |

### Problem during conversion
- `Multi-byte values` (such as `int`) use `different byte orders`
- Copying raw memory between systems with different endianness causes:
  - `Incorrect numerical interpretation`
- `Single-byte values` (char) are not affected
- Typical issues:
  - File formats
  - Network communication
- Solution:
  - Use `explicit serialization`
  - Convert to `network byte order` (big endian) before transmission
  - Convert back on the receiving system

---

## (14) On what principle do cache memories work?
- Cache memory is based on the principle of:
  - `Reference Locality`

### Types of locality
- `Temporal locality`
  - Data accessed recently is likely to be accessed again soon
- `Spatial locality`
  - Memory locations close to each other are likely to be accessed together

### Examples proving locality
- `Loops` repeatedly accessing the same variables  
  → demonstrates `temporal locality`
- `Sequential array traversal`  
  → demonstrates `spatial locality`
- `Function calls` reuse the same instructions  
  → instructions remain in the cache

### Result
- Significantly `reduced average memory access time`
- Fewer `CPU stalls`
- Improved overall `system performance`

---

## (15) Why was RAID invented? What is the idea behind RAID?
- RAID was designed to:
  - Combine `multiple disks` into one `logical storage unit`
- Main goals:
  - Increase `performance` (parallel I/O)
  - Improve `reliability` through `redundancy`
  - Provide `fault tolerance` at lower cost than a single high-end disk
- Core idea:
  - Trade `extra disks` for better `speed` and/or `data safety`

---

## (16) Why is there a need for a redundant disk in RAID?
- Disks are:
  - `Mechanical devices` with a high failure probability
- Redundancy allows:
  - `Data recovery` after a disk failure
- Redundant information stores:
  - `Parity bits`
  - Or `mirrored data`
- Without redundancy:
  - A single disk failure causes `data loss`

---

## (17) What is the impact of stripe size on performance?
- `Stripe size` determines how data is split across disks
- Small stripe size:
  - Better `parallelism` for small random I/O
  - Higher `overhead`
- Large stripe size:
  - Better `sequential read/write performance`
  - Less effective for small random accesses
- Optimal stripe size depends on:
  - `Workload characteristics`

---

## (18) Why does RAID-4 have a write penalty? Proof with 4 I/O operations
- RAID-4 uses:
  - A `dedicated parity disk`
- To update a single data block:
  - Old data must be read
  - Old parity must be read
  - New data must be written
  - New parity must be written
- Total:
  - `2 read + 2 write = 4 I/O operations`
- This remains:
  - `Constant (4 I/O)` regardless of the number of data disks
- Reason:
  - Parity calculation depends only on:
    - Old data
    - Old parity
    - New data

---

## (19) What does mechanically synchronized mean in RAID-2 and why is RAID-2 more reliable than RAID-3?
- `Mechanically synchronized` means:
  - All disks rotate in `lockstep`
  - Heads are aligned to the same position
- RAID-2 uses:
  - `Hamming code` for error correction
- Reliability:
  - RAID-2 can:
    - Detect and correct `bit-level errors`
- RAID-3 uses:
  - `Single parity`
  - Can only handle `one disk failure`
- Therefore:
  - RAID-2 provides `stronger fault detection and correction`

---

## (20) Why do solid-state drives have write amplification but hard disks do not?
- SSDs use:
  - `Flash memory` with `erase-before-write` constraint
- Writes require:
  - Erasing large `blocks` before writing small `pages`
- Results in:
  - `Multiple internal writes` for one logical write
- This effect is called:
  - `Write amplification`
- HDDs:
  - Can overwrite data `in place`
  - Do not need erase cycles
- Therefore:
  - No write amplification in `magnetic disks`

# introduction
>`Solid State Drives (SSDs)` are storage devices that use `flash memory` instead of spinning disks to store data. 
>
> They offer `faster read and write speeds`, `lower latency`, and `greater durability` compared to traditional hard drives, as they have no moving parts.

## characteristics
- `NVMe over PCIe:` Modern SSDs use `NVMe over PCIe` as the default interface, replacing SATA.  
- `Cost & Reliability:` Generally `more expensive` and `less reliable` than SATA drives, but significantly `faster`.  
- `Wear Leveling:` SSDs use `wear leveling` to distribute writes evenly across the memory to extend lifespan.  
- `Bit Rot:` Over time, stored data can degrade, a phenomenon called `bit rot`.


- `Reads:` The controller reads data at the `page level`; no erase needed to read. Page size is approximately `4–16 KB`.  
- `Writes (“programs”):` NAND can only write to an `empty (erased) page`—no in-place overwrite.  
- `Erase:` Happens at the `block level` (many pages at once) and is relatively slow. Typical block size: `128–1024 pages`.  
- `Modify/Update:` To change data, the SSD writes a `new copy` to a fresh page and marks the old page as `invalid`; it then updates the `logical-to-physical mapping`.  
- `Cleanup (Garbage Collection):` Valid pages are moved together, and whole blocks are erased to free space. This extra housekeeping contributes to `write amplification`.

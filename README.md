# machojs
Javascript to deal with MachO files

Usage:

Assuming you are running your code in an iOS application environment.

read(addr, len) --- allows you to read @len amount of byte at the address @addr in current
process address space and returns an instance of Uint8Array containing the data retrieved.

data --- contains the macho file header data as Uint8Array for one of the dynamic libraries
mapped into current process address space.

The following code resolves a symbol "dlsym" exported by that library.

```javascript
...
let machO = new MachO(data);
machO.parseHeader();
let exports = machO.getLinkeditStartInProcess(aslrSlide);
let dyld_info = machO.get_DYLD_INFO();
var exportsData = read(exports, dyld_info.export_size);
findSymbolInLinkedit(exportsData, "dlsym");
``` 

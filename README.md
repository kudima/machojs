# machojs
Javascript to deal with MachO files

Usage:
```javascript
...
let machO = new MachO(data);
machO.parseHeader();
let exports = machO.getLinkeditStartInProcess(aslrSlide);
let dyld_info = machO.get_DYLD_INFO();
var exportsData = read(exports, dyld_info.export_size);
findSymbolInLinkedit(exportsData, "dlsym");
``` 

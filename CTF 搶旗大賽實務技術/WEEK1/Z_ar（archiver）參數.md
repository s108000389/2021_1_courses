# ar -h
```
ar（archiver）是Unix系統上的歸檔工具，用於將多個檔案歸檔為一個檔案。
ar目前一般僅被連結器用建立更新靜態庫和生成.deb包。
它的歸檔功能現在基本被 tar所取代。
GNU Binutils包含ar
```
```

Usage: ar [emulation options] [-]{dmpqrstx}[abcDfilMNoPsSTuvV] [--plugin <name>] [member-name] [count] archive-file file...
       ar -M [<mri-script]
 commands:
  d            - delete file(s) from the archive
  m[ab]        - move file(s) in the archive
  p            - print file(s) found in the archive
  q[f]         - quick append file(s) to the archive
  r[ab][f][u]  - replace existing or insert new file(s) into the archive
  s            - act as ranlib
  t            - display contents of archive
  x[o]         - extract file(s) from the archive
 command specific modifiers:
  [a]          - put file(s) after [member-name]
  [b]          - put file(s) before [member-name] (same as [i])
  [D]          - use zero for timestamps and uids/gids (default)
  [U]          - use actual timestamps and uids/gids
  [N]          - use instance [count] of name
  [f]          - truncate inserted file names
  [P]          - use full path names when matching
  [o]          - preserve original dates
  [u]          - only replace files that are newer than current archive contents
 generic modifiers:
  [c]          - do not warn if the library had to be created
  [s]          - create an archive index (cf. ranlib)
  [S]          - do not build a symbol table
  [T]          - make a thin archive
  [v]          - be verbose
  [V]          - display the version number
  @<file>      - read options from <file>
  --target=BFDNAME - specify the target object format as BFDNAME
 optional:
  --plugin <p> - load the specified plugin
 emulation options: 
  No emulation specific options
  
ar: supported targets: elf32-i386 elf32-iamcu a.out-i386-linux pei-i386 elf32-little elf32-big 
elf64-x86-64 elf32-x86-64 pei-x86-64 elf64-l1om elf64-k1om elf64-little elf64-big pe-x86-64 pe-bigobj-x86-64 
pe-i386 plugin srec symbolsrec verilog tekhex binary ihex trad-core
Report bugs to <http://www.sourceware.org/bugzilla/>
```

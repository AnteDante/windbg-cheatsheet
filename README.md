# WinDbg cheatsheet

command - built in command functions  
.command - meta commands  
!command - extension comands coming from dll's, typically in form dll!command but some dlls are preloaded and can be omitted.

| Command   | Description |
| --------- | ----------- |
| `.help`   | View all meta commands |
| `.hh` *command* | Open command help view |
| `version` | Displays debugging info |
| `vertarget`  | Displays machine info |
| `.lastevent`  | Shows last event that stopped the Debugger |
| `lm` *[m,l,e]* | List modules [name of module, only modules with loaded symbols, other modules] |
| `!lmi` *module.dll* | More information about the module |
| `!dh` *address* \| *module name* `-f` | Even more information about module |
|`.sympath` | Shows or sets symbol path, srv* denotes symbol server |
|`.sympath+` *path* | Appends to sympath |
|`.symfix` | fixes symbol path to default MS path |
|`.symfix+`| Appends default MS path to existing sympath |
| `.reload` *[module name]* | Drops all symbols or symbol for given module name, doesn't load them until they're needed |
| `.reload /f` | Forces the reload
| `.sym noisy` | Verbose mode for symbol resolution |
| `!chksym` *module* \| *address* | Check do symbol file and module match |
| `.srcpath` | Path to source files. Note: If compiled on same machine path isn't needed, the dll has the absolute path to the source file |
| `srcfix+` | |
| `.srcnoisy` *1* \| *0* | Set or disable verbose output for soruce file resolution |
| `x` *[options]* *module*!*symbols* | Basic command for examining symbols, wildcards work for module and symbols. |
| `x /v /t` | Additional info |
| `ln` *address* |  List Near - lists symbols near to address or exact match if there is one. |
| `r` | View registers |
| `r` *regiser* | View register e.g r eax |
| `r` *register* = *value* | Set register to value e.g r eax = 1 |
| `rm ?` | See register masks |
| `rm` *mask* | Sets r to show those registers |
| $ip | Pseudo-register $ip is eip on x86 and rip on x64, other pseudo registers exists $t0-$t19, $ra - return address, $retreg - result of func (eax), $csp - current stack pointer, $proc, $thread, $tpid, $tid, $teb |
| `u` | Unassembly eight instructions as the address current $ip |
| `ub .` | Unassembly eight instr prior to current $ip |
| `uf .` | Unassembly entire function containing $ip |
| `u . L2` | Unassembly two instructions prior to current $ip |
| `u . .+a` | Unassembly ten instruction between $ip and $ip plus ten |
| _stdcall convention | ebp - frame base pointer, ebp+4 - return address, ebp+8 - first function param, ebp-4 - local params |
| `k` | Shows call stack |
| `.kframes` | Controlls how many frames to show with k command |
| `kP` *num* | Shows call stack together with parameters per line, small p for same line |
| `kb` *num* |  Shows call stack with first 3 params passed to on the stack (might not be valid) |
| `kf` *num* | Shows call stack and memory used by each frame |
| `bl` | List breakpoints |
| *thread* `bp` *symbol* or *address* *[options]* "*commands*" | Set breakpoint using a symbol or address with given options and run commands after breakpoint is hit. Commands ; divided |
| `bm` | Set multiple breakpoints (when using a wildcard e.g) |
| `bu` | Set deferred breakpoint for modules that haven't been loaded yet |
| `dv` | Display local variablesm /i -shows symbol type, /V - shows where variable is stored |
| `dt` | Display type |
| `d`{*type*} | Display memory as type e.g dd - display double word, dq- display quad word, du - display uncode string |
| `d`*`s` | Display area of memory as type e.g dds - treat each group of four bytes as a symbol, dqs - 8 bytes as a symbol, dps - use native proc arch length, dpu - array of unicode strings |
| `s` | Search for known values in memory |
| `ba` *operation**size* *address* | Break on access e.g ba w4 symbol+0 |
| `!address` | Show type of memory at address or without args list all memory |
| `!peb` | Show processor execution block |
| `!teb` | Thread execution block |
| `!gle` | Get last error |
| `t` | Single step l+t sets source stepping, l-t sets assembly stepping |
| `p` | Single step, treat function as a single command |
| `pc` | Jump before the next function call |
| `g` | Continue executing |
| `gu` | Continue executing untill the end of the function |
| `g` *address* | Continue executing until address |
| `wt` [*-l1] | Like p but gives function statistics. -l nesting level |
| `eb` *address or name* | Change memory to given bytes e.g eb .-3 90 90 90 |
| `ed` | Change memory to given dword value |
| `!error` *err* | Shows error |
| `!dreg` | Show registry HKLM.. |
| `?` *expression* | Evaluate math expression |
| `??` | Evaluate c++ expression |
| `.formats` *num* | Gives all formats for a number |
| `sx` | Inspect event handling settings |
| `sx`{`e`\|`d`\|`i`\|`n`\|`r`} | Set Exception {enable \| disable \| ignore \| notify \| reset } |
| `~`\<tid>`n` | Suspend thread tid |
| `~`\<tid>`m` | Resume thread tid (f/u freeze/ unfreeze) |
| `~`\<tid>`s` | Change thread execution to tid |





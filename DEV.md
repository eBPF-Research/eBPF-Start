
### 具体开发任务



### Notes
1. 查看安装的eBPF程序
```
sudo bpftool prog show
```


2. eBPF加载报错 map .rodata  
couldn't load eBPF programs: map .rodata: map create: read- and write-only maps not supported (requires >= v5.2)  
是bpf_printk创建的数组报错了：   
```
$ llvm-objdump pkg/ebpf/bin/tc.o -dj .rodata
pkg/ebpf/bin/tc.o:      file format elf64-bpf

Disassembly of section .rodata:

0000000000000000 <one.____fmt>:
       0:       28 63 6c 61 73 73 69 66 r0 = *(u16 *)skb[1718186867]
```

3. 编译bpf报错  
/usr/include/features-time64.h:20:10: fatal error: 'bits/wordsize.h' file not found  
解决：  
> apt install gcc-multilib
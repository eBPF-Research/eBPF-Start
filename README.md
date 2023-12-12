
## eBPF Demo项目
基于datadog ebpf-manager的最简go eBPF项目。

### 开发说明
项目结构遵循[Go标准项目布局](https://dev.to/jinxankit/go-project-structure-and-guidelines-4ccm), 其文件如下：
```
$ tree -L 1 
.
├── bin  		# 编译后的可执行文件	
├── cmd			# 若干个go主程序 (main.go)
├── DEV.md		# 开发说明
├── ebpf		# eBPF程序
├── go.mod		# go 工程文件
├── go.sum		# go 依赖库版本锁定
├── Makefile	# 编译脚本
├── pkg			# 项目主要代码
├── README.md
├── scripts		# 启动和测试脚本
└── tools		# 测试程序
```

#### 编译说明  
1. 安装项目依赖库  
```
go mod tidy
```

2. 编译测试项目
```
# 编译
make 

# 基本测试  
$ sudo make run
023/03/07 12:30:37 [LOG]             node-10627   [000] d.... 56291.786582: bpf_trace_printk: (classifier/one) new packet captured (TC)
```
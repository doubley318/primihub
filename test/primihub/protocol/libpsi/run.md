### 编译指令

```shell
cd primihub
bazel build --config=linux :libpsi_test
```

### 运行KKRT

```shell
#单进程运行
bazel-bin/libpsi_test -kkrt
#双进程运行
bazel-bin/libpsi_test -kkrt -r 0 & bazel-bin/libpsi_test -kkrt -r 1
```
### 运行MKKRT(多线程KKRT)

```shell
#单进程运行
bazel-bin/libpsi_test -mkkrt -t 2
#双进程运行
bazel-bin/libpsi_test -mkkrt -r 0 -t 2 & bazel-bin/libpsi_test -kkrt -r 1 -t 2
```

### 运行CM20

```shell
#单进程运行
bazel-bin/libpsi_test -cm20 -s 1 -t 2
#双进程运行
bazel-bin/libpsi_test -cm20 -r 0 -s 1 -t 2& bazel-bin/libpsi_test -cm20 -r 1 -s 1 -t 2
```

### libpsi_test运行参数

-r -role：客户端模式，0为Sender，1为Receiver

-ip: Sender的IP地址

-n -numItems：输入数据的大小

-t: PSI运行的线程数

-nn -powNumItems：输入数据的二次幂

-s: CM20的scale参数，s越大，通讯量越大，但计算量会减少

-trials：重复运行次数
![image](https://github.com/apodxx/oerv-team/assets/33642755/6e747b20-a161-4f82-83d2-04627cee1c77)![image](https://github.com/apodxx/oerv-team/assets/33642755/2cfec5e7-0425-4928-9dcc-f7a60db1a00c)## 问题描述：让 WasmEngine 支持 riscv64
## 解决方法：尝试补丁升级其中的 wasmtime 至2.0.0以上版本，因为wasmtime在2.0.0之后才支持riscv64
## 解决问题流程：
1. 将WasmEngine源文件中的Cargo.toml的关于wasmtime改写为2.0.1，之前均为0.30.0
   ![image](https://github.com/apodxx/oerv-team/assets/33642755/aaa99e1d-df91-49b9-aacf-9c352b0c2724)
2. 修改完后，使用cargo build --release命令进行编译，会遇到两个问题：
   ![image](https://github.com/apodxx/oerv-team/assets/33642755/ac11335f-7674-434d-891b-12daf27b62a7)
    ![1703568940233](https://github.com/apodxx/oerv-team/assets/33642755/a83a68bc-9dd9-41d7-93a7-bc187301ecc3)

3. 通过查文档可知，.wasm_module_linking方法已经被废弃以及.profiler(ProfilingStrategy::None)?后面不再需要加问号，因此将这行代码以及？去掉
   ![image](https://github.com/apodxx/oerv-team/assets/33642755/0fc3692e-a487-4cae-8b75-21a486da65a4)
4. 再次编译，成功通过
   ![30d90295f95e695252966e38dc6b6a7](https://github.com/apodxx/oerv-team/assets/33642755/fadf238f-38bf-43ad-a483-00e97fd05de5)
5. 接下来，切换root用户下启动WasmEngine应用，WasmEngine已经成功启动
   ![760ed31bfbf2015328e73bcce7acef8](https://github.com/apodxx/oerv-team/assets/33642755/c211242f-b54f-4d05-9c4b-af413ed1dc5b)
6. 之后按照[WasmEngine项目](https://gitee.com/openeuler/WasmEngine)要求走一遍样例测试流程，可以看到WasmEngine已经能够成功启动！
  ![c0ba445cde0ed1ad533baa19fdf8190](https://github.com/apodxx/oerv-team/assets/33642755/3a87d694-2770-4e82-af9e-58c43a553c71)


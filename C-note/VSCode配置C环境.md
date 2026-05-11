完全理解你的选择：学习阶段用 IDE（如 Visual Studio、CLion 等）确实感觉笨重，VSCode 轻快、美观，写 C 语言作业足够了。

针对 **Windows 11 + 学习 C 语言** 的场景，我把配置精简为 **三步**，跟着走就行：

---

## ✅ 第一步：安装编译器（MinGW-W64 或 MSYS2）

学习 C 语言只需要能编译、运行单文件程序，推荐 **MinGW-W64**（轻量、简单）。

1. 下载：[https://www.mingw-w64.org/downloads/](https://www.mingw-w64.org/downloads/)  
   或者直接使用 **winlibs** 提供的独立压缩包（**更方便**）：  
   [https://winlibs.com/](https://winlibs.com/) 下载 `UCRT runtime` 版本的 `mingw64.zip`

2. 解压到 `C:\mingw64`（**路径不要有中文或空格**）

3. 将 `C:\mingw64\bin` 添加到系统 **环境变量 Path** 中：
   - 右键“此电脑” → 属性 → 高级系统设置 → 环境变量
   - 在“系统变量”中找到 `Path` → 编辑 → 新建 → 填入 `C:\mingw64\bin`
   - 确定保存

4. 验证：打开 **CMD** 或 **PowerShell**，输入  
   ```bash
   gcc --version
   ```
   看到版本信息即成功。

> 如果嫌配置环境变量麻烦，也可以安装 **MSYS2**（稍大一点点），但更省心。不过 MinGW-W64 完全够你用一学期了。

---

## ✅ 第二步：安装 VSCode 扩展

打开 VSCode，按 `Ctrl+Shift+X` 搜索并安装以下 **2 个**：

1. **C/C++**（微软官方）  
   提供语法高亮、代码补全、调试支持

2. **Code Runner**  
   一键运行 `.c` 文件，不用手动敲编译命令（非常适合快速写小作业）

> 可选的：`Chinese (Simplified)` 中文界面包

---

## ✅ 第三步：写一个 Hello World 测试

1. 在电脑上新建一个文件夹，比如 `C-Learning`
2. 在 VSCode 中打开这个文件夹：`文件` → `打开文件夹`
3. 新建文件 `hello.c`，输入：
   ```c
   #include <stdio.h>
   int main() {
       printf("Hello, VSCode!\n");
       return 0;
   }
   ```

4. **运行（两种方式）**：
   - **用 Code Runner**：直接点击代码右上角的 ▶️ 图标，或按 `Ctrl+Alt+N`，输出会显示在“输出”面板中。
   - **手动编译**：打开终端（`` Ctrl+` ``），输入  
     
     ```bash
     gcc hello.c -o hello
     .\hello.exe
     ```
   
5. **调试**：  
   在想暂停的行号左侧单击一下（设置红点断点），然后按 `F5` → 选择 `C++ (GDB/LLDB)` → 它会自动生成配置并启动调试。如果提示找不到编译器路径，会弹出选择，你直接选 `gcc.exe` 就行。

---

## 💡 几点针对学习的小建议

- **中文乱码**：如果打印中文出现乱码，把 `hello.c` 右下角的编码改为 `GB 2312` 或 `GBK`（Windows 终端默认编码），或者保持 UTF-8 然后在终端输入 `chcp 65001` 切换编码。简单起见，学习阶段代码中尽量写英文注释和输出。
- **多文件作业**（比如大作业需要分多个 `.c` 和 `.h` 文件）：  
  初期用 Code Runner 可能只编译当前文件，会报“未定义引用”。这时候需要打开终端手动编译：  
  ```bash
  gcc main.c utils.c -o program
  ```
  等学到后面再用 `tasks.json` 或 Makefile，初期不必过早折腾。

- **不要被 VSCode 的 `launch.json` / `tasks.json` 吓到**：  
  学习阶段用 Code Runner 跑通代码 + F5 调试点单步执行就够了。那两套配置文件等你自己想要更精细控制编译参数时再去学。

---

## 🎯 总结

**你的配置路线就是：**  
装 MinGW → 装两个扩展 → 写 `.c` 文件 → 点 ▶️ 运行。

比起 IDE，这套搭配非常轻巧，适合边学边敲。如果在调试或路径上卡住，随时可以再来问！
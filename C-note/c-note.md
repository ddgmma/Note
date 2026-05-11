# C-Note

## 1、vocde运行c语言乱码问题

vscode内用utf-8格式保存下面的代码：

```c
#include <stdio.h>
int main() {
    printf("你好");
    return 0;
}
```

**如果运行出现乱码：**

1. 直接右下角用**GBK**编码保存

2. 在main函数开头加一行：

   * ```c
     system("chcp 65001 > nul"); //每次运行都强行切 UTF-8
     ```
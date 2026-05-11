# Win10 Win11激活方法:
**方法1：**桌面创建“激活Windows.bat”文件。编辑打开，输入两行代码:

1. slmgr /skms kms.03k.org

   slmgr /ato

2. 保存后以管理员身份运行。

  * 提示：如果出现非核心版本提示则先安装一个通用授权密钥：slmgr /ipk W269N-WFGWX-YVC9B-4J6C9-T83GX（次激活为KM激活期限180天，180天以后命令提示符输入slmgr /ato即可再次激活）**kms激活不支持家庭版。**

3. 查看kms激活剩余时间：
slmgr /xpr
slmgr /dlv

**方法2(永久)：**Win+R输入powershell
对话框输入
`irm https://get.activated.win | iex`
回车等待对话框弹出
然后输入1
等几分钟就激活了
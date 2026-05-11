# 命令行阿里云千问ai启动报错

## 问题详情

启动命令：
```bash
python3 hello_qwen.py
```
报错提示：
```bash
Traceback (most recent call last):
  File "/home/ddgmmf/qwen_ai/hello_qwen.py", line 12, in <module>
    import dashscope
ModuleNotFoundError: No module named 'dashscope'
```

## 解决步骤
第一步：安装DashScope Python SDK
```bash
sudo pip install dashscope

```
第二步：重新启动
```bash
python3 hello_qwen.py
```

## 💡 预防措施
**进入项目目录,创建生成requirements.txt**
执行：

```bash
cd ~/qwen_ai
sudo pip freeze > requirements.txt
```
重装环境时，执行：
```bash
sudo pip install -r requirements.txt
```

## node

### 问题

非 root 用户不能 `npm install -g` 

### 说明

二进制文件将放在 `~/.local/bin/`。
其余文件将放在 `~/.local/lib/node_modules/`.

### 1. 配置 npm
运行:

```bash
npm config set prefix '~/.local/'
```

该命令将（生成）并修改 `~/.npmrc` 使其含有该行：

```
prefix=~/.local/
```

### 2. 确认 ~/.local/bin 存在并在 PATH 中

运行 `echo "$PATH"` 来检查 PATH. 如果 `~/.local/bin/` 不在其中，执行下面的命令.

```bash
mkdir -p ~/.local/bin
echo 'export PATH=~/.local/bin/:$PATH' >> ~/.bashrc
```

如果你使用的 shell 不是 bash，将 `.bashrc` 替换成对应的配置文件。

### 3. 安装对应包

```bash
npm install -g <package_name>
```

### 参考:

[how-to-npm-install-global-not-as-root](https://stackoverflow.com/questions/18088372/how-to-npm-install-global-not-as-root)
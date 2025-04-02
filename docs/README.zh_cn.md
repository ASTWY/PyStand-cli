# PyStand-cli

该工具使用 PyStand 和嵌入式 Python 将 Python 项目打包为独立的可执行文件。它支持排除特定目录和文件，并提供文件复制的进度条。

## 安装

1. **安装**：
   ```bash
   pip install pystand-cli
   ```
2. **升级**：
   ```bash
   pip install --upgrade pystand-cli
   ```

## 使用

### 基本命令

pystand-cl entry_script.py [OPTIONS]

### 参数

| Option            | Description                                                             |
| ----------------- | ----------------------------------------------------------------------- |
| `--project-dir`   | T 项目目录（可选）。(optional).                                         |
| `--exclude-dirs`  | 要排除的文件夹（可选，可多次指定）。                                    |
| `--exclude-files` | 要排除的文件（可选，可多次指定）。                                      |
| `--output-dir`    | 输出目录（可选，默认为 dist）。                                         |
| `--noconsole`     | 运行应用程序时不显示控制台窗口（可选）。                                |
| `--python-repo`   | Python FTP 仓库 URL（可选，默认为 https://www.python.org/ftp/python）。 |

### 示例

1. **打包带有入口脚本的项目**：

   ```bash
   pystand-cl entry_script.py --project-dir /path/to/project
   ```

2. **排除特定目录和文件**：

   ```bash
   pystand-cl entry_script.py --project-dir /path/to/project --exclude-dirs node_modules --exclude-files .gitignore
   ```

3. **运行时不显示控制台窗口**：

   ```bash
   pystand-cl entry_script.py --project-dir /path/to/project --noconsole
   ```

4. **自定义输出目录**：

   ```bash
   pystand-cl entry_script.py --project-dir /path/to/project --output-dir /path/to/output
   ```

## 输出结构

输出目录将包含以下结构：

```
output_dir/
├── runtime/                # 嵌入式 Python 运行时
├── site-packages/          # Python 第三方库
├── main.exe                # PyStand 可执行文件
├── main.py                 # 入口脚本
└── ...                     # 其他文件和目录
```

## 注意事项

**嵌入式 Python**：该工具从官方 Python FTP 仓库下载嵌入式 Python 运行时。
**PyStand**：PyStand 用于从入口脚本创建独立的可执行文件。
**排除功能**：排除的目录和文件不会被复制到输出目录。
**GUI 应用程序**：使用 `--noconsole` 选项运行应用程序时不显示控制台窗口。CLI 应用程序不应使用此选项。

## 许可证

本项目采用 MIT 许可证。详情请参阅 LICENSE 文件。

## 致谢

- [PyStand](https://github.com/skywind3000/PyStand)由 skywind3000 开发。
- [Click](https://click.palletsprojects.com/) 用于命令行界面支持。

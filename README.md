### TexWrap README

[English-README](https://github.com/Xproit/TexWrap/blob/main/Docs/En-README.md)

#### 基本语法

```
.\TexWrap input.md output.md
```

#### 功能说明

1. 支持标准格式转换
2. 必须严格指定输入文件和输出文件路径
    1. 如没有找到文件，会`Error: Cannot open input file xxx.md `
    2. 若格式错误，会`Usage: .\TexWrap <input.md> <output.md>`
3. **转换规则**：
    - 行内公式：`/(公式/)` → `$公式$`
    - 行间公式：`/[公式/]` → `$$公式$$`

#### 使用示例

```bash
# 基础转换（Windows）
.\TexWrap draft.md final.md

# Linux/macOS
./TexWrap input.md output.md
```

#### 文件要求

| 项目     | 要求                          |
| -------- | ----------------------------- |
| 输入文件 | 必须为UTF-8编码的Markdown文件 |
| 输出路径 | 必须具有写入权限              |
| 文件大小 | 建议不超过100MB               |

#### 错误处理

1. **参数错误**：

    - 缺少参数时报错：`Usage: .\TexWrap <input.md> <output.md>`

    - 示例错误：

        ```bash
        .\TexWrap input.md  # 缺少输出文件
        ```

2. **文件错误**：

    - 输入文件不存在时报错：`Error: Input file not found`
    - 输出路径不可写时报错：`Error: Cannot write to output path`

#### 典型输出

1. 成功时：

    ```
    Successfully processed delimiters!
    Converted file saved to: out.md
    ```

2. 失败时：

    ```
    Error: Cannot open input file input.md
    ```

#### 注意事项

1. 所有公式分隔符必须正确闭合
2. 不支持嵌套公式转换
3. 转换后不会修改原文件
4. 不支持管道输入/输出

#### 转换示例

输入文件 `input.md` 内容：

```markdown
# 测试文档
行内公式：/(E=mc^2/)
行间公式：
/[ \int_a^b f(x)dx /]
```

转换命令：

```bash
.\TexWrap input.md output.md
```

输出文件 `output.md` 内容：

```markdown
# 测试文档
行内公式：$E=mc^2$
行间公式：
$$ \int_a^b f(x)dx $$
```

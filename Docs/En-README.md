### TexWrap README

#### Basic Syntax

```
.\TexWrap input.md output.md
```

#### Feature Description

1. Supports standard format conversion.
2. Input and output file paths must be strictly specified.
  - If the file is not found: `Error: Cannot open input file xxx.md`
  - If the format is incorrect: `Usage: .\TexWrap <input.md> <output.md>`
3. **Conversion Rules**:
  - Inline formulas: `/(formula/)` → `$formula$`
  - Block formulas: `/[formula/]` → `$$formula$$`

#### Usage Example

```bash
# Basic conversion (Windows)
.\TexWrap draft.md final.md

# Linux/macOS
./TexWrap input.md output.md
```

#### File Requirements

| Item | Requirement |
| --- | --- |
| Input File | Must be a UTF-8 encoded Markdown file |
| Output Path | Must have write permissions |
| File Size | Recommended not to exceed 100MB |

#### Error Handling

1. **Parameter Errors**:
  
  - Missing parameters: `Usage: .\TexWrap <input.md> <output.md>`
  - Example error:
    
    ```bash
    .\TexWrap input.md  # Missing output file
    ```
    
2. **File Errors**:
  
  - Input file not found: `Error: Input file not found`
  - Output path not writable: `Error: Cannot write to output path`

#### Typical Output

1. On success:
  
  ```
  Successfully processed delimiters!
  Converted file saved to: out.md
  ```
  
2. On failure:
  
  ```
  Error: Cannot open input file input.md
  ```
  

#### Notes

1. All formula delimiters must be properly closed.
2. Nested formula conversion is not supported.
3. The original file will not be modified after conversion.
4. Pipe input/output is not supported.

#### Conversion Example

Input file `input.md` content:

```markdown
# Test Document
Inline formula: /(E=mc^2/)
Block formula:
/[ \int_a^b f(x)dx /]
```

Conversion command:

```bash
.\TexWrap input.md output.md
```

Output file `output.md` content:

```markdown
# Test Document
Inline formula: $E=mc^2$
Block formula:
$$ \int_a^b f(x)dx $$
```

# Markdown and LaTeX Formatting Cheatsheet

## Table of Contents
- [Basic Markdown](#basic-markdown)
- [Extended Formatting](#extended-formatting)
- [Lists](#lists)
- [Links and Images](#links-and-images)
- [Code](#code)
- [Tables](#tables)
- [LaTeX Math Formatting](#latex-math-formatting)
- [GitHub-Specific Markdown](#github-specific-markdown)

## Basic Markdown

| Element | Syntax |
|---------|--------|
| Heading 1 | `# Heading 1` |
| Heading 2 | `## Heading 2` |
| Heading 3 | `### Heading 3` |
| Heading 4 | `#### Heading 4` |
| Heading 5 | `##### Heading 5` |
| Heading 6 | `###### Heading 6` |
| Paragraph | Plain text |
| Line break | End a line with two or more spaces, then return |
| Horizontal rule | `---` or `***` or `___` |

## Extended Formatting

| Element | Syntax |
|---------|--------|
| Bold | `**bold text**` or `__bold text__` |
| Italic | `*italicized text*` or `_italicized text_` |
| Bold and Italic | `***bold and italic***` or `___bold and italic___` |
| Strikethrough | `~~strikethrough text~~` |
| Blockquote | `> blockquote` |
| Nested blockquote | `> blockquote` <br> `>> nested blockquote` |

## Lists

### Ordered Lists
```
1. First item
2. Second item
3. Third item
```

### Unordered Lists
```
- First item
- Second item
- Third item
```
or
```
* First item
* Second item
* Third item
```
or
```
+ First item
+ Second item
+ Third item
```

### Nested Lists
```
1. First item
   - Nested item
   - Nested item
2. Second item
   * Nested item
     * Deeply nested item
```

### Task Lists
```
- [x] Completed task
- [ ] Incomplete task
```

## Links and Images

### Links
```
[Link text](URL "Title")
```

### Reference-style Links
```
[Link text][reference]

[reference]: URL "Title"
```

### Automatic Links
```
<https://www.example.com>
<email@example.com>
```

### Images
```
![Alt text](URL "Title")
```

### Reference-style Images
```
![Alt text][reference]

[reference]: URL "Title"
```

## Code

### Inline Code
```
`inline code`
```

### Code Blocks
````
```
code block
```
````

### Syntax Highlighting
````
```javascript
function hello() {
  console.log("Hello, world!");
}
```
````

## Tables

```
| Header 1 | Header 2 | Header 3 |
|----------|----------|----------|
| Cell 1   | Cell 2   | Cell 3   |
| Cell 4   | Cell 5   | Cell 6   |
```

### Alignment
```
| Left-aligned | Center-aligned | Right-aligned |
|:-------------|:--------------:|---------------:|
| Left         | Center         | Right          |
```

## LaTeX Math Formatting

LaTeX math can be used in Markdown when supported by the renderer (like GitHub, Jupyter notebooks, or dedicated Markdown editors).

### Inline Math
```
$E = mc^2$
```

### Display Math
```
$$
E = mc^2
$$
```

### Common Math Symbols

| Description | Symbol | LaTeX Code |
|-------------|--------|------------|
| Addition | + | `+` |
| Subtraction | - | `-` |
| Multiplication | × | `\times` |
| Division | ÷ | `\div` |
| Fraction | ½ | `\frac{1}{2}` |
| Square root | √ | `\sqrt{x}` |
| Cube root | ∛ | `\sqrt[3]{x}` |
| Power | x² | `x^2` |
| Subscript | xₙ | `x_n` |
| Pi | π | `\pi` |
| Infinity | ∞ | `\infty` |
| Partial derivative | ∂ | `\partial` |
| Integral | ∫ | `\int` |
| Double integral | ∬ | `\iint` |
| Triple integral | ∭ | `\iiint` |
| Sum | ∑ | `\sum` |
| Product | ∏ | `\prod` |
| Less than or equal | ≤ | `\leq` |
| Greater than or equal | ≥ | `\geq` |
| Not equal | ≠ | `\neq` |
| Approximately equal | ≈ | `\approx` |
| Element of | ∈ | `\in` |
| Not element of | ∉ | `\notin` |
| Subset | ⊂ | `\subset` |
| Superset | ⊃ | `\supset` |
| Intersection | ∩ | `\cap` |
| Union | ∪ | `\cup` |
| Empty set | ∅ | `\emptyset` |
| For all | ∀ | `\forall` |
| Exists | ∃ | `\exists` |
| Does not exist | ∄ | `\nexists` |
| Therefore | ∴ | `\therefore` |
| Because | ∵ | `\because` |
| Dot product | ⋅ | `\cdot` |
| Cross product | × | `\times` |
| Gradient | ∇ | `\nabla` |
| Degree | ° | `^\circ` |
| Angle | ∠ | `\angle` |
| Perpendicular | ⊥ | `\perp` |
| Parallel | ∥ | `\parallel` |
| Alpha | α | `\alpha` |
| Beta | β | `\beta` |
| Gamma | γ | `\gamma` |
| Delta | δ | `\delta` |
| Epsilon | ε | `\epsilon` |
| Theta | θ | `\theta` |
| Lambda | λ | `\lambda` |
| Mu | μ | `\mu` |
| Sigma | σ | `\sigma` |
| Phi | φ | `\phi` |
| Omega | ω | `\omega` |

### Common Math Expressions

| Description | LaTeX Code |
|-------------|------------|
| Limit | `\lim_{x \to \infty} f(x)` |
| Summation | `\sum_{i=1}^{n} x_i` |
| Product | `\prod_{i=1}^{n} x_i` |
| Definite integral | `\int_{a}^{b} f(x) dx` |
| Derivative | `\frac{d}{dx} f(x)` |
| Partial derivative | `\frac{\partial f}{\partial x}` |
| Matrix | `\begin{pmatrix} a & b \\ c & d \end{pmatrix}` |
| Determinant | `\begin{vmatrix} a & b \\ c & d \end{vmatrix}` |
| Vector | `\vec{v}` or `\overrightarrow{AB}` |
| Hat/circumflex | `\hat{x}` |
| Bar/overline | `\bar{x}` |
| Tilde | `\tilde{x}` |
| Dot | `\dot{x}` or `\ddot{x}` (double dot) |
| System of equations | `\begin{cases} a + b = c \\ x - y = z \end{cases}` |
| Cases | `f(x) = \begin{cases} x^2 & \text{if } x > 0 \\ 0 & \text{otherwise} \end{cases}` |

## GitHub-Specific Markdown

### Collapsed Sections
```
<details>
<summary>Click to expand</summary>

Content goes here...
</details>
```

### Emoji
`:emoji_name:` e.g. `:smile:` :smile:

### Mentions
`@username`

### Issue/PR References
`#issue_number` or `username/repository#issue_number`

### SHA References
Use any commit SHA

### Auto-Linked References
GitHub automatically links:
- URLs
- Issues and PRs: `#123`
- Commits: 7-char SHA
- Username mentions: `@username`

## Acknowledgements

This cheatsheet was developed with assistance from Anthropic's Claude AI assistant, which helped with:
- Documentation writing and organization
- Content structure suggestions

Claude was used as a development aid while all final implementation decisions and review were performed by Joshua Michael Hall.

## Disclaimer

This cheatsheet is provided as-is without any warranty or liability. It is a work in progress and may contain errors or omissions. Please report any issues you encounter.

## Ripgrep (rg) Usage Guide

### Basic syntax:
```
rg [OPTIONS] PATTERN [PATH ...]
rg [OPTIONS] -e PATTERN ... [PATH ...]
```

### Key best practices:
1. **Always use `-e` flag for patterns** to avoid issues with patterns starting with `-` or containing special characters
2. **Always use single quotes** around patterns to prevent shell interpolation
3. **Use `--` delimiter** when needed to separate options from arguments

### Common usage examples:
```bash
# Basic search (with -e flag and single quotes)
rg -e 'pattern' 

# Search in specific directory
rg -e 'pattern' /path/to/dir

# Case-insensitive search
rg -i -e 'pattern'

# Search for exact string (no regex)
rg -F -e 'exact string'

# Search specific file types
rg -e 'pattern' -t js  # JavaScript files
rg -e 'pattern' -g '*.py'  # Python files

# Exclude patterns/directories
rg -e 'pattern' -g '!*.test.js'
rg -e 'pattern' -g '!node_modules'

# Show context lines
rg -e 'pattern' -C 3  # 3 lines before and after
rg -e 'pattern' -B 2  # 2 lines before
rg -e 'pattern' -A 2  # 2 lines after

# Count matches
rg -c -e 'pattern'  # Count matching lines
rg --count-matches -e 'pattern'  # Count total matches

# List files with matches
rg -l -e 'pattern'

# Search for multiple patterns
rg -e 'pattern1' -e 'pattern2'

# Invert match (lines NOT containing pattern)
rg -v -e 'pattern'

# Search for line numbers
rg -n -e 'pattern'
```

### Important flags:
- `-e PATTERN`: Specify pattern (use this always)
- `-i`: Case-insensitive
- `-F`: Fixed string (literal, no regex)
- `-w`: Word boundaries
- `-x`: Whole line must match
- `-v`: Invert match
- `-c`: Count matching lines
- `-l`: List files with matches
- `-L`: List files without matches
- `-n`: Show line numbers (default)
- `-H`: Show filenames (default for multiple files)
- `-g GLOB`: Include/exclude files
- `-t TYPE`: Search only in file type
- `-C/-B/-A NUM`: Context lines

### Common file type flags (-t):
- **JavaScript**: `-t js` (includes .js, .jsx, .mjs, .cjs, .vue)
- **TypeScript**: `-t ts` (includes .ts, .tsx, .cts, .mts)
- **Python**: `-t py` (includes .py, .pyi)
- **Java**: `-t java` (includes .java, .jsp, .jspx, .properties)
- **C**: `-t c` (includes .c, .h, .C, .H)
- **C++**: `-t cpp` (includes .cpp, .cc, .cxx, .hpp, .hh, .C, .H)
- **Go**: `-t go` (includes .go)
- **Rust**: `-t rust` (includes .rs)
- **Ruby**: `-t ruby` (includes .rb, .rbw, .gemspec, Gemfile, Rakefile)
- **Clojure**: `-t clojure` (includes .clj, .cljc, .cljs, .cljx)
- **ClojureScript**: `-t cljs` (includes .cljs)
- **Perl**: `-t perl` (includes .pl, .pm, .t, .PL, .perl, .plx, .plh)
- **Shell**: `-t sh` (includes .sh, .bash, .zsh, .ksh, .csh, .bashrc, .zshrc, etc.)
- **HTML**: `-t html` (includes .html, .htm, .ejs)
- **CSS**: `-t css` (includes .css, .scss)
- **Markdown**: `-t md` or `-t markdown` (includes .md, .markdown, .mdown, .mdx)
- **YAML**: `-t yaml` (includes .yaml, .yml)
- **JSON**: `-t json` (includes .json, .sarif, composer.lock)
- **XML**: `-t xml` (includes .xml, .xsd, .xsl, .xslt, .dtd)

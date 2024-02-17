---
layout: page
title: Converting standard markdown to kramdown markdown
description: Kramdown markdown seems to follow a different style from standard markdown. This leads to complications when publicating a standard markdown page quickly.
importance: 1
date: 2023-06-23 12:30:00-0400
category: Tools
---

One of the many merits of Jekyll is that markdown documents can be easily handled and converted to html pages using [kramdown](https://kramdown.gettalong.org/) parser. Kramdown markdown, however, seems to be slightly different in interpreting the contents, compared to the standard flavour of markdown.
In particular, kramdown seems to have different delimiters for equation environment.
Kramdown takes the double dollar sign "\$\$" as the inline equation delimiters, and double dollar sign with empty lines before or after as the display equation delimiters.
This makes publishing a standard markdown page complicated, as the standard .md usually renders contents bracketed by single dollar sign as inline equation, and double dollar sign as display equation.

In some scenarios, it is possible to disable math processing of kramdown, and leave it directly to MathJax or KaTeX to interpret and render the result.
However, this no longer works perfectly when there is markdown escape characters in the equation environment. For instance, the underscore is a valid character in equations. If kramdown does not know it is equation and process it as plain markdown text, it will be interpreted into italics or other formatting marks. Eventually, the formatting html segments will also break the rendering of MathJax or KaTex.

The only approach that worked for me is to manually converting the standard markdown into kramdown style. To this end I use the regular expression to capture the equation environments and replace the delimiters. The python code is as follows (see also the [GitHub gist page](https://gist.github.com/GentleMin/39fe427d7f9f387c805e2432e4178b82)).

```python
import re
import argparse

parser = argparse.ArgumentParser(description="Convert standard markdown to kramdown-style markdown.")
parser.add_argument("in_file", nargs='+', type=str)
parser.add_argument("-t", '--yaml_template', nargs='+', type=str)
parser.add_argument("-o", '--out_file', nargs='+', type=str)

inline_pattern = re.compile(r"(?<=[^\$])\$(?P<formula>[^\$]+?)\$(?=[^\$])")
inline_pattern_bof = re.compile(r"^\$(?P<formula>[^\$]+?)\$")
inline_pattern_eof = re.compile(r"\$(?P<formula>[^\$]+?)\$$")

def inline_replace(inline_obj):
    str_repl = "$$" + inline_obj.group("formula") + "$$"
    return str_repl

display_pattern = re.compile(r"(?P<prefix>.{1})\n\$\$(?P<formula>[^\$]+?)\$\$\n(?P<suffix>.{1})", flags=re.DOTALL)
display_pattern_bof = re.compile(r"^\$\$(?P<formula>[^\$]+?)\$\$\n(?=[^\n])")
display_pattern_eof = re.compile(r"(?<=[^\n])\n\$\$(?P<formula>[^\$]+?)\$\$$")

def display_replace(display_obj):
    prefix = display_obj.group("prefix") if display_obj.group("prefix") == '\n' else display_obj.group("prefix") + '\n'
    suffix = display_obj.group("suffix") if display_obj.group("suffix") == '\n' else '\n' + display_obj.group("suffix")
    str_repl = prefix + "\n$$" + display_obj.group("formula") + "$$\n" + suffix
    return str_repl

yaml_hdr_pattern = re.compile(r"---.*?---", flags=re.DOTALL)
def get_yaml_hdr(yaml_template):
    with open(yaml_template, 'r') as f_yaml:
        doc_string = ''.join(f_yaml.readlines())
    match_obj = yaml_hdr_pattern.search(doc_string)
    return match_obj.group(0)


if __name__ == "__main__":
    
    args = parser.parse_args()
    assert len(args.in_file) == len(args.out_file)
    
    for i in range(len(args.in_file)):
        in_fname = args.in_file[i]
        out_fname = args.out_file[i]
        yaml_template = args.yaml_template[i]
        
        with open(in_fname, 'r') as f:
            doc_string = ''.join(f.readlines())
        
        doc_string = '\n' + doc_string + '\n'
        
        doc_string = inline_pattern.sub(inline_replace, doc_string)
        doc_string = display_pattern.sub(display_replace, doc_string)
        doc_string = yaml_hdr_pattern.sub("\n", doc_string)
        
        hdr = get_yaml_hdr(yaml_template)
        doc_string = hdr + '\n' + doc_string
        
        with open(out_fname, 'w') as f:
            print(doc_string, file=f)
```

The aforementioned code can be accessed directly via commandline. 
For instance, to convert `<src-md-file>` to `<out-md-file>`, using the yaml header block in `<yaml-template>`, one can invoke this script using the following command:

```bash
python .\std2kramdown.py <src-md-file> -t <yaml-template> -o <out-md-file>
```

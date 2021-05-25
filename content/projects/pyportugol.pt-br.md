+++
description = "A toy project for a Portugol's transpiler made in Python."
repository  = "https://github.com/carlosdamazio/pyportugol"
linkTitle   = "PyPortugol"
slug        = "pyportugol"
title       = "PyPortugol"
+++

Small project for a "Portugol" transpiler made in Python 3.6

## Installation

Just clone the repository and install dependencies.

{{< highlight console >}}

$ git clone git@github.com:carlosdamazio/pyportugol.git
$ cd pyportugol && pip install -r requirements.txt

{{< / highlight >}}

## Usage

On main.py, you can see the text input for the transpiler. I'll add the language specs later.

{{< highlight python "linenos=table,hl_lines=5 6 7 8 9 10 11">}}
from lexer.lexer import Lexer
from parser.parser import Parser


text_input = """
    inteiro:x;
    inteiro:y;
    leia(x);
    leia(y);
    para x ate y passo 1 imprima(x); fim_para
"""

lexer = Lexer().get_lexer()

pg = Parser()
pg.parse()
parser = pg.get_parser()

for line in list(filter(None, text_input.split('\n'))):
    tokens = lexer.lex(line)
    parser.parse(tokens).eval()
{{< / highlight >}}

Just run the project with Python.

{{< highlight console >}}
$ python main.py
{{< / highlight >}}

## Introduction

no such thing as interpreted languages/compiled languages. e.g. there are C interpreters

## Lexical Analysis

source code $\xrightarrow{\text{lexical analysis}}$  token stream $\xrightarrow{\text{parsing}}$ useful tree-like representation

token = syntactic category (i.e. type of token, e.g. IF, ID, EQUALS, ASSIGN) + lexical value (name of variable, value of integer, etc. only exists if syntactic cat = ID). only syntactic category important to parser

use regular expressions to implement lexer. each regular expression $R$ corresponds to a set of strings $L(R)$
---
title: "C3 Tutorial"
weight: 0
---
{{<start>}}
## Welcome to the C3 programming language tutorial.

C3 is a systems programming language that aims to be an evolution of C;
enabling the same paradigms and syntax where possible, while adding more modern
quality of life features.<br>
The purpose of this tutorial is to get you started programming in C3 as soon
as possible.<br>
Some familiarity with the C language is reccomended, but general programming
concepts will still be covered.<br>
We begin with Hello World!
{{<end>}}

{{<defcod>}}
module example;
import std::io;

fn void main()
{
	io::printfn("Hello, World!");
}
{{</defcod>}}

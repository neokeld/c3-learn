---
title: "Named Arguments"
slug: "named arguments"
weight: 3
---
{{<start>}}
- C3 allows use of named arguments. Note that any unnamed arguments must appear before any named arguments and in the same order that they are declared.
{{<end>}}

{{<defcod>}}
import std::io;

fn void test(int x, double y)
{
	io::printfn("%f", x + y);
}

fn void main()
{
	test(x: 1, y: 3.0);
	test(3, 4.0);
	test(15, y: 3.141592);
}
{{</defcod>}}


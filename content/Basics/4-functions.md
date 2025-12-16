---
title: "Functions"
slug: "functions"
aliases:
 - "/Basics/4"
weight: 4
---
{{<start>}}
Functions in C3 are declared the same way as in C with the addition of the `fn`
keyword.

{{<defcod>}}
import std::io;

fn void test(int x)
{
	io::printfn("%d", x);
}

fn void main()
{
	test(100);
}

{{</defcod>}}
{{<end>}}


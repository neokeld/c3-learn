---
title: "Function Pointers"
slug: "function pointers"
aliases:
 - "/More/29"
weight: 16
---
{{<start>}}
- Similar to C function pointers.
- Function pointer types must be defined explicitly using `alias`, they cannot be defined inline in the function declaration.

{{<defcod>}}
import std::io;

alias IntCallback = fn int(int x);

fn int square(int x)
{
	return x * x;
}

fn int cube(int x)
{
	return x * x * x;
}

fn void print10(IntCallback callback)
{
	for (int i = 1; i <= 10; i++)
	{
		io::printfn("%d -> %d", i, callback(i));
	}
}

fn void main()
{
	print10(&square);
	print10(&cube);
}
{{</defcod>}}
{{<end>}}

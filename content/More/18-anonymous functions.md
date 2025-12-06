---
title: "Anonymous Functions"
slug: "anonymous functions"
weight: 18
---
{{<start>}}
- Work like regular functions and do not capture the calling environment.
- Anonymous functions can use regular or short function syntax.
- Types may be left out if they can be inferred.
{{<end>}}

{{<defcod>}}
import std::io;

alias IntCallback = fn int(int x);

fn void print3(IntCallback callback)
{
	for (int i = 1; i <= 3; i++)
	{
		io::printfn("%d -> %d", i, callback(i));
	}
}

fn void main()
{
	print3(fn int(int x) { return x * x; });
	print3(fn(x) => x * x * x);
}
{{</defcod>}}

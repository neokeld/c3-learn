---
title: "Error Handling 5"
slug: "error handling 5"
weight: 12
---
{{<start>}}
- The downside of `if try` is that it usually puts the main code inside of a block.
- We can instead use `if catch` which instead executes on an optional to get the error. And if there is a `return` from this `if` then the variable will be considered checked to be a real type.
{{<end>}}

{{<defcod>}}
import std::io;

faultdef DIVISION_BY_ZERO;

fn int? divide_int(int x, int y)
{
	if (!y) return DIVISION_BY_ZERO?;
	return x / y;
}

fn void main()
{
	int a = 4;
	int b = 0;
	int? x = divide_int(a, b);
	// int y = x * 2 this would be an error here

	if (catch err = x)
	{
		// Running if b == 0
		io::printfn("Had error: '%s'.", err);
		return;
	}
	// x is a normal "int" now,
	// so this works:
	int y = x * 2;
}

{{</defcod>}}

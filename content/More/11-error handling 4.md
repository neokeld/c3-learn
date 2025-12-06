---
title: "Error Handling 4"
slug: "error handling 4"
weight: 11
---
{{<start>}}
- Returning a value is similar, but to extract the value we need to make a test. Let's first look at a simple function illustrating the use.
- Both `divide_int(4, 2)` and `divide_int(4, 0)` would give us an `int?` result, so how do we decide what we got? We use `if-catch` or `if-try`.
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
	int b = 2;

	if (try div = divide_int(a, b))
	{
		// This code will only be run if b != 0
		io::printfn("b is not zero");
	}
}

{{</defcod>}}

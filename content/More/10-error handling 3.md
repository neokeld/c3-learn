---
title: "Error Handling 3"
slug: "error handling 3"
aliases:
 - "/More/23"
weight: 10
---
{{<start>}}
- This will print `-1 had error`.
{{<end>}}

{{<defcod>}}
import std::io;

faultdef SOMETHING_MISSING, GENERAL_ERROR_WAS_HERE;

fn void? x(int i)
{
	if (i < 0) return SOMETHING_MISSING?;
}

fn void main()
{
	fault y = @catch(x(10));

	if (y) io::printfn("10 had error.");
	y = @catch(x(-1));
	if (y) io::printfn("-1 had error.");
}

{{</defcod>}}

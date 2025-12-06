---
title: "Arrays"
slug: "arrays"
weight: 12
---
{{<start>}}
- Array sizes are written next to the type.
- Arrays do not decay to pointers, you need to do it manually.
{{<end>}}

{{<defcod>}}
import std::io;

fn void main()
{
	int[6] list = { 2, 3, 5, 7, 11, 13 };
	int* p;

	p = &list;
	io::printfn("%d", list[4]);
	io::printfn("%d", *p);
}
{{</defcod>}}


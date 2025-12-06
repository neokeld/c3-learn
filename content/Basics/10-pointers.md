---
title: "Pointers"
slug: "pointers"
aliases:
 - "/Basics/10"
weight: 10
---
{{<start>}}
{{<end>}}

{{<defcod>}}
import std::io;

fn void main()
{
	int i;
	int* p;

	i = 0;
	p = &i;
	io::printfn("%d", i);
	io::printfn("%d", *p);
	*p = 1;
	io::printfn("%d", i);
	io::printfn("%d", *p);
}
{{</defcod>}}

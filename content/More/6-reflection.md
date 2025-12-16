---
title: "Reflection"
slug: "reflection"
aliases:
 - "/More/19"
weight: 6
---
{{<start>}}
- There are several built-in functions to inspect the code during compile time.
- `.len` on arrays return their length.
- `$defined(<expr>)` returns true if the expression inside is defined.
- `$alignof(<expr>)` returns alignment.
- `$sizeof(<expr>)` returns size.
- `$qnameof(<identifier>)` to get the qualified name of the identifier, e.g `std::io::printf`
- `$nameof(<identifier>)` to get the base name of the identifier, e.g. `printf`
- `$typeof(<expr>)` returns the type of the expression.
- `$stringify(<expr>)` returns the expression as a string.
- `<type>.sizeof` returns the size of a type.
- `<type>.alignof` returns the alignment of a type.
- `<type>.nameof` return the name of a type.

See https://c3-lang.org/generic-programming/reflection/ for the full details.
{{<end>}}

{{<defcod>}}
import std::io;

fn void main()
{
	int x;
	double y;

	if ($defined(z))
	{
		io::printfn("hello, world");
	}
	io::printfn($qnameof(io::printfn));
	io::printfn("%s %s", $sizeof(x), $sizeof(y));
	io::printfn("isz has size: %d", isz.sizeof);
}
{{</defcod>}}

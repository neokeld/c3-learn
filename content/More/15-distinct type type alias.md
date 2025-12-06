---
title: "Distinct Types & Type Aliases"
slug: "distinct type type alias"
weight: 15
---
{{<start>}}
- Uses the uniform `alias` syntax.
- Regular type aliases are the same as C `typedef`, C3 `typedef` creates a distinct type.
- Distinct types are type aliases that doesn't implicitly convert to the aliased type.
- `typedef inline` types can automatically convert to its underlying type and inherit the methods of its underlying type, but otherwise works as distinct types.
{{<end>}}

{{<defcod>}}
import std::io;

alias MyInt = int;
typedef MyId = int;

fn void main()
{
	MyInt x = 27;
	MyId y = 3;
	int a = x;
	// int b = y; <- This doesn't work

	// Explicit conversion works
	x += (int)y;

	io::printfn("%s %s", y, x);
}
{{</defcod>}}

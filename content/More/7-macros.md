---
title: "Macros"
slug: "macros"
weight: 7
---
{{<start>}}
- Macros are inlined each time they are called.
- Macros can have untyped parameters.
- Macros are allowed to use `var` to infer the type of any variable.
- Macros must start with `@` when they use expression parameters.
- Expression parameters start with a `#` and copy the passed expression every time they are used, similar to C macro parameters except the expression must be valid before it is copied.
{{<end>}}

{{<defcod>}}
import std::io;

macro void @swap(#x, #y)
{
	var temp = #x;

	#x = #y;
	#y = temp;
}

fn void main()
{
	int a = 0;
	int b = 1;

	io::printfn("%d", a);
	@swap(a, b);
	io::printfn("%d", a);
	// @swap(1, 2); // This will error because it will evaluate to `1 = 2`
}

{{</defcod>}}

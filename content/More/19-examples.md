+++
title = "More C3 Idioms"
slug = "idioms"
weight = 19
+++

{{<toc>}}

Some examples of "idiomatic" C3 code, or, code that follows patterns from the standard library.

# Type names and namespacing

## In general

Types in C3 do not need to be prefixed with their module namespace, and it is
recommended not to namespace types unless there is a name conflict.

Using types without namespacing can make your code more readable, especially with
longer module names, since you can instantly tell something is a type without needing
to read the module path first.

{{<codeblock id="types_general">}}
import std::io;
fn void main()
{
	// Not recommended
	std::io::File a;
	io::File b;
	// Recommended
	File c;
}
{{</codeblock>}}

## For library developers

If writing a library, the names of public types should be prefixed with a shortened
form of the library or module name to show what library it came from and prevent
possible name conflicts from using a generic name like `File`, `Window`, or `Rectangle`.

{{<codeblock id="0">}}
module raylib;
// Not recommended, may cause a conflict with another library and need to be used as `raylib::Rectangle`
struct Rectangle {float x, y, w, h;}
// Recommended, won't cause a conflict with other rectangle types
struct RLRectangle {float x, y, w, h;}
{{</codeblock>}}

# Functions that allocate data

Functions that allocate should take an `Allocator` as the first parameter and
use the `allocator::` functions such as `allocator::malloc` instead of `mem::malloc`.
Any intermediary allocations should be made on the temp allocator inside
an `@pool` block.<br>
If there is an allocator that is intended to be used by default then the
`Allocator` should be the final parameter and use a default value instead of
hardcoding the allocator inside the function.

This pattern both shows which functions make allocations (and thus need their
return values freed) due to the explicit allocator parameter and allows users
to pass an allocator of their choice.

{{<codeblock id="1">}}
import std::io;

fn void main()
{
	usz count = 5;
	int starting_value = 0;
	String res = some_func(mem, count, starting_value);
	io::printn(res);
	mem::free(res);
}

fn String some_func(Allocator alloc, usz count, int starting_value)
{
	@pool()
	{
		DString buf;
		// Initialise the string builder using the temporary allocator
		// The `@pool()` ensures it will be automatically freed when the function exits
		buf.init(tmem);
		for (usz i = 0; i < count; i++) buf.appendf("[%s]", starting_value + i);
		// Copy the final string into the passed allocator
		return buf.copy_str(alloc);
	};
}
{{</codeblock>}}

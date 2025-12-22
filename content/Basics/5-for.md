---
title: "For loops"
slug: "for"
aliases:
 - "/Basics/5"
weight: 5
---
C3 `for` loops are the same as in C.<br>
A `for` loop is made of 3 sections that are enclosed in parentheses and separated by semicolons:
 - the init section, which is is run once when the loop is first started and
   usually used to declare the counter (eg `usz i = 0`).
 - the condition section, which is checked before the code in the loop body is
   executed each iteration of the loop. The loop will continue running until the
   condition is no longer true.
 - the next section, which is run each iteration after the code in the loop body
   runs, and is usually used to add to the counter.

Any of these sections can be empty, but the semicolons must always be included.
If the condition is empty it will loop forever.

After the closing parenthesis there can either be a block or single line of code
as the body. If a body is not needed a semicolon can be used instead.

{{<codeblock id="sections">}}
import std::io;
fn void main()
{
	const TIMES = 5;
	for (usz i = 0; i < TIMES; i = i + 1)
	{
		io::printfn("Iteration %s", i);
	}
}
{{</codeblock>}}

The `break` keyword can be used to exit out of a loop early, and the `continue`
keyword will skip the rest of the code in the body and continue at the next
iteration of the loop.
{{<codeblock id="break">}}
import std::io;
fn void main()
{
	const TIMES = 10;
	for (usz i = 0; i < TIMES; i++)
	{
		if (i == 3)
		{
			io::printn("Continuing at 3");
			continue;
		}
		else if (i == 8)
		{
			io::printn("Breaking at 8");
			break;
		}
		io::printfn("Iteration %s", i);
	}
}
{{</codeblock>}}

Repeatedly doing `collection[index]` when iterating over a collection such as an
array or hashmap with a `for` loop can become a bit cumbersome, this is where
[`foreach`](/Basics/foreach) comes in.
{{<codeblock id="foreach">}}
fn void main()
{
	int[3] items = {123, 456, 789};
	for (usz i = 0; i < items.len; i++)
	{
		items[i] += items[i];
	}

	foreach (&item : items)
	{
		*item += *item;
	}
}
{{</codeblock>}}

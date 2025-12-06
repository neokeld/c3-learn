---
title: "Error Handling 2"
slug: "error handling 2"
aliases:
 - "/More/22"
weight: 9
---
{{<start>}}
- You will want to define your own faults (optional failure values) using `faultdef`.
- To return a fault, simply use return but with a `?` suffix.
- Fault values follow the same naming standard as global constants.
{{<end>}}

{{<defcod>}}
faultdef SOMETHING_MISSING, GENERAL_ERROR_WAS_HERE;

fn void? x(int i)
{
	if (i < 0) return SOMETHING_MISSING?;
}

fn void main()
{
}
{{</defcod>}}

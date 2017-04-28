PHP VDF Parser
---
---
Also knowns as Valve Data Format, Valve Key Values
Read at official wiki: https://developer.valvesoftware.com/wiki/KeyValues
---
**Usage example:**
Let's parse this VDF
```
#base "base1.vdf"
#base "base2.vdf"
#include "include1.vdf"
#include "include2.vdf"

"Block1" 
{
	"Key1"	"Value1"
	Key2	Value2
	Key3	"V a l u e 3"
	"K e y 4" VALUE4
	
	Block2 
	{
		"Key"	"Value"  //comment
	}
}
```
Use this code in your PHP file:
```
<?php require('vdf.php');
print_r(parse(file_get_contents('test.vdf')));
```
It will output an array
```
Array ( 
	[base] => Array ( 
		[0] => base1.vdf 
		[1] => base2.vdf 
	) 
	[include] => Array ( 
		[0] => include1.vdf 
		[1] => include2.vdf 
	) 
	[Block1] => Array (
		[Key1] => Value1 
		[Key2] => Value2 
		[Key3] => V a l u e 3 
		[K e y 4] => VALUE4 
		[Block2] => Array ( 
			[Key] => Value 
		) 
	) 
)
```
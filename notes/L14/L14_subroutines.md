# Subroutines
**Name:**
<br>
<br>
**Section:**
<br>
<br>
**Documentation:**
<br>
<br>

This is actual code produced by a C compiler and recovered by a disassembler. What does it do?  It's ok to start by analyzing each assembly instruction, but you should arrive at a simple, one-sentence purpose.

Takes in inputs from r14 and r15.
Returns output in r15.

```
0000c0a2 <mystery_routine>:
    c0a2:	0d 4f       	mov	r15,	r13	
    c0a4:	0f 43       	clr	r15		
    c0a6:	0e 93       	tst	r14		
    c0a8:	07 24       	jz	$+16     	;abs 0xc0b8
    c0aa:	12 c3       	clrc			
    c0ac:	0d 10       	rrc	r13		
    c0ae:	01 28       	jnc	$+4      	;abs 0xc0b2
    c0b0:	0f 5e       	add	r14,	r15	
    c0b2:	0e 5e       	rla	r14		
    c0b4:	0d 93       	tst	r13		
    c0b6:	f7 23       	jnz	$-16     	;abs 0xc0a6
    c0b8:	30 41       	ret			
```

What does this subroutine do?


<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>	


In the MSP430G2553 detailed Tech Doc (75 pages):<br>

Look at the top of your MSP430 chip and write down all the numbers you can read.� Consult the Package Option Addendum section of the Tech Doc and determine the following information for your chip.<br>
<br>
-	Orderable Device &#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f; 
<br>
<br>
-	Status &#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f; 
<br>
<br>
-	Package Type &#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f; 
<br>
<br>
-	Package Drawing &#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f; 
<br>
<br>
-	Pins &#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f; 
<br>
<br>
-	Package Qty &#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f; 
<br>
<br>
-	Eco Plan &#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f; 
<br>
<br>
-	Lead/Ball Finish &#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f; 
<br>
<br>
-	MSL Peak Temp &#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f; 
<br>
<br>
-	Op Temp  &#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f; 
<br>
<br>
-	Device Marking &#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f;&#x5f; 
<br>
<br>


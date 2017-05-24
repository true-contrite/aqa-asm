---
layout: post
title: How to add two integers together
---
With the limited amount of commands that the AQA assembler has, it is currently impossible to add two variables together. You can however use the ADDW command to simply add a specific value to W, however, if you have a two changing variables, you are unable to add these two values together.

The following program allows you to add two values together.

~~~asm
;0XB0  Register containing the result of addition
;0XB1  Register containing the value to be added to the other

MAIN:
 MOVW 0X20    ; your desired value to be added
 MOVWR 0XB1   ; move it into the dedicated register
 CALL ADD     ; call the addition subroutine to add these two numbers together
 JMP MAIN     ; repeat this process

ADD:          ; the NOP allows the subroutine to be called
 NOP
 LOOP:        ; adding loop subroutine
  INC 0XB0    ; increment the register
  DEC 0XB1    ; decrement the register
              ; this has the effect of repeated addition, i.e.
              ; VAR + 1 + 1 + 1 + 1 + 1 in the adding register
              ; and then VAR - 1 - 1 - 1
  MOVRW 0XB1  ; we check the value of the variable thats being added
  JPZ FIN     ; if this value has been decremented to 0, the repeat addition is complete
  JMP LOOP    ; if not, then continue to increment/decrement the registers
 FIN:        
  RET         ; return back to main program, subroutine finished, values added.
 ~~~

With this subroutine you can add the value in one register to the value of another, the function of this subroutine may be easier to understand in pseudo-code, for example.

~~~
b0 = 0 -- Product
b1 = 0 -- Variable containg addition value

function add(v)
  b1 = v -- Set register b0 equal to value you want to add
  while b1 > 0 do -- Repeat until value of b0 > 0 
   b1 = b1 - 1 -- Decrement value being added
   b0 = b0 + 1 -- Increment value you want adding
  end
  return b0 -- Return product
end

print(add(20))
print(add(48))
~~~

This program is shown [here](https://repl.it/IOtV).

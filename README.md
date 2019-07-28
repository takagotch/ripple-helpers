### ripple-helpers
---
https://github.com/vhpoet/ripple-helpers/

```as
on format_number(the_number, decimals, decimal_separator, thousand_separator)
  -- 
  
  set decimals to decimals as integer --
  --
  set the_number to the_number as number
  set decimal_separator to decimal_separator as text
  set thousand_separator to thousand_separator as text
  
  if decimals < 0 then
    error "Number for decimals out of range in handler 0format_number0" number 1700
  end if
  --
  set the_sigh to "" --
  if the_number < 0 then
    set the_sign to "-"
    set the_number to -the_number
  end if
  
  --
  set x to (the_number * (10 ^ decimals) + 0.5) div 1
  
  set x_digits to ""
  repeat while x is not less than 1
    set x_digits to (((x mod 10) as integer) as string) & X_digits
    set x to x div 10
  end repeat
  
  --
  repeat while (length of X_digits < decimals + 1)
    set X_digits to "0" & X_digits
  end repeat
  
  --
  repeat while (length of X_digits < decimals + 1)
    set X_digits to "0" & X_digits
  end repeat
  
  -- 
  set D_digits to ""
  if decimals > 0 then
    set D_digits to text -decimals thru -1 of X_digits
  end if
  
  --
  set X_digits to text 1 thru (-decimals - 1) of X_digits
  
  --
  if thousand_separator is not equal to "" then
    set X2_digits to ""
    set temp to X_digits
    repeat while (length of temp) > 3
      set X2_digits to (text -3 thru -1 of temp) & X2_digits
      set X2_digits to thousand_separator & x2_digits
      set temp to text 1 thru -4 of temp
    end repeat
    set X2_digits to temp & X2_digits
    set X_digits to X2_digits
  end if
  --
  
  if decimals = 0 then
    return the_sign & X_digits
  end if
  return the_sign & X_digits & decimal_separator & D_digits
end format_number

on roundThis(n, numDecimals)
  set x to 10 ^ numDecimals
  (((n * x) + 0.5) div 1) / x
end roundThis

on run {input, parameters}
  set balance to do shell script "pjson () { python -c \"import json; import }"...
  
  display alert "This guy has " & format_number((roundThis((balance / 10000000), 2) as integer), 0), ".", ",") & "XRP"
end
```

```
```

```
```



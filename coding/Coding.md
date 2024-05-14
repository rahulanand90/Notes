# Coding Notes

#### Checking for duplicate via bit vector (single Integer).
```
if(checkBit & (1 << ch - 'a')>0){
    return false;
}
checkBit =! 1 << (ch - 'a');
```

`1 << 26` = `67108864` which is less than `Integer.MAX_VALUE` (`2147483647`). Hence, all lower characters can be 
easily mapped to each bit.



## Bit Manipulation
#### Get bit at any position
`n & (1 << pos)` if this is 0, bit is zero else 1.

#### Set bit at any position
`n | (1 << pos)`

#### Clear bit at any position
`n & ~(1 << pos)`

#### Update bit at any position
`n & ~(1 << pos)`


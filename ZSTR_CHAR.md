# ZSTR_CHAR

## Type
macro

## Name
ZSTR_CHAR


## Declartion
```
#define ZSTR_CHAR(c) zend_one_char_string[c]
```

### Source Location
https://github.com/php/php-src/blob/49a4e695845bf55e059e7f88e54b1111fe284223/Zend/zend_string.h#L72


### Parameters
- c
get a character(one character zend string) by its corresponding ASCII code 'c', between 0 and 255, from the pre-defined variable `zend_one_char_string`. 

## Description
`zend_one_char_string` stores each ASCII character as a interned zend string, as zend_one_char_string[i] is a one character zend string corresponding the i-th ASCII character.

## Definition

## Additional Information

The `zend_one_char_string` is defined as follow

```
// https://github.com/php/php-src/blob/49a4e695845bf55e059e7f88e54b1111fe284223/Zend/zend_string.c#L46
ZEND_API extern zend_string  *zend_one_char_string[256];

// https://github.com/php/php-src/blob/49a4e695845bf55e059e7f88e54b1111fe284223/Zend/zend_string.c#L78
ZEND_API void zend_interned_strings_init(void)
{
    char s[2];
    ...
    s[1] = 0;
    for (i = 0; i < 256; i++) {
	    s[0] = i;
	    zend_one_char_string[i] = zend_new_interned_string_permanent(zend_string_init(s, 1, 1));
    }
    ...
}
```

## Categories
Zend String



---
layout: post
title: 'Easy form validation with php filter_var'

---



No need to write your own regular expression.  php has got your back.

Check here for more.  I have created a list of parameters that I can easily reference.  

http://php.net/manual/en/function.filter-var.php


<pre>
1. Validation 

FILTER_VALIDATE_BOOLEAN
FILTER_NULL_ON_FAILURE
  Returns TRUE for .
  Returns FALSE otherwise.
  If FILTER_NULL_ON_FAILURE is set, FALSE is
  returned only for , and
  NULL is returned for all non-boolean values.


FILTER_VALIDATE_EMAIL
  Validates value as e-mail.


FILTER_VALIDATE_FLOAT
  decimal

FILTER_FLAG_ALLOW_THOUSAND
  Validates value as float.


FILTER_VALIDATE_INT
  min_range,
  max_range

FILTER_FLAG_ALLOW_OCTAL,
  FILTER_FLAG_ALLOW_HEX
  Validates value as integer, optionally from the specified range.


FILTER_VALIDATE_IP
FILTER_FLAG_IPV4,
  FILTER_FLAG_IPV6,
  FILTER_FLAG_NO_PRIV_RANGE,

FILTER_FLAG_NO_RES_RANGE
  Validates value as IP address, optionally only IPv4 or IPv6 or not from private or reserved ranges.


FILTER_VALIDATE_REGEXP
  regexp Validates value against regexp, a Perl-compatible regular expression.

FILTER_VALIDATE_URL
FILTER_FLAG_PATH_REQUIRED,
FILTER_FLAG_QUERY_REQUIRED


2. Sanitation

FILTER_SANITIZE_EMAIL
  Remove all characters except letters, digits and !#$%*+-/=?^_`{|}~@.[].

FILTER_SANITIZE_ENCODED
FILTER_FLAG_STRIP_LOW,
FILTER_FLAG_STRIP_HIGH,
FILTER_FLAG_ENCODE_LOW,
FILTER_FLAG_ENCODE_HIGH
  URL-encode string, optionally strip or encode special characters.

       
FILTER_SANITIZE_MAGIC_QUOTES
  Apply addslashes().

       
FILTER_SANITIZE_NUMBER_FLOAT
FILTER_FLAG_ALLOW_FRACTION,
FILTER_FLAG_ALLOW_THOUSAND,
FILTER_FLAG_ALLOW_SCIENTIFIC
  Remove all characters except digits, +- and
  optionally .,eE.
       

FILTER_SANITIZE_NUMBER_INT
  Remove all characters except digits, plus and minus sign.

       
FILTER_SANITIZE_SPECIAL_CHARS
        
FILTER_FLAG_STRIP_LOW,
FILTER_FLAG_STRIP_HIGH,
FILTER_FLAG_ENCODE_HIGH
  HTML-escape  and characters with
  ASCII value less than 32, optionally strip or encode other special characters.

FILTER_SANITIZE_STRING 
FILTER_FLAG_NO_ENCODE_QUOTES, 
FILTER_FLAG_STRIP_LOW,
FILTER_FLAG_STRIP_HIGH,
FILTER_FLAG_ENCODE_LOW,
FILTER_FLAG_ENCODE_HIGH,
FILTER_FLAG_ENCODE_AMP
  Strip tags, optionally strip or encode special characters.
       
FILTER_SANITIZE_STRIPPED
  Alias of  filter.
       
FILTER_SANITIZE_URL
  Remove all characters except letters, digits and $-_.+!*=.
        
       
FILTER_UNSAFE_RAW
FILTER_FLAG_STRIP_LOW,
FILTER_FLAG_STRIP_HIGH,
FILTER_FLAG_ENCODE_LOW,
FILTER_FLAG_ENCODE_HIGH,
FILTER_FLAG_ENCODE_AMP
  Do nothing, optionally strip or encode special characters.
			 </pre>

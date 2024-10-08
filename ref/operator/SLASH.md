## / operator

**Format:**
+   A / B

**Returns:**
+   A divided by B.


Divides A and B. The result of the operation depends on the
types of values being multiplied, mostly on A.
  A type            B type                                                    Result
  ----------------- --------------------------------------------------------- ----------------------------------------------------------------------------
  num or null (0)   num or null (0)                                           Numeric division; crashes if B is equivalent to 0
  icon or /icon     num or color                                              New icon dividing RGB components by color
  matrix            matrix                                                    New matrix, product of A and the inverse of B
                    num                                                       New matrix scaling A by 1/B
                    vector                                                    New matrix scaling A by 1/B.x and 1/B.y
  pixloc            num or vector                                             Creates a 2D vector from pixloc\'s x,y and divides that by the rules below
  vector            2D vector dividing x,y components by the divisor\'s x,y   
  vector            vector                                                    New vector with components divided
                    matrix                                                    New vector with 2D transformation applied in reverse
                    num                                                       New vector scaling A by 1/B

> [!TIP] 
> **See also:**
> +   [* operator](/ref/operator/*.md) 
> +   [+ operator](/ref/operator/+.md) 
> +   [- operator](/ref/operator/-.md) 
> +   [/ path operator](/ref/operator/path//.md) 
> +   [/= operator](/ref/operator//=.md) 
> +   [operators](/ref/operator.md) 
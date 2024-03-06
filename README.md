[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/OlW38W4k)
# Recurrence Analysis -- Mystery Function

Analyze the running time of the following recursive procedure as a function of
$n$ and find a tight big $O$ bound on the runtime for the function. You may
assume that each operation takes unit time. You do not need to provide a formal
proof, but you should show your work: at a minimum, show the recurrence relation
you derive for the runtime of the code, and then how you solved the recurrence
relation.

```javascript
function mystery(n) {
    if(n <= 1)
        return;
    else {
        mystery(n / 3);
        var count = 0;
        mystery(n / 3);
        for(var i = 0; i < n*n; i++) {
            for(var j = 0; j < n; j++) {
                for(var k = 0; k < n*n; k++) {
                    count = count + 1;
                }
            }
        }
        mystery(n / 3);
    }
}
```

### My Recurrence Relation:

$f(n) = { <br/>
1              if n <= 1 <br/>
3f(n/3) + n^5    else <br/>

<br/>

$3f(n/3) + n^5$ <br/>
$9(f(n) + 4n^5$ <br/>
$27f(n) + 13n^5$ <br/>
$3^i * f(n/3^i) +(($ $\sum_{j=0}^{i-1} 3^j) * n^5)$ <br/>
To get into our base case we will set $3^i = n$ <br/>
$i = log_3(n) <br/>
Plugging $i$ back in we get: <br/>
$n * 1 + ((n - 1)/2) * n^5$ <br/>
The sum evaluates to be less than linear, so: <br/>
$n + n^5$ <br/>
$f(n) \in O(n^5)$

<br/>
<br/>
Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

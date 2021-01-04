## Mr.Indescribable's Fork of Tabular

Tabular offers a conveniet way to format code, it does well in formatting whole lines of code.

**BUT**, what was not very conveniet is the way it implements the limited splitting, [which](https://github.com/godlygeek/tabular/blob/master/doc/Tabular.txt#L133) is painful to use:

```
But, what if you only wanted to act on the first comma on the line, rather than
all of the commas on the line?  Let's say we want everything before the first
comma right aligned, then the comma, then everything after the comma left
aligned:
>
    abc,def,ghi
    a,b
    a,b,c
  :Tabularize /^[^,]*\zs,/r0c0l0
    abc,def,ghi
      a,b
      a,b,c
<
```

So, here comes the question: **what if you only wanted to act on the first 1000 commas on the line?**

And here is the sulotion:

```
:Tabularize /,/b1000
:Tabularize /,/b1000l1r1c1
```

I implemented a new grammar for the format string, with an **optional** `b` bit placed at the **START** of the format string, you can specify any times of split you want instead of using that obscure regex grammar.


----------

See also: [The original README.md](ORIGINAL-README.md)

### Pattern Matching

```
= # is a match operator
^ # is a pin operator for accessing previously bound values
```

```
x = 1 # assignment (only on the left side of the =)
1 = x # matching
2 = x # will raise MatchError
```

### Matching

```
{a, b, c} = {:hello, "world", 42} # assignment
a                                 # :hello
b                                 # "world"


{a, b, c} = {:hello, "world"}       # MatchError, tuples must have same size
{a, b, c} = [:stuff, "things", "!"] # Match error, different types, i.e. tuple matching list

{:ok, result} = {:ok, 13}           # matches when the right side is a tuple that starts with :ok
{:ok, result} = {:anything, :else}  # MatchError, does not start with :ok
```


```
[head | tail] = [1, 2, 3] # head/tail matching
head                      # 1
tail                      # [2, 3]
```

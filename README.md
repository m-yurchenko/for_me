# for_me
```
import pandas as pd
from itertools import product


def truth_table(f):
    values = [list(x) + [f(*x)] for x in product([False, True], repeat=f.__code__.co_argcount)]
    return pd.DataFrame(values, columns=(list(f.__code__.co_varnames) + [f.__name__]))


def f1(a, b):
    return a == b if a is not None else True


def f2(a, b):
    return a is None or a == b


if __name__ == "__main__":
    print(truth_table(f1))
    print(truth_table(f2))
```

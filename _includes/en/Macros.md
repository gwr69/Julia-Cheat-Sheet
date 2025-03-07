Macros allow generated code (i.e. expressions) to be included in a
program.

|                 |                                                            |
| --------------- | ---------------------------------------------------------- |
| Definition      | `macro macroname(expr)`<br>`    # do stuff`<br>`end`       |
| Usage           | `@macroname(ex1, ex2, ...)` or `@macroname ex1 ex2 ...`   |
| Built-in macros | `@test           # equal (exact)`<br>`@test x ≈ y    # isapprox(x, y)`<br>`@assert         # assert (unit test)`<br>`@which          # find definition`<br>`@time           # time and memory statistics`<br>`@elapsed        # time elapsed`<br>`@allocated      # memory allocated`<br>`@profile        # profile`<br>`@spawn          # run at some worker`<br>`@spawnat        # run at specified worker`<br>`@async          # asynchronous task`<br>`@distributed    # parallel for loop`<br>`@everywhere     # make available to workers` |


Rules for creating *hygienic* macros:

- Declare variables inside macro with `local` .
- Do not call `eval` inside macro.
- Escape interpolated expressions to avoid expansion: `$(esc(expr))`

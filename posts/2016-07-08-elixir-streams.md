Elixir [streams](http://elixir-lang.org/docs/stable/elixir/Stream.html) are essentially lazy-loaded [Enums](http://elixir-lang.org/docs/stable/elixir/Enum.html). You can do a lot of neat things with them.

Calling `map` an an `Enum` will execute that call in place, whereas a stream is composable. For example, you can chain a couple of maps, and selects together without actually executing anything until you want to. Here's an example:

```elixir
a = 1..5

IO.puts "Eager enumeration:"

a
|> Enum.map(fn x -> IO.puts("x") end)
|> Enum.map(fn x -> IO.puts("o") end)

IO.puts ""
IO.puts "Now lazy enumeration:"

a
|> Stream.map(fn x -> IO.puts("x") end)
|> Stream.map(fn x -> IO.puts("o") end)
|> Enum.to_list
```

Running this in `iex` will produce:

```
Eager enumeration:
x
x
x
o
o
o

Now lazy enumeration:
x
o
x
o
x
o
```

`Enum` prints all the `x`'s first and then the `o`'s, whereas the `Stream` will print `x` and then `o` for every iteration

You can also do neat things with [`Stream.unfold/2`](http://elixir-lang.org/docs/stable/elixir/Stream.html#unfold/2) like wrap generating random numbers with an enumerable interface:

```elixir
random = Stream.unfold(nil, fn _ -> {:random.uniform(100), nil} end)

# Get 10 random numbers
values = Enum.take(random, 10)

# Get only even numbers
even_random = 
  Stream.filter(random, fn e -> rem(e, 2) == 0 end)
  |> Enum.take(10)

# Make a long random number
long_random = Enum.take(random, 10) |> Enum.join

```

We use `Enum` with a stream as an argument for when we actually want to return the values, and `Stream` when we want to keep composing the stream. Be careful not to call `Enum.to_list/0` on this random stream as it will probably crash and never return. 
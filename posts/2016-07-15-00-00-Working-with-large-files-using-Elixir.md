Here's an example of how you can use streams to read and manipulate very large files without busting your memory:

```elixir
[input_file, output_file] = System.argv

File.stream!(input_file)
|> Stream.reject(fn line ->
  case line do
    "INSERT INTO `logs`" <> _ -> true
    "INSERT INTO `states_changes`" <> _ -> true
    _anything -> false
  end
end)
|> Stream.map( fn line ->
  String.trim(line) <> "\n"
end)
|> Stream.into( File.stream!(output_file) )
|> Stream.run
```

Let's break this down. On line 1 we pattern match on `System.argv` which returns a list of arguments that were passed in. We could use elixir's built in [OptionParser](http://elixir-lang.org/docs/stable/elixir/OptionParser.html) but we don't need it for our purposes. It's usage will look like:

```bash
elixir trim_large.exs input_file.sql output_file.sql
```

Next we grab a stream from a file using `File.stream!/3` and we use `Stream.reject/2` to remove entire lines that we don't want. We then remove any leading or trailing whitespace with `Stream.map/2` and `String.trim/2`.

We use `Stream.into/2` to convert our working stream into an output file. And finally we use `Stream.run` to "execute" the stream. This is similar to calling `Enum.to_list` to return the enum but since it's a file we use a slightly different mechanism.

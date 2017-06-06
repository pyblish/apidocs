# Command-line interface

The Pyblish command-line interface can be accessed via `python -m pyblish`, or directly via `pyblish` when installed via `pip`.

You can use this interface to trigger publishes via the command-line.

```bash
$ pip install pyblish
$ pyblish --help
Usage: pyblish [OPTIONS] COMMAND [ARGS]...

  Pyblish command-line interface

  Use the appropriate sub-command to initiate a publish.

  Use the --help flag of each subcommand to learn more about what it can do.

  Usage:
      $ pyblish publish --help
      $ pyblish test --help

Options:
  --verbose                       Display detailed information. Useful for
                                  debugging purposes.
  --version                       Print the current version of Pyblish
  --paths                         List all available paths
  --plugins                       List all available plugins
  --registered-paths              Print only registered-paths
  --environment-paths             Print only paths added via environment
  -pp, --plugin-path TEXT         Replace all normally discovered paths with
                                  this This may be called multiple times.
  -ap, --add-plugin-path TEXT     Append to normally discovered paths.
  -d, --data TEXT...              Initialise context with data. This takes two
                                  arguments, key and value.
  -ll, --logging-level [debug|info|warning|critical|error]
                                  Specify with which level to produce logging
                                  messages. A value lower than the default
                                  "warning" will produce more messages. This
                                  can be useful for debugging.
  --help                          Show this message and exit.

Commands:
  publish  Publish instances of path.
```

<div class="modified-date">{{ file.mtime }}</div>
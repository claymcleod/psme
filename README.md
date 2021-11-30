<p align="center">
  <h1 align="center">
    psme
  </h1>

  <p align="center">
    <a href="https://github.com/claymcleod/psme/actions/workflows/CI.yml" target="_blank">
      <img alt="Actions: CI Status"
          src="https://github.com/claymcleod/psme/actions/workflows/CI.yml/badge.svg" />
    </a>
    <a href="https://pypi.org/project/psme/" target="_blank">
      <img alt="PyPI"
          src="https://img.shields.io/pypi/v/psme?color=orange">
    </a>
    <a href="https://pypi.org/project/psme/" target="_blank">
      <img alt="PyPI: Downloads"
          src="https://img.shields.io/pypi/dm/psme?color=orange">
    </a>
    <a href="https://codecov.io/gh/claymcleod/psme" target="_blank">
      <img alt="Code Coverage"
          src="https://codecov.io/gh/claymcleod/psme/branch/main/graph/badge.svg" />
    </a>
    <a href="https://github.com/claymcleod/psme/blob/main/LICENSE.md" target="_blank">
    <img alt="License: MIT"
          src="https://img.shields.io/badge/License-MIT-blue.svg" />
    </a>
  </p>


  <p align="center">
    Python subcommands made easy.
    <br />
    <!-- <a href="https://claymcleod.github.io/psme/"><strong>Explore the docs »</strong></a> -->
    <a href="https://github.com/claymcleod/psme-example"><strong>See the example »</strong></a>
    <br />
    <br />
    <a href="https://github.com/claymcleod/psme/issues/new?assignees=&labels=&template=feature_request.md&title=Descriptive%20Title&labels=enhancement">Request Feature</a>
    ·
    <a href="https://github.com/claymcleod/psme/issues/new?assignees=&labels=&template=bug_report.md&title=Descriptive%20Title&labels=bug">Report Bug</a>
    ·
    ⭐ Consider starring the repo! ⭐
    <br />
  </p>
</p>

## 🎨 Features


* <b>Project Structure.</b> Salient project structure to build small to large command line applications with many subcommands.
* <b>Easy to understand and implement.</b> Best practices for implementing subcommands for free (almost!). 

## 📚 Getting Started

### Installation

#### Python Package Index

If you're using [poetry] (recommended), you can easily add `psme` as a dependency to your command line application.

```bash
poetry add psme
```

You can also install `psme` using the Python Package Index ([PyPI](https://pypi.org/)).

```bash
pip install psme
```

## 🚌 A Quick Tour

At its foundation, `psme` is meant to make it easy to design and implement command line tools with multiple subcommands. Commonly, you will want to use it to create multiple subcommands and run the command line engine to distinguish between them and run the correct one.

<!-- If you're interested in a complete overview of psme's capabilities, please see [**the documentation pages**](https://claymcleod.github.io/psme/)</a>. -->

In your main package, you can do something like the following:

```python
from psme.engine import Engine
from .subcommands.add import Add

e = Engine('psme-example', [Add()],
		description="Python subcommands made easy tutorial.")
e.run()
```

Assuming you have a directory in your Python package for subcommands, and `Add` subcommand may look like this:

```python
from psme.subcommand import BaseSubcommand

class Add(BaseSubcommand):
	def name(self):
		return "add"

	def register_args(self, subparser):
		subparser.add_argument("operand_one", type=int, help="First operand to add together.")
		subparser.add_argument("operand_two", type=int, help="Second operand to add together.")

	def run(self, args):
		print(f"{args.get('operand_one')} + {args.get('operand_two')} = {args.get('operand_one') + args.get('operand_two')}")
```

For more information, please see [the example application](https://github.com/claymcleod/psme-example).

## 🤝 Contributing

Contributions, issues and feature requests are welcome!<br />Feel free to check [issues page](https://github.com/claymcleod/psme/issues). Please ensure you fill out the entire template for each of these. You can also take a look at the [contributing guide][contributing-md].

## 📝 License

Copyright © 2021 Clay McLeod. This project is [MIT][license-md] licensed.

[poetry]: https://python-poetry.org/
[contributing-md]: https://github.com/claymcleod/psme/blob/main/CONTRIBUTING.md
[license-md]: https://github.com/claymcleod/psme/blob/main/LICENSE.md
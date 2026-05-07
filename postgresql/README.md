# PostgreSQL

## Setup with podman/docker compose

* replcae podman with docker if your're running with docker related tools

```shell
podman compose up -d
```

## Test connect with DBeaver or CLI tools on macOS

* CLI tools
    * [pgcli](https://www.pgcli.com/)

```shell
$ brew install pgcli
```

```shell
$ pgcli --help        
Traceback (most recent call last):
  File "/opt/homebrew/bin/pgcli", line 3, in <module>
    from pgcli.main import cli
  File "/opt/homebrew/Cellar/pgcli/4.4.0_1/libexec/lib/python3.14/site-packages/pgcli/main.py", line 37, in <module>
    from prompt_toolkit.completion import DynamicCompleter, ThreadedCompleter
  File "/opt/homebrew/Cellar/pgcli/4.4.0_1/libexec/lib/python3.14/site-packages/prompt_toolkit/__init__.py", line 29, in <module>
    from .shortcuts import PromptSession, choice, print_formatted_text, prompt
  File "/opt/homebrew/Cellar/pgcli/4.4.0_1/libexec/lib/python3.14/site-packages/prompt_toolkit/shortcuts/__init__.py", line 13, in <module>
    from .progress_bar import ProgressBar, ProgressBarCounter
  File "/opt/homebrew/Cellar/pgcli/4.4.0_1/libexec/lib/python3.14/site-packages/prompt_toolkit/shortcuts/progress_bar/__init__.py", line 3, in <module>
    from .base import ProgressBar, ProgressBarCounter
  File "/opt/homebrew/Cellar/pgcli/4.4.0_1/libexec/lib/python3.14/site-packages/prompt_toolkit/shortcuts/progress_bar/base.py", line 57, in <module>
    from .formatters import Formatter, create_default_formatters
  File "/opt/homebrew/Cellar/pgcli/4.4.0_1/libexec/lib/python3.14/site-packages/prompt_toolkit/shortcuts/progress_bar/formatters.py", line 129, in <module>
    class Percentage(Formatter):
    ...<15 lines>...
            return D.exact(6)
  File "/opt/homebrew/Cellar/pgcli/4.4.0_1/libexec/lib/python3.14/site-packages/prompt_toolkit/shortcuts/progress_bar/formatters.py", line 134, in Percentage
    template = HTML("<percentage>{percentage:>5}%</percentage>")
  File "/opt/homebrew/Cellar/pgcli/4.4.0_1/libexec/lib/python3.14/site-packages/prompt_toolkit/formatted_text/html.py", line 35, in __init__
    document = minidom.parseString(f"<html-root>{value}</html-root>")
  File "/opt/homebrew/Cellar/python@3.14/3.14.4_1/Frameworks/Python.framework/Versions/3.14/lib/python3.14/xml/dom/minidom.py", line 2010, in parseString
    from xml.dom import expatbuilder
  File "/opt/homebrew/Cellar/python@3.14/3.14.4_1/Frameworks/Python.framework/Versions/3.14/lib/python3.14/xml/dom/expatbuilder.py", line 32, in <module>
    from xml.parsers import expat
  File "/opt/homebrew/Cellar/python@3.14/3.14.4_1/Frameworks/Python.framework/Versions/3.14/lib/python3.14/xml/parsers/expat.py", line 4, in <module>
    from pyexpat import *
ImportError: dlopen(/opt/homebrew/Cellar/python@3.14/3.14.4_1/Frameworks/Python.framework/Versions/3.14/lib/python3.14/lib-dynload/pyexpat.cpython-314-darwin.so, 0x0002): Symbol not found: _XML_SetAllocTrackerActivationThreshold
  Referenced from: <44AFDBDF-C9C3-35EF-A723-C0C54E2C9C3F> /opt/homebrew/Cellar/python@3.14/3.14.4_1/Frameworks/Python.framework/Versions/3.14/lib/python3.14/lib-dynload/pyexpat.cpython-314-darwin.so
  Expected in:     <4D62FA9D-D86A-3DD0-98F2-C6D0718849E8> /usr/lib/libexpat.1.dylib
```

* [Solution](https://github.com/dbcli/pgcli/issues/1589)

* DBeaver

## Tips/Docs/MISC...etc

* [github.com/blackdesert575/postgresql-101](https://github.com/blackdesert575/postgresql-101)
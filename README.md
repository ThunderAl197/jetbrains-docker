# [JetBrains](https://www.jetbrains.com/) IDE containers

Here you can find containerized versions of [JetBrains](https://www.jetbrains.com/) IDE.  
It can be helpful in your ci for inspecting and formatting code or remote ide setup.  
All containers based on ubi8-minimal, if you want to install additional things use `microdnf install -y some-package`.

Note: You **MUST** have JetBrains licence to run these containers.

## Available IDEs versions and tags

| Ide      | Version  | Container                               |
|----------|----------|-----------------------------------------|
| PhpStorm | 2022.3.3 | `thunderal/jetbrains:phpstorm-2022.3.3` |

## Usage

### Related commands

| Command                     | Description             |
|-----------------------------|-------------------------|
| `idename`                   | Start ide               |
| `idename-remote-dev-server` | Start remote dev server |
| `idename-inspect`           | Run code inspections    |
| `idename-format`            | Run code formatter      |

Note: Replace `idename` with your ide name, ex: `phpstorm`, `phpstorm-inspect`, `phpstorm-format`

# [JetBrains](https://www.jetbrains.com/) IDE containers

Here you can find containerized versions of [JetBrains](https://www.jetbrains.com/) IDE.  
It can be helpful in your ci for inspecting and formatting code or remote ide setup.  
All containers based on ubi8-minimal, if you want to install additional things use `microdnf install -y some-package`.

Note: You **MUST** have JetBrains licence to run these containers.

## Available IDEs versions and tags

| Ide      | Version  | Container                               |
|----------|----------|-----------------------------------------|
| PhpStorm | 2022.3.3 | `thunderal/jetbrains:phpstorm-2022.3.3` |

### Pre-installed plugins

PhpStorm 2022.3.3:

* Vue *org.jetbrains.plugins.vue*
* Graphql *com.intellij.lang.jsgraphql*

## Usage

### Licence

To pass a licence key to container mount `*.key` (not activation code) to
`/root/.config/JetBrains/<ide><version>/<ide>.key`
(For phpstorm2022.3.3 it will be `/root/.config/JetBrains/PhpStorm2022.3/phpstorm.key`).

If you are using licence server, you can pass licence server url via `JETBRAINS_LICENSE_SERVER` environment variable.

### Related commands

| Command                     | Description             |
|-----------------------------|-------------------------|
| `idename`                   | Start ide               |
| `idename-remote-dev-server` | Start remote dev server |
| `idename-inspect`           | Run code inspections    |
| `idename-format`            | Run code formatter      |

Note: Replace `idename` with your ide name, ex: `phpstorm`, `phpstorm-inspect`, `phpstorm-format`

### Check code formatting

It will exit with non-zero exit code if at least one file is not formatted properly.
([see doc](https://www.jetbrains.com/help/idea/command-line-formatter.html))

```bash
docker run --rm -it \
  -v "phpstorm.key:/root/.config/JetBrains/PhpStorm2022.3/phpstorm.key" \
  -v "/my-project-path:/code" \
  thunderal/jetbrains:phpstorm-2022.3.3 \
  phpstorm-format -settings /code/code-style-profile.xml -dry -r /code
```

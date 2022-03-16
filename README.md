# breakbot-forker
A simple script that forks a GitHub repository and its pull requests to test BreakBot.

## Dependencies
  - Git
  - [GitHub CLI](https://cli.github.com/)

The script requires that GitHub CLI has write access to the organization the fork should be pushed to. See [gh auth login](https://cli.github.com/manual/gh_auth_login).

## Example
To fork [google/guava](https://github.com/google/guava) and its ten most recent pull requests on the GitHub organization `breakbot-test`:

```
breakbot-forker -o google -r guava -t breakbot-test -b guava.yml -l 10
```

The `guava.yml` file gives a basic configuration for building the library and testing a handful of clients:

```
build:
  pom: guava/pom.xml
  jar: guava/target/guava-HEAD-jre-SNAPSHOT.jar
clients:
  - repository: sofastack/sofa-boot
  - repository: salesforce/zsync4j
  - repository: mspnp/ha-nva
  - repository: wujun728/jun_java_plugin
  - repository: data-integrations/salesforce
  - repository: leonchen83/redis-rdb-cli
  - repository: xaecbd/KCenter
```

## Usage
```
Forks a repository, commits a BreakBot configuration file, and copies its pull requests.

Syntax: breakbot-forker -o source-organization -r repository -t dest-organization [-b file.yml] [-l limit] [-h]
options:
o     The organization to fork from.
r     The name of the repository.
t     The organization to fork to.
b     The .github/breakbot.yml file to commit.
l     Limit the number of PRs to copy.
h     Print this help.
```

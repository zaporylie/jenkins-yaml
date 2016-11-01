# jenkins-yaml
.jenkins.yml script runner

## How to:
- Add .jenkins.yml to your repo
- Run `jenkins-yaml.runner` in your jenkins build

## .jenkins.yml

Syntax for .jenkins.yml is similar to .travis.yml, just simplified.

```yaml
job1:
  - ls -la
  - touch test
  - chmod +x test
  - ./test
  
job2:
  - rm *
  
job3:
  - curl -I http://www.google.com
```

## How to add it to Jenkins?

- Create freestyle Jenkins Job
- Add "Execute shell" in "Build" section
- Add single command - `jenkins-yaml.runner <section>` - where <section> is has to match one of the parent keys in .jenkins.yml (i.e. `job2` from example above)

## Parameters

`jenkins-yaml.runner [--errors] [--missing-section] [--missing-file] <section>`

- Use `--errors` if you don't want to break excution on first error
- Use `--missing-section` if script should return exit code > 0 for missing section in .jenkins.yml file
- Use `--missing-file` if script should return exit code > 0 for missing .jenkins.yml file

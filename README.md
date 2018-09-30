# matsui

Executes playbooks. Named after the Japanese playwright, critic, and director Matsui Shoo.

## About

Matsui is meant to be containerized replacement for ansible bins to ensure consistency across environments. If you notice there's a missing dependency required for a core ansible module, please raise an issue or make a pull request.

## Using Matsui

To use matsui to run a playbook:

```bash
$ docker run --rm -it -v $(pwd):/ansible/playbooks stageright/matsui site.yml
```

You may want to mount volumes to capture artifacts like ssh keys:

```bash
$ docker run --rm -it -v $(pwd):/ansible/playbooks -v ~/.ssh:/root/.ssh stageright/matsui setup.yml
```

## Extending Matsui

Matsui does not have libraries to interact with third party environments by default. If you need to extend matsui to work with for instance digital ocean, you need to create a new dockerfile:

```Dockerfile
FROM stageright/matsui:1.0.0

RUN pip install dopy
```

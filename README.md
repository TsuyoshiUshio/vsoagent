# vsoagent
Assorted Docker images with the new Build.vNext xplat agent baked in

Vsoagent Dockerfile for Ruby. Now on development.

# 1. Start docker-machine

Start docker host. I use docker-machine for this purpose

```
$ docker-machine start dev
```

# 2. Start VSO agent

This command should be automated.
I need move investigation.

```
$ docker run -it vsoagent-ruby bash
> node host -u USERNAME -p PASSWORD
```

# Reference

[jgarverick/vsoagent](https://github.com/jgarverick/vsoagent)

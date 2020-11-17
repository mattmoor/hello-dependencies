# hello-dependencies

This is an adaptation of the [CNCF buildpacks samples repo](https://github.com/buildpacks/samples)
to demonstrate a buildpack with dependencies.

# Build this buildpack

This buildpack can be built (from the root of the repo) with:

```shell
pack package-buildpack my-buildpack --config ./package.toml
```

# Use this buildpack

```shell
pack build blah --buildpack my-buildpack
```

# Sample output

```
===> DETECTING
hello-buildpacks 0.0.1
hello-dependent  0.0.1
===> ANALYZING
===> RESTORING
===> BUILDING
---> Buildpack Template
     platform_dir files:
       /platform:
       total 12
       drwxr-xr-x 1 root root 4096 Jan  1  1980 .
       drwxr-xr-x 1 root root 4096 Nov 17 00:19 ..
       drwxr-xr-x 1 root root 4096 Jan  1  1980 env

       /platform/env:
       total 8
       drwxr-xr-x 1 root root 4096 Jan  1  1980 .
       drwxr-xr-x 1 root root 4096 Jan  1  1980 ..
     env_dir: /platform/env
     env vars:
       declare -x CNB_BUILDPACK_DIR="/cnb/buildpacks/hello-buildpacks/0.0.1"
       declare -x CNB_STACK_ID="io.buildpacks.stacks.bionic"
       declare -x HOME="/home/cnb"
       declare -x HOSTNAME="6a299ff04561"
       declare -x OLDPWD
       declare -x PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
       declare -x PWD="/workspace"
       declare -x SHLVL="1"
     layers_dir: /layers/hello-buildpacks
     plan_path: /tmp/plan.568148337/hello-buildpacks/plan.toml
     plan contents:
       [[entries]]
         name = "some-thing"

---> Done
---> Buildpack (dependent) Template
     platform_dir files:
       /platform:
       total 12
       drwxr-xr-x 1 root root 4096 Jan  1  1980 .
       drwxr-xr-x 1 root root 4096 Nov 17 00:19 ..
       drwxr-xr-x 1 root root 4096 Jan  1  1980 env

       /platform/env:
       total 8
       drwxr-xr-x 1 root root 4096 Jan  1  1980 .
       drwxr-xr-x 1 root root 4096 Jan  1  1980 ..
     env_dir: /platform/env
     env vars:
       declare -x CNB_BUILDPACK_DIR="/cnb/buildpacks/hello-dependent/0.0.1"
       declare -x CNB_STACK_ID="io.buildpacks.stacks.bionic"
       declare -x HOME="/home/cnb"
       declare -x HOSTNAME="6a299ff04561"
       declare -x OLDPWD
       declare -x PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
       declare -x PWD="/workspace"
       declare -x SHLVL="1"
     layers_dir: /layers/hello-dependent
     plan_path: /tmp/plan.568148337/hello-dependent/plan.toml
     plan contents:
       [[entries]]
         name = "some-other-thing"

---> Done
===> EXPORTING
Reusing 1/1 app layer(s)
Reusing layer 'launcher'
Adding layer 'config'
Adding label 'io.buildpacks.lifecycle.metadata'
Adding label 'io.buildpacks.build.metadata'
Adding label 'io.buildpacks.project.metadata'
Warning: default process type 'web' not present in list []
*** Images (7f5ae43d13af):
      blah
Successfully built image blah
```

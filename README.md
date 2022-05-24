# install Flux on your workstation

```

brew install fluxctl

```

***Linux***

```
sudo snap install fluxctl --classic
```

***windows***
```
choco install fluxctl
````

### install flux 

GHUSER=thedevopsstore

fluxctl install \
--git-user=${GHUSER} \
--git-email=${GHUSER}@users.noreply.github.com \
--git-url=git@github.com:${GHUSER}/go-redis-app \
--git-path=manifests/deployment \
--git-branch=main \
--namespace=flux | kubectl apply -f -


### Set the environment variable for the fluxctl command:

```
$ export FLUX_FORWARD_NAMESPACE=flux

```

#### Grab the RSA key created by Flux:

```
$ fluxctl identity
The alternative is to not set the FLUX_FORWARD_NAMESPACE variable and instead use this command:

$ fluxctl identity --k8s-fwd-ns flux
Copy and past that RSA key into the Deploy Keys within your GitHub Repo.

```

#### Add the Deploy Key to Your Repo

Use the RSA key copied to the clipboard to add a "Deploy Key" in GitHub, or an SSH RSA Key in other Git servers, to grant read and write access to your QA Kubernetes Cluster.


#### Use the list-workloads Command To Examine The Deployed Container Images
If you have not set the FLUX_FORWARD_NAMESPACE variable, you should do so now:

```
$ export FLUX_FORWARD_NAMESPACE=flux
Use fluxctl to examine the container images deployed:

$ fluxctl list-workloads --all-namespaces

```






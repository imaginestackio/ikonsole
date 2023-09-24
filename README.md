# iKonsole
iKonsole is the web-based UI for ImagineKube clusters. 

# Imagine Konsole

iKonsole console is the web interface for [ImagineKube](https://github.com/imaginekube/imaginekube-platform).


## Getting Started

iKonsole should be always used with ImagineKube, you can either use [Kubekey](https://github.com/imaginekube/ikonsole) or [ks-installer](https://github.com/imaginekube/ikube-installer) to create a ImagineKube cluster.  
The following will show you how to build console from source code.


### Prerequisite
#### Node.js
iKonsole is written using Javascript. If you don't have a Node.js development environment, please [set it up](https://nodejs.org/en/download/). The minimum version required is 12.18.

#### Yarn
We use [Yarn](https://yarnpkg.com/) to do package management. If you don't have yarn, use the following to install:
```
npm install -g yarn@1.22.4
```
The minimum version required is 1.22.4, but you can use a newer version.

#### [Optional]Docker
This is optional. If you just want to test and build on your local environment, there is no need to install docker. Otherwise, you need to install it.
[Install on Mac](https://docs.docker.com/desktop/mac/install/)
[Install on Windows](https://docs.docker.com/desktop/windows/install/)
[Install on Ubuntu](https://docs.docker.com/engine/install/ubuntu/)

#### [Optional]Make
This is optional too, we use `make` to reduce hand work, but it's totally ok without it.

## How to build

Clone the repository, and run `yarn && yarn build`
```sh
git clone https://github.com/imaginekube/ikonsole.git
cd console/
yarn && yarn build
npm run serve
```
> If you have trouble downloading the dependencies, try the following
>
> `yarn config set registry https://registry.npmmirror.com`


After `npm run serve`, you should see the output like the following

```
> imaginekube-ikonsole@master serve
> NODE_ENV=production node server/server.js

Dashboard app running at port 8000
```
Now, console is up and running. But since there is no backed ImagineKube cluster, you shouldn't be able to login.

## How to debug
A ImagineKube cluster is required to start debugging. You can refer to [Installation](https://github.com/imaginekube/imaginekube#installation) to create a ImagineKube cluster.

Once the cluster is up, you replace the address of `ks-apiserver` in `server/config.yaml` with your real address. You can refer to [access ImagineKube apiserver](docs/access-backend.md) to expose your cluster `ik-apiserver`.
```
  # backend service gateway server
  apiServer:
    clientID: imaginekube
    clientSecret: imaginekube
    url: http://ik-apiserver
    wsUrl: ws://ik-apiserver
```

## How to build container image

Just run the following command with your real `REPO` address.
```
REPO=yourawesomerepo make container
```

## How to submit a PR

Follow [Development Workflow](/docs/development-workflow.md) to commit your codes.

## Support, Discussion, and Community

If you need any help with ImagineKube, please join us at [Slack Channel](https://join.slack.com/t/imaginekube/shared_invite/).

Please submit any ImagineKube iKonsole bugs, issues, and feature requests to [ImagineKube iKonsole GitHub Issue](https://github.com/imaginekube/ikonsole/issues).

## Contributing to the project

Welcome to contribute to ImagineKube iKonsole, see [Contributing Guide](CONTRIBUTING.md).


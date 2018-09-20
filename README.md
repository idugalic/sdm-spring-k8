# Software Delivery Machine (K8) - by Atomist

The SDM framework enables you to control your delivery process in
code.  Think of it as an API for your software delivery.  See this
[introduction][atomist-doc] for more information on the concept of a
Software Delivery Machine and how to create and develop on an SDM.

[atomist-doc]: https://docs.atomist.com/ (Atomist Documentation)

## Getting Started

### Clone this repo to:

```
~/atomist/<owner>/sdm-spring-k8
```
Note: `<owner>` is your Github owner, e.g: idugalic

### Minikube on a Mac

 - Install VirtualBox or another supported hypervisor for your operating system
 - Install the Kubernetes command line client [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/) with Homebrew `brew install kubernetes-cli`
 - Install the [Minikube](https://kubernetes.io/docs/tasks/tools/install-minikube/) with Homebrew by running `brew cask install minikube`

Once the installation is complete, start Minikube to create a new cluster:
```
$ minikube start
```

Install the [ingress](https://github.com/kubernetes/ingress-nginx#what-is-an-ingress-controller) addon:

```
$ minikube addons enable ingress
```
Now check the status of your local Kubernetes cluster by running:
```
$ kubectl get pods --all-namespaces
```

After a couple of minutes all system internal pods should show in `Running` status with a ready count of `1/1`

### Install the Atomist command-line utility

```
$ npm install -g @atomist/cli
```

### Start your local SDM

Install the project dependencies using NPM, compile the TypeScript, and start your SDM in local mode:
```
$ cd ~/atomist/<owner>/sdm-spring-k8
$ atomist start --local
```

### See messages from SDM events

In order to see messages from events (not interspersed with logs), activate a message listener in another terminal:
```
atomist feed
```

### Adding Projects

Further projects can be added under the expanded directory tree in two ways:

#### Configure Existing Projects
If you already have repositories cloned/copied under your `~/atomist/<owner>/`, configure them to activate the local SDM on commit.

Add the Atomist git hook to the existing git projects within this directory structure by running the following command/s:
```
$ cd ~/atomist/<owner>/<repo>
$ atomist add git hooks
```
#### 'atomist clone' Command
The easiest way to add an existing project to your SDM projects is: run the atomist clone command to clone a GitHub.com repository in the right place in the expanded tree and automatically install the git hooks:

`atomist clone https://github.com/<owner>/<repo>`
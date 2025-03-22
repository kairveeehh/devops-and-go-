## Kubernetes Ping Operator

The Kubernetes Ping Operator is a custom operator designed to automate ping tests to specified hostnames by creating and managing Kubernetes jobs. The operator leverages custom resources to enable users to define the parameters of their ping tests, such as the target hostname and the number of attempts.

### Overview

This operator provides a streamlined way to:
- Define ping tests using Kubernetes custom resources.
- Specify the target hostname for the ping test.
- Set the number of attempts for each ping test.
- Automate the execution of ping tests through Kubernetes jobs.

### Usage

#### Create a Basic Ping Test

To create a basic ping test, open a new terminal and apply the following resource:

```bash
kubectl apply -f - <<EOF
apiVersion: monitors.demo.io/v1beta1
kind: Ping
metadata:
  name: ping-sample
spec:
  hostname: "www.google.com"
  attempts: 1
EOF
```

#### Check the Results

Verify the ping test by observing the Kubernetes resources created:

```bash
# View the Ping resource
kubectl get ping

# Check the created job
kubectl get jobs

# View the pod running the ping
kubectl get pods

# Check the ping results
kubectl logs <pod-name>
```

### Customization Examples

#### Ping a Different Website with More Attempts

```bash
kubectl apply -f - <<EOF
apiVersion: monitors.demo.io/v1beta1
kind: Ping
metadata:
  name: github-test
spec:
  hostname: "github.com"
  attempts: 5
EOF
```

#### Test Multiple Websites

```bash
kubectl apply -f - <<EOF
apiVersion: monitors.demo.io/v1beta1
kind: Ping
metadata:
  name: microsoft-test
spec:
  hostname: "microsoft.com"
  attempts: 3
EOF
```


### Task1 

Workign with SBOM

- Download the `Syft` tool and move the binary to `/usr/local/bin`.
- Generate an SBOM for the `docker.io/nginx:latest` image in SPDX format using Syft and store it in `/tmp/webapp-spdx.sbom`.
- Generate an SBOM for the `docker.io/nginx:latest` image in CycloneDX JSON format using Syft and store it in `/tmp/webapp-sbom.json`.
- Download the `Grype` tool and move the binary to `/usr/local/bin`.
- Analyze the `/tmp/webapp-sbom.json` SBOM using Grype to generate a vulnerability report and store it in `/tmp/grype-report.json`.

<details>
        <summary>Hint</summary>

Install Syft
```bash
curl -sSfL https://raw.githubusercontent.com/anchore/syft/main/install.sh | sh -s -- -b /usr/local/bin
```
Generate first report
```bash
syft docker.io/nginx:latest -o spdx > /tmp/webapp-spdx.sbom
```
Generate secont report
```bash
syft docker.io/nginx:latest -o cyclonedx-json > /tmp/webapp-sbom.json
```
Install Grype
```bash
curl -sSfL https://raw.githubusercontent.com/anchore/grype/main/install.sh | sh -s -- -b /usr/local/bin
```
Generate sec report
```bash
grype sbom:/tmp/webapp-sbom.json -o json > /tmp/grype-report.json
```
</details>

### Task2 

Install and configure Kata container and gVisor

- Install gVisor
- Configure Docker/ContainerD to run with gVisor
- Install Kata
- Configure Docker/ContainerD to run with Kata

<details>
        <summary>Hint</summary>

gVisor installation and config guide `https://gvisor.dev/docs/user_guide/install/`

kata installation and config guide `https://github.com/kata-containers/kata-containers/tree/main/docs/install`
</details>

### Task 3

Install Kubernetes Cluster in version 1.32

- Use vagrant to crate our cluster nodes
- Install and cobfigure Kubernetes with kubeadm

</details>

### Task 4

Install and configure Kata container and gVisor

- Install gVisor
- Configure Docker/ContainerD to run with gVisor
- Install Kata
- Configure Docker/ContainerD to run with Kata

<details>
        <summary>Hint</summary>

Kubernetes installation guide `https://v1-33.docs.kubernetes.io/docs/setup/production-environment/tools/kubeadm/`

</details>

### Task 5
Install Kubernetes Dashboard

- Install Kubernetes Dashboard
- Create Admin User and RBAC permissions
- Login to Dashboard and check waht you can do
- Add read-only user
- relogin and repet check

<details>
        <summary>Hint</summary>

Kubernetes DAshboard installation guide `https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/`

</details>

### Task 6 

Upgrade Kubernetes Cluster to version 1.33

### Task 7

Handling Linux users

- Create a user named `sam` on the controlplane host. The user's home directory must be `/opt/sam`. Login shell must be `/bin/bash` and uid must be `2328`. Make sam a member of the `admin group`.
- Change password for `sam` to `www123`
- Suspend but don't delete `sam` user 

<details>
        <summary>Hint</summary>

```bash
useradd -d /opt/sam -s /bin/bash -G admin -u 2328 sam
passwd sam
usermod -s /usr/sbin/nologin sam
```

</details>
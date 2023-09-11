# cdevents-controller signed releases

cdevents-controller deployment manifests are published to GitHub Container Registry as OCI artifacts
and are signed using [cosign](https://github.com/sigstore/cosign).

## Verify the artifacts with cosign

Install the [cosign](https://github.com/sigstore/cosign) CLI:

```sh
brew install sigstore/tap/cosign
```

Verify a cdevents-controller release with cosign CLI:

```sh
cosign verify -key https://raw.githubusercontent.com/bradmccoydev/cdevents-controller/master/cosign/cosign.pub \
ghcr.io/bradmccoydev/cdevents-controller-deploy:latest
```

## Download the artifacts with crane

Install the [crane](https://github.com/google/go-containerregistry/tree/main/cmd/crane) CLI:

```sh
brew install crane
```

Download the cdevents-controller deployment manifests with crane CLI:

```console
$ crane export ghcr.io/bradmccoydev/cdevents-controller-deploy:latest -| tar -xf -

$ ls -1
deployment.yaml
hpa.yaml
kustomization.yaml
service.yaml
```

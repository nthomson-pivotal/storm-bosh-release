# BOSH release for Apache Storm

This BOSH release and deployment manifest deploy a cluster of Apache Storm.

## Usage

This repository includes base manifests and operator files. They can be used for initial deployments and subsequently used for updating your deployments:

```plain
export BOSH_ENVIRONMENT=<bosh-alias>
export BOSH_DEPLOYMENT=apache-storm
git clone https://github.com/cloudfoundry-community/apache-storm-boshrelease.git
bosh deploy apache-storm-boshrelease/manifests/apache-storm.yml
```

If your BOSH does not have Credhub/Config Server, then remember `--vars-store` to allow generation of passwords and certificates.

### Update

When new versions of `apache-storm-boshrelease` are released the `manifests/apache-storm.yml` file will be updated. This means you can easily `git pull` and `bosh deploy` to upgrade.

```plain
export BOSH_ENVIRONMENT=<bosh-alias>
export BOSH_DEPLOYMENT=apache-storm
cd apache-storm-boshrelease
git pull
cd -
bosh deploy apache-storm-boshrelease/manifests/apache-storm.yml
```

### Deploy Topologies

There is a simple example of an errand that will deploy the `ExclamationTopology` sample topology to the Storm cluster. After the cluster has been deployed simply run the following command:

```plain
bosh run-errand deploy-topologies
```
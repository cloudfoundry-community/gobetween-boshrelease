# BOSH Release for gobetween

Dynamic load balancer bosh release using [gobetween](http://gobetween.io/). A default configuration is loaded on new deployments.
A cron job is used to dump config of gobetween to keep configuration in sync to persist through restarts to allow configuration from gobetween [API](http://gobetween.io/documentation.html#REST-API).

## Usage

To use this bosh release, first upload it to your bosh:

```
bosh target BOSH_HOST
git clone https://github.com/cloudfoundry-community/gobetween-boshrelease.git
cd gobetween-boshrelease
bosh upload release releases/gobetween/gobetween-1.yml
```

For [bosh-lite](https://github.com/cloudfoundry/bosh-lite), you can quickly create a deployment manifest & deploy a cluster. Note that this requires that you have installed [spruce](https://github.com/geofffranks/spruce).

```
templates/make_manifest warden
bosh -n deploy
```

### Development

As a developer of this release, create new releases and upload them:

```
bosh create release --force && bosh -n upload release
```

### Final releases

To share final releases:

```
bosh create release --final
```

By default the version number will be bumped to the next major number. You can specify alternate versions:


```
bosh create release --final --version 2.1
```

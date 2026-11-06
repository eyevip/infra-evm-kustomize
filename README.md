# Deployment kustomize Templates for eyevip
This repository contains the deployment for running an eyevip on kubernetes. It also contains example services for redis, mariadb (for testing only, proper setup should be done via operators).

## Usage
Please check the [example](./_example/openshift/) for a quick demo. The image source **must** be changed and some passwords should be configured.

Every workload running the eyevip image needs the DB/eyevip env and the shared volume patched in: `phpfpm`, the `database-setup` Job, and `job` (CronJob) or `job-scheduler` (`sched-job/`, use one of the two); `web` needs the volume only. Check with `kubectl kustomize _example/openshift` — patches whose target matches nothing are skipped silently.

Env key names must match the image's instance `config.json`.

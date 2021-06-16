# CronJob Helm Chart

## Chart Details
Install K8s CronJob object that will run scheduled processes in Openshift or EKS or AKS. This will create ephemeral pods on a schedule, perform a command and kill the pod. Logs will be printed in the completed pod log.

## Installing the Chart
To install the chart with the release name `my-release`:

```bash
helm install --name my-release helm/cronjob
```

## Configuration
The following tables list the configurable parameters of the chart and their default values.

### Parameters

| Parameter                                 | Description                                                                                                                                                                                                         | Default                                                              |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `name`                            | Job name |                                                             |
| `schedule`                        | Cron tab based schedule. Also allows @hourly, @daily, @monthly, @yeraly, @weekly| |
| `concurrencyPolicy`                    | Whether to run jobs concurrently. Allowed  values: Allow, Forbid | `Allow`                                                               |
| `suspend` | Whether to stop job| `false`                                                              |
| `image.repository`     | Image name and repo to be used run as the container|                                                             |
| `image.tag`                     | Image tag/versionn |                                                              |
| `image.pullPolicy`               | Whether to  pull image all the time or  if not  present| `IfNotPresent`                                                       |
| `containerEnv`                   | Provide a list of conatiner environment variables to be used for the job|                                                             |
| `resources`                   | Specify resource request and limits|    |
| `restartPolicy`                | Whether to restart job on failure or no restart| `OnFailure`                                                   |
| `command`                            | Set of shell commands|                                                                 |


Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```bash
helm install --name my-release -f values.yaml stable/cronjob
```

> **Tip**: You can use the default [values.yaml](values.yaml)
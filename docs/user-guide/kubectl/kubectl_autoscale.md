---
---

## kubectl autoscale

Auto-scale a Deployment, ReplicaSet, or ReplicationController

### 摘要


Creates an autoscaler that automatically chooses and sets the number of pods that run in a kubernetes cluster.

Looks up a Deployment, ReplicaSet, or ReplicationController by name and creates an autoscaler that uses the given resource as a reference.
An autoscaler can automatically increase or decrease number of pods deployed within the system as needed.

```
kubectl autoscale (-f FILENAME | TYPE NAME | TYPE/NAME) [--min=MINPODS] --max=MAXPODS [--cpu-percent=CPU] [flags]
```

### 示例

```
# Auto scale a deployment "foo", with the number of pods between 2 to 10, no target CPU utilization specfied so a default autoscaling policy will be used:
kubectl autoscale deployment foo --min=2 --max=10

# Auto scale a replication controller "foo", with the number of pods between 1 to 5, target CPU utilization at 80%:
kubectl autoscale rc foo --max=5 --cpu-percent=80
```

### 选项

```
      --cpu-percent=-1: The target average CPU utilization (represented as a percent of requested CPU) over all the pods. If it's not specified or negative, a default autoscaling policy will be used.
      --dry-run[=false]: If true, only print the object that would be sent, without sending it.
  -f, --filename=[]: Filename, directory, or URL to a file identifying the resource to autoscale.
      --generator="horizontalpodautoscaler/v1": The name of the API generator to use. Currently there is only 1 generator.
      --include-extended-apis[=true]: If true, include definitions of new APIs via calls to the API server. [default true]
      --max=-1: The upper limit for the number of pods that can be set by the autoscaler. Required.
      --min=-1: The lower limit for the number of pods that can be set by the autoscaler. If it's not specified or negative, the server will apply a default value.
      --name="": The name for the newly created object. If not specified, the name of the input resource will be used.
      --no-headers[=false]: 当使用默认输出格式时不打印标题栏。
  -o, --output="": Output format. One of: json|yaml|wide|name|go-template=...|go-template-file=...|jsonpath=...|jsonpath-file=... See golang template [http://golang.org/pkg/text/template/#pkg-overview] and jsonpath template [http://releases.k8s.io/release-1.2/docs/user-guide/jsonpath.md].
      --output-version="": Output the formatted object with the given group version (for ex: 'extensions/v1beta1').
      --record[=false]: Record current kubectl command in the resource annotation.
  -R, --recursive[=false]: Process the directory used in -f, --filename recursively. Useful when you want to manage related manifests organized within the same directory.
      --save-config[=false]: If true, the configuration of current object will be saved in its annotation. This is useful when you want to perform kubectl apply on this object in the future.
  -a, --show-all[=false]: When printing, show all resources (default hide terminated pods.)
      --show-labels[=false]: When printing, show all labels as the last column (default hide labels column)
      --sort-by="": If non-empty, sort list types using this field specification.  The field specification is expressed as a JSONPath expression (e.g. '{.metadata.name}'). The field in the API resource specified by this JSONPath expression must be an integer or a string.
      --template="": Template string or path to template file to use when -o=go-template, -o=go-template-file. The template format is golang templates [http://golang.org/pkg/text/template/#pkg-overview].
```

{% include_relative parent_commands.md %}

### 参见

* [kubectl](kubectl.md)	 - 使用kubectl来管理Kubernetes集群。



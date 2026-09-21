zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops$ ls
LICENSE                     session-11-kubernetes-services         session-14-kubernetes-troubleshooting  session2-linux            session4             session6-7-docker
README.md                   session-12-ingress-configmaps-secrets  session-15-helm                        session3                  session4-networking  session8-docker-networking-volume
session10-k8s-core-objects  session-13-storage-hpa-probes          session1-devops-engineer-roadmap       session3-shell-scripting  session5-git-github  session9-k8s
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops$ cd session-14-kubernetes-troubleshooting/
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting$ ls
01-kubectl-get       03-kubectl-logs  05-events            07-imagepullbackoff  09-service-dns-troubleshooting  README.md
02-kubectl-describe  04-kubectl-exec  06-crashloopbackoff  08-pending-pods      mini-project
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting$ cd 01-kubectl-get/
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/01-kubectl-get$ ls
README.md  sample-workload.yaml
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/01-kubectl-get$ cd ..
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting$ cd 02-kubectl-describe/
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/02-kubectl-describe$ la
bash: la: command not found...
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/02-kubectl-describe$ ^C
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/02-kubectl-describe$ ls
demo-pod.yaml  README.md
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/02-kubectl-describe$ kubectl apply -f demo-pod.yaml 
pod/describe-demo created
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/02-kubectl-describe$ kubectl get all
NAME                            READY   STATUS    RESTARTS      AGE
pod/describe-demo               1/1     Running   0             4s
pod/emptydir-demo               1/1     Running   2 (12m ago)   46h
pod/hostpath-demo               1/1     Running   2 (12m ago)   46h
pod/hpa-demo-5d6676989b-pnv9d   1/1     Running   1 (12m ago)   45h
pod/storage-demo                1/1     Running   2 (12m ago)   46h

NAME                       TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)   AGE
service/hpa-demo-service   ClusterIP   10.106.222.57   <none>        80/TCP    45h
service/kubernetes         ClusterIP   10.96.0.1       <none>        443/TCP   46h

NAME                       READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/hpa-demo   1/1     1            1           45h

NAME                                  DESIRED   CURRENT   READY   AGE
replicaset.apps/hpa-demo-5d6676989b   1         1         1       45h

NAME                                           REFERENCE             TARGETS       MINPODS   MAXPODS   REPLICAS   AGE
horizontalpodautoscaler.autoscaling/hpa-demo   Deployment/hpa-demo   cpu: 0%/50%   1         5         1          45h
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/02-kubectl-describe$ kubectl get pods
NAME                        READY   STATUS    RESTARTS      AGE
describe-demo               1/1     Running   0             18s
emptydir-demo               1/1     Running   2 (13m ago)   46h
hostpath-demo               1/1     Running   2 (13m ago)   46h
hpa-demo-5d6676989b-pnv9d   1/1     Running   1 (13m ago)   45h
storage-demo                1/1     Running   2 (13m ago)   46h
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/02-kubectl-describe$ kubectl describe deploy/^C
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/02-kubectl-describe$ cd ..
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting$ cd 03
bash: cd: 03: No such file or directory
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting$ cd 03-kubectl-logs/
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/03-kubectl-logs$ ls
pod.yaml  README.md
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/03-kubectl-logs$ kubectl apply -f pod.yaml 
pod/logs-demo created
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/03-kubectl-logs$ kubectl logs pod/logs-demo
Application started
Connecting to database...
Database connection successful
Application is running
Application is healthy
Application is healthy
Application is healthy
Application is healthy
Application is healthy
Application is healthy
Application is healthy
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/03-kubectl-logs$ cd ..
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting$ cd 05-events/
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/05-events$ ls
pod.yaml  README.md
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/05-events$ kubectl apply -f pod.yaml 
pod/events-demo created
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/05-events$ kubectl get pods
NAME                        READY   STATUS    RESTARTS      AGE
describe-demo               1/1     Running   0             8m2s
emptydir-demo               1/1     Running   2 (20m ago)   47h
events-demo                 1/1     Running   0             7s
hostpath-demo               1/1     Running   2 (20m ago)   47h
hpa-demo-5d6676989b-pnv9d   1/1     Running   1 (20m ago)   45h
logs-demo                   1/1     Running   0             4m45s
storage-demo                1/1     Running   2 (20m ago)   46h
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/05-events$ kubectl exec -it pod/events-demo -- bash
root@events-demo:/# ls   
bin  boot  dev  docker-entrypoint.d  docker-entrypoint.sh  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@events-demo:/# cd data
bash: cd: data: No such file or directory
root@events-demo:/# exit
exit
command terminated with exit code 1
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/05-events$ docker ps
CONTAINER ID   IMAGE                                 COMMAND                  CREATED       STATUS          PORTS                                                                                                                                  NAMES
581bfbb8d20f   postgres:16                           "docker-entrypoint.s…"   3 days ago    Up 9 minutes    0.0.0.0:5432->5432/tcp, [::]:5432->5432/tcp                                                                                            jaagrmind-postgres
06669829a792   gcr.io/k8s-minikube/kicbase:v0.0.51   "/usr/local/bin/entr…"   12 days ago   Up 22 minutes   127.0.0.1:32768->22/tcp, 127.0.0.1:32769->2376/tcp, 127.0.0.1:32770->5000/tcp, 127.0.0.1:32771->8443/tcp, 127.0.0.1:32772->32443/tcp   minikube
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/05-events$ docker images
                                                                                                                                                                             i Info →   U  In Use
IMAGE                                                                                                 ID             DISK USAGE   CONTENT SIZE   EXTRA
alpine:latest                                                                                         28bd5fe8b56d         14MB         3.93MB    U   
gcr.io/k8s-minikube/kicbase:v0.0.51                                                                   146cd636030e       1.89GB          532MB        
gcr.io/k8s-minikube/kicbase@sha256:4a1c825b61479e6c898851ea66f13c620aaeab6002746e95067fc2c4b38a0b24   4a1c825b6147       1.89GB          532MB    U   
mysql:8.0                                                                                             7dcddc01f13b        1.1GB          249MB        
nginx:latest                                                                                          b34848eff6db        241MB         66.2MB        
postgres:16                                                                                           f1c3376c26f2        639MB          166MB    U   
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/05-events$ docker rmi gcr.io/k8s-minikube/kicbase^C
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/05-events$ kubectl events
LAST SEEN           TYPE      REASON                         OBJECT                             MESSAGE
25m                 Normal    Starting                       Node/minikube                      Starting kubelet.
25m                 Normal    NodeAllocatableEnforced        Node/minikube                      Updated Node Allocatable limit across pods
25m (x7 over 25m)   Normal    NodeHasSufficientPID           Node/minikube                      Node minikube status is now: NodeHasSufficientPID
25m (x8 over 25m)   Normal    NodeHasNoDiskPressure          Node/minikube                      Node minikube status is now: NodeHasNoDiskPressure
25m (x8 over 25m)   Normal    NodeHasSufficientMemory        Node/minikube                      Node minikube status is now: NodeHasSufficientMemory
25m                 Normal    Created                        Pod/hpa-demo-5d6676989b-pnv9d      Container created
25m                 Normal    SandboxChanged                 Pod/hpa-demo-5d6676989b-pnv9d      Pod sandbox changed, it will be killed and re-created.
25m                 Warning   Rebooted                       Node/minikube                      Node minikube has been rebooted, boot id: 93b11e1f-b6ec-42e1-9cf9-d5ae10a67895
25m                 Normal    Started                        Pod/hpa-demo-5d6676989b-pnv9d      Container started
25m                 Normal    Pulled                         Pod/hpa-demo-5d6676989b-pnv9d      Container image "nginx:1.27" already present on machine and can be accessed by the pod
25m                 Normal    SandboxChanged                 Pod/storage-demo                   Pod sandbox changed, it will be killed and re-created.
25m                 Normal    Started                        Pod/storage-demo                   Container started
25m                 Normal    SandboxChanged                 Pod/hostpath-demo                  Pod sandbox changed, it will be killed and re-created.
25m                 Normal    Pulled                         Pod/hostpath-demo                  Container image "nginx:1.27" already present on machine and can be accessed by the pod
25m                 Normal    Created                        Pod/hostpath-demo                  Container created
25m                 Normal    Started                        Pod/hostpath-demo                  Container started
25m                 Normal    Pulled                         Pod/storage-demo                   Container image "nginx:1.27" already present on machine and can be accessed by the pod
25m                 Normal    Created                        Pod/storage-demo                   Container created
25m                 Normal    Pulled                         Pod/emptydir-demo                  Container image "nginx:1.27" already present on machine and can be accessed by the pod
25m                 Normal    SandboxChanged                 Pod/emptydir-demo                  Pod sandbox changed, it will be killed and re-created.
25m                 Normal    Created                        Pod/emptydir-demo                  Container created
25m                 Normal    Started                        Pod/emptydir-demo                  Container started
25m                 Normal    Starting                       Node/minikube                      
25m                 Normal    RegisteredNode                 Node/minikube                      Node minikube event: Registered Node minikube in Controller
24m (x6 over 25m)   Warning   FailedComputeMetricsReplicas   HorizontalPodAutoscaler/hpa-demo   invalid metrics (1 invalid out of 1), first error is: failed to get cpu resource metric value: failed to get cpu utilization: unable to get metrics for resource cpu: unable to fetch metrics from resource metrics API: the server is currently unable to handle the request (get pods.metrics.k8s.io)
24m (x6 over 25m)   Warning   FailedGetResourceMetric        HorizontalPodAutoscaler/hpa-demo   failed to get cpu utilization: unable to get metrics for resource cpu: unable to fetch metrics from resource metrics API: the server is currently unable to handle the request (get pods.metrics.k8s.io)
12m                 Normal    Scheduled                      Pod/describe-demo                  Successfully assigned default/describe-demo to minikube
12m                 Normal    Pulled                         Pod/describe-demo                  Container image "nginx:1.27" already present on machine and can be accessed by the pod
12m                 Normal    Started                        Pod/describe-demo                  Container started
12m                 Normal    Created                        Pod/describe-demo                  Container created
9m22s               Normal    Scheduled                      Pod/logs-demo                      Successfully assigned default/logs-demo to minikube
9m21s               Normal    Started                        Pod/logs-demo                      Container started
9m21s               Normal    Created                        Pod/logs-demo                      Container created
9m21s               Normal    Pulled                         Pod/logs-demo                      Container image "busybox:1.36" already present on machine and can be accessed by the pod
4m44s               Normal    Started                        Pod/events-demo                    Container started
4m44s               Normal    Created                        Pod/events-demo                    Container created
4m44s               Normal    Pulled                         Pod/events-demo                    Container image "nginx:1.27" already present on machine and can be accessed by the pod
4m44s               Normal    Scheduled                      Pod/events-demo                    Successfully assigned default/events-demo to minikube
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/05-events$ kubectl get events
LAST SEEN   TYPE      REASON                         OBJECT                             MESSAGE
15m         Normal    Scheduled                      pod/describe-demo                  Successfully assigned default/describe-demo to minikube
15m         Normal    Pulled                         pod/describe-demo                  Container image "nginx:1.27" already present on machine and can be accessed by the pod
15m         Normal    Created                        pod/describe-demo                  Container created
15m         Normal    Started                        pod/describe-demo                  Container started
27m         Normal    SandboxChanged                 pod/emptydir-demo                  Pod sandbox changed, it will be killed and re-created.
27m         Normal    Pulled                         pod/emptydir-demo                  Container image "nginx:1.27" already present on machine and can be accessed by the pod
27m         Normal    Created                        pod/emptydir-demo                  Container created
27m         Normal    Started                        pod/emptydir-demo                  Container started
7m8s        Normal    Scheduled                      pod/events-demo                    Successfully assigned default/events-demo to minikube
7m8s        Normal    Pulled                         pod/events-demo                    Container image "nginx:1.27" already present on machine and can be accessed by the pod
7m8s        Normal    Created                        pod/events-demo                    Container created
7m8s        Normal    Started                        pod/events-demo                    Container started
27m         Normal    SandboxChanged                 pod/hostpath-demo                  Pod sandbox changed, it will be killed and re-created.
27m         Normal    Pulled                         pod/hostpath-demo                  Container image "nginx:1.27" already present on machine and can be accessed by the pod
27m         Normal    Created                        pod/hostpath-demo                  Container created
27m         Normal    Started                        pod/hostpath-demo                  Container started
27m         Normal    SandboxChanged                 pod/hpa-demo-5d6676989b-pnv9d      Pod sandbox changed, it will be killed and re-created.
27m         Normal    Pulled                         pod/hpa-demo-5d6676989b-pnv9d      Container image "nginx:1.27" already present on machine and can be accessed by the pod
27m         Normal    Created                        pod/hpa-demo-5d6676989b-pnv9d      Container created
27m         Normal    Started                        pod/hpa-demo-5d6676989b-pnv9d      Container started
26m         Warning   FailedGetResourceMetric        horizontalpodautoscaler/hpa-demo   failed to get cpu utilization: unable to get metrics for resource cpu: unable to fetch metrics from resource metrics API: the server is currently unable to handle the request (get pods.metrics.k8s.io)
26m         Warning   FailedComputeMetricsReplicas   horizontalpodautoscaler/hpa-demo   invalid metrics (1 invalid out of 1), first error is: failed to get cpu resource metric value: failed to get cpu utilization: unable to get metrics for resource cpu: unable to fetch metrics from resource metrics API: the server is currently unable to handle the request (get pods.metrics.k8s.io)
11m         Normal    Scheduled                      pod/logs-demo                      Successfully assigned default/logs-demo to minikube
11m         Normal    Pulled                         pod/logs-demo                      Container image "busybox:1.36" already present on machine and can be accessed by the pod
11m         Normal    Created                        pod/logs-demo                      Container created
11m         Normal    Started                        pod/logs-demo                      Container started
27m         Normal    Starting                       node/minikube                      Starting kubelet.
27m         Normal    NodeHasSufficientMemory        node/minikube                      Node minikube status is now: NodeHasSufficientMemory
27m         Normal    NodeHasNoDiskPressure          node/minikube                      Node minikube status is now: NodeHasNoDiskPressure
27m         Normal    NodeHasSufficientPID           node/minikube                      Node minikube status is now: NodeHasSufficientPID
27m         Normal    NodeAllocatableEnforced        node/minikube                      Updated Node Allocatable limit across pods
27m         Warning   Rebooted                       node/minikube                      Node minikube has been rebooted, boot id: 93b11e1f-b6ec-42e1-9cf9-d5ae10a67895
27m         Normal    Starting                       node/minikube                      
27m         Normal    RegisteredNode                 node/minikube                      Node minikube event: Registered Node minikube in Controller
27m         Normal    SandboxChanged                 pod/storage-demo                   Pod sandbox changed, it will be killed and re-created.
27m         Normal    Pulled                         pod/storage-demo                   Container image "nginx:1.27" already present on machine and can be accessed by the pod
27m         Normal    Created                        pod/storage-demo                   Container created
27m         Normal    Started                        pod/storage-demo                   Container started
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/05-events$ kubectl get events --sort-by=timestamp
No resources found in default namespace.
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/05-events$ kubectl get events --sort-by=Lasttimestamp
No resources found in default namespace.
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/05-events$ kubectl get events --sort-by=Last-timestamp
No resources found in default namespace.
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/05-events$ kubectl get events --sort-by= --help
Display one or many resources.

 Prints a table of the most important information about the specified resources. You can filter the list using a label
selector and the --selector flag. If the desired resource type is namespaced you will only see results in the current
namespace if you don't specify any namespace.

 By specifying the output as 'template' and providing a Go template as the value of the --template flag, you can filter
the attributes of the fetched resources.

Use "kubectl api-resources" for a complete list of supported resources.

Examples:
  # List all pods in ps output format
  kubectl get pods
  
  # List all pods in ps output format with more information (such as node name)
  kubectl get pods -o wide
  
  # List a single replication controller with specified NAME in ps output format
  kubectl get replicationcontroller web
  
  # List deployments in JSON output format, in the "v1" version of the "apps" API group
  kubectl get deployments.v1.apps -o json
  
  # List a single pod in JSON output format
  kubectl get -o json pod web-pod-13je7
  
  # List a pod identified by type and name specified in "pod.yaml" in JSON output format
  kubectl get -f pod.yaml -o json
  
  # List resources from a directory with kustomization.yaml - e.g. dir/kustomization.yaml
  kubectl get -k dir/
  
  # Return only the phase value of the specified pod
  kubectl get -o template pod/web-pod-13je7 --template={{.status.phase}}
  
  # List resource information in custom columns
  kubectl get pod test-pod -o custom-columns=CONTAINER:.spec.containers[0].name,IMAGE:.spec.containers[0].image
  
  # List all replication controllers and services together in ps output format
  kubectl get rc,services
  
  # List one or more resources by their type and names
  kubectl get rc/web service/frontend pods/web-pod-13je7
  
  # List the 'status' subresource for a single pod
  kubectl get pod web-pod-13je7 --subresource status
  
  # List all deployments in namespace 'backend'
  kubectl get deployments.apps --namespace backend
  
  # List all pods existing in all namespaces
  kubectl get pods --all-namespaces

Options:
    -A, --all-namespaces=false:
        If present, list the requested object(s) across all namespaces. Namespace in current context is ignored even
        if specified with --namespace.

    --allow-missing-template-keys=true:
        If true, ignore any errors in templates when a field or map key is missing in the template. Only applies to
        golang and jsonpath output formats.

    --chunk-size=500:
        Return large lists in chunks rather than all at once. Pass 0 to disable.

    --field-selector='':
        Selector (field query) to filter on, supports '=', '==', and '!='.(e.g. --field-selector
        key1=value1,key2=value2). The server only supports a limited number of field queries per type.

    -f, --filename=[]:
        Filename, directory, or URL to files identifying the resource to get from a server.

    --ignore-not-found=false:
        If set to true, suppresses NotFound error for specific objects that do not exist. Using this flag with
        commands that query for collections of resources has no effect when no resources are found.

    -k, --kustomize='':
        Process the kustomization directory. This flag can't be used together with -f or -R.

    -L, --label-columns=[]:
        Accepts a comma separated list of labels that are going to be presented as columns. Names are case-sensitive.
        You can also use multiple flag options like -L label1 -L label2...

    --no-headers=false:
        When using the default or custom-column output format, don't print headers (default print headers).

    -o, --output='':
        Output format. One of: (json, yaml, kyaml, name, go-template, go-template-file, template, templatefile,
        jsonpath, jsonpath-as-json, jsonpath-file, custom-columns, custom-columns-file, wide). See custom columns
        [https://kubernetes.io/docs/reference/kubectl/#custom-columns], golang template
        [http://golang.org/pkg/text/template/#pkg-overview] and jsonpath template
        [https://kubernetes.io/docs/reference/kubectl/jsonpath/].

    --output-watch-events=false:
        Output watch event objects when --watch or --watch-only is used. Existing objects are output as initial ADDED
        events.

    --raw='':
        Raw URI to request from the server.  Uses the transport specified by the kubeconfig file.

    -R, --recursive=false:
        Process the directory used in -f, --filename recursively. Useful when you want to manage related manifests
        organized within the same directory.

    -l, --selector='':
        Selector (label query) to filter on, supports '=', '==', '!=', 'in', 'notin'.(e.g. -l
        key1=value1,key2=value2,key3 in (value3)). Matching objects must satisfy all of the specified label
        constraints.

    --server-print=true:
        If true, have the server return the appropriate table output. Supports extension APIs and CRDs.

    --show-kind=false:
        If present, list the resource type for the requested object(s).

    --show-labels=false:
        When printing, show all labels as the last column (default hide labels column)

    --show-managed-fields=false:
        If true, keep the managedFields when printing objects in JSON or YAML format.

    --sort-by='':
        If non-empty, sort list types using this field specification.  The field specification is expressed as a
        JSONPath expression (e.g. '{.metadata.name}'). The field in the API resource specified by this JSONPath
        expression must be an integer or a string.

    --subresource='':
        If specified, gets the subresource of the requested object.

    --template='':
        Template string or path to template file to use when -o=go-template, -o=go-template-file. The template format
        is golang templates [http://golang.org/pkg/text/template/#pkg-overview].

    -w, --watch=false:
        After listing/getting the requested object, watch for changes.

    --watch-only=false:
        Watch for changes to the requested object(s), without listing/getting first.

Usage:
  kubectl get
[(-o|--output=)json|yaml|kyaml|name|go-template|go-template-file|template|templatefile|jsonpath|jsonpath-as-json|jsonpath-file|custom-columns|custom-columns-file|wide]
(TYPE[.VERSION][.GROUP] [NAME | -l label] | TYPE[.VERSION][.GROUP]/NAME ...) [flags] [options]

Use "kubectl options" for a list of global command-line options (applies to all commands).
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/05-events$ kubectl get events --sort-by=time
No resources found in default namespace.
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/05-events$ kubectl get events --sort-by=LastTimestamp
No resources found in default namespace.
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/05-events$ kubectl get events --sort-by=LastTimestamp^C
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/05-events$ cd ..
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting$ cd 06-crashloopbackoff/
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/06-crashloopbackoff$ kubectl apply -f broken-pod.yaml 
pod/crash-demo created
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/06-crashloopbackoff$ kubectl logs pod/crash-demo
Application starting...
Something went wrong!
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/06-crashloopbackoff$ kubectl get events
LAST SEEN   TYPE      REASON                         OBJECT                             MESSAGE
28s         Normal    Scheduled                      pod/crash-demo                     Successfully assigned default/crash-demo to minikube
15s         Normal    Pulled                         pod/crash-demo                     Container image "busybox:1.36" already present on machine and can be accessed by the pod
15s         Normal    Created                        pod/crash-demo                     Container created
15s         Normal    Started                        pod/crash-demo                     Container started
14s         Warning   BackOff                        pod/crash-demo                     Back-off restarting failed container app in pod crash-demo_default(2a7452c1-51dd-46de-baa6-0972bafa77ec)
19m         Normal    Scheduled                      pod/describe-demo                  Successfully assigned default/describe-demo to minikube
19m         Normal    Pulled                         pod/describe-demo                  Container image "nginx:1.27" already present on machine and can be accessed by the pod
19m         Normal    Created                        pod/describe-demo                  Container created
19m         Normal    Started                        pod/describe-demo                  Container started
32m         Normal    SandboxChanged                 pod/emptydir-demo                  Pod sandbox changed, it will be killed and re-created.
32m         Normal    Pulled                         pod/emptydir-demo                  Container image "nginx:1.27" already present on machine and can be accessed by the pod
32m         Normal    Created                        pod/emptydir-demo                  Container created
32m         Normal    Started                        pod/emptydir-demo                  Container started
12m         Normal    Scheduled                      pod/events-demo                    Successfully assigned default/events-demo to minikube
12m         Normal    Pulled                         pod/events-demo                    Container image "nginx:1.27" already present on machine and can be accessed by the pod
12m         Normal    Created                        pod/events-demo                    Container created
12m         Normal    Started                        pod/events-demo                    Container started
32m         Normal    SandboxChanged                 pod/hostpath-demo                  Pod sandbox changed, it will be killed and re-created.
32m         Normal    Pulled                         pod/hostpath-demo                  Container image "nginx:1.27" already present on machine and can be accessed by the pod
32m         Normal    Created                        pod/hostpath-demo                  Container created
32m         Normal    Started                        pod/hostpath-demo                  Container started
32m         Normal    SandboxChanged                 pod/hpa-demo-5d6676989b-pnv9d      Pod sandbox changed, it will be killed and re-created.
32m         Normal    Pulled                         pod/hpa-demo-5d6676989b-pnv9d      Container image "nginx:1.27" already present on machine and can be accessed by the pod
32m         Normal    Created                        pod/hpa-demo-5d6676989b-pnv9d      Container created
32m         Normal    Started                        pod/hpa-demo-5d6676989b-pnv9d      Container started
31m         Warning   FailedGetResourceMetric        horizontalpodautoscaler/hpa-demo   failed to get cpu utilization: unable to get metrics for resource cpu: unable to fetch metrics from resource metrics API: the server is currently unable to handle the request (get pods.metrics.k8s.io)
31m         Warning   FailedComputeMetricsReplicas   horizontalpodautoscaler/hpa-demo   invalid metrics (1 invalid out of 1), first error is: failed to get cpu resource metric value: failed to get cpu utilization: unable to get metrics for resource cpu: unable to fetch metrics from resource metrics API: the server is currently unable to handle the request (get pods.metrics.k8s.io)
16m         Normal    Scheduled                      pod/logs-demo                      Successfully assigned default/logs-demo to minikube
16m         Normal    Pulled                         pod/logs-demo                      Container image "busybox:1.36" already present on machine and can be accessed by the pod
16m         Normal    Created                        pod/logs-demo                      Container created
16m         Normal    Started                        pod/logs-demo                      Container started
32m         Normal    Starting                       node/minikube                      Starting kubelet.
32m         Normal    NodeHasSufficientMemory        node/minikube                      Node minikube status is now: NodeHasSufficientMemory
32m         Normal    NodeHasNoDiskPressure          node/minikube                      Node minikube status is now: NodeHasNoDiskPressure
32m         Normal    NodeHasSufficientPID           node/minikube                      Node minikube status is now: NodeHasSufficientPID
32m         Normal    NodeAllocatableEnforced        node/minikube                      Updated Node Allocatable limit across pods
32m         Warning   Rebooted                       node/minikube                      Node minikube has been rebooted, boot id: 93b11e1f-b6ec-42e1-9cf9-d5ae10a67895
32m         Normal    Starting                       node/minikube                      
32m         Normal    RegisteredNode                 node/minikube                      Node minikube event: Registered Node minikube in Controller
32m         Normal    SandboxChanged                 pod/storage-demo                   Pod sandbox changed, it will be killed and re-created.
32m         Normal    Pulled                         pod/storage-demo                   Container image "nginx:1.27" already present on machine and can be accessed by the pod
32m         Normal    Created                        pod/storage-demo                   Container created
32m         Normal    Started                        pod/storage-demo                   Container started
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/06-crashloopbackoff$ kubectl delete pod/crash-demo
pod "crash-demo" deleted from default namespace
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/06-crashloopbackoff$ kubectl apply -f fixed-pod.yaml 
pod/crash-demo created
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/06-crashloopbackoff$ kubectl events
LAST SEEN               TYPE      REASON                         OBJECT                             MESSAGE
38m                     Normal    NodeAllocatableEnforced        Node/minikube                      Updated Node Allocatable limit across pods
38m                     Normal    Starting                       Node/minikube                      Starting kubelet.
38m (x8 over 38m)       Normal    NodeHasSufficientMemory        Node/minikube                      Node minikube status is now: NodeHasSufficientMemory
38m (x8 over 38m)       Normal    NodeHasNoDiskPressure          Node/minikube                      Node minikube status is now: NodeHasNoDiskPressure
38m (x7 over 38m)       Normal    NodeHasSufficientPID           Node/minikube                      Node minikube status is now: NodeHasSufficientPID
38m                     Normal    Pulled                         Pod/hpa-demo-5d6676989b-pnv9d      Container image "nginx:1.27" already present on machine and can be accessed by the pod
38m                     Normal    Created                        Pod/hpa-demo-5d6676989b-pnv9d      Container created
38m                     Warning   Rebooted                       Node/minikube                      Node minikube has been rebooted, boot id: 93b11e1f-b6ec-42e1-9cf9-d5ae10a67895
38m                     Normal    Started                        Pod/hpa-demo-5d6676989b-pnv9d      Container started
38m                     Normal    SandboxChanged                 Pod/hpa-demo-5d6676989b-pnv9d      Pod sandbox changed, it will be killed and re-created.
38m                     Normal    Pulled                         Pod/emptydir-demo                  Container image "nginx:1.27" already present on machine and can be accessed by the pod
38m                     Normal    Pulled                         Pod/storage-demo                   Container image "nginx:1.27" already present on machine and can be accessed by the pod
38m                     Normal    Created                        Pod/storage-demo                   Container created
38m                     Normal    SandboxChanged                 Pod/emptydir-demo                  Pod sandbox changed, it will be killed and re-created.
38m                     Normal    SandboxChanged                 Pod/storage-demo                   Pod sandbox changed, it will be killed and re-created.
38m                     Normal    Created                        Pod/emptydir-demo                  Container created
38m                     Normal    Started                        Pod/emptydir-demo                  Container started
38m                     Normal    Started                        Pod/storage-demo                   Container started
38m                     Normal    Started                        Pod/hostpath-demo                  Container started
38m                     Normal    Created                        Pod/hostpath-demo                  Container created
38m                     Normal    Pulled                         Pod/hostpath-demo                  Container image "nginx:1.27" already present on machine and can be accessed by the pod
38m                     Normal    SandboxChanged                 Pod/hostpath-demo                  Pod sandbox changed, it will be killed and re-created.
38m                     Normal    Starting                       Node/minikube                      
38m                     Normal    RegisteredNode                 Node/minikube                      Node minikube event: Registered Node minikube in Controller
37m (x6 over 38m)       Warning   FailedGetResourceMetric        HorizontalPodAutoscaler/hpa-demo   failed to get cpu utilization: unable to get metrics for resource cpu: unable to fetch metrics from resource metrics API: the server is currently unable to handle the request (get pods.metrics.k8s.io)
37m (x6 over 38m)       Warning   FailedComputeMetricsReplicas   HorizontalPodAutoscaler/hpa-demo   invalid metrics (1 invalid out of 1), first error is: failed to get cpu resource metric value: failed to get cpu utilization: unable to get metrics for resource cpu: unable to fetch metrics from resource metrics API: the server is currently unable to handle the request (get pods.metrics.k8s.io)
25m                     Normal    Scheduled                      Pod/describe-demo                  Successfully assigned default/describe-demo to minikube
25m                     Normal    Created                        Pod/describe-demo                  Container created
25m                     Normal    Pulled                         Pod/describe-demo                  Container image "nginx:1.27" already present on machine and can be accessed by the pod
25m                     Normal    Started                        Pod/describe-demo                  Container started
22m                     Normal    Scheduled                      Pod/logs-demo                      Successfully assigned default/logs-demo to minikube
22m                     Normal    Pulled                         Pod/logs-demo                      Container image "busybox:1.36" already present on machine and can be accessed by the pod
22m                     Normal    Started                        Pod/logs-demo                      Container started
22m                     Normal    Created                        Pod/logs-demo                      Container created
17m                     Normal    Created                        Pod/events-demo                    Container created
17m                     Normal    Scheduled                      Pod/events-demo                    Successfully assigned default/events-demo to minikube
17m                     Normal    Pulled                         Pod/events-demo                    Container image "nginx:1.27" already present on machine and can be accessed by the pod
17m                     Normal    Started                        Pod/events-demo                    Container started
6m23s                   Normal    Scheduled                      Pod/crash-demo                     Successfully assigned default/crash-demo to minikube
3m28s (x6 over 6m23s)   Normal    Started                        Pod/crash-demo                     Container started
3m28s (x6 over 6m23s)   Normal    Created                        Pod/crash-demo                     Container created
3m28s (x6 over 6m23s)   Normal    Pulled                         Pod/crash-demo                     Container image "busybox:1.36" already present on machine and can be accessed by the pod
117s (x7 over 6m21s)    Warning   BackOff                        Pod/crash-demo                     Back-off restarting failed container app in pod crash-demo_default(2a7452c1-51dd-46de-baa6-0972bafa77ec)
11s                     Normal    Started                        Pod/crash-demo                     Container started
11s                     Normal    Created                        Pod/crash-demo                     Container created
11s                     Normal    Pulled                         Pod/crash-demo                     Container image "busybox:1.36" already present on machine and can be accessed by the pod
11s                     Normal    Scheduled                      Pod/crash-demo                     Successfully assigned default/crash-demo to minikube
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/06-crashloopbackoff$ kubectl get pods
NAME                        READY   STATUS    RESTARTS      AGE
crash-demo                  1/1     Running   0             21s
describe-demo               1/1     Running   0             26m
emptydir-demo               1/1     Running   2 (38m ago)   47h
events-demo                 1/1     Running   0             18m
hostpath-demo               1/1     Running   2 (38m ago)   47h
hpa-demo-5d6676989b-pnv9d   1/1     Running   1 (38m ago)   46h
logs-demo                   1/1     Running   0             22m
storage-demo                1/1     Running   2 (38m ago)   46h
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/06-crashloopbackoff$ cd ..
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting$ cd 07-imagepullbackoff/
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/07-imagepullbackoff$ ls
broken-pod.yaml  fixed-pod.yaml  README.md
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/07-imagepullbackoff$ kubectl apply -f broken-pod.yaml 
pod/image-demo created
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/07-imagepullbackoff$ kubectl get pods
NAME                        READY   STATUS         RESTARTS      AGE
crash-demo                  1/1     Running        0             45s
describe-demo               1/1     Running        0             26m
emptydir-demo               1/1     Running        2 (39m ago)   47h
events-demo                 1/1     Running        0             18m
hostpath-demo               1/1     Running        2 (39m ago)   47h
hpa-demo-5d6676989b-pnv9d   1/1     Running        1 (39m ago)   46h
image-demo                  0/1     ErrImagePull   0             5s
logs-demo                   1/1     Running        0             23m
storage-demo                1/1     Running        2 (39m ago)   46h
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/07-imagepullbackoff$ kubectl delete pod/describe-demo
pod "describe-demo" deleted from default namespace
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/07-imagepullbackoff$ kubectl apply -f fixed-pod.yaml 
pod/image-demo configured
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/07-imagepullbackoff$ kubectl get pods
\NAME                        READY   STATUS    RESTARTS      AGE
crash-demo                  1/1     Running   0             73s
emptydir-demo               1/1     Running   2 (39m ago)   47h
events-demo                 1/1     Running   0             18m
hostpath-demo               1/1     Running   2 (39m ago)   47h
hpa-demo-5d6676989b-pnv9d   1/1     Running   1 (39m ago)   46h
image-demo                  1/1     Running   0             33s
logs-demo                   1/1     Running   0             23m
storage-demo                1/1     Running   2 (39m ago)   46h
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/07-imagepullbackoff$ ls
broken-pod.yaml  fixed-pod.yaml  README.md
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/07-imagepullbackoff$ cd ../08-pending-pods/
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/08-pending-pods$ ls
broken-pod.yaml  fixed-pod.yaml  README.md
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/08-pending-pods$ kubectl apply -f broken-pod.yaml 
pod/pending-demo created
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/08-pending-pods$ kubectl get pods
NAME                        READY   STATUS    RESTARTS      AGE
crash-demo                  1/1     Running   0             112s
emptydir-demo               1/1     Running   2 (40m ago)   47h
events-demo                 1/1     Running   0             19m
hostpath-demo               1/1     Running   2 (40m ago)   47h
hpa-demo-5d6676989b-pnv9d   1/1     Running   1 (40m ago)   46h
image-demo                  1/1     Running   0             72s
logs-demo                   1/1     Running   0             24m
pending-demo                0/1     Pending   0             6s
storage-demo                1/1     Running   2 (40m ago)   46h
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/08-pending-pods$ kubectl get events
LAST SEEN   TYPE      REASON                         OBJECT                             MESSAGE
8m29s       Normal    Scheduled                      pod/crash-demo                     Successfully assigned default/crash-demo to minikube
5m34s       Normal    Pulled                         pod/crash-demo                     Container image "busybox:1.36" already present on machine and can be accessed by the pod
5m34s       Normal    Created                        pod/crash-demo                     Container created
5m34s       Normal    Started                        pod/crash-demo                     Container started
4m3s        Warning   BackOff                        pod/crash-demo                     Back-off restarting failed container app in pod crash-demo_default(2a7452c1-51dd-46de-baa6-0972bafa77ec)
2m17s       Normal    Scheduled                      pod/crash-demo                     Successfully assigned default/crash-demo to minikube
2m17s       Normal    Pulled                         pod/crash-demo                     Container image "busybox:1.36" already present on machine and can be accessed by the pod
2m17s       Normal    Created                        pod/crash-demo                     Container created
2m17s       Normal    Started                        pod/crash-demo                     Container started
27m         Normal    Scheduled                      pod/describe-demo                  Successfully assigned default/describe-demo to minikube
27m         Normal    Pulled                         pod/describe-demo                  Container image "nginx:1.27" already present on machine and can be accessed by the pod
27m         Normal    Created                        pod/describe-demo                  Container created
27m         Normal    Started                        pod/describe-demo                  Container started
72s         Normal    Killing                        pod/describe-demo                  Stopping container nginx
40m         Normal    SandboxChanged                 pod/emptydir-demo                  Pod sandbox changed, it will be killed and re-created.
40m         Normal    Pulled                         pod/emptydir-demo                  Container image "nginx:1.27" already present on machine and can be accessed by the pod
40m         Normal    Created                        pod/emptydir-demo                  Container created
40m         Normal    Started                        pod/emptydir-demo                  Container started
20m         Normal    Scheduled                      pod/events-demo                    Successfully assigned default/events-demo to minikube
20m         Normal    Pulled                         pod/events-demo                    Container image "nginx:1.27" already present on machine and can be accessed by the pod
20m         Normal    Created                        pod/events-demo                    Container created
20m         Normal    Started                        pod/events-demo                    Container started
40m         Normal    SandboxChanged                 pod/hostpath-demo                  Pod sandbox changed, it will be killed and re-created.
40m         Normal    Pulled                         pod/hostpath-demo                  Container image "nginx:1.27" already present on machine and can be accessed by the pod
40m         Normal    Created                        pod/hostpath-demo                  Container created
40m         Normal    Started                        pod/hostpath-demo                  Container started
40m         Normal    SandboxChanged                 pod/hpa-demo-5d6676989b-pnv9d      Pod sandbox changed, it will be killed and re-created.
40m         Normal    Pulled                         pod/hpa-demo-5d6676989b-pnv9d      Container image "nginx:1.27" already present on machine and can be accessed by the pod
40m         Normal    Created                        pod/hpa-demo-5d6676989b-pnv9d      Container created
40m         Normal    Started                        pod/hpa-demo-5d6676989b-pnv9d      Container started
39m         Warning   FailedGetResourceMetric        horizontalpodautoscaler/hpa-demo   failed to get cpu utilization: unable to get metrics for resource cpu: unable to fetch metrics from resource metrics API: the server is currently unable to handle the request (get pods.metrics.k8s.io)
39m         Warning   FailedComputeMetricsReplicas   horizontalpodautoscaler/hpa-demo   invalid metrics (1 invalid out of 1), first error is: failed to get cpu resource metric value: failed to get cpu utilization: unable to get metrics for resource cpu: unable to fetch metrics from resource metrics API: the server is currently unable to handle the request (get pods.metrics.k8s.io)
97s         Normal    Scheduled                      pod/image-demo                     Successfully assigned default/image-demo to minikube
84s         Normal    Pulling                        pod/image-demo                     Pulling image "nginx:this-image-does-not-exist"
82s         Warning   Failed                         pod/image-demo                     Failed to pull image "nginx:this-image-does-not-exist": rpc error: code = NotFound desc = failed to pull and unpack image "docker.io/library/nginx:this-image-does-not-exist": failed to resolve reference "docker.io/library/nginx:this-image-does-not-exist": docker.io/library/nginx:this-image-does-not-exist: not found
82s         Warning   Failed                         pod/image-demo                     Error: ErrImagePull
70s         Normal    BackOff                        pod/image-demo                     Back-off pulling image "nginx:this-image-does-not-exist"
70s         Warning   Failed                         pod/image-demo                     Error: ImagePullBackOff
67s         Normal    Pulled                         pod/image-demo                     Container image "nginx:1.27" already present on machine and can be accessed by the pod
67s         Normal    Created                        pod/image-demo                     Container created
67s         Normal    Started                        pod/image-demo                     Container started
24m         Normal    Scheduled                      pod/logs-demo                      Successfully assigned default/logs-demo to minikube
24m         Normal    Pulled                         pod/logs-demo                      Container image "busybox:1.36" already present on machine and can be accessed by the pod
24m         Normal    Created                        pod/logs-demo                      Container created
24m         Normal    Started                        pod/logs-demo                      Container started
40m         Normal    Starting                       node/minikube                      Starting kubelet.
40m         Normal    NodeHasSufficientMemory        node/minikube                      Node minikube status is now: NodeHasSufficientMemory
40m         Normal    NodeHasNoDiskPressure          node/minikube                      Node minikube status is now: NodeHasNoDiskPressure
40m         Normal    NodeHasSufficientPID           node/minikube                      Node minikube status is now: NodeHasSufficientPID
40m         Normal    NodeAllocatableEnforced        node/minikube                      Updated Node Allocatable limit across pods
40m         Warning   Rebooted                       node/minikube                      Node minikube has been rebooted, boot id: 93b11e1f-b6ec-42e1-9cf9-d5ae10a67895
40m         Normal    Starting                       node/minikube                      
40m         Normal    RegisteredNode                 node/minikube                      Node minikube event: Registered Node minikube in Controller
31s         Warning   FailedScheduling               pod/pending-demo                   0/1 nodes are available: 1 node(s) didn't match Pod's node affinity/selector. preemption: 0/1 nodes are available: 1 Preemption is not helpful for scheduling.
40m         Normal    SandboxChanged                 pod/storage-demo                   Pod sandbox changed, it will be killed and re-created.
40m         Normal    Pulled                         pod/storage-demo                   Container image "nginx:1.27" already present on machine and can be accessed by the pod
40m         Normal    Created                        pod/storage-demo                   Container created
40m         Normal    Started                        pod/storage-demo                   Container started
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/08-pending-pods$ kubectl apply -f fixed-pod.yaml 
The Pod "pending-demo" is invalid: spec: Forbidden: pod updates may not change fields other than `spec.containers[*].image`,`spec.initContainers[*].image`,`spec.activeDeadlineSeconds`,`spec.tolerations` (only additions to existing tolerations),`spec.terminationGracePeriodSeconds` (allow it to be set to 1 if it was previously negative)
@@ -142,9 +142,7 @@
  "TerminationGracePeriodSeconds": 30,
  "ActiveDeadlineSeconds": null,
  "DNSPolicy": "ClusterFirst",
- "NodeSelector": {
-  "kubernetes.io/hostname": "node-that-does-not-exist"
- },
+ "NodeSelector": null,
  "ServiceAccountName": "default",
  "DeprecatedServiceAccount": "default",
  "AutomountServiceAccountToken": null,

zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/08-pending-pods$ kubectl delete pod/broken-demo
Error from server (NotFound): pods "broken-demo" not found
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/08-pending-pods$ cat broken-pod.yaml 
apiVersion: v1
kind: Pod

metadata:
  name: pending-demo

spec:
  nodeSelector:
    kubernetes.io/hostname: node-that-does-not-exist

  containers:
    - name: nginx
      image: nginx:1.27zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/08-pending-pods$ kubectl delete pod/pending-demo
pod "pending-demo" deleted from default namespace
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/08-pending-pods$ kubectl apply -f fixed-pod.yaml 
pod/pending-demo created
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/08-pending-pods$ kubectl logs pod/pending-demo
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2026/09/21 06:49:04 [notice] 1#1: using the "epoll" event method
2026/09/21 06:49:04 [notice] 1#1: nginx/1.27.5
2026/09/21 06:49:04 [notice] 1#1: built by gcc 12.2.0 (Debian 12.2.0-14) 
2026/09/21 06:49:04 [notice] 1#1: OS: Linux 7.2.5-200.fc44.x86_64
2026/09/21 06:49:04 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2026/09/21 06:49:04 [notice] 1#1: start worker processes
2026/09/21 06:49:04 [notice] 1#1: start worker process 29
2026/09/21 06:49:04 [notice] 1#1: start worker process 30
2026/09/21 06:49:04 [notice] 1#1: start worker process 31
2026/09/21 06:49:04 [notice] 1#1: start worker process 32
2026/09/21 06:49:04 [notice] 1#1: start worker process 33
2026/09/21 06:49:04 [notice] 1#1: start worker process 34
2026/09/21 06:49:04 [notice] 1#1: start worker process 35
2026/09/21 06:49:04 [notice] 1#1: start worker process 36
2026/09/21 06:49:04 [notice] 1#1: start worker process 37
2026/09/21 06:49:04 [notice] 1#1: start worker process 38
2026/09/21 06:49:04 [notice] 1#1: start worker process 39
2026/09/21 06:49:04 [notice] 1#1: start worker process 40
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/08-pending-pods$ kubectl get pods
NAME                        READY   STATUS    RESTARTS      AGE
crash-demo                  1/1     Running   0             3m28s
emptydir-demo               1/1     Running   2 (41m ago)   47h
events-demo                 1/1     Running   0             21m
hostpath-demo               1/1     Running   2 (41m ago)   47h
hpa-demo-5d6676989b-pnv9d   1/1     Running   1 (41m ago)   46h
image-demo                  1/1     Running   0             2m48s
logs-demo                   1/1     Running   0             25m
pending-demo                1/1     Running   0             18s
storage-demo                1/1     Running   2 (41m ago)   46h
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/08-pending-pods$ cd ../09-service-dns-troubleshooting/
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/09-service-dns-troubleshooting$ ls
broken-service.yaml  deployment.yaml  dns-test-pod.yaml  README.md  service.yaml
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/09-service-dns-troubleshooting$ kubectl apply -f deployment.yaml 
deployment.apps/web created
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/09-service-dns-troubleshooting$ kubectl apply -f service.yaml 
service/web-service created
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/09-service-dns-troubleshooting$ kubectl get events
LAST SEEN   TYPE      REASON                         OBJECT                             MESSAGE
13m         Normal    Scheduled                      pod/crash-demo                     Successfully assigned default/crash-demo to minikube
10m         Normal    Pulled                         pod/crash-demo                     Container image "busybox:1.36" already present on machine and can be accessed by the pod
10m         Normal    Created                        pod/crash-demo                     Container created
10m         Normal    Started                        pod/crash-demo                     Container started
9m12s       Warning   BackOff                        pod/crash-demo                     Back-off restarting failed container app in pod crash-demo_default(2a7452c1-51dd-46de-baa6-0972bafa77ec)
7m26s       Normal    Scheduled                      pod/crash-demo                     Successfully assigned default/crash-demo to minikube
7m26s       Normal    Pulled                         pod/crash-demo                     Container image "busybox:1.36" already present on machine and can be accessed by the pod
7m26s       Normal    Created                        pod/crash-demo                     Container created
7m26s       Normal    Started                        pod/crash-demo                     Container started
33m         Normal    Scheduled                      pod/describe-demo                  Successfully assigned default/describe-demo to minikube
33m         Normal    Pulled                         pod/describe-demo                  Container image "nginx:1.27" already present on machine and can be accessed by the pod
33m         Normal    Created                        pod/describe-demo                  Container created
33m         Normal    Started                        pod/describe-demo                  Container started
6m21s       Normal    Killing                        pod/describe-demo                  Stopping container nginx
45m         Normal    SandboxChanged                 pod/emptydir-demo                  Pod sandbox changed, it will be killed and re-created.
45m         Normal    Pulled                         pod/emptydir-demo                  Container image "nginx:1.27" already present on machine and can be accessed by the pod
45m         Normal    Created                        pod/emptydir-demo                  Container created
45m         Normal    Started                        pod/emptydir-demo                  Container started
25m         Normal    Scheduled                      pod/events-demo                    Successfully assigned default/events-demo to minikube
25m         Normal    Pulled                         pod/events-demo                    Container image "nginx:1.27" already present on machine and can be accessed by the pod
25m         Normal    Created                        pod/events-demo                    Container created
25m         Normal    Started                        pod/events-demo                    Container started
45m         Normal    SandboxChanged                 pod/hostpath-demo                  Pod sandbox changed, it will be killed and re-created.
45m         Normal    Pulled                         pod/hostpath-demo                  Container image "nginx:1.27" already present on machine and can be accessed by the pod
45m         Normal    Created                        pod/hostpath-demo                  Container created
45m         Normal    Started                        pod/hostpath-demo                  Container started
45m         Normal    SandboxChanged                 pod/hpa-demo-5d6676989b-pnv9d      Pod sandbox changed, it will be killed and re-created.
45m         Normal    Pulled                         pod/hpa-demo-5d6676989b-pnv9d      Container image "nginx:1.27" already present on machine and can be accessed by the pod
45m         Normal    Created                        pod/hpa-demo-5d6676989b-pnv9d      Container created
45m         Normal    Started                        pod/hpa-demo-5d6676989b-pnv9d      Container started
44m         Warning   FailedGetResourceMetric        horizontalpodautoscaler/hpa-demo   failed to get cpu utilization: unable to get metrics for resource cpu: unable to fetch metrics from resource metrics API: the server is currently unable to handle the request (get pods.metrics.k8s.io)
44m         Warning   FailedComputeMetricsReplicas   horizontalpodautoscaler/hpa-demo   invalid metrics (1 invalid out of 1), first error is: failed to get cpu resource metric value: failed to get cpu utilization: unable to get metrics for resource cpu: unable to fetch metrics from resource metrics API: the server is currently unable to handle the request (get pods.metrics.k8s.io)
6m46s       Normal    Scheduled                      pod/image-demo                     Successfully assigned default/image-demo to minikube
6m33s       Normal    Pulling                        pod/image-demo                     Pulling image "nginx:this-image-does-not-exist"
6m31s       Warning   Failed                         pod/image-demo                     Failed to pull image "nginx:this-image-does-not-exist": rpc error: code = NotFound desc = failed to pull and unpack image "docker.io/library/nginx:this-image-does-not-exist": failed to resolve reference "docker.io/library/nginx:this-image-does-not-exist": docker.io/library/nginx:this-image-does-not-exist: not found
6m31s       Warning   Failed                         pod/image-demo                     Error: ErrImagePull
6m19s       Normal    BackOff                        pod/image-demo                     Back-off pulling image "nginx:this-image-does-not-exist"
6m19s       Warning   Failed                         pod/image-demo                     Error: ImagePullBackOff
6m16s       Normal    Pulled                         pod/image-demo                     Container image "nginx:1.27" already present on machine and can be accessed by the pod
6m16s       Normal    Created                        pod/image-demo                     Container created
6m16s       Normal    Started                        pod/image-demo                     Container started
29m         Normal    Scheduled                      pod/logs-demo                      Successfully assigned default/logs-demo to minikube
29m         Normal    Pulled                         pod/logs-demo                      Container image "busybox:1.36" already present on machine and can be accessed by the pod
29m         Normal    Created                        pod/logs-demo                      Container created
29m         Normal    Started                        pod/logs-demo                      Container started
45m         Normal    Starting                       node/minikube                      Starting kubelet.
45m         Normal    NodeHasSufficientMemory        node/minikube                      Node minikube status is now: NodeHasSufficientMemory
45m         Normal    NodeHasNoDiskPressure          node/minikube                      Node minikube status is now: NodeHasNoDiskPressure
45m         Normal    NodeHasSufficientPID           node/minikube                      Node minikube status is now: NodeHasSufficientPID
45m         Normal    NodeAllocatableEnforced        node/minikube                      Updated Node Allocatable limit across pods
45m         Warning   Rebooted                       node/minikube                      Node minikube has been rebooted, boot id: 93b11e1f-b6ec-42e1-9cf9-d5ae10a67895
45m         Normal    Starting                       node/minikube                      
45m         Normal    RegisteredNode                 node/minikube                      Node minikube event: Registered Node minikube in Controller
5m40s       Warning   FailedScheduling               pod/pending-demo                   0/1 nodes are available: 1 node(s) didn't match Pod's node affinity/selector. preemption: 0/1 nodes are available: 1 Preemption is not helpful for scheduling.
4m16s       Normal    Scheduled                      pod/pending-demo                   Successfully assigned default/pending-demo to minikube
4m16s       Normal    Pulled                         pod/pending-demo                   Container image "nginx:1.27" already present on machine and can be accessed by the pod
4m16s       Normal    Created                        pod/pending-demo                   Container created
4m15s       Normal    Started                        pod/pending-demo                   Container started
45m         Normal    SandboxChanged                 pod/storage-demo                   Pod sandbox changed, it will be killed and re-created.
45m         Normal    Pulled                         pod/storage-demo                   Container image "nginx:1.27" already present on machine and can be accessed by the pod
45m         Normal    Created                        pod/storage-demo                   Container created
45m         Normal    Started                        pod/storage-demo                   Container started
19s         Normal    Scheduled                      pod/web-557577df75-882xn           Successfully assigned default/web-557577df75-882xn to minikube
18s         Normal    Pulled                         pod/web-557577df75-882xn           Container image "nginx:1.27" already present on machine and can be accessed by the pod
18s         Normal    Created                        pod/web-557577df75-882xn           Container created
18s         Normal    Started                        pod/web-557577df75-882xn           Container started
19s         Normal    Scheduled                      pod/web-557577df75-x6ttw           Successfully assigned default/web-557577df75-x6ttw to minikube
18s         Normal    Pulled                         pod/web-557577df75-x6ttw           Container image "nginx:1.27" already present on machine and can be accessed by the pod
18s         Normal    Created                        pod/web-557577df75-x6ttw           Container created
18s         Normal    Started                        pod/web-557577df75-x6ttw           Container started
19s         Normal    SuccessfulCreate               replicaset/web-557577df75          Created pod: web-557577df75-x6ttw
19s         Normal    SuccessfulCreate               replicaset/web-557577df75          Created pod: web-557577df75-882xn
19s         Normal    ScalingReplicaSet              deployment/web                     Scaled up replica set web-557577df75 from 0 to 2
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/09-service-dns-troubleshooting$ kubectl get pods
NAME                        READY   STATUS    RESTARTS      AGE
crash-demo                  1/1     Running   0             7m36s
emptydir-demo               1/1     Running   2 (46m ago)   47h
events-demo                 1/1     Running   0             25m
hostpath-demo               1/1     Running   2 (46m ago)   47h
hpa-demo-5d6676989b-pnv9d   1/1     Running   1 (46m ago)   46h
image-demo                  1/1     Running   0             6m56s
logs-demo                   1/1     Running   0             29m
pending-demo                1/1     Running   0             4m26s
storage-demo                1/1     Running   2 (46m ago)   46h
web-557577df75-882xn        1/1     Running   0             29s
web-557577df75-x6ttw        1/1     Running   0             29s
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/09-service-dns-troubleshooting$ kubectl get svc
NAME               TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)   AGE
hpa-demo-service   ClusterIP   10.106.222.57   <none>        80/TCP    46h
kubernetes         ClusterIP   10.96.0.1       <none>        443/TCP   47h
web-service        ClusterIP   10.99.248.180   <none>        80/TCP    41s
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/09-service-dns-troubleshooting$ kubectl apply -f dns-test-pod.yaml 
pod/dns-test created
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/09-service-dns-troubleshooting$ kubectl get pods
NAME                        READY   STATUS         RESTARTS      AGE
crash-demo                  1/1     Running        0             8m11s
dns-test                    0/1     ErrImagePull   0             5s
emptydir-demo               1/1     Running        2 (46m ago)   47h
events-demo                 1/1     Running        0             25m
hostpath-demo               1/1     Running        2 (46m ago)   47h
hpa-demo-5d6676989b-pnv9d   1/1     Running        1 (46m ago)   46h
image-demo                  1/1     Running        0             7m31s
logs-demo                   1/1     Running        0             30m
pending-demo                1/1     Running        0             5m1s
storage-demo                1/1     Running        2 (46m ago)   46h
web-557577df75-882xn        1/1     Running        0             64s
web-557577df75-x6ttw        1/1     Running        0             64s
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/09-service-dns-troubleshooting$ cd ../03-kubectl-logs/
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/03-kubectl-logs$ ls
pod.yaml  README.md
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/03-kubectl-logs$ kubectl exec -it pod/logs-demo -- bash
error: Internal error occurred: Internal error occurred: error executing command in container: failed to exec in container: failed to start exec "9b8ab409d788f388efb9bfecd629a81034bd0e0f12ce6240553cfbd0095e7e15": OCI runtime exec failed: exec failed: unable to start container process: exec: "bash": executable file not found in $PATH
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/03-kubectl-logs$ kubectl exec -it pod/logs-demo -- sh
/ # 
/ # ls
bin    dev    etc    home   lib    lib64  proc   root   sys    tmp    usr    var
/ # curl
sh: curl: not found
/ # ping
BusyBox v1.36.1 (2023-05-18 22:34:17 UTC) multi-call binary.

Usage: ping [OPTIONS] HOST

Send ICMP ECHO_REQUESTs to HOST

        -4,-6           Force IP or IPv6 name resolution
        -c CNT          Send only CNT pings
        -s SIZE         Send SIZE data bytes in packets (default 56)
        -i SECS         Interval
        -A              Ping as soon as reply is received
        -t TTL          Set TTL
        -I IFACE/IP     Source interface or IP address
        -W SEC          Seconds to wait for the first response (default 10)
                        (after all -c CNT packets are sent)
        -w SEC          Seconds until ping exits (default:infinite)
                        (can exit earlier with -c CNT)
        -q              Quiet, only display output at start/finish
        -p HEXBYTE      Payload pattern
/ # ping 10.99.248.180
PING 10.99.248.180 (10.99.248.180): 56 data bytes
^C
--- 10.99.248.180 ping statistics ---
8 packets transmitted, 0 packets received, 100% packet loss
/ # ping web-service
PING web-service (10.99.248.180): 56 data bytes
^C
--- web-service ping statistics ---
5 packets transmitted, 0 packets received, 100% packet loss
/ # exit
command terminated with exit code 1
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/03-kubectl-logs$ cd ../09-service-dns-troubleshooting/
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/09-service-dns-troubleshooting$ kubectl exec -it pod/events-demo -- bash
root@events-demo:/# curl web-service
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
root@events-demo:/# curl -i web-service
HTTP/1.1 200 OK
Server: nginx/1.27.5
Date: Mon, 21 Sep 2026 06:59:33 GMT
Content-Type: text/html
Content-Length: 615
Last-Modified: Wed, 16 Apr 2025 12:01:11 GMT
Connection: keep-alive
ETag: "67ff9c07-267"
Accept-Ranges: bytes

<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
root@events-demo:/# exit
exit
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/09-service-dns-troubleshooting$ kubectl get endpoints web-service
Warning: v1 Endpoints is deprecated in v1.33+; use discovery.k8s.io/v1 EndpointSlice
NAME          ENDPOINTS                       AGE
web-service   10.244.0.15:80,10.244.0.16:80   11m
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/09-service-dns-troubleshooting$ kubectl get pods
NAME                        READY   STATUS             RESTARTS      AGE
crash-demo                  1/1     Running            0             22m
dns-test                    0/1     ImagePullBackOff   0             14m
emptydir-demo               1/1     Running            2 (60m ago)   47h
events-demo                 1/1     Running            0             39m
hostpath-demo               1/1     Running            2 (60m ago)   47h
hpa-demo-5d6676989b-pnv9d   1/1     Running            1 (60m ago)   46h
image-demo                  1/1     Running            0             21m
logs-demo                   1/1     Running            0             44m
pending-demo                1/1     Running            0             18m
storage-demo                1/1     Running            2 (60m ago)   47h
web-557577df75-882xn        1/1     Running            0             15m
web-557577df75-x6ttw        1/1     Running            0             15m
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/09-service-dns-troubleshooting$ kubectl get all
NAME                            READY   STATUS             RESTARTS      AGE
pod/crash-demo                  1/1     Running            0             22m
pod/dns-test                    0/1     ImagePullBackOff   0             14m
pod/emptydir-demo               1/1     Running            2 (60m ago)   47h
pod/events-demo                 1/1     Running            0             39m
pod/hostpath-demo               1/1     Running            2 (60m ago)   47h
pod/hpa-demo-5d6676989b-pnv9d   1/1     Running            1 (60m ago)   46h
pod/image-demo                  1/1     Running            0             21m
pod/logs-demo                   1/1     Running            0             44m
pod/pending-demo                1/1     Running            0             19m
pod/storage-demo                1/1     Running            2 (60m ago)   47h
pod/web-557577df75-882xn        1/1     Running            0             15m
pod/web-557577df75-x6ttw        1/1     Running            0             15m

NAME                       TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)   AGE
service/hpa-demo-service   ClusterIP   10.106.222.57   <none>        80/TCP    46h
service/kubernetes         ClusterIP   10.96.0.1       <none>        443/TCP   47h
service/web-service        ClusterIP   10.99.248.180   <none>        80/TCP    15m

NAME                       READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/hpa-demo   1/1     1            1           46h
deployment.apps/web        2/2     2            2           15m

NAME                                  DESIRED   CURRENT   READY   AGE
replicaset.apps/hpa-demo-5d6676989b   1         1         1       46h
replicaset.apps/web-557577df75        2         2         2       15m

NAME                                           REFERENCE             TARGETS       MINPODS   MAXPODS   REPLICAS   AGE
horizontalpodautoscaler.autoscaling/hpa-demo   Deployment/hpa-demo   cpu: 0%/50%   1         5         1          46h
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/09-service-dns-troubleshooting$ kubectl get events
LAST SEEN   TYPE      REASON                         OBJECT                             MESSAGE
28m         Normal    Scheduled                      pod/crash-demo                     Successfully assigned default/crash-demo to minikube
25m         Normal    Pulled                         pod/crash-demo                     Container image "busybox:1.36" already present on machine and can be accessed by the pod
25m         Normal    Created                        pod/crash-demo                     Container created
25m         Normal    Started                        pod/crash-demo                     Container started
24m         Warning   BackOff                        pod/crash-demo                     Back-off restarting failed container app in pod crash-demo_default(2a7452c1-51dd-46de-baa6-0972bafa77ec)
22m         Normal    Scheduled                      pod/crash-demo                     Successfully assigned default/crash-demo to minikube
22m         Normal    Pulled                         pod/crash-demo                     Container image "busybox:1.36" already present on machine and can be accessed by the pod
22m         Normal    Created                        pod/crash-demo                     Container created
22m         Normal    Started                        pod/crash-demo                     Container started
48m         Normal    Scheduled                      pod/describe-demo                  Successfully assigned default/describe-demo to minikube
48m         Normal    Pulled                         pod/describe-demo                  Container image "nginx:1.27" already present on machine and can be accessed by the pod
48m         Normal    Created                        pod/describe-demo                  Container created
48m         Normal    Started                        pod/describe-demo                  Container started
21m         Normal    Killing                        pod/describe-demo                  Stopping container nginx
14m         Normal    Scheduled                      pod/dns-test                       Successfully assigned default/dns-test to minikube
11m         Normal    Pulling                        pod/dns-test                       Pulling image "registry.k8s.io/e2e-test-images/dnsutils:1.3"
11m         Warning   Failed                         pod/dns-test                       Failed to pull image "registry.k8s.io/e2e-test-images/dnsutils:1.3": rpc error: code = NotFound desc = failed to pull and unpack image "registry.k8s.io/e2e-test-images/dnsutils:1.3": failed to resolve reference "registry.k8s.io/e2e-test-images/dnsutils:1.3": registry.k8s.io/e2e-test-images/dnsutils:1.3: not found
11m         Warning   Failed                         pod/dns-test                       Error: ErrImagePull
4m12s       Normal    BackOff                        pod/dns-test                       Back-off pulling image "registry.k8s.io/e2e-test-images/dnsutils:1.3"
4m12s       Warning   Failed                         pod/dns-test                       Error: ImagePullBackOff
60m         Normal    SandboxChanged                 pod/emptydir-demo                  Pod sandbox changed, it will be killed and re-created.
60m         Normal    Pulled                         pod/emptydir-demo                  Container image "nginx:1.27" already present on machine and can be accessed by the pod
60m         Normal    Created                        pod/emptydir-demo                  Container created
60m         Normal    Started                        pod/emptydir-demo                  Container started
40m         Normal    Scheduled                      pod/events-demo                    Successfully assigned default/events-demo to minikube
40m         Normal    Pulled                         pod/events-demo                    Container image "nginx:1.27" already present on machine and can be accessed by the pod
40m         Normal    Created                        pod/events-demo                    Container created
40m         Normal    Started                        pod/events-demo                    Container started
60m         Normal    SandboxChanged                 pod/hostpath-demo                  Pod sandbox changed, it will be killed and re-created.
60m         Normal    Pulled                         pod/hostpath-demo                  Container image "nginx:1.27" already present on machine and can be accessed by the pod
60m         Normal    Created                        pod/hostpath-demo                  Container created
60m         Normal    Started                        pod/hostpath-demo                  Container started
60m         Normal    SandboxChanged                 pod/hpa-demo-5d6676989b-pnv9d      Pod sandbox changed, it will be killed and re-created.
60m         Normal    Pulled                         pod/hpa-demo-5d6676989b-pnv9d      Container image "nginx:1.27" already present on machine and can be accessed by the pod
60m         Normal    Created                        pod/hpa-demo-5d6676989b-pnv9d      Container created
60m         Normal    Started                        pod/hpa-demo-5d6676989b-pnv9d      Container started
59m         Warning   FailedGetResourceMetric        horizontalpodautoscaler/hpa-demo   failed to get cpu utilization: unable to get metrics for resource cpu: unable to fetch metrics from resource metrics API: the server is currently unable to handle the request (get pods.metrics.k8s.io)
59m         Warning   FailedComputeMetricsReplicas   horizontalpodautoscaler/hpa-demo   invalid metrics (1 invalid out of 1), first error is: failed to get cpu resource metric value: failed to get cpu utilization: unable to get metrics for resource cpu: unable to fetch metrics from resource metrics API: the server is currently unable to handle the request (get pods.metrics.k8s.io)
21m         Normal    Scheduled                      pod/image-demo                     Successfully assigned default/image-demo to minikube
21m         Normal    Pulling                        pod/image-demo                     Pulling image "nginx:this-image-does-not-exist"
21m         Warning   Failed                         pod/image-demo                     Failed to pull image "nginx:this-image-does-not-exist": rpc error: code = NotFound desc = failed to pull and unpack image "docker.io/library/nginx:this-image-does-not-exist": failed to resolve reference "docker.io/library/nginx:this-image-does-not-exist": docker.io/library/nginx:this-image-does-not-exist: not found
21m         Warning   Failed                         pod/image-demo                     Error: ErrImagePull
21m         Normal    BackOff                        pod/image-demo                     Back-off pulling image "nginx:this-image-does-not-exist"
21m         Warning   Failed                         pod/image-demo                     Error: ImagePullBackOff
21m         Normal    Pulled                         pod/image-demo                     Container image "nginx:1.27" already present on machine and can be accessed by the pod
21m         Normal    Created                        pod/image-demo                     Container created
21m         Normal    Started                        pod/image-demo                     Container started
44m         Normal    Scheduled                      pod/logs-demo                      Successfully assigned default/logs-demo to minikube
44m         Normal    Pulled                         pod/logs-demo                      Container image "busybox:1.36" already present on machine and can be accessed by the pod
44m         Normal    Created                        pod/logs-demo                      Container created
44m         Normal    Started                        pod/logs-demo                      Container started
60m         Normal    Starting                       node/minikube                      Starting kubelet.
60m         Normal    NodeHasSufficientMemory        node/minikube                      Node minikube status is now: NodeHasSufficientMemory
60m         Normal    NodeHasNoDiskPressure          node/minikube                      Node minikube status is now: NodeHasNoDiskPressure
60m         Normal    NodeHasSufficientPID           node/minikube                      Node minikube status is now: NodeHasSufficientPID
60m         Normal    NodeAllocatableEnforced        node/minikube                      Updated Node Allocatable limit across pods
60m         Warning   Rebooted                       node/minikube                      Node minikube has been rebooted, boot id: 93b11e1f-b6ec-42e1-9cf9-d5ae10a67895
60m         Normal    Starting                       node/minikube                      
60m         Normal    RegisteredNode                 node/minikube                      Node minikube event: Registered Node minikube in Controller
20m         Warning   FailedScheduling               pod/pending-demo                   0/1 nodes are available: 1 node(s) didn't match Pod's node affinity/selector. preemption: 0/1 nodes are available: 1 Preemption is not helpful for scheduling.
19m         Normal    Scheduled                      pod/pending-demo                   Successfully assigned default/pending-demo to minikube
19m         Normal    Pulled                         pod/pending-demo                   Container image "nginx:1.27" already present on machine and can be accessed by the pod
19m         Normal    Created                        pod/pending-demo                   Container created
19m         Normal    Started                        pod/pending-demo                   Container started
60m         Normal    SandboxChanged                 pod/storage-demo                   Pod sandbox changed, it will be killed and re-created.
60m         Normal    Pulled                         pod/storage-demo                   Container image "nginx:1.27" already present on machine and can be accessed by the pod
60m         Normal    Created                        pod/storage-demo                   Container created
60m         Normal    Started                        pod/storage-demo                   Container started
15m         Normal    Scheduled                      pod/web-557577df75-882xn           Successfully assigned default/web-557577df75-882xn to minikube
15m         Normal    Pulled                         pod/web-557577df75-882xn           Container image "nginx:1.27" already present on machine and can be accessed by the pod
15m         Normal    Created                        pod/web-557577df75-882xn           Container created
15m         Normal    Started                        pod/web-557577df75-882xn           Container started
15m         Normal    Scheduled                      pod/web-557577df75-x6ttw           Successfully assigned default/web-557577df75-x6ttw to minikube
15m         Normal    Pulled                         pod/web-557577df75-x6ttw           Container image "nginx:1.27" already present on machine and can be accessed by the pod
15m         Normal    Created                        pod/web-557577df75-x6ttw           Container created
15m         Normal    Started                        pod/web-557577df75-x6ttw           Container started
15m         Normal    SuccessfulCreate               replicaset/web-557577df75          Created pod: web-557577df75-x6ttw
15m         Normal    SuccessfulCreate               replicaset/web-557577df75          Created pod: web-557577df75-882xn
15m         Normal    ScalingReplicaSet              deployment/web                     Scaled up replica set web-557577df75 from 0 to 2
zephoryx@fedora:~/Documents/Academics/SST/TERM - IX/DevOps/devops/session-14-kubernetes-troubleshooting/09-service-dns-troubleshooting$ 

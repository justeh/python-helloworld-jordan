SOURCE_IMAGE = os.getenv("SOURCE_IMAGE", default='docker.io/justeh/python-helloworld-jordan')
LOCAL_PATH = os.getenv("LOCAL_PATH", default='.')
NAMESPACE = os.getenv("NAMESPACE", default='justeh')

k8s_custom_deploy(
   'python-helloworld-jordan',
   apply_cmd="tanzu apps workload apply -f config/workload.yaml --live-update" +
       " --local-path " + LOCAL_PATH +
       " --source-image " + SOURCE_IMAGE +
       " --namespace " + NAMESPACE +
       " --yes >/dev/null" +
       " && kubectl get workload python-helloworld-jordan --namespace " + NAMESPACE + " -o yaml",
   delete_cmd="tanzu apps workload delete -f config/workload.yaml --namespace " + NAMESPACE + " --yes" ,
   deps=['pom.xml', './target/classes'],
   container_selector='workload',
   live_update=[
       sync('./target/classes', '/workspace/BOOT-INF/classes')
   ]
)

k8s_resource('python-helloworld-jordan', port_forwards=["8080:8080"],
   extra_pod_selectors=[{'serving.knative.dev/service': 'python-helloworld-jordan'}])
allow_k8s_contexts('jaguchi-pinniped')

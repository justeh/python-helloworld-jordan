# python-helloworld-jordan
To deploy 
tanzu apps workload create "python-helloworld-jordan" \
--git-repo "https://github.com/justeh/python-helloworld-jordan" \
--git-branch main \
--git-tag tap-1.0 \
--namespace justeh \
--type web \
--label app.kubernetes.io/part-of="python-helloworld-jordan" \
--yes
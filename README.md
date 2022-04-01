# openshift-provider-certification

OpenShift Provider Certification Tool.

> TODO: improve the description

## Install

```sh
curl -s https://github.com/mtulio/openshift-provider-certification/blob/draft/openshift-provider-cert
chmod u+x openshift-provider-cert
```


## Usage

### Running

Disable container security [see container security restrictions are removed][scc-add]:
~~~
oc adm policy add-scc-to-group anyuid system:authenticated system:serviceaccounts
oc adm policy add-scc-to-group privileged system:authenticated system:serviceaccounts
~~~

Run certification tool:
```bash
./run.sh
```

Check results:
- Sonobuoy result file should be placed on current directory

### Check results

Get the certification tests status:
```bash
sonobuouy status
```

Get general guidance to troubleshoot results:
```bash
./report.sh
```

### Destroy

Destroy certification environment:
```bash
./destroy.sh
```

Remove custom SCC:
```bash
oc adm policy remove-scc-from-group anyuid system:authenticated system:serviceaccounts
oc adm policy remove-scc-from-group privileged system:authenticated system:serviceaccounts
```

## Troubleshooting

### Failed executions

1. Check the tests statusess and error tests:

```bash
./report.sh
```

1. Check the [documentation](TODO:path/to/tests/doc) to troubleshoot the failing tests

> The documentation referencing the test definition should be delivered on the main repo as part of the tool. For reference, the k8s-conformance auto generates that doc for each release. https://github.com/cncf/k8s-conformance/tree/master/docs



[scc-add]:https://github.com/openshift/kubernetes/blob/master/openshift-hack/conformance-k8s.sh#L47

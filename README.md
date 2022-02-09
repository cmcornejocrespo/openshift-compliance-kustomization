README.md
# Kustomization for Deploying OpenShift Compliance Operator

## Deploying OpenShift Compliance Operator

Install openshift-pipelines-operator using:
```
$ oc apply --kustomize openshift-pipelines-operator/base
```

Verify that the operator is running:

```
$ oc get pod --namespace openshift-compliance | grep compliance
openshift-pipelines-operator-9cdbbb854-rhzsx   1/1     Running   0          98s
```

## Using the OpenShift Compliance Operator

Check available profiles
```
$ oc get profiles.compliance -n openshift-compliance
NAME                 AGE
ocp4-cis             2m50s
ocp4-cis-node        2m50s
ocp4-e8              2m50s
ocp4-moderate        2m49s
ocp4-moderate-node   2m49s
ocp4-nerc-cip        2m49s
ocp4-nerc-cip-node   2m49s
ocp4-pci-dss         2m49s
ocp4-pci-dss-node    2m49s
rhcos4-e8            2m45s
rhcos4-moderate      2m45s
rhcos4-nerc-cip      2m45s
```

View the details of a profile
```
$ oc get profiles.compliance ocp4-cis -oyaml  -n openshift-compliance

apiVersion: compliance.openshift.io/v1alpha1
description: This profile defines a baseline that aligns to the Center for Internet
  Security® Red Hat OpenShift Container Platform 4 Benchmark™, V1.1. This profile
  includes Center for Internet Security® Red Hat OpenShift Container Platform 4 CIS
  Benchmarks™ content. Note that this part of the profile is meant to run on the Platform
  that Red Hat OpenShift Container Platform 4 runs on top of. This profile is applicable
  to OpenShift versions 4.6 and greater.
id: xccdf_org.ssgproject.content_profile_cis
kind: Profile
metadata:
  annotations:
    compliance.openshift.io/product: redhat_openshift_container_platform_4.1
    compliance.openshift.io/product-type: Platform
  labels:
    compliance.openshift.io/profile-bundle: ocp4
  name: ocp4-cis
  namespace: openshift-compliance
rules:
- ocp4-accounts-restrict-service-account-tokens
- ocp4-accounts-unique-service-account
- ocp4-api-server-admission-control-plugin-alwaysadmit
- ocp4-api-server-admission-control-plugin-alwayspullimages
- ocp4-api-server-admission-control-plugin-namespacelifecycle
- ocp4-api-server-admission-control-plugin-noderestriction
- ocp4-api-server-admission-control-plugin-scc
- ocp4-api-server-admission-control-plugin-securitycontextdeny
- ocp4-api-server-admission-control-plugin-serviceaccount
- ocp4-api-server-anonymous-auth
- ocp4-api-server-api-priority-flowschema-catch-all
- ocp4-api-server-api-priority-gate-enabled
- ocp4-api-server-api-priority-v1alpha1-flowschema-catch-all
- ocp4-api-server-audit-log-maxbackup
- ocp4-api-server-audit-log-maxsize
- ocp4-api-server-audit-log-path
- ocp4-api-server-auth-mode-no-aa
- ocp4-api-server-auth-mode-node
- ocp4-api-server-auth-mode-rbac
- ocp4-api-server-basic-auth
- ocp4-api-server-bind-address
- ocp4-api-server-client-ca
- ocp4-api-server-encryption-provider-cipher
- ocp4-api-server-encryption-provider-config
- ocp4-api-server-etcd-ca
- ocp4-api-server-etcd-cert
- ocp4-api-server-etcd-key
- ocp4-api-server-https-for-kubelet-conn
- ocp4-api-server-insecure-bind-address
- ocp4-api-server-insecure-port
- ocp4-api-server-kubelet-certificate-authority
- ocp4-api-server-kubelet-client-cert
- ocp4-api-server-kubelet-client-key
- ocp4-api-server-no-adm-ctrl-plugins-disabled
- ocp4-api-server-oauth-https-serving-cert
- ocp4-api-server-openshift-https-serving-cert
- ocp4-api-server-profiling-protected-by-rbac
- ocp4-api-server-request-timeout
- ocp4-api-server-service-account-lookup
- ocp4-api-server-service-account-public-key
- ocp4-api-server-tls-cert
- ocp4-api-server-tls-cipher-suites
- ocp4-api-server-tls-private-key
- ocp4-api-server-token-auth
- ocp4-audit-log-forwarding-enabled
- ocp4-audit-profile-set
- ocp4-configure-network-policies
- ocp4-configure-network-policies-namespaces
- ocp4-controller-insecure-port-disabled
- ocp4-controller-rotate-kubelet-server-certs
- ocp4-controller-secure-port
- ocp4-controller-service-account-ca
- ocp4-controller-service-account-private-key
- ocp4-controller-use-service-account
- ocp4-etcd-auto-tls
- ocp4-etcd-cert-file
- ocp4-etcd-client-cert-auth
- ocp4-etcd-key-file
- ocp4-etcd-peer-auto-tls
- ocp4-etcd-peer-cert-file
- ocp4-etcd-peer-client-cert-auth
- ocp4-etcd-peer-key-file
- ocp4-file-groupowner-proxy-kubeconfig
- ocp4-file-owner-proxy-kubeconfig
- ocp4-file-permissions-proxy-kubeconfig
- ocp4-general-apply-scc
- ocp4-general-configure-imagepolicywebhook
- ocp4-general-default-namespace-use
- ocp4-general-default-seccomp-profile
- ocp4-general-namespaces-in-use
- ocp4-idp-is-configured
- ocp4-kubeadmin-removed
- ocp4-kubelet-configure-tls-cert
- ocp4-kubelet-configure-tls-key
- ocp4-kubelet-disable-readonly-port
- ocp4-ocp-api-server-audit-log-maxbackup
- ocp4-ocp-api-server-audit-log-maxsize
- ocp4-openshift-api-server-audit-log-path
- ocp4-rbac-debug-role-protects-pprof
- ocp4-rbac-limit-cluster-admin
- ocp4-rbac-limit-secrets-access
- ocp4-rbac-pod-creation-access
- ocp4-rbac-wildcard-use
- ocp4-scc-drop-container-capabilities
- ocp4-scc-limit-container-allowed-capabilities
- ocp4-scc-limit-ipc-namespace
- ocp4-scc-limit-net-raw-capability
- ocp4-scc-limit-network-namespace
- ocp4-scc-limit-privilege-escalation
- ocp4-scc-limit-privileged-containers
- ocp4-scc-limit-process-id-namespace
- ocp4-scc-limit-root-containers
- ocp4-scheduler-no-bind-address
- ocp4-secrets-consider-external-storage
- ocp4-secrets-no-environment-variables
title: CIS Red Hat OpenShift Container Platform 4 Benchmark
```

View the rules within a desired profile:
```
$ oc get rules.compliance ocp4-accounts-restrict-service-account-tokens -oyaml -n openshift-compliance

apiVersion: compliance.openshift.io/v1alpha1
description: Service accounts tokens should not be mounted in pods except where the
  workload running in the pod explicitly needs to communicate with the API server.
  To ensure pods do not automatically mount tokens, set automountServiceAccountToken
  to false.
id: xccdf_org.ssgproject.content_rule_accounts_restrict_service_account_tokens
instructions: |-
  For each pod in the cluster, review the pod specification and
  ensure that pods that do not need to explicitly communicate with
  the API server have automountServiceAccountToken
  configured to false.
kind: Rule
metadata:
  annotations:
    compliance.openshift.io/rule: accounts-restrict-service-account-tokens
    control.compliance.openshift.io/CIS-OCP: 5.1.6
    control.compliance.openshift.io/NERC-CIP: CIP-003-8 R6;CIP-004-6 R3;CIP-007-3
      R6.1
    control.compliance.openshift.io/NIST-800-53: CM-6;CM-6(1)
    control.compliance.openshift.io/PCI-DSS: Req-2.2
    policies.open-cluster-management.io/controls: 5.1.6,CIP-003-8 R6,CIP-004-6 R3,CIP-007-3
      R6.1,CM-6,CM-6(1),Req-2.2
    policies.open-cluster-management.io/standards: CIS-OCP,NERC-CIP,NIST-800-53,PCI-DSS
  labels:
    compliance.openshift.io/profile-bundle: ocp4
  name: ocp4-accounts-restrict-service-account-tokens
  namespace: openshift-compliance
rationale: Mounting service account tokens inside pods can provide an avenue for privilege
  escalation attacks where an attacker is able to compromise a single pod in the cluster.
severity: medium
title: Restrict Automounting of Service Account Tokens

```
## Running compliance scans

 The Compliance Operator creates a ScanSetting object with reasonable defaults on startup. This ScanSetting object is named default.

 Inspect the ScanSetting object by running:

```sh
$ oc get  scansettings default -n openshift-compliance -o yaml

apiVersion: compliance.openshift.io/v1alpha1
kind: ScanSetting
metadata:
  name: default
  namespace: openshift-compliance
rawResultStorage:
  nodeSelector:
    node-role.kubernetes.io/master: ""
  pvAccessModes:
  - ReadWriteOnce
  rotation: 3
  size: 1Gi
  tolerations:
  - effect: NoSchedule
    key: node-role.kubernetes.io/master
    operator: Exists
  - effect: NoExecute
    key: node.kubernetes.io/not-ready
    operator: Exists
    tolerationSeconds: 300
  - effect: NoExecute
    key: node.kubernetes.io/unreachable
    operator: Exists
    tolerationSeconds: 300
  - effect: NoSchedule
    key: node.kubernetes.io/memory-pressure
    operator: Exists
roles:
- master
- worker
scanTolerations:
- operator: Exists
schedule: 0 1 * * *
showNotApplicable: false
strictNodeScan: true
```

Create the ScanSettingBinding object by running:
```sh
$ oc create -f compliance-scan/cis-compliance-ssb.yaml -n openshift-compliance
scansettingbinding.compliance.openshift.io/cis-compliance created
```

Follow the compliance scan progress by running:
```
$ oc get compliancescan -w -n openshift-compliance
ocp4-cis               DONE    NON-COMPLIANT
ocp4-cis-node-master   DONE    NON-COMPLIANT
ocp4-cis-node-worker   DONE    NON-COMPLIANT
```

## Check compliance scans results

To check the failed compliance scans results run the following:

```
$ oc get compliancecheckresults -l compliance.openshift.io/check-status=FAIL --no-headers -n openshift-compliance

ocp4-cis-api-server-encryption-provider-cipher                                 FAIL   medium
ocp4-cis-api-server-encryption-provider-config                                 FAIL   medium
ocp4-cis-api-server-no-adm-ctrl-plugins-disabled                               FAIL   medium
ocp4-cis-audit-log-forwarding-enabled                                          FAIL   medium
ocp4-cis-configure-network-policies-namespaces                                 FAIL   high
ocp4-cis-file-permissions-proxy-kubeconfig                                     FAIL   medium
ocp4-cis-kubeadmin-removed                                                     FAIL   medium
ocp4-cis-node-master-file-groupowner-ip-allocations                            FAIL   medium
ocp4-cis-node-master-file-groupowner-openshift-sdn-cniserver-config            FAIL   medium
ocp4-cis-node-master-file-owner-ip-allocations                                 FAIL   medium
ocp4-cis-node-master-file-owner-openshift-sdn-cniserver-config                 FAIL   medium
ocp4-cis-node-master-file-permissions-openshift-pki-cert-files                 FAIL   medium
ocp4-cis-node-master-file-permissions-openshift-pki-key-files                  FAIL   medium
ocp4-cis-node-master-kubelet-configure-event-creation                          FAIL   medium
ocp4-cis-node-master-kubelet-configure-tls-cipher-suites                       FAIL   medium
ocp4-cis-node-master-kubelet-enable-iptables-util-chains                       FAIL   medium
ocp4-cis-node-master-kubelet-enable-protect-kernel-defaults                    FAIL   medium
ocp4-cis-node-master-kubelet-enable-protect-kernel-sysctl                      FAIL   medium
ocp4-cis-node-master-kubelet-eviction-thresholds-set-hard-imagefs-available    FAIL   medium
ocp4-cis-node-master-kubelet-eviction-thresholds-set-hard-imagefs-inodesfree   FAIL   medium
ocp4-cis-node-master-kubelet-eviction-thresholds-set-hard-memory-available     FAIL   medium
ocp4-cis-node-master-kubelet-eviction-thresholds-set-hard-nodefs-available     FAIL   medium
ocp4-cis-node-master-kubelet-eviction-thresholds-set-hard-nodefs-inodesfree    FAIL   medium
ocp4-cis-node-master-kubelet-eviction-thresholds-set-soft-imagefs-available    FAIL   medium
ocp4-cis-node-master-kubelet-eviction-thresholds-set-soft-imagefs-inodesfree   FAIL   medium
ocp4-cis-node-master-kubelet-eviction-thresholds-set-soft-memory-available     FAIL   medium
ocp4-cis-node-master-kubelet-eviction-thresholds-set-soft-nodefs-available     FAIL   medium
ocp4-cis-node-master-kubelet-eviction-thresholds-set-soft-nodefs-inodesfree    FAIL   medium
ocp4-cis-node-worker-file-groupowner-ip-allocations                            FAIL   medium
ocp4-cis-node-worker-file-groupowner-openshift-sdn-cniserver-config            FAIL   medium
ocp4-cis-node-worker-file-owner-ip-allocations                                 FAIL   medium
ocp4-cis-node-worker-file-owner-openshift-sdn-cniserver-config                 FAIL   medium
ocp4-cis-node-worker-kubelet-configure-event-creation                          FAIL   medium
ocp4-cis-node-worker-kubelet-configure-tls-cipher-suites                       FAIL   medium
ocp4-cis-node-worker-kubelet-enable-iptables-util-chains                       FAIL   medium
ocp4-cis-node-worker-kubelet-enable-protect-kernel-defaults                    FAIL   medium
ocp4-cis-node-worker-kubelet-enable-protect-kernel-sysctl                      FAIL   medium
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-hard-imagefs-available    FAIL   medium
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-hard-imagefs-inodesfree   FAIL   medium
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-hard-memory-available     FAIL   medium
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-hard-nodefs-available     FAIL   medium
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-hard-nodefs-inodesfree    FAIL   medium
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-soft-imagefs-available    FAIL   medium
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-soft-imagefs-inodesfree   FAIL   medium
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-soft-memory-available     FAIL   medium
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-soft-nodefs-available     FAIL   medium
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-soft-nodefs-inodesfree    FAIL   medium
```

To review a single checkresult you can run:
```
$ oc get compliancecheckresult ocp4-cis-node-master-kubelet-enable-protect-kernel-sysctl -o yaml -n openshift-compliance | kubectl neat
apiVersion: compliance.openshift.io/v1alpha1
description: |-
  kubelet - Set Up Sysctl to Enable Protect Kernel Defaults
  Kernel parameters are usually tuned and hardened by the system administrators
  before putting the systems into production. These parameters protect the
  kernel and the system. Your kubelet kernel defaults that rely on such
  parameters should be appropriately set to match the desired secured system
  state. Ignoring this could potentially lead to running pods with undesired
  kernel behavior.
id: xccdf_org.ssgproject.content_rule_kubelet_enable_protect_kernel_sysctl
instructions: "Run the following command on the kubelet node to check if sysctl configuration
  file exist(s):\n$ sudo [ -f /etc/sysctl.d/90-kubelet.conf ] || echo Not Exists \nThe
  output should not return Not Exists.\n\nRun the following command on the kubelet
  node(s) to check parameter vm.panic_on_oom:\n$ sudo grep vm.panic_on_oom /etc/sysctl.d/90-kubelet.conf\nThe
  output should return a value.\n\nRun the following command on the kubelet node(s)
  to check parameter kernel.keys.root_maxbytes:\n$ sudo grep kernel.keys.root_maxbytes
  /etc/sysctl.d/90-kubelet.conf\nThe output should return a value.\n\nRun the following
  command on the kubelet node(s) to check parameter kernel.keys.root_maxkeys:\n$ sudo
  grep kernel.keys.root_maxkeys /etc/sysctl.d/90-kubelet.conf\nThe output should return
  a value.\n\nRun the following command on the kubelet node(s) to check parameter
  kernel.panic:\n$ sudo grep kernel.panic /etc/sysctl.d/90-kubelet.conf\nThe output
  should return a value.\n\nRun the following command on the kubelet node(s) to check
  parameter kernel.panic_on_oops:\n$ sudo grep kernel.panic_on_oops /etc/sysctl.d/90-kubelet.conf\nThe
  output should return a value.\n\nRun the following command on the kubelet node(s)
  to check parameter vm.overcommit_memory:\n$ sudo grep vm.overcommit_memory /etc/sysctl.d/90-kubelet.conf\nThe
  output should return a value.\n\nRun the following command on the kubelet node(s)
  to check parameter kernel.panic:\n$ sudo grep kernel.panic /etc/sysctl.d/90-kubelet.conf\nThe
  output should return a value."
kind: ComplianceCheckResult
metadata:
  annotations:
    compliance.openshift.io/rule: kubelet-enable-protect-kernel-sysctl
  labels:
    compliance.openshift.io/automated-remediation: ""
    compliance.openshift.io/check-severity: medium
    compliance.openshift.io/check-status: FAIL
    compliance.openshift.io/scan-name: ocp4-cis-node-master
    compliance.openshift.io/suite: cis-compliance
  name: ocp4-cis-node-master-kubelet-enable-protect-kernel-sysctl
  namespace: openshift-compliance
severity: medium

```

### Reviewing a remediation

Each ComplianceCheckResult represents a result of one compliance rule check. Unless requested, the remediations are not applied automatically, which gives an OpenShift Container Platform administrator the opportunity to review what the remediation does and only apply a remediation once it has been verified.

To get all the compliance remediations, run the following command:

```sh
$ oc get complianceremediation -n openshift-compliance

NAME                                                                             STATE
ocp4-cis-api-server-encryption-provider-cipher                                   NotApplied
ocp4-cis-api-server-encryption-provider-config                                   NotApplied
ocp4-cis-node-master-kubelet-configure-event-creation                            NotApplied
ocp4-cis-node-master-kubelet-configure-tls-cipher-suites                         NotApplied
ocp4-cis-node-master-kubelet-enable-iptables-util-chains                         NotApplied
ocp4-cis-node-master-kubelet-enable-protect-kernel-defaults                      NotApplied
ocp4-cis-node-master-kubelet-enable-protect-kernel-sysctl                        NotApplied
ocp4-cis-node-master-kubelet-eviction-thresholds-set-hard-imagefs-available      NotApplied
ocp4-cis-node-master-kubelet-eviction-thresholds-set-hard-imagefs-available-1    NotApplied
ocp4-cis-node-master-kubelet-eviction-thresholds-set-hard-imagefs-inodesfree     NotApplied
ocp4-cis-node-master-kubelet-eviction-thresholds-set-hard-imagefs-inodesfree-1   NotApplied
ocp4-cis-node-master-kubelet-eviction-thresholds-set-hard-memory-available       NotApplied
ocp4-cis-node-master-kubelet-eviction-thresholds-set-hard-memory-available-1     NotApplied
ocp4-cis-node-master-kubelet-eviction-thresholds-set-hard-nodefs-available       NotApplied
ocp4-cis-node-master-kubelet-eviction-thresholds-set-hard-nodefs-available-1     NotApplied
ocp4-cis-node-master-kubelet-eviction-thresholds-set-hard-nodefs-inodesfree      NotApplied
ocp4-cis-node-master-kubelet-eviction-thresholds-set-hard-nodefs-inodesfree-1    NotApplied
ocp4-cis-node-master-kubelet-eviction-thresholds-set-soft-imagefs-available      NotApplied
ocp4-cis-node-master-kubelet-eviction-thresholds-set-soft-imagefs-available-1    NotApplied
ocp4-cis-node-master-kubelet-eviction-thresholds-set-soft-imagefs-available-2    NotApplied
ocp4-cis-node-master-kubelet-eviction-thresholds-set-soft-imagefs-inodesfree     NotApplied
ocp4-cis-node-master-kubelet-eviction-thresholds-set-soft-imagefs-inodesfree-1   NotApplied
ocp4-cis-node-master-kubelet-eviction-thresholds-set-soft-imagefs-inodesfree-2   NotApplied
ocp4-cis-node-master-kubelet-eviction-thresholds-set-soft-memory-available       NotApplied
ocp4-cis-node-master-kubelet-eviction-thresholds-set-soft-memory-available-1     NotApplied
ocp4-cis-node-master-kubelet-eviction-thresholds-set-soft-memory-available-2     NotApplied
ocp4-cis-node-master-kubelet-eviction-thresholds-set-soft-nodefs-available       NotApplied
ocp4-cis-node-master-kubelet-eviction-thresholds-set-soft-nodefs-available-1     NotApplied
ocp4-cis-node-master-kubelet-eviction-thresholds-set-soft-nodefs-available-2     NotApplied
ocp4-cis-node-master-kubelet-eviction-thresholds-set-soft-nodefs-inodesfree      NotApplied
ocp4-cis-node-master-kubelet-eviction-thresholds-set-soft-nodefs-inodesfree-1    NotApplied
ocp4-cis-node-master-kubelet-eviction-thresholds-set-soft-nodefs-inodesfree-2    NotApplied
ocp4-cis-node-worker-kubelet-configure-event-creation                            NotApplied
ocp4-cis-node-worker-kubelet-configure-tls-cipher-suites                         NotApplied
ocp4-cis-node-worker-kubelet-enable-iptables-util-chains                         NotApplied
ocp4-cis-node-worker-kubelet-enable-protect-kernel-defaults                      NotApplied
ocp4-cis-node-worker-kubelet-enable-protect-kernel-sysctl                        NotApplied
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-hard-imagefs-available      NotApplied
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-hard-imagefs-available-1    NotApplied
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-hard-imagefs-inodesfree     NotApplied
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-hard-imagefs-inodesfree-1   NotApplied
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-hard-memory-available       NotApplied
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-hard-memory-available-1     NotApplied
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-hard-nodefs-available       NotApplied
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-hard-nodefs-available-1     NotApplied
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-hard-nodefs-inodesfree      NotApplied
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-hard-nodefs-inodesfree-1    NotApplied
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-soft-imagefs-available      NotApplied
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-soft-imagefs-available-1    NotApplied
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-soft-imagefs-available-2    NotApplied
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-soft-imagefs-inodesfree     NotApplied
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-soft-imagefs-inodesfree-1   NotApplied
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-soft-imagefs-inodesfree-2   NotApplied
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-soft-memory-available       NotApplied
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-soft-memory-available-1     NotApplied
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-soft-memory-available-2     NotApplied
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-soft-nodefs-available       NotApplied
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-soft-nodefs-available-1     NotApplied
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-soft-nodefs-available-2     NotApplied
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-soft-nodefs-inodesfree      NotApplied
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-soft-nodefs-inodesfree-1    NotApplied
ocp4-cis-node-worker-kubelet-eviction-thresholds-set-soft-nodefs-inodesfree-2    NotApplied
```

To review an specific compliance remediation, run the following command:

```
$ oc get complianceremediation ocp4-cis-node-master-kubelet-enable-protect-kernel-sysctl -o yaml -n openshift-compliance

apiVersion: compliance.openshift.io/v1alpha1
kind: ComplianceRemediation
metadata:
  labels:
    compliance.openshift.io/scan-name: ocp4-cis-node-master
    compliance.openshift.io/suite: cis-compliance
  name: ocp4-cis-node-master-kubelet-enable-protect-kernel-sysctl
  namespace: openshift-compliance
spec:
  apply: false
  current:
    object:
      apiVersion: machineconfiguration.openshift.io/v1
      kind: MachineConfig
      spec:
        config:
          ignition:
            version: 3.1.0
          storage:
            files:
            - contents:
                source: data:,vm.overcommit_memory%3D1%0Avm.panic_on_oom%3D0%0Akernel.panic%3D10%0Akernel.panic_on_oops%3D1%0Akernel.keys.root_maxkeys%3D1000000%0Akernel.keys.root_maxbytes%3D25000000
              mode: 420
              overwrite: true
              path: /etc/sysctl.d/90-kubelet.conf
  type: Configuration
```

### Applying a remediation

The boolean attribute spec.apply controls whether the remediation should be applied by the Compliance Operator. You can apply the remediation by setting the attribute to true:

```
$ oc patch complianceremediations/ocp4-cis-node-master-kubelet-enable-protect-kernel-sysctl --patch '{"spec":{"apply":true}}' --type=merge -n openshift-compliance
```

Check that the compliance remediation has been applied:

```
$ oc get complianceremediation ocp4-cis-node-master-kubelet-enable-protect-kernel-sysctl -n openshift-compliance
NAME                                                        STATE
ocp4-cis-node-master-kubelet-enable-protect-kernel-sysctl   Applied
```

Alternatively you could have configured the ScanSettingBinding to use the auto apply ScanSetting.

```
$ oc create -f compliance-scan/cis-compliance-ssb-auto-apply.yaml -n openshift-compliance
scansettingbinding.compliance.openshift.io/cis-compliance-auto-apply created
```
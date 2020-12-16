# Logs from `kritis-validation-hook-*` Pod

> log from `kritis-validation-hook-*` Pod after running `./no_attestation.sh`

I1216 19:06:55.263563       1 admission.go:172] Starting admission review handler
version: v0.2.2
commit: bea073f2a2f299af94363dc399b7780fde8f2afc
I1216 19:06:55.264929       1 admission.go:137] handling pod java in...
I1216 19:06:55.264962       1 admission.go:258] Reviewing images for &Pod{ObjectMeta:k8s_io_apimachinery_pkg_apis_meta_v1.ObjectMeta{Name:java,GenerateName:,Namespace:default,SelfLink:,UID:20bc6879-2368-4697-8469-bc7b65f02f7a,ResourceVersion:,Generation:0,CreationTimestamp:2020-12-16 19:06:55 +0000 UTC,DeletionTimestamp:<nil>,DeletionGracePeriodSeconds:nil,Labels:map[string]string{},Annotations:map[string]string{kubectl.kubernetes.io/last-applied-configuration: {"apiVersion":"v1","kind":"Pod","metadata":{"annotations":{},"name":"java","namespace":"default"},"spec":{"containers":[{"image":"gcr.io/kritis-tutorial/java-with-vulnz:latest","name":"java","ports":[{"containerPort":80}]}]}}
,},OwnerReferences:[],Finalizers:[],ClusterName:,Initializers:nil,},Spec:PodSpec{Volumes:[{default-token-z54gw {nil nil nil nil nil SecretVolumeSource{SecretName:default-token-z54gw,Items:[],DefaultMode:nil,Optional:nil,} nil nil nil nil nil nil nil nil nil nil nil nil nil nil nil nil nil nil nil nil nil}}],Containers:[{java gcr.io/kritis-tutorial/java-with-vulnz:latest [] []  [{ 0 80 TCP }] [] [] {map[] map[]} [{default-token-z54gw true /var/run/secrets/kubernetes.io/serviceaccount  <nil>}] [] nil nil nil /dev/termination-log File Always nil false false false}],RestartPolicy:Always,TerminationGracePeriodSeconds:*30,ActiveDeadlineSeconds:nil,DNSPolicy:ClusterFirst,NodeSelector:map[string]string{},ServiceAccountName:default,DeprecatedServiceAccount:default,NodeName:,HostNetwork:false,HostPID:false,HostIPC:false,SecurityContext:&PodSecurityContext{SELinuxOptions:nil,RunAsUser:nil,RunAsNonRoot:nil,SupplementalGroups:[],FSGroup:nil,RunAsGroup:nil,Sysctls:[],},ImagePullSecrets:[],Hostname:,Subdomain:,Affinity:nil,SchedulerName:default-scheduler,InitContainers:[],AutomountServiceAccountToken:nil,Tolerations:[{node.kubernetes.io/not-ready Exists  NoExecute 0xc000042500} {node.kubernetes.io/unreachable Exists  NoExecute 0xc000042550}],HostAliases:[],PriorityClassName:,Priority:*0,DNSConfig:nil,ShareProcessNamespace:nil,ReadinessGates:[],},Status:PodStatus{Phase:Pending,Conditions:[],Message:,Reason:,HostIP:,PodIP:,StartTime:<nil>,ContainerStatuses:[],QOSClass:BestEffort,InitContainerStatuses:[],NominatedNodeName:,},} in namespace default: [gcr.io/kritis-tutorial/java-with-vulnz:latest]
I1216 19:06:55.270790       1 admission.go:269] Found 1 Generic Attestation Policies
I1216 19:06:55.271835       1 review.go:68] Check if gcr.io/kritis-tutorial/java-with-vulnz:latest has valid Attestations.
I1216 19:06:55.271852       1 review.go:71] Validating against GenericAttestationPolicy my-gap
2020/12/16 19:06:55 http: panic serving 10.128.0.33:37814: runtime error: invalid memory address or nil pointer dereference
goroutine 131 [running]:
net/http.(*conn).serve.func1(0xc00014e000)
	/usr/local/go/src/net/http/server.go:1769 +0x139
panic(0x123a460, 0x212e600)
	/usr/local/go/src/runtime/panic.go:522 +0x1b5
github.com/grafeas/kritis/pkg/kritis/secrets.(*PgpKey).Fingerprint(...)
	/go/src/github.com/grafeas/kritis/pkg/kritis/secrets/pgpkey.go:69
github.com/grafeas/kritis/pkg/kritis/secrets.KeyAndFingerprint(0x0, 0x0, 0x472552, 0x1, 0x1583ae0, 0xc00054a4e0, 0x47214a, 0xc0001af9a0)
	/go/src/github.com/grafeas/kritis/pkg/kritis/secrets/pgpkey.go:127 +0x10b
github.com/grafeas/kritis/pkg/kritis/review.(*AttestorValidatingTransport).GetValidatedAttestations(0xc00013a000, 0xc00003ed20, 0x2d, 0xc00058a120, 0x14, 0x13c87e6, 0x11, 0x13be9c0)
	/go/src/github.com/grafeas/kritis/pkg/kritis/review/validating_transport.go:44 +0xaf
github.com/grafeas/kritis/pkg/kritis/review.Reviewer.findUnsatisfiedAuths(0xc000327a10, 0xc00003ed20, 0x2d, 0xc0000eedc0, 0x1, 0x1, 0x159f680, 0xc0003cdc60, 0x0, 0xc00009a710, ...)
	/go/src/github.com/grafeas/kritis/pkg/kritis/review/review.go:149 +0x203
github.com/grafeas/kritis/pkg/kritis/review.Reviewer.ReviewGAP(0xc000327a10, 0xc0003c4230, 0x1, 0x1, 0xc000262a20, 0x1, 0x1, 0xc0003a4380, 0x159f680, 0xc0003cdc60, ...)
	/go/src/github.com/grafeas/kritis/pkg/kritis/review/review.go:77 +0x24c
github.com/grafeas/kritis/pkg/kritis/admission.reviewGenericAttestationPolicy(0xc0003c4230, 0x1, 0x1, 0xc000042474, 0x7, 0xc0003a4380, 0xc0002c70b0, 0xc000262a20, 0x1, 0x1, ...)
	/go/src/github.com/grafeas/kritis/pkg/kritis/admission/admission.go:318 +0x2b5
github.com/grafeas/kritis/pkg/kritis/admission.reviewImages(0xc0003c4230, 0x1, 0x1, 0xc000042474, 0x7, 0xc0003a4380, 0xc0002c70b0, 0xc0003ec570)
	/go/src/github.com/grafeas/kritis/pkg/kritis/admission/admission.go:270 +0x849
github.com/grafeas/kritis/pkg/kritis/admission.reviewPod(0xc0003a4380, 0xc0002c70b0, 0xc0003ec570)
	/go/src/github.com/grafeas/kritis/pkg/kritis/admission/admission.go:336 +0x1f1
github.com/grafeas/kritis/pkg/kritis/admission.handlePod(0xc0002c6f30, 0xc0002c70b0, 0xc0003ec570, 0xc00003c901, 0x18)
	/go/src/github.com/grafeas/kritis/pkg/kritis/admission/admission.go:138 +0x148
github.com/grafeas/kritis/pkg/kritis/admission.ReviewHandler(0x15acb00, 0xc0003921c0, 0xc00010a600, 0xc0003ec570)
	/go/src/github.com/grafeas/kritis/pkg/kritis/admission/admission.go:213 +0x391
main.main.func1(0x15acb00, 0xc0003921c0, 0xc00010a600)
	/go/src/github.com/grafeas/kritis/cmd/kritis/admission/main.go:138 +0x48
net/http.HandlerFunc.ServeHTTP(0xc000438160, 0x15acb00, 0xc0003921c0, 0xc00010a600)
	/usr/local/go/src/net/http/server.go:1995 +0x44
net/http.(*ServeMux).ServeHTTP(0x21479a0, 0x15acb00, 0xc0003921c0, 0xc00010a600)
	/usr/local/go/src/net/http/server.go:2375 +0x1d6
net/http.serverHandler.ServeHTTP(0xc0003f3e10, 0x15acb00, 0xc0003921c0, 0xc00010a600)
	/usr/local/go/src/net/http/server.go:2774 +0xa8
net/http.(*conn).serve(0xc00014e000, 0x15b4f40, 0xc000374380)
	/usr/local/go/src/net/http/server.go:1878 +0x851
created by net/http.(*Server).Serve
	/usr/local/go/src/net/http/server.go:2884 +0x2f4

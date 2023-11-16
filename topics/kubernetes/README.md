# Kubernetes

<!-- {% raw %} -->

What's your goal?

* I would like to prepare for CKA certification
  * See [CKA](CKA.md) page
* I would like to learn Kubernetes by practicing both theoritcal and practical material
  * Solve [exercises](#kubernetes-exercises)
  * Solve [questions](#kubernetes-questions)
* I would like to learn practical Kubernetes
  * Solve [exercises](#kubernetes-exercises)

- [Kubernetes](#kubernetes)
  - [Kubernetes Exercises](#kubernetes-exercises)
    - [Pods](#pods)
    - [Service](#service)
    - [ReplicaSet](#replicaset)
    - [Labels and Selectors](#labels-and-selectors)
    - [Scheduler](#scheduler)
    - [Kustomize](#kustomize)
  - [Kubernetes Questions](#kubernetes-questions)
    - [Kubernetes 101](#kubernetes-101)
    - [클러스터 및 아키텍처](#클러스터-및-아키텍처)
      - [Kubelet](#kubelet)
      - [노드 명령어](#노드-명령어)
    - [Pods](#pods-1)
      - [정적 Pods](#정적-pods)
      - [Pods 명령](#pods-명령)
      - [Pods 문제 해결 및 디버깅](#pods-문제-해결-및-디버깅)
    - [레이블과 선택기](#레이블과-선택기)
    - [Deployments](#deployments)
      - [Deployments Commands](#deployments-commands)
    - [Services](#services)
    - [Ingress](#ingress)
    - [ReplicaSets](#replicasets)
    - [DaemonSet](#daemonset)
      - [DaemonSet - 명령어](#daemonset---명령어)
    - [StatefulSet](#statefulset)
    - [저장소](#저장소)
      - [볼륨](#볼륨)
    - [네트워킹](#네트워킹)
    - [Namespaces](#namespaces)
      - [네임스페이스 - 명령어](#네임스페이스---명령어)
      - [리소스 쿼터](#리소스-쿼터)
    - [Operators](#operators)
    - [Secrets](#secrets)
    - [Volumes](#volumes)
    - [접근 제어](#접근-제어)
    - [Patterns](#patterns)
    - [CronJob](#cronjob)
    - [기타](#기타)
    - [Gatekeeper](#gatekeeper)
    - [정책 테스트](#정책-테스트)
    - [헬름](#헬름)
      - [명령어](#명령어)
    - [보안](#보안)
    - [문제 해결 시나리오](#문제-해결-시나리오)
    - [Istio](#istio)
    - [컨트롤러](#컨트롤러)
    - [스케줄러](#스케줄러)
      - [노드 선호도](#노드-선호도)
    - [Taints](#taints)
    - [리소스 제한](#리소스-제한)
      - [리소스 제한 - 명령어](#리소스-제한---명령어)
    - [모니터링](#모니터링)
    - [Kustomize](#kustomize-1)
    - [Deployment Strategies](#deployment-strategies)
    - [시나리오](#시나리오)

## Kubernetes Exercises

### Pods

|Name|Topic|Objective & Instructions|Solution|Comments|
|--------|--------|------|----|----|
| My First Pod | Pods | [Exercise](pods_01.md) | [Solution](solutions/pods_01_solution.md)
| "Killing" Containers | Pods | [Exercise](killing_containers.md) | [Solution](solutions/killing_containers.md)

### Service

|Name|Topic|Objective & Instructions|Solution|Comments|
|--------|--------|------|----|----|
| Creating a Service | Service | [Exercise](services_01.md) | [Solution](solutions/services_01_solution.md)

### ReplicaSet

|Name|Topic|Objective & Instructions|Solution|Comments|
|--------|--------|------|----|----|
| Creating a ReplicaSet | ReplicaSet | [Exercise](replicaset_01.md) | [Solution](solutions/replicaset_01_solution.md)
| Operating ReplicaSets | ReplicaSet | [Exercise](replicaset_02.md) | [Solution](solutions/replicaset_02_solution.md)
| ReplicaSets Selectors | ReplicaSet | [Exercise](replicaset_03.md) | [Solution](solutions/replicaset_03_solution.md)

### Labels and Selectors

|Name|Topic|Objective & Instructions|Solution|Comments|
|--------|--------|------|----|----|
| Labels and Selectors 101 | Labels, Selectors | [Exercise](exercises/labels_and_selectors/exercise.md) | [Solution](exercises/labels_and_selectors/solution.md)
| Node Selectors | Labels, Selectors | [Exercise](exercises/node_selectors/exercise.md) | [Solution](exercises/node_selectors/solution.md)


### Scheduler

|Name|Topic|Objective & Instructions|Solution|Comments|
|--------|--------|------|----|----|
| Taints 101 | Taints | [Exercise](exercises/taints_101/exercise.md) | [Solution](exercises/taints_101/solution.md)

### Kustomize

|Name|Topic|Objective & Instructions|Solution|Comments|
|--------|--------|------|----|----|
| common labels | Kustomize | [Exercise](exercises/kustomize_common_labels/exercise.md) | [Solution](exercises/kustomize_common_labels/solution.md)

## Kubernetes Questions

### Kubernetes 101

<details>
<summary>쿠버네티스란 무엇인가? 왜 조직들이 이를 사용하나요?</summary><br><b>

쿠버네티스는 컨테이너화된 애플리케이션을 관리, 확장 및 배포할 수 있는 기능을 제공하는 오픈 소스 시스템입니다.

쿠버네티스가 어떤 점에서 좋은지 이해하기 위해 몇 가지 예를 들어보겠습니다:

* 특정 애플리케이션을 여러 위치에서 컨테이너로 실행하는데, 실행하는 위치에 상관없이 모든 변경사항을 동기화하고 싶을 때
* 수백 개의 컨테이너를 업데이트하고 변경할 때
* 현재 부하에 따라 확장(혹은 축소)이 필요한 경우

</b></details>

<details>
<summary>쿠버네티스를 사용하지 않는 경우는 언제인가요?</summary><br><b>

  - 저수준 인프라나 베어메탈을 관리하는 경우, 쿠버네티스는 필요하지 않거나 원하는 것이 아닐 수 있습니다
  - 엔지니어가 20명 미만이고 컨테이너가 일 년에 몇 개 미만인 소규모 팀의 경우, 쿠버네티스는 과할 수 있습니다(확장이 필요하더라도, 업데이트를 진행해야 하는 경우 등). 매니지드 쿠버네티스를 사용하는 것은 좋을 수 있지만, 채택하기 전에 신중하게 생각해야 합니다.

</b></details>

<details>
<summary>쿠버네티스의 주요 기능은 무엇인가요?</summary><br><b>

  - 자가 복구: 쿠버네티스는 컨테이너의 상태를 모니터링하고 실패나 기타 이벤트가 발생하면 특정 조치를 취합니다, 예를 들어 컨테이너를 재시작합니다
  - 로드 밸런싱: 쿠버네티스는 클러스터에서 실행되는 애플리케이션에 대한 요청을 애플리케이션을 실행하는 파드의 상태에 따라 분할하거나 균형을 맞출 수 있습니다
  - 오퍼레이터: 클러스터 API를 사용하여 애플리케이션 상태를 업데이트하고 이벤트 및 애플리케이션 상태 변경에 따라 조치를 취할 수 있는 패키지화된 쿠버네티스 애플리케이션
  - 자동 롤아웃: 애플리케이션에 대한 점진적 업데이트를 지원하고 문제가 발생한 경우 롤백을 지원합니다
  - 스케일링: 다양한 상태 매개변수 및 사용자 정의 기준에 따라 수평적으로(아래로 및 위로) 확장합니다
  - 시크릿: 사용자 이름, 비밀번호 및 서비스 엔드포인트를 프라이빗하게 저장할 수 있는 메커니즘을 제공합니다. 클러스터를 사용하는 모든 사람이 볼 수 있는 것은 아닙니다

</b></details>

<details>
<summary>쿠버네티스 오브젝트에는 어떤 것들이 있나요?</summary><br><b>

  * 파드(Pod)
  * 서비스(Service)
  * 복제 컨트롤러(ReplicationController)
  * 복제 세트(ReplicaSet)
  * 데몬 세트(DaemonSet)
  * 네임스페이스(Namespace)
  * 설정 맵(ConfigMap)
  ...
</b></details>

<details>
<summary>쿠버네티스 오브젝트에서 필수적인 필드는 무엇인가요?</summary><br><b>

메타데이터(metadata), 종류(kind) 및 API 버전(apiVersion)

</b></details>

<details>
<summary>kubectl이란 무엇인가요?</summary><br><b>

Kubectl은 쿠버네티스 클러스터에 대한 명령을 실행할 수 있게 해주는 쿠버네티스 명령 줄 도구입니다. 예를 들어, kubectl을 사용하여 애플리케이션을 배포하고, 클러스터 리소스를 검사 및 관리하며, 로그를 확인할 수 있습니다.

</b></details>

<details>
<summary>쿠버네티스에서 애플리케이션을 배포할 때 일반적으로 사용하는 쿠버네티스 오브젝트는 무엇인가요?</summary><br><b>

* 배포(Deployment) - 파드를 생성( )하고 감시합니다
* 서비스(Service): 내부적으로 파드로 트래픽을 라우팅합니다
* 인그레스(Ingress): 클러스터 외부에서 트래픽을 라우팅합니다

</b></details>

<details>
<summary>쿠버네티스에서 다음과 같은 명령이 없는 이유는 무엇인가요? <code>kubectl get containers</code></summary><br><b>

컨테이너는 쿠버네티스 오브젝트가 아니기 때문입니다. 쿠버네티스에서 가장 작은 오브젝트 단위는 파드입니다. 하나의 파드에는 하나 이상의 컨테이너가 있을 수 있습니다.

</b></details>

<details>
<summary>쿠버네티스와 관련하여 어떤 작업이나 조작을 모범 사례로 간주하나요?</summary><br><b>

  - 항상 쿠버네티스 YAML 파일이 유효한지 확인하세요. 자동화된 검사 및 파이프라인을 적용하는 것이 권장됩니다.
  - 컨테이너가 클러스터 메모리 전체를 사용하는 상황을 방지하기 위해 항상 요청과 제한을 지정하세요
  - 파드, 배포 등을 논리적으로 그룹화하기 위해 레이블을 지정하세요. 예를 들어, 애플리케이션의 유형을 식별하는 데 레이블을 사용할 수 있습니다

</b></details>

### 클러스터 및 아키텍처

<details>
<summary>쿠버네티스 클러스터란 무엇인가?</summary><br><b>

레드햇 정의: "쿠버네티스 클러스터는 컨테이너화된 애플리케이션을 실행하기 위한 노드 기계들의 집합입니다. 쿠버네티스를 실행하고 있다면, 클러스터를 실행하고 있는 것입니다.
최소한, 클러스터에는 워커 노드와 마스터 노드가 포함되어 있습니다."

더 읽어보기 [여기](https://www.redhat.com/en/topics/containers/what-is-a-kubernetes-cluster)
</b></details>

<details>
<summary>노드란 무엇인가?</summary><br><b>

노드는 애플리케이션을 실행하는 데 사용되는 가상 또는 물리적 기계입니다.<br>
생산 환경에서는 최소 3개의 노드를 갖는 것이 권장됩니다.
</b></details>

<details>
<summary>마스터 노드의 역할은 무엇인가?</summary><br><b>

마스터는 클러스터의 모든 워크플로우를 조정합니다:

* 애플리케이션 스케줄링
* 원하는 상태 관리
* 새로운 업데이트 배포

</b></details>

<details>
<summary><code>kubectl get nodes</code>를 실행할 때 간단하고 고수준으로 무슨 일이 일어나는지 설명하라</summary><br><b>

1. 사용자 인증이 이루어집니다
2. kube-apiserver에 의해 요청이 검증됩니다
3. etcd에서 데이터가 검색됩니다
</b></details>

<details>
<summary>참 또는 거짓? 모든 클러스터는 0개 이상의 마스터 노드와 최소 1개의 워커를 가져야 한다</summary><br><b>

거짓. 쿠버네티스 클러스터는 최소 1개의 마스터를 포함하며, 0개의 워커를 가질 수 있습니다 (비록 그렇게 하면 별로 유용하지 않겠지만...)

</b></details> 

<details>
<summary>마스터 노드(또는 제어 평면)의 구성 요소는 무엇인가?</summary><br><b>

  * API 서버 - 쿠버네티스 API. 모든 클러스터 구성 요소가 이를 통해 통신합니다
  * 스케줄러 - 애플리케이션을 실행할 수 있는 워커 노드에 할당합니다
  * 컨트롤러 매니저 - 클러스터 유지 관리(복제, 노드 장애 등)
  * etcd - 클러스터 구성을 저장합니다

</b></details>

<details>
<summary>워커 노드(데이터 플레인으로도 알려짐)의 구성 요소는 무엇인가?</summary><br><b>

  * Kubelet - 마스터와 노드 간의 통신을 담당하는 에이전트.
  * Kube-proxy - 앱 구성 요소 간의 트래픽을 로드 밸런싱
  * 컨테이너 런타임 - 컨테이너(포드맨, 도커 등)를 실행하는 엔진

</b></details>

<details>
<summary>그림 속 이미지 오른쪽에 구성 요소들을 적절한 위치에 배치하시오<br>
<img src="images/cluster_architecture_exercise.png"/>
</summary><br><b>
<img src="images/cluster_architecture_solution.png"/>

</b></details>

<details>
<summary>여러 쿠버네티스 클러스터를 관리하는 중에, kubectl을 사용하여 클러스터 간에 빠르게 전환하는 방법은?</summary><br><b>

`kubectl config use-context`
</b></details>

<details>
<summary>쿠버네티스 클러스터에서 메모리 사용량이 높아지는 것을 어떻게 방지하며, 메모리 누수나 OOM과 같은 문제를 방지할 수 있나요?</summary><br><b>

요청과 제한을 적용하며, 특히 불확실성이 더 큰 타사 애플리케이션에 대해서 적용합니다.
</b></details>

<details>
<summary>쿠버네티스 클러스터를 배포하는 경험이 있습니까? 있다면, 그 과정을 고수준에서 설명할 수 있나요?</summary><br><b>

1. 쿠버네티스 노드/워커로 사용될 여러 인스턴스를 생성합니다. 마스터로 작동할 인스턴스도 생성합니다. 인스턴스는 클라우드에 프로비저닝되거나 베어 메탈 호스트의 가상 머신일 수 있습니다.
2. 쿠버네티스 클러스터의 다양한 구성 요소(kubelet, etcd, ...)에 사용될 TLS 인증서를 생성할 인증 기관을 프로비저닝합니다.
  1. 다양한 구성 요소에 대한 인증서와 개인 키를 생성합니다.
3. 쿠버네티스의 다양한 클라이언트가 API 서버를 찾고 인증할 수 있도록 kubeconfig를 생성합니다.
4. 클러스터 데이터 암호화에 사용될 암호화 키를 생성합니다.
5. etcd 클러스터를 생성합니다.
</b></details>

<details>
<summary>클러스터의 모든 오브젝트 유형을 나열하는 명령어는 무엇인가?</summary><br><b>

`kubectl api-resources`
</b></details>

<details>
<summary><code>kubectl get componentstatus</code> 명령어는 무엇을 하는가?</summary><br><b>

제어 평면 구성 요소의 각각의 상태를 출력합니다.
</b></details>

#### Kubelet

<details>
<summary>워커 노드에서 Kubelet을 중지하면 실행 중인 파드에 어떤 일이 발생합니까?</summary><br><b>

</b></details>

#### 노드 명령어

<details>
<summary>클러스터의 모든 노드를 보는 명령어를 실행하시오</summary><br><b>

`kubectl get nodes`

Note: You might want to create an alias (`alias k=kubectl`) and get used to `k get no`
</b></details>

<details>
<summary>Create a list of all nodes in JSON format and store it in a file called "some_nodes.json"</summary><br><b>

`k get nodes -o json > some_nodes.json`
</b></details>

<details>
<summary>Check what labels one of your nodes in the cluster has</summary><br><b>

`k get no minikube --show-labels`
</b></details>

### Pods

<details>
<summary>파드란 무엇인가</summary><br><b>

파드는 공유 스토리지와 네트워크 리소스를 가지고, 컨테이너를 실행하는 방법에 대한 명세를 가진 하나 이상의 컨테이너들의 그룹입니다.

파드는 쿠버네티스에서 생성하고 관리할 수 있는 가장 작은 배포 가능한 컴퓨팅 단위입니다.

</b></details>

<details>
<summary>"my-pod"라는 이름의 파드를 nginx:alpine 이미지를 사용하여 배포하시오</summary><br><b>

`kubectl run my-pod --image=nginx:alpine`

쿠버네티스 초보자라면, 파드를 실행하는 일반적인 방법이 아니라는 것을 알아야 합니다. 일반적인 방법은 파드를 실행하는 디플로이먼트를 실행하는 것입니다.

또한, 파드와/또는 디플로이먼트는 일반적으로 CLI 인자만을 사용하여 직접 실행하기보다는 파일에서 정의됩니다.
</b></details>

<details>
<summary>"파드는 직접 생성되지 않는다"에 대한 당신의 생각은 무엇인가?</summary><br><b>

파드는 실제로 대부분 직접 생성되지 않습니다. 파드가 디플로이먼트나 레플리카셋과 같은 다른 엔티티의 일부로 생성되는 것을 보게 될 것입니다.

파드가 죽으면, 쿠버네티스는 그것을 다시 데려오지 않습니다. 이것이 특정 파드가 죽은 후에도 일정 수의 파드가 항상 실행되도록 하는 레플리카셋을 정의하는 것이 더 유용한 이유입니다.
</b></details>

<details>
<summary>한 파드에 몇 개의 컨테이너가 들어갈 수 있는가?</summary><br><b>

파드는 여러 컨테이너를 포함할 수 있지만 대부분의 경우 한 파드 당 하나의 컨테이너가 될 것입니다.

로깅이나 앱 컨테이너와 동일한 파드에서 실행되는 다른 작업을 수행하기 위해 "사이드카" 패턴과 같은 여러 컨테이너를 실행하는 패턴이 있습니다.
</b></details>

<details>
<summary>단일 파드에서 여러 컨테이너를 실행하는 사용 사례는 무엇인가?</summary><br><b>

웹 애플리케이션은 별도의 (= 각자의 컨테이너에 있는) 로깅 및 모니터링 구성 요소/어댑터를 가질 수 있습니다.<br>
예를 들어, 테크톤(Tekton)을 사용하는 CI/CD 파이프라인은 작업(Task)이 여러 명령을 포함하는 경우 한 파드에서 여러 컨테이너를 실행할 수 있습니다.
</b></details>

<details>
<summary>가능한 파드 상태는 무엇인가?</summary><br><b>

  * Running - 파드가 노드에 바인딩되고 최소한 하나의 컨테이너가 실행 중
  * Failed/Error - 파드 내 최소한 하나의 컨테이너가 실패로 종료됨
  * Succeeded - 파드 내 모든 컨테이너가 성공적으로 종료됨
  * Unknown - 파드의 상태를 확인할 수 없음
  * Pending - 컨테이너가 아직 실행 중이지 않음 (아직 이미지가 다운로드 중이거나 파드가 아직 스케줄되지 않은 경우)
</b></details>

<details>
<summary>참 또는 거짓? 기본적으로 파드는 고립되어 있으며, 이는 어떠한 소스로부터도 트래픽을 받을 수 없다는 의미이다</summary><br><b>

거짓. 기본적으로 파드는 비고립 상태이며, 모든 소스로부터의 트래픽을 허용합니다.
</b></details>

<details>
<summary>참 또는 거짓? "Pending" 상태는 파드가 아직 쿠버네티스 클러스터에 의해 수락되지 않았으며, 스케줄러는 수락되지 않는 한 실행할 수 없다는 의미이다</summary><br><b>

거짓. "Pending"은 파드가 클러스터에 의해 이미 수락된 후지만, 이미지가 아직 다운로드되지 않았거나 파드가 아직 스케줄되지 않은 다른 이유로 컨테이너를 실행할 수 없는 상태를 의미합니다.
</b></details>

<details>
<summary>참 또는 거짓? 단일 파드는 여러 노드에 걸쳐 분할될 수 있다</summary><br><b>

거짓. 단일 파드는 단일 노드에서만 실행될 수 있습니다.
</b></details>

<details>
<summary>파드를 실행하고 <code>ContainerCreating</code> 상태를 본다면?</summary><br><b>
</b></details>

<details>
<summary>참 또는 거짓? 파드에서 정의된 볼륨은 해당 파드의 모든 컨테이너에서 접근할 수 있다</summary><br><b>

참.
</b></details>

<details>
<summary>파드를 kubectl로 실행하면 무슨 일이 일어나는가?</summary><br><b>

1. Kubectl은 API 서버(kube-apiserver)에 파드를 생성하라는 요청을 보냅니다
   1. 이 과정에서 사용자는 인증을 받고 요청이 검증됩니다.
   2. etcd가 데이터로 업데이트됩니다.
2. 스케줄러는 API 서버를 모니터링하면서 할당되지 않은 파드를 감지합니다(kube-apiserver)
3. 스케줄러는 파드를 할당할 노드를 선택합니다
   1. etcd가 정보로 업데이트됩니다
4. 스케줄러는 어떤 노드를 선택했는지 API 서버에 업데이트합니다
5. Kubelet(역시 API 서버를 모니터링)은 동일한 노드에 할당되었지만 아직 실행되지 않은 파드가 있음을 알아차립니다
6. Kubelet은 컨테이너 엔진(예: Docker)에 컨테이너를 생성하고 실행하라는 요청을 보냅니다
7. Kubelet은 API 서버에 업데이트를 보내 파드가 실행 중임을 알립니다
   1. API 서버가 다시 etcd를 업데이트합니다
</b></details>

<details>
<summary>`kubectl run web --image nginxinc/nginx-unprivileged` 명령을 실행한 후 컨테이너가 실행 중인지 확인하는 방법</summary><br><b>

* `kubectl describe pods <POD_NAME>`을 실행하면 컨테이너가 실행 중인지 알 수 있습니다:
`상태:       실행 중`
* 컨테이너 내부에서 명령을 실행합니다: `kubectl exec web -- ls`
</b></details>

<details>
<summary>`kubectl run database --image mongo`를 실행한 후 상태가 "CrashLoopBackOff"로 표시된다면, 어떤 문제가 발생했을 수 있고 어떻게 확인하나요?</summary><br><b>

"CrashLoopBackOff"는 Pod가 시작되었다가 충돌하고, 다시 시작하는 것을 반복한다는 것을 의미합니다.<br>
이 오류가 발생하는 이유는 여러 가지가 있습니다 - 권한 부족, init 컨테이너 설정 오류, 영구 볼륨 연결 문제 등.

이 문제가 발생한 이유를 확인하는 방법 중 하나는 `kubectl describe po <POD_NAME>`를 실행해 종료 코드를 확인하는 것입니다.

```yaml
 Last State:     Terminated
   Reason:       Error
   Exit Code:    100
```

다른 방법으로는 `kubectl logs <POD_NAME>`를 실행하는 것입니다. 이렇게 하면 해당 Pod에서 실행 중인 컨테이너의 로그를 볼 수 있습니다.
</b></details>

<details>
<summary>다음 줄의 목적을 설명하시오

```yaml
livenessProbe:
  exec:
    command:
    - cat
    - /appStatus
  initialDelaySeconds: 10
  periodSeconds: 5
```
</summary><br><b>

이 줄들은 `liveness probe`를 사용합니다. 이것은 컨테이너가 원치 않는 상태에 도달했을 때 컨테이너를 재시작하는 데 사용됩니다.<br>
이 경우, `cat /appStatus` 명령이 실패하면 쿠버네티스는 컨테이너를 종료하고 재시작 정책을 적용합니다. `initialDelaySeconds: 10`은 kubelet이 처음으로 명령/프로브를 실행하기 전에 10초를 기다린다는 것을 의미합니다. 그 후로는 `periodSeconds`로 정의된 대로 5초마다 실행됩니다.
</b></details>

<details>
<summary>다음 줄의 목적을 설명하시오

```yaml
readinessProbe:
      tcpSocket:
        port: 2017
      initialDelaySeconds: 15
      periodSeconds: 20
```
</summary><br><b>

이들은 readiness probe를 정의하는데, 여기서 Pod는 컨테이너의 2017 포트에 연결할 수 있게 되기 전까지 "Ready"로 표시되지 않습니다. 첫 번째 체크/프로브는 컨테이너가 실행을 시작한 후 15초 후에 시작되며, 정의된 포트에 연결할 수 있을 때까지 20초마다 체크/프로브를 계속 실행합니다.
</b></details>

<details>
<summary>Pod의 "ErrImagePull" 상태는 무엇을 의미하나요?</summary><br><b>

컨테이너를 실행하기 위해 지정된 이미지를 가져오지 못했습니다. 예를 들어, 클라이언트가 인증하지 않은 경우에 이런 일이 발생할 수 있습니다.<br>
더 자세한 내용은 `kubectl describe po <POD_NAME>`로 확인할 수 있습니다.
</b></details>

<details>
<summary>Pod를 삭제하면 어떤 일이 발생하나요?</summary><br><b>

1. 주어진 Pod의 컨테이너 내부의 주 프로세스를 종료하기 위해 `TERM` 신호가 전송됩니다.
2. 각 컨테이너는 프로세스를 우아하게 종료하기 위해 30초의 시간을 갖습니다.
3. 만일 유예 기간이 만료되면, `KILL` 신호가 프로세스를 강제로 종료시키고 컨테이너도 종료됩니다.
</b></details>

<details>
<summary>liveness probes를 설명하시오</summary><br><b>

Liveness probes는 사용자가 정의한 특정 체크/프로브가 실패했을 때 컨테이너를 재시작하는 유용한 메커니즘입니다.<br>
예를 들어, 사용자는 `cat /app/status` 명령이 X초마다 실행되도록 정의하고, 이 명령이 실패하는 순간 컨테이너가 재시작되도록 할 수 있습니다.

자세한 내용은 [kubernetes.io](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes)에서 읽어볼 수 있습니다.
</b></details>

<details>
<summary>Readiness probes를 설명하시오</summary><br><b>

Readiness probes는 Kubelet이 컨테이너가 실행 준비가 되었고, 트래픽을 받을 준비가 되었을 때를 알기 위해 사용됩니다.<br>
예를 들어, Readiness probes는 컨테이너의 8080 포트에 연결하는 것일 수 있습니다. Kubelet이 연결에 성공하면, Pod는 준비 상태로 표시됩니다.

자세한 내용은 [kubernetes.io](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes)에서 읽어볼 수 있습니다.
</b></details>

<details>
<summary>서비스와 결합될 때 readiness probe 상태가 서비스에 어떤 영향을 미치나요?</summary><br><b>

성공 상태로 설정된 컨테이너만이 서비스로 전송된 요청을 받을 수 있습니다.
</b></details>

<details>
<summary>대부분의 경우에 Pod당 하나의 컨테이너만 있는 이유는 무엇인가요?</summary><br><b>

하나의 이유는 주어진 Pod의 컨테이너 중 하나만 확장해야 할 때 확장하기가 더 어렵기 때문입니다.
</b></details>

<details>
<summary>참 또는 거짓? Pod가 한 번 작업 노드에 할당되면, 해당 노드에서만 실행되며, 어떤 지점에서 실패하고 새로운 Pod가 생성되더라도 동일한 노드에서만 실행됩니다.</summary><br><b>

참.
</b></details>

<details>
<summary>참 또는 거짓? 생성될 때마다 각 Pod는 자신만의 공개 IP 주소를 갖습니다.</summary><br><b>

거짓. 각 Pod는 IP 주소를 받지만 내부 IP이며 공개적으로 접근할 수 없습니다.

Pod를 외부에서 접근 가능하게 하려면 쿠버네티스에서 Service라는 객체를 사용해야 합니다.
</b></details>

#### 정적 Pods

<details>
<summary>정적 Pods란 무엇인가요?</summary><br><b>

[Kubernetes.io](https://kubernetes.io/docs/tasks/configure-pod-container/static-pod/): "정적 Pods는 API 서버가 관찰하지 않고 특정 노드의 kubelet 데몬에 의해 직접 관리됩니다. 컨트롤 플레인(예: Deployment)에 의해 관리되는 Pods와 달리, 정적 Pod은 kubelet이 감시하고 실패하면 재시작합니다."
</b></details>

<details>
<summary>참 또는 거짓? "정적 Pods"가 있듯이 "deployments" 및 "replicasets"와 같은 다른 정적 리소스도 있습니다.</summary><br><b>

거짓.
</b></details>

<details>
<summary>정적 Pods를 사용하는 몇 가지 사례는 무엇인가요?</summary><br><b>

한 가지 분명한 사례는 컨트롤 플레인 Pods를 실행하는 것입니다 - kube-apiserver, 스케줄러 등과 같은 Pods를 실행합니다. 이러한 Pods는 클러스터의 일부 구성 요소가 작동하지 않더라도 실행되고 운영되어야 하며, 클러스터의 특정 노드에서 실행되어야 합니다.
</b></details>

<details>
<summary>어떤 Pods가 정적 Pods인지 어떻게 확인하나요?</summary><br><b>

Pod의 접미사가 실행되는 노드의 이름과 동일합니다.
TODO: 항상 그런지 확인해야 합니다.
</b></details>

<details>
<summary>다음 중 어느 것이 정적 Pod이 아닌가요?:

* kube-scheduler
* kube-proxy
* kube-apiserver
</summary><br><b>

kube-proxy - 클러스터의 모든 노드에 존재해야 하기 때문에 DaemonSet입니다. 특정 노드에서 실행되어야 할 필요가 없습니다.
</b></details>

<details>
<요약>정적 Pod 매니페스트가 어디에 위치하나요?</요약><br><b>

대부분의 경우 `/etc/kubernetes/manifests`에 있지만 `grep -i static /var/lib/kubelet/config.yaml`를 실행하여 `staticPodsPath`의 값을 확인할 수 있습니다.

설정 파일이 다른 경로에 있을 수도 있습니다. 확인하려면 `ps -ef | grep kubelet`을 실행하고 프로세스 `/usr/bin/kubelet`의 --config 인수 값을 확인하세요.

정적 Pod의 경로를 정의하는 키는 `staticPodPath`입니다. 따라서 설정이 `/var/lib/kubelet/config.yaml`에 있다면 `grep staticPodPath /var/lib/kubelet/config.yaml`을 실행할 수 있습니다.
</b></details>

<details>
<요약>정적 Pod를 삭제하는 방법을 설명하세요.
</요약><br><b>

kubelet 설정 파일에서 정적 Pod 디렉토리(`staticPodPath`)를 찾습니다.

해당 디렉토리로 이동하여 정적 Pod의 매니페스트/정의를 제거합니다(`rm <STATIC_POD_PATH>/<POD_DEFINITION_FILE>`).
</b></details>

#### Pods 명령

<details>
<요약>어떤 노드에 Pod가 예약되었는지, 즉 어떤 노드에서 특정 Pod가 실행되고 있는지 확인하는 방법은 무엇인가요?</요약><br><b>

`kubectl get pods -o wide`
</b></details>

<details>
<요약>Pod를 삭제하는 방법은?</요약><br><b>

`kubectl delete pod pod_name`
</b></details>

<details>
<요약>레이블 "env=prod"가 있는 모든 Pod를 나열하세요</요약><br><b>

`k get po -l env=prod`

개수를 세려면: `k get po -l env=prod --no-headers | wc -l`
</b></details>

<details>
<요약>현재 네임스페이스의 Pod를 나열하는 방법은?</요약><br><b>

`kubectl get po`
</b></details>

<details>
<요약>모든 네임스페이스에서 실행 중인 모든 Pod를 보는 방법은?</요약><br><b>

`kubectl get pods --all-namespaces`
</b></details>

#### Pods 문제 해결 및 디버깅

<details>
<요약>Pod를 실행하려고 하지만 "Pending" 상태에 머물러 있습니다. 이유가 무엇일까요?</요약><br><b>

한 가지 가능한 이유는 Pod를 노드에 예약해야 하는 스케줄러가 실행되지 않는 것입니다. 확인하려면 `kubectl get po -A | grep scheduler`를 실행하거나 `kube-system` 네임스페이스에서 직접 확인하세요.
</b></details>

<details>
<요약><code>kubectl logs [pod-name]</code> 명령어는 무엇을 합니까?</요약><br><b>

Pod의 컨테이너에 대한 로그를 출력합니다.
</b></details>

<details>
<요약><code>kubectl describe pod [pod name]</code> 명령어는 무엇을 합니까?</요약><br><b>

특정 리소스나 리소스 그룹의 세부 정보를 표시합니다.
</b></details>

<details>
<요약>이미지 <code>python</code>을 사용하여 명령 <code>sleep 2017</code>을 실행하는 정적 pod를 생성하세요</요약><br><b>

먼저 kubelet이 정적 pod를 생성하기 위해 추적하는 디렉토리로 변경합니다: `cd /etc/kubernetes/manifests` (kubelet 설정 파일을 읽어 경로를 확인할 수 있습니다)

이제 해당 디렉토리에서 정의/매니페스트를 생성합니다
`k run some-pod --image=python --command sleep 2017 --restart=Never --dry-run=client -o yaml > static-pod.yaml`
</b></details>

### 레이블과 선택기

<details>
<요약>레이블 설명</요약><br><b>

[Kubernetes.io](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/): "레이블은 Pod와 같은 객체에 부착되는 키/값 쌍입니다. 레이블은 사용자에게 의미가 있고 관련이 있는 객체의 식별 속성을 지정하는 데 사용되지만, 코어 시스템에 직접적인 의미를 내포하지는 않습니다. 레이블은 객체의 하위 집합을 구성하고 선택하는 데 사용될 수 있습니다. 레이블은 생성 시 객체에 부착할 수 있으며, 이후에도 언제든지 추가하고 수정할 수 있습니다. 각 객체는 정의된 키/값 레이블 세트를 가질 수 있습니다. 각 키는 주어진 객체에 대해 고유해야 합니다."
</b></details>

<details>
<요약>선택기 설명</요약><br><b>

[Kubernetes.io](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/#label-selectors): "이름과 UID와 달리, 레이블은 고유성을 제공하지 않습니다. 일반적으로 많은 객체가 동일한 레이블을 가질 것으로 예상합니다.

레이블 선택기를 통해 클라이언트/사용자는 객체 집합을 식별할 수 있습니다. 레이블 선택기는 쿠버네티스의 핵심 그룹화 기본 단위입니다.

API는 현재 두 가지 유형의 선택기를 지원합니다: 동등 기반 및 집합 기반. 레이블 선택기는 여러 요구 사항으로 구성될 수 있으며, 쉼표로 구분됩니다. 여러 요구 사항의 경우, 모두 만족해야 하므로 쉼표 구분자는 논리적 AND(&&) 연산자로 작동합니다."
</b></details>

<details>
<요약>레이블이 사용되는 실제 예시를 제공하세요</요약><br><b>

* 스케줄러가 특정 레이블이 있는 Pod를 특정 노드에 배치하는 데 사용될 수 있습니다.
* 리플리카셋이 확장해야 할 Pod를 추적하는 데 사용됩니다.
</b></details>

<details>
<요약>주석(Annotations)이란 무엇인가요?</요약><br><b>

[Kubernetes.io](https://kubernetes.io/docs/concepts/overview/working-with-objects/annotations/): "쿠버네티스 주석을 사용하여 객체에 임의의 비식별 메타데이터를 첨부할 수 있습니다. 도구와 라이브러리와 같은 클라이언트는 이 메타데이터를 검색할 수 있습니다."
</b></details>

<details>
<요약>주석이 레이블과 어떻게 다른가요?</요약><br><b>

[Kuberenets.io](레이블은 객체를 선택하고 특정 조건을 만족하는 객체의 컬렉션을 찾는 데 사용될 수 있습니다. 반면, 주석은 객체를 식별하고 선택하는 데 사용되지 않습니다. 주석의 메타데이터는 작거나 크고, 구조화되었거나 비구조화될 수 있으며, 레이블에서 허용되지 않는 문자를 포함할 수 있습니다.): "레이블은 객체를 선택하고 특정 조건을 만족하는 객체의 컬렉션을 찾는 데 사용될 수 있습니다. 반면, 주석은 객체를 식별하고 선택하는 데 사용되지 않습니다. 주석의 메타데이터는 작거나 크고, 구조화되었거나 비구조화될 수 있으며, 레이블에서 허용되지 않는 문자를 포함할 수 있습니다."
</b></details>

<details>
<summary>Pod에서 실행 중인 컨테이너의 로그를 어떻게 볼 수 있나요?</summary><br><b>

`k logs POD_NAME`
</b></details>

<details>
<summary>"some-pod"라는 Pod 안에 두 개의 컨테이너가 있을 때, <code>kubectl logs some-pod</code>를 실행하면 어떻게 될까요?</summary><br><b>

Pod 안에 두 개의 컨테이너가 있기 때문에 작동하지 않습니다. `kubectl logs POD_NAME -c CONTAINER_NAME`을 사용하여 하나의 컨테이너를 지정해야 합니다.
</b></details>

### Deployments

<details>
<summary>Kubernetes에서 "Deployment"란 무엇인가요?</summary><br><b>

Kubernetes Deployment는 Kubernetes에 컨테이너화된 애플리케이션을 담고 있는 파드의 인스턴스를 생성하거나 수정하는 방법을 알려줍니다.
Deployments는 복제 파드의 수를 조정할 수 있으며, 업데이트된 코드를 제어된 방식으로 롤아웃하거나 필요한 경우 이전 deployment 버전으로 롤백할 수 있습니다.

Deployment는 파드와 복제 세트에 대한 원하는 상태에 대한 선언적 진술입니다.
</b></details>

<details>
<summary>"nginx:alpine" 이미지로 deployment를 생성하는 방법은 무엇인가요?</code></summary><br><b>

`kubectl create deployment my_first_deployment --image=nginx:alpine`

혹은

```yaml
cat << EOF | kubectl create -f -
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  - name: nginx
    image: nginx:alpine
EOF
```
</b></details>

<details>
<summary>deployment가 생성되었는지 어떻게 확인할 수 있나요?</code></summary><br><b>

`kubectl get deployments` 또는 `kubectl get deploy`

이 명령은 클러스터에 생성되어 존재하는 모든 Deployment 객체를 나열합니다. 이것은 deployment들이 준비되어 실행 중이라는 것을 의미하지는 않습니다. "READY"와 "AVAILABLE" 열을 확인하여 이를 확인할 수 있습니다.
</b></details>

<details>
<summary>deployment를 어떻게 수정할 수 있나요?</code></summary><br><b>

`kubectl edit deployment <DEPLOYMENT_NAME>`
</b></details>

<details>
<summary>deployment를 편집하여 이미지를 변경한 후에 무슨 일이 일어나나요?</summary><br><b>

파드가 종료되고 새로운 파드가 생성됩니다.

또한 replicaset을 살펴보면 이전 replica에는 파드가 없고 새로운 replicaset이 생성된 것을 볼 수 있습니다.
</b></details>

<details>
<summary>deployment를 어떻게 삭제할 수 있나요?</summary><br><b>

한 가지 방법은 deployment 이름을 지정하는 것입니다: `kubectl delete deployment [deployment_name]`

다른 방법은 deployment 설정 파일을 사용하는 것입니다: `kubectl delete -f deployment.yaml`
</b></details>

<details>
<summary>deployment를 삭제하면 어떤 일이 일어나나요?</summary><br><b>

deployment와 관련된 파드가 종료되고 replicaset이 제거됩니다.
</b></details>

<details>
<summary>Deployment 객체를 생성할 때 무슨 일이 일어나나요?</summary><br><b>

`kubectl create deployment some_deployment --image=nginx`를 실행할 때 다음과 같은 일이 일어납니다.

1. 새로운 deployment를 생성하기 위해 클러스터의 kubernetes API 서버로 HTTP 요청이 전송됩니다.
2. 새로운 Pod 객체가 생성되어 작업자 노드 중 하나에 스케줄됩니다.
3. 작업자 노드의 Kublet이 새로운 Pod를 인지하고 컨테이너 런타임 엔진에 레지스트리에서 이미지를 가져오도록 지시합니다.
4. 방금 가져온 이미지를 사용하여 새 컨테이너가 생성됩니다.
</b></details>

<details>
<summary>앱을 개인 또는 외부 네트워크에서 어떻게 접근 가능하게 할 수 있나요?</summary><br><b>

Service를 사용합니다.
</b></details>

<details>
<summary>Stateful 애플리케이션에 Deployment를 사용할 수 있나요?</summary><br><b>
</b></details>

<details>
<summary>다음 deployment 매니페스트를 고치세요

```yaml
apiVersion: apps/v1
kind: Deploy
metadata:
  creationTimestamp: null
  labels:
    app: dep
  name: dep
spec:
  replicas: 3
  selector:
    matchLabels:
      app: dep
  strategy: {}
  template:
    metadata:
      creationTimestamp: null
      labels:
        app: dep
    spec:
      containers:
      - image: redis
        name: redis
        resources: {}
status: {}
```
</summary><br><b>

`kind: Deploy`를 `kind: Deployment`로 변경하세요
</b></details>

<details>
<summary>다음 deployment 매니페스트를 고치세요

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  creationTimestamp: null
  labels:
    app: dep
  name: dep
spec:
  replicas: 3
  selector:
    matchLabels:
      app: depdep
  strategy: {}
  template:
    metadata:
      creationTimestamp: null
      labels:
        app: dep
    spec:
      containers:
      - image: redis
        name: redis
        resources: {}
status: {}
```
</summary><br><b>

selector가 레이블과 일치하지 않습니다 (dep vs depdep). 해결하기 위해 depdep을 dep으로 수정하세요.
</b></details>

#### Deployments Commands

<details>
<summary>"dep"라는 이름의 deployment 파일 정의/매니페스트를 생성하세요. 3개의 복제본을 사용하며 이미지는 'redis'입니다</summary><br><b>

`k create deploy dep -o yaml --image=redis --dry-run=client --replicas 3 > deployment.yaml `

</b></details>

<details>
<summary>deployment `depdep`를 삭제하세요</summary><br><b>

`k delete deploy depdep`

</b></details>

<details>
<summary>"redis" 이미지를 사용하여 "pluck"이라는 deployment를 생성하고 5개의 복제본이 실행되도록 하세요</summary><br><b>

`kubectl create deployment pluck --image=redis`

`kubectl scale deployment pluck --replicas=5`
</b></details>

<details>
<summary>다음 속성을 가진 deployment를 생성하세요:

* 이름은 "blufer"
* 이미지는 "python"
* 3개의 복제본 실행
* 모든 파드는 "blufer" 레이블이 있는 노드에 배치됨
</summary><br><b>

`kubectl create deployment blufer --image=python --replicas=3 -o yaml --dry-run=client > deployment.yaml`

다음 섹션을 추가하세요 (`vi deployment.yaml`):

```yaml
spec:
  affinity:
    nodeAffinity:
      requiredDuringSchedlingIgnoredDuringExecution:
        nodeSelectorTerms:
        - matchExpressions:
          - key: blufer
            operator: Exists
```

`kubectl apply -f deployment.yaml`
</b></details>

### Services

<details>
<summary>Kubernetes에서 서비스(Service)란 무엇인가요?</summary><br><b>

"일련의 파드에서 실행되는 애플리케이션을 네트워크 서비스로 노출하는 추상적인 방법." - 자세한 내용은 [여기](https://kubernetes.io/docs/concepts/services-networking/service)에서 읽을 수 있습니다.

더 간단한 말로, 컨테이너에서 실행되는 특정 애플리케이션에 내부 또는 외부 연결을 추가할 수 있게 해줍니다.
</b></details>

<details>
<summary>Kubernetes 서비스와 관련된 구성요소를 올바른 위치에 배치하세요<br>
<img src="images/service_exercise.png"/>
</summary><br><b>

<img src="images/service_solution.png"/>

</b></details>


<details>
<summary>"alle"라는 기존 deployment에 대해 8080 포트에서 Pod(s)에 Load Balancer를 통해 접근할 수 있는 서비스를 생성하는 방법은 무엇인가요?</summary><br><b>

명령적 방법:

`kubectl expose deployment alle --type=LoadBalancer --port 8080`
</b></details>

<details>
<summary>다음 문장이 참인지 거짓인지 판별하시오. Pod와 서비스의 수명주기는 연결되어 있지 않으므로 Pod가 사라지더라도 서비스는 계속 유지됩니다</summary><br><b>

True
</b></details>

<details>
<summary>서비스를 생성한 후 생성되었는지 어떻게 확인할 수 있나요?</summary><br><b>

`kubectl get svc`
</b></details>

<details>
<summary>기본 서비스 타입은 무엇이고, 어떤 용도로 사용되나요?</summary><br><b>

ClusterIP - 내부 통신용으로 사용됩니다.
</b></details>

<details>
<summary>어떤 서비스 타입들이 있나요?</summary><br><b>

* ClusterIP
* NodePort
* LoadBalancer
* ExternalName

이 주제에 대한 자세한 내용은 [여기](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types)에서 확인할 수 있습니다.
</b></details>

<details>
<summary>서비스(Service)와 디플로이먼트(Deployment)는 어떻게 연결되어 있나요?</summary><br><b>

사실 그들은 연결되어 있지 않습니다. 서비스는 Deployment와는 어떤 방식으로도 연결되지 않고 직접적으로 Pod(s)를 가리킵니다.
</b></details>

<details>
<summary>서비스를 정의/추가하는 중요한 단계는 무엇인가요?</summary><br><b>

1. 서비스의 targetPort가 파드의 containerPort와 일치하는지 확인하기
2. 선택자가 파드의 레이블 중 적어도 하나와 일치하는지 확인하기

</b></details>

<details>
<summary>Kubernetes에서 기본 서비스 타입은 무엇이며 어떤 용도로 사용되나요?</summary><br><b>

기본값은 ClusterIP이며, 내부적으로 포트를 노출하는 데 사용됩니다. 파드 간의 내부 통신을 가능하게 하고 외부 접근을 차단하고자 할 때 유용합니다.

</b></details>

<details>
<summary>특정 서비스에 대한 정보를 어떻게 얻을 수 있나요?</summary><br><b>

`kubctl describe service <SERVICE_NAME>`

일반적으로 `kubectl describe svc ...`를 사용합니다.

</b></details>

<details>
<summary>다음 명령어가 수행하는 작업은 무엇인가요?

```sh
kubectl expose rs some-replicaset --name=replicaset-svc --target-port=2017 --type=NodePort
```
</summary><br><b>

이 명령어는 ReplicaSet을 'replicaset-svc'라는 서비스를 생성하여 노출합니다. 노출된 포트는 2017(애플리케이션에서 사용하는 포트)이며, 서비스 타입은 NodePort입니다. 이는 외부에서 접근 가능하다는 것을 의미합니다.
</b></details>

<details>
<summary>다음 문장이 참인지 거짓인지 판별하시오. 다음 명령어를 실행할 경우, 타겟 포트는 Kubernetes 클러스터 노드 중 하나에서만 노출되지만 모든 파드로 라우팅됩니다

```sh
kubectl expose rs some-replicaset --name=replicaset-svc --target-port=2017 --type=NodePort
```
</summary><br><b>

거짓. 클러스터의 모든 노드에서 노출되며 ReplicaSet에 속한 파드 중 하나로 라우팅됩니다.
</b></details>

<details>
<summary>특정 서비스가 주어진 파드로 요청을 전달하도록 구성되었는지 어떻게 확인할 수 있나요?</summary><br><b>

`kubectl describe service`를 실행하고 "Endpoints"의 IP가 `kubectl get pod -o wide`의 출력에서 어떤 IP와 일치하는지 확인합니다.
</b></details>

<details>
<summary>다음 블록에 apply를 실행할 때 무슨 일이 일어나는지 설명하세요

```yaml
apiVersion: v1
kind: Service
metadata:
  name: some-app
spec:
  type: NodePort
  ports:
  - port: 8080
    nodePort: 2017
    protocol: TCP
  selector:
    type: backend
    service: some-app
```
</summary><br><b>

새로운 "NodePort" 타입의 서비스를 생성합니다. 이는 애플리케이션과 내부 및 외부 통신을 위해 사용될 수 있습니다.<br>
애플리케이션의 포트는 8080이며 요청은 이 포트로 전달됩니다. 노출된 포트는 2017입니다. nodePort를 지정하는 것은 일반적인 관행은 아닙니다.<br>
사용되는 포트는 TCP이며(UDP 대신) 이는 기본값이므로 지정할 필요가 없습니다.<br>
서비스가 어떤 파드에 요청을 전달할지 알기 위해 사용하는 선택자입니다. 이 경우, "type: backend" 및 "service: some-app" 레이블이 있는 파드입니다.<br>
</b></details>

<details>
<summary>다음 서비스를 외부 서비스로 전환하는 방법은 무엇인가요?

```yaml
spec:
  selector:
    app: some-app
  ports:
    - protocol: TCP
      port: 8081
      targetPort: 8081
```
</summary><br><b>

Adding `type: LoadBalancer` and `nodePort`

```yaml
spec:
  selector:
    app: some-app
  type: LoadBalancer
  ports:
    - protocol: TCP
      port: 8081
      targetPort: 8081
      nodePort: 32412
```
</b></details>

<details>
<summary>Kubernetes 클러스터 외부에서 클러스터 내부 서비스로 트래픽을 라우팅하기 위해 무엇을 사용하나요?</summary><br><b>

Ingress
</b></details>

<details>
<summary>다음 문장이 참인지 거짓인지 판별하시오. "NodePort"를 사용할 때, "ClusterIP"가 자동으로 생성됩니까?</summary><br><b>

True
</b></details>

<details>
<summary>"LoadBalancer" 타입을 사용하는 경우는 언제인가요?</summary><br><b>

주로 클라우드 제공업체의 로드 밸런서와 결합하고자 할 때 사용합니다.
</b></details>

<details>
<summary>서비스를 외부 주소에 매핑하는 방법은 무엇인가요?</summary><br><b>

'ExternalName' 지시어를 사용합니다.
</b></details>

<details>
<summary>서비스를 생성할 때 발생하는 상세한 과정을 설명하세요</summary><br><b>

1. Kubectl이 API 서버에 서비스 생성 요청을 보냅니다.
2. 컨트롤러가 새로운 서비스를 감지합니다.
3. 컨트롤러에 의해 서비스와 동일한 이름을 가진 엔드포인트 객체가 생성됩니다.
4. 컨트롤러는 서비스 선택자를 사용하여 엔드포인트를 식별합니다.
5. kube-proxy가 새로운 엔드포인트 객체 및 서비스를 감지하고 서비스 포트로 전송되는 트래픽을 엔드포인트로 리디렉션하기 위한 iptables 규칙을 추가합니다.
6. kube-dns가 새로운 서비스를 감지하고 dns 서버에 컨테이너 레코드를 추가합니다.
</b></details>

<details>
<summary>특정 앱의 엔드포인트를 어떻게 나열하나요?</summary><br><b>

`kubectl get ep <name>`
</b></details>

<details>
<summary>특정 Pod와 관련된 서비스에 대한 정보를 찾으려면 <code>kubectl exec <POD_NAME> -- </code>만 사용할 수 있다면 어떻게 하나요?</summary><br><b>

`kubectl exec <POD_NAME> -- env`를 실행할 수 있으며, 이는 서비스와 관련된 몇 가지 환경 변수를 제공합니다.<br>
예를 들어, `[SERVICE_NAME]_SERVICE_HOST`, `[SERVICE_NAME]_SERVICE_PORT`, ...
</b></details>

<details>
<summary>컨테이너가 처음으로 해당 서비스와 연결을 시도할 때 무슨 일이 일어나는지 설명하세요. 설명에 포함된 각 구성요소를 누가 추가했는지 설명하세요</summary><br><b>

  - 컨테이너는 /etc/resolv.conf에 정의된 네임서버를 확인합니다.
  - 컨테이너는 네임서버에 쿼리를 보내 서비스 IP로 주소를 확인합니다.
  - 서비스 IP로 보내진 요청은 iptables 규칙(또는 다른 선택된 소프트웨어)을 통해 엔드포인트(들)로 전달됩니다.

누가 추가했는지에 대한 설명:

  - 컨테이너의 네임서버는 Pod 스케줄링 시 kubelet에 의해 kube-dns를 사용하여 추가됩니다.
  - 서비스의 DNS 레코드는 서비스 생성 시 kube-dns에 의해 추가됩니다.
  - iptables 규칙은 엔드포인트 및 서비스 생성 시 kube-proxy에 의해 추가됩니다.
</b></details>

<details>
<summary><code>kubctl expose deployment remo --type=LoadBalancer --port 8080</code>를 실행할 때 고수준에서 무슨 일이 일어나는지 설명하세요</summary><br><b>

1. Kubectl이 Kubernetes API에 서비스 객체를 생성하라는 요청을 보냅니다.
2. Kubernetes는 클라우드 제공업체(예: AWS, GCP, Azure)에 로드 밸런서를 제공하도록 요청합니다.
3. 새로 생성된 로드 밸런서는 들어오는 트래픽을 관련 작업 노드(들)로 전달하고, 이는 트래픽을 관련 컨테이너로 전달합니다.
</b></details>

<details>
<summary>컨테이너화된 애플리케이션으로 들어오는 외부 트래픽을 전달하는 서비스를 생성한 후, 이것이 작동하는지 어떻게 확인할 수 있나요?</summary><br><b>

`curl <SERVICE IP>:<SERVICE PORT>`를 실행하여 출력을 확인할 수 있습니다.
</b></details>

<details>
<summary>Kubernetes에서 내부 로드 밸런서는 <code>____</code>라고 하며, 외부 로드 밸런서는 <code>____</code>라고 합니다</summary><br><b>

Kubernetes에서 내부 로드 밸런서는 Service라고 하며, 외부 로드 밸런서는 Ingress라고 합니다
</b></details>

### Ingress

<details>
<summary>Ingress란 무엇인가요?</summary><br><b>

Kubernetes 문서에서: "Ingress는 클러스터 외부에서 클러스터 내부 서비스로 HTTP 및 HTTPS 경로를 노출합니다. 트래픽 라우팅은 Ingress 리소스에 정의된 규칙에 의해 제어됩니다."

자세한 내용은 [여기](https://kubernetes.io/docs/concepts/services-networking/ingress/)에서 읽을 수 있습니다.
</b></details>

<details>
<summary>다음 구성 파일을 완성하여 Ingress로 만드세요

```yaml
metadata:
  name: someapp-ingress
spec:
```
</summary><br><b>
이 질문에 대한 답은 여러가지가 있습니다.

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: someapp-ingress
spec:
  rules:
  - host: my.host
    http:
      paths:
      - backend:
          serviceName: someapp-internal-service
          servicePort: 8080
```
</b></details>


<details>
<summary>"http", "host", "backend" directive의 의미를 설명하세요.

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: someapp-ingress
spec:
  rules:
  - host: my.host
    http:
      paths:
      - backend:
          serviceName: someapp-internal-service
          servicePort: 8080
```
</summary><br><b>

host는 클러스터의 진입점으로, 기본적으로 클러스터의 노드 IP 주소에 매핑되는 유효한 도메인 주소입니다.<br>
http 줄은 들어오는 요청이 http를 사용하여 내부 서비스로 전달되도록 지정하는 데 사용됩니다.<br>
backend는 내부 서비스를 참조합니다 (serviceName은 metadata 아래의 이름이고 servicePort는 ports 섹션 아래의 포트입니다).
</b></details>

<details>
<summary>Ingress 호스트에서 와일드카드를 사용하면 문제가 발생할 수 있는 이유는 무엇인가요?</summary><br><b>

호스트에서 와일드카드 값을 사용하지 않아야 하는 이유(`- host: *` 같은)는 기본적으로 Kubernetes 클러스터에 이 ingress를 사용하는 컨테이너로 모든 트래픽을 전달하도록 지시하기 때문입니다. 이로 인해 전체 클러스터가 다운될 수 있습니다.
</b></details>

<details>
<summary>Ingress Controller란 무엇인가요?</summary><br><b>

Ingress를 위한 구현체입니다. 기본적으로 Ingress 규칙을 평가하고 처리하며 모든 리디렉션을 관리하는 또 다른 파드(또는 파드 집합)입니다.

여러 Ingress Controller 구현이 있습니다 (Kubernetes에서 제공하는 것은 Kubernetes Nginx Ingress Controller입니다).
</b></details>

<details>
<summary>Ingress를 사용하는 몇 가지 사례는 무엇인가요?</summary><br><b>

* 여러 서브도메인 (각자의 서비스를 가진 여러 호스트 항목)
* 하나의 도메인에 여러 서비스 (각기 다른 서비스/애플리케이션에 매핑된 여러 경로)
</b></details>

<details>
<summary>네임스페이스에서 Ingress를 어떻게 나열하나요?</summary><br><b>

kubectl get ingress
</b></details>

<details>
<summary>Ingress 기본 백엔드(Default Backend)란 무엇인가요?</summary><br><b>

Kubernetes 클러스터로 들어오는 요청이 어떤 백엔드에도 매핑되지 않을 때 (= 서비스에 요청을 매핑하기 위한 규칙이 없을 때) 어떻게 처리할지를 지정합니다. 기본 백엔드 서비스가 정의되지 않은 경우, 사용자들이 아무것도 보지 못하거나 불분명한 오류 대신 어떤 종류의 메시지를 볼 수 있도록 정의하는 것이 권장됩니다.
</b></details>

<details>
<summary>기본 백엔드를 어떻게 구성하나요?</summary><br><b>

`kubectl describe ingress ...`에서 반영된 기본 백엔드의 이름과 ports 섹션 아래의 포트를 지정하는 서비스 리소스를 생성합니다.
</b></details>

<details>
<summary>Ingress에서 TLS를 어떻게 구성하나요?</summary><br><b>

tls 및 secretName 항목을 추가합니다.

```yaml
spec:
  tls:
  - hosts:
    - some_app.com
    secretName: someapp-secret-tls
```
</b></details>

<details>
<summary>다음 문장이 참인지 거짓인지 판별하시오. Ingress를 TLS와 함께 구성할 때, Secret 구성요소는 Ingress 구성요소와 동일한 네임스페이스에 있어야 합니다</summary><br><b>

True
</b></details>

<details>
<summary>IP 주소나 포트 수준에서 트래픽 흐름을 제어하기 위해 어떤 Kubernetes 개념을 사용하나요?</summary><br><b>

Network Policies
</b></details>

<details>
<summary>애플리케이션(배포)을 어떻게 확장하여 애플리케이션의 인스턴스를 하나 이상 실행하나요?</summary><br><b>

애플리케이션의 두 인스턴스를 실행하려면?

`kubectl scale deployment <DEPLOYMENT_NAME> --replicas=2`

애플리케이션이 확장 방법을 알고 있다면, 다른 숫자를 지정할 수 있습니다.
</b></details>

### ReplicaSets

<details>
<summary>ReplicaSet의 목적은 무엇인가요?</summary><br><b>

[kubernetes.io](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset): "ReplicaSet의 목적은 언제든지 안정적인 복제 파드 세트를 유지하는 것입니다. 따라서, 지정된 수의 동일한 파드의 가용성을 보장하는 데 종종 사용됩니다."

더 간단한 말로, ReplicaSet은 선택된 파드에 대해 지정된 수의 파드 복제본이 실행 중인지를 보장합니다. ReplicaSet에서 정의한 것보다 더 많은 파드가 있으면 일부가 제거됩니다. ReplicaSet에서 정의한 것보다 적으면 더 많은 복제본이 추가됩니다.
</b></details>

<details>
<summary>다음 블록의 코드 라인은 무엇을 하는가?

```yaml
spec:
  replicas: 2
  selector:
    matchLabels:
      type: backend
  template:
    metadata:
      labels:
        type: backend
    spec:
      containers:
      - name: httpd-yup
        image: httpd
```
</summary><br><b>

ReplicaSet이 "backend" 유형으로 설정된 파드에 대해 정의됩니다. 따라서 어떤 시점에서든 동시에 실행되는 파드가 2개 있을 것입니다.
</b></details>

<details>
<summary>ReplicaSet에 의해 생성된 Pod를 직접 <code>kubectl delete po ...</code>로 삭제하면 어떤 일이 일어나나요?</summary><br><b>

ReplicaSet은 원하는 복제본 수에 도달하기 위해 새로운 Pod를 생성할 것입니다.
</b></details>

<details>
<summary>다음 문장이 참인지 거짓인지 판별하시오. ReplicaSet이 2개의 복제본을 정의했지만 ReplicaSet 선택자와 일치하는 3개의 Pod가 실행 중인 경우 아무것도 하지 않을 것입니다</summary><br><b>

거짓. 원하는 상태인 2개의 복제본에 도달하기 위해 Pod 중 하나를 종료할 것입니다.
</b></details>

<details>
<summary>ReplicaSet을 생성하는 경우의 이벤트 순서를 설명하세요</summary><br><b>

* 클라이언트(예: kubectl)가 API 서버에 ReplicaSet 생성 요청을 보냅니다.
* 컨트롤러는 ReplicaSet을 요청하는 새로운 이벤트가 있다는 것을 감지합니다.
* 컨트롤러는 새로운 Pod 정의를 생성합니다(정확한 수는 ReplicaSet 정의에 따라 다릅니다).
* 스케줄러는 할당되지 않은 Pod를 감지하고 Pod를 할당할 노드를 결정합니다. 이 정보는 API 서버로 전송됩니다.
* Kubelet은 API 서버를 지속적으로 모니터링하고 있으며, 실행 중인 노드에 2개의 Pod가 할당되었다는 것을 감지합니다.
* Kubelet은 컨테이너 엔진에 요청을 보내 Pod의 일부인 컨테이너를 생성합니다.
* Kubelet은 API 서버에 요청을 보내 Pod가 생성되었다는 것을 알립니다.
</b></details>

<details>
<summary>현재 네임스페이스에서 ReplicaSet을 어떻게 나열하나요?</summary><br><b>

`kubectl get rs`
</b></details>

<details>
<summary>ReplicaSet이 생성한 Pod를 삭제하지 않고 ReplicaSet을 삭제할 수 있나요?</summary><br><b>

네, `--cascade=false` 옵션을 사용하면 가능합니다.

`kubectl delete -f rs.yaml --cascade=false`
</b></details>

<details>
<summary>명시적으로 지정되지 않은 경우 기본 복제본 수는 몇 개인가요?</summary><br><b>

1
</b></details>

<details>
<summary><code>kubectl get rs</code>의 다음 출력이 의미하는 바는 무엇인가요?

NAME                    DESIRED   CURRENT   READY   AGE
web                     2         2         0       2m23s
</summary><br><b>

`web` replicaset은 2개의 복제본을 가지고 있습니다. Pod 내부의 컨테이너가 아직 실행되지 않은 것 같으므로 READY 값이 0입니다. 일부 컨테이너가 실행되기 시작하는 데 시간이 걸릴 수 있으므로 정상일 수도 있고, 오류로 인한 것일 수도 있습니다. `kubectl describe po POD_NAME` 또는 `kubectl logs POD_NAME`을 실행하면 더 많은 정보를 얻을 수 있습니다.
</b></details>

<details>
<summary>다음 문장이 참인지 거짓인지 판별하시오. ReplicaSet의 selector 필드에 지정된 Pod는 ReplicaSet 자체에 의해 생성되어야 합니다</summary><br><b>

거짓. Pod는 이미 실행 중일 수 있으며 처음에는 어떤 객체에 의해 생성될 수 있습니다. ReplicaSet에게 그것들을 획득하고 모니터링하는 것은 중요하지 않으며 필수 요건이 아닙니다.
</b></details>

<details>
<summary>다음 문장이 참인지 거짓인지 판별하시오. ReplicaSet의 경우, selector 필드에 지정된 Pod가 존재하지 않으면, ReplicaSet은 그것들이 실행되기를 기다린 후에야 작업을 시작할 것입니다</summary><br><b>

거짓. 누락된 Pod를 실행하는 데 필요한 조치를 취할 것입니다.
</b></details>

<details>
<summary>ReplicaSet의 경우, spec 섹션에서 필수적인 필드는 무엇인가요?</summary><br><b>

spec 섹션의 `template` 필드는 필수적입니다. 필요할 때 새로운 Pod를 생성하는 데 ReplicaSet에 의해 사용됩니다.
</b></details>

<details>
<summary>ReplicaSet을 생성했을 때, ReplicaSet이 일치하는 Pod를 찾았는지 아니면 새로운 Pod를 생성했는지 어떻게 확인하나요?</summary><br><b>

`kubectl describe rs <ReplicaSet 이름>`

`Events` 섹션(맨 마지막 줄)에서 확인할 수 있습니다.
</b></details>

<details>
<summary>다음 문장이 참인지 거짓인지 판별하시오. ReplicaSet을 삭제하면 그것이 생성한 Pod도 삭제됩니다</summary><br><b>

참. (그리고 Pod뿐만 아니라 다른 모든 것도 삭제됩니다).
</b></details>

<details>
<summary>다음 문장이 참인지 거짓인지 판별하시오. ReplicaSet에서 추적하는 Pod에서 레이블을 제거하면, ReplicaSet은 새로운 Pod를 생성할 것입니다</summary><br><b>

참. ReplicaSet의 선택자 필드에서 사용하는 레이블이 Pod에서 제거되면, 그 Pod는 더 이상 ReplicaSet에 의해 제어되지 않으며 ReplicaSet은 "잃어버린" 것을 보상하기 위해 새로운 Pod를 생성할 것입니다.
</b></details>

<details>
<summary>deployment를 8개의 복제본으로 확장하는 방법은 무엇인가요?</code></summary><br><b>

kubectl scale deploy <DEPLOYMENT_NAME> --replicas=8
</b></details>

<details>
<summary>ReplicaSets는 사용자가 생성 명령(예: <code>kubectl create -f rs.yaml</code>)을 실행하는 순간 실행됩니다</summary><br><b>

거짓. 얼마나 걸릴지는 실행하려는 것에 따라 다릅니다. 실행 중인지 확인하려면 `kubectl get rs`를 실행하고 'READY' 열을 확인하세요.
</b></details>

<details>
<summary>ReplicaSet을 새로운 서비스로 노출하는 방법은 무엇인가요?</summary><br><b>

`kubectl expose rs <ReplicaSet 이름> --name=<서비스 이름> --target-port=<노출할 포트> --type=NodePort`

몇 가지 참고사항:
  - target port는 컨테이너에서 사용하는 앱의 포트에 따라 다릅니다.
  - type은 다를 수 있으며 반드시 "NodePort"일 필요는 없습니다.
</b></details>

<details>
<summary>다음 ReplicaSet 정의를 수정하세요

```yaml
apiVersion: apps/v1
kind: ReplicaCet
metadata:
  name: redis
  labels:
    app: redis
    tier: cache
spec:
  selector:
    matchLabels:
      tier: cache
  template:
    metadata:
      labels:
        tier: cachy
    spec:
      containers:
      - name: redis
        image: redis
```
</summary><br><b>

kind는 ReplicaCet이 아니라  ReplicaSet입니다 :)
</b></details>

<details>
<summary>다음 ReplicaSet 정의를 수정하세요

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: redis
  labels:
    app: redis
    tier: cache
spec:
  selector:
    matchLabels:
      tier: cache
  template:
    metadata:
      labels:
        tier: cachy
    spec:
      containers:
      - name: redis
        image: redis
```
</summary><br><b>

선택기가 레이블과 일치하지 않습니다 (cache vs cachy). 해결하기 위해 cachy를 cache로 수정하세요.
</b></details>

<details>
<summary>"repli"라는 이름의 레플리카 세트에서 사용된 컨테이너 이미지를 어떻게 확인할 수 있나요?</summary><br><b>

`k describe rs repli | grep -i image`
</b></details>

<details>
<summary>"repli"라는 레플리카 세트의 일부로 준비된 Pod의 수를 어떻게 확인할 수 있나요?</summary><br><b>

`k describe rs repli | grep -i "Pods Status"`
</b></details>

<details>
<summary>"rori"라는 레플리카 세트를 어떻게 삭제할 수 있나요?</summary><br><b>

`k delete rs rori`
</b></details>

<details>
<summary>"rori"라는 레플리카 세트에서 사용하는 이미지를 다른 이미지로 어떻게 변경할 수 있나요?</summary><br><b>

`k edit rs rori`
</b></details>

<details>
<summary>"rori"라는 레플리카 세트를 확장하여 2개 대신 5개의 Pod를 실행하도록 하려면 어떻게 하나요?</summary><br><b>

`k scale rs rori --replicas=5`
</b></details>

<details>
<summary>"rori"라는 레플리카 세트를 축소하여 5개 대신 1개의 Pod를 실행하도록 하려면 어떻게 하나요?</summary><br><b>

`k scale rs rori --replicas=1`
</b></details>

### DaemonSet

<details>
<summary>DaemonSet이란 무엇인가요?</summary><br><b>

[Kubernetes.io](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset): "DaemonSet은 모든 (또는 일부) 노드가 Pod의 복사본을 실행하도록 보장합니다. 클러스터에 노드가 추가되면 해당 노드에 Pod가 추가됩니다. 클러스터에서 노드가 제거되면 해당 Pod도 가비지 수집됩니다. DaemonSet을 삭제하면 생성된 Pod들이 정리됩니다."
</b></details>

<details>
<summary>ReplicaSet과 DaemonSet의 차이점은 무엇인가요?</summary><br><b>

ReplicaSet의 목적은 언제든지 안정적인 복제 Pod 세트를 유지하는 것입니다.
DaemonSet은 모든 노드가 Pod의 복사본을 실행하도록 보장합니다.
</b></details>

<details>
<summary>DaemonSet을 사용하는 몇 가지 사례는 무엇인가요?</summary><br><b>

* 모니터링: 클러스터의 모든 노드에서 모니터링을 수행하려는 경우. 예를 들어 datadog pod는 daemonset을 사용하여 모든 노드에서 실행됩니다.
* 로깅: 클러스터의 모든 노드에서 로깅 설정을 하고 싶은 경우
* 네트워킹: 모든 노드가 서로 통신하기 위해 모든 노드에 필요한 네트워킹 구성요소
</b></details>

<details>
<summary>DaemonSet은 어떻게 작동하나요?</summary><br><b>

역사적으로 1.12 버전까지는 NodeName 속성을 사용했습니다.

1.12 버전부터는 정규 스케줄러와 노드 친화성을 사용하여 달성됩니다.
</b></details>

#### DaemonSet - 명령어

<details>
<summary>현재 네임스페이스의 모든 daemonset을 어떻게 나열하나요?</summary><br><b>

`kubectl get ds`
</b></details>

### StatefulSet

<details>
<summary>StatefulSet에 대해 설명하세요</summary><br><b>

StatefulSet은 상태 유지 애플리케이션을 관리하기 위해 사용되는 워크로드 API 객체입니다. 일련의 Pod의 배포 및 확장을 관리하며, 이러한 Pod의 순서와 고유성에 대한 보장을 제공합니다.[자세히 알아보기](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/)
</b></details>

### 저장소

#### 볼륨

<details>
<summary>Kubernetes와 관련하여 볼륨이란 무엇인가요?</summary><br><b>

특정 Pod 내의 컨테이너가 접근할 수 있는 디렉토리입니다. 디렉토리를 생성하고 관리하는 메커니즘은 주로 볼륨 유형에 따라 다릅니다.

</b></details>

<details>
<summary>어떤 볼륨 유형을 알고 있나요?</summary><br><b>

* emptyDir: Pod가 노드에 할당될 때 생성되며, 해당 노드에서 Pod가 더 이상 실행되지 않을 때 존재하지 않습니다.
* hostPath: 호스트 자체의 경로를 마운트합니다. 보안 위험으로 인해 일반적으로 사용되지 않지만 (`/sys`, `/var/lib` 등의 내부 호스트 경로에 대한 액세스와 같은) 필요한 여러 사용 사례가 있습니다.

</b></details>

<details>
<summary>Kubernetes에서 볼륨이 해결하는 문제는 무엇인가요?</summary><br><b>

1. 동일한 Pod에서 실행 중인 컨테이너 간에 파일을 공유합니다.
2. 컨테이너의 저장소는 일시적입니다 - 일반적으로 오래 지속되지 않습니다. 예를 들어, 컨테이너가 충돌하면 디스크에 있는 모든 데이터가 손실됩니다. 특정 볼륨을 사용하면 영구 볼륨을 통해 이러한 상황을 관리할 수 있습니다.

</b></details>

<details>
<summary>Pod와 관련하여 일시적인(ephemeral) 볼륨 유형과 영구(persistent) 볼륨의 차이점을 설명하세요</summary><br><b>

일시적인 볼륨 유형은 Pod의 수명과 같은 반면, 영구 볼륨은 Pod의 수명을 넘어 존재합니다.

</b></details>

<details>
<summary>다음 볼륨 유형에 대한 각각 하나 이상의 사용 사례를 제공하세요:

* emptyDir
* hostPath
</summary><br><b>

* EmptyDir: Pod가 삭제되면 잃어도 되는 임시 데이터가 필요한 경우. 예를 들어, 일회성 작업에 필요한 단기 데이터.
* hostPath: 호스트 자체의 경로에 액세스해야 하는 경우 (예: `/sys`의 데이터 또는 `/var/lib`에서 생성된 데이터)
</b></details>

### 네트워킹

<details>
<summary>다음 문장이 참인지 거짓인지 판별하시오. 기본적으로 두 개의 서로 다른 네임스페이스에 있는 두 개의 Pod 간에는 통신이 없습니다</summary><br><b>

거짓. 기본적으로 두 개의 다른 네임스페이스에 있는 두 개의 Pod는 서로 통신할 수 있습니다.

### Namespaces

<details>
<summary>네임스페이스란 무엇인가요?</summary><br><b>

네임스페이스를 사용하면 클러스터를 가상 클러스터로 분할하여 애플리케이션을 그룹화하고 완전히 분리된 다른 그룹과 구분할 수 있습니다(예를 들어, 두 개의 다른 네임스페이스에서 동일한 이름의 앱을 생성할 수 있습니다).
</b></details>

<details>
<summary>네임스페이스를 사용하는 이유는 무엇이며, 하나의 기본 네임스페이스만 사용하는 것이 문제인 이유는 무엇인가요?</summary><br><b>

기본 네임스페이스만 사용하면 시간이 지남에 따라 클러스터에서 관리하는 모든 애플리케이션의 개요를 파악하기 어려워집니다. 네임스페이스는 의미 있는 그룹으로 애플리케이션을 조직화하는 데 도움이 됩니다. 예를 들어, 모든 모니터링 애플리케이션을 하나의 네임스페이스에, 모든 보안 애플리케이션을 다른 네임스페이스에 두는 것과 같습니다.

네임스페이스는 블루/그린 환경을 관리하는 데에도 유용할 수 있습니다. 여기서 각 네임스페이스는 앱의 다른 버전을 포함할 수 있고, 다른 네임스페이스(로깅, 모니터링 등)의 리소스를 공유할 수도 있습니다.

네임스페이스의 또 다른 사용 사례는 한 클러스터, 여러 팀입니다. 여러 팀이 동일한 클러스터를 사용하는 경우, 서로 발을 밟을 수 있습니다. 예를 들어, 동일한 이름의 앱을 생성하게 되면 한 팀이 다른 팀의 앱을 덮어쓰게 됩니다. Kubernetes에서는 동일한 네임스페이스에서 동일한 이름의 두 앱이 있을 수 없기 때문입니다.
</b></details>

<details>
<summary>다음 문장이 참인지 거짓인지 판별하시오. 네임스페이스가 삭제되면 해당 네임스페이스의 모든 리소스가 삭제되지 않고 다른 기본 네임스페이스로 이동됩니다</summary><br><b>

거짓. 네임스페이스가 삭제되면 해당 네임스페이스의 리소스도 삭제됩니다.
</b></details>

<details>
<summary>Kubernetes 클러스터를 생성할 때 기본적으로 어떤 특별한 네임스페이스가 있나요?</summary><br><b>

* default
* kube-system
* kube-public
* kube-node-lease
</b></details>

<details>
<summary>kube-system 네임스페이스에는 무엇이 포함되어 있나요?</summary><br><b>

* 마스터 및 Kubectl 프로세스
* 시스템 프로세스
</b></details>

<details>
<summary>네임스페이스는 리소스에 대한 범위를 제공하지만, 그들을 분리하지는 않습니다</summary><br><b>

참. 예를 들어, 두 개의 별도 네임스페이스에 있는 두 개의 파드를 생성해 보면 두 개 사이에 연결이 있음을 알 수 있습니다.
</b></details>

#### 네임스페이스 - 명령어

<details>
<summary>모든 네임스페이스를 어떻게 나열하나요?</code></summary><br><b>

`kubectl get namespaces` 또는 `kubectl get ns`

</b></details>

<details>
<summary>'alle'라는 네임스페이스를 생성하세요</summary><br><b>

`k create ns alle`

</b></details>

<details>
<summary>몇 개의 네임스페이스가 있는지 확인하세요</summary><br><b>

`k get ns --no-headers | wc -l`

</b></details>

<details>
<summary>"dev" 네임스페이스에 몇 개의 파드가 있는지 확인하세요</summary><br><b>

`k get po -n dev`

</b></details>

<details>
<summary>"dev" 네임스페이스에 "kartos"라는 이름의 파드를 생성하세요. 파드는 "redis" 이미지를 사용해야 합니다.</summary><br><b>

네임스페이스가 이미 존재하지 않는 경우: `k create ns dev`

`k run kratos --image=redis -n dev`

</b></details>

<details>
<summary>"atreus"라는 이름의 파드를 찾고 있습니다. 어느 네임스페이스에서 실행 중인지 어떻게 확인할 수 있나요?</summary><br><b>

`k get po -A | grep atreus`

</b></details>

<details>
<summary>kube-public에는 무엇이 포함되어 있나요?</summary><br><b>

* 클러스터 정보가 포함된 configmap
* 공개적으로 접근 가능한 데이터
</b></details>

<details>
<summary>현재 네임스페이스의 이름을 어떻게 얻을 수 있나요?</code></summary><br><b>

`kubectl config view | grep namespace`
</b></details>

<details>
<summary>kube-node-lease에는 무엇이 포함되어 있나요?</summary><br><b>

노드의 하트비트에 대한 정보가 포함됩니다. 각 노드에는 가용성에 대한 정보를 담고 있는 객체가 있습니다.
</b></details>

<details>
<summary>다음 문장이 참인지 거짓인지 판별하시오. 네임스페이스를 사용하면 사용자/팀이 소비하는 리소스를 제한할 수 있습니다</summary><br><b>

참. 네임스페이스를 사용하면 CPU, RAM 및 스토리지 사용을 제한할 수 있습니다.
</b></details>

<details>
<summary>다른 네임스페이스로 어떻게 전환할 수 있나요? 즉, 활성 네임스페이스를 어떻게 변경할 수 있나요?</code></summary><br><b>

`kubectl config set-context --current --namespace=some-namespace`를 실행하고 `kubectl config view --minify | grep namespace:`로 확인합니다.

또는

`kubens some-namespace`를 실행합니다.
</b></details>

#### 리소스 쿼터

<details>
<summary>리소스 쿼터(Resource Quota)란 무엇인가요?</code></summary><br><b>
  
리소스 쿼터는 네임스페이스 당 총 리소스 소비를 제한하는 제약을 제공합니다. 네임스페이스에서 생성할 수 있는 객체의 수량을 타입별로 제한할 수 있으며, 해당 네임스페이스에서 소비할 수 있는 총 컴퓨트 리소스의 양도 제한할 수 있습니다.
</b></details>

<details>
<summary>리소스 쿼터를 어떻게 생성하나요?</code></summary><br><b>

kubectl create quota some-quota --hard-cpu=2,pods=2
</b></details>

<details>
<summary>어떤 리소스가 다른 네임스페이스에서 접근할 수 있나요?</code></summary><br><b>

서비스.
</b></details>

<details>
<summary>다음 파일이 어느 서비스와 어느 네임스페이스를 참조하고 있나요?

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: some-configmap
data:
  some_url: samurai.jack
```
</summary><br><b>

It's referencing the service "samurai" in the namespace called "jack".
</b></details>

<details>
<summary>네임스페이스에 생성할 수 없는 구성 요소는 무엇인가요?</code></summary><br><b>

볼륨(Volume)과 노드(Node).
</b></details>

<details>
<summary>네임스페이스에 속한 모든 구성 요소를 어떻게 나열하나요?</code></summary><br><b>

`kubectl api-resources --namespaced=true`
</b></details>

<details>
<summary>네임스페이스에서 구성 요소를 어떻게 생성하나요?</code></summary><br><b>

한 가지 방법은 `--namespace`를 지정하는 것입니다: `kubectl apply -f my_component.yaml --namespace=some-namespace`
다른 방법은 YAML 파일 자체에 지정하는 것입니다:

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: some-configmap
  namespace: some-namespace
```

그리고 `kubectl get configmap -n some-namespace`로 확인할 수 있습니다.
</b></details>

<details>
<summary>기존 파드에서 "ls" 명령을 어떻게 실행하나요?</code></summary><br><b>

kubectl exec some-pod -it -- ls
</b></details>

<details>
<summary>디플로이먼트를 노출하는 서비스를 어떻게 생성하나요?</code></summary><br><b>

kubectl expose deploy some-deployment --port=80 --target-port=8080
</b></details>

<details>
<summary>한 명령으로 파드와 서비스를 어떻게 생성하나요?</code></summary><br><b>

kubectl run nginx --image=nginx --restart=Never --port 80 --expose
</b></details>

<details>
<summary><code>kubectl create deployment kubernetes-httpd --image=httpd</code> 명령은 구체적으로 무엇을 하는지 자세히 설명하세요</summary><br><b>
</b></details>

<details>
<summary>파드는 레플리카셋으로도 실행할 수 있는데, 왜 디플로이먼트를 생성하나요?</summary><br><b>
</b></details>

<details>
<summary>특정 네임스페이스에 속하지 않는 리소스 목록을 어떻게 얻나요?</code></summary><br><b>

kubectl api-resources --namespaced=false
</b></details>

<details>
<summary>"Running" 상태가 아닌 모든 파드를 어떻게 삭제하나요?</code></summary><br><b>

kubectl delete pods --field-selector=status.phase!='Running'
</b></details>

<details>
<summary>파드의 리소스 사용량을 어떻게 표시하나요?</summary><br><b>

kubectl top pod
</b></details>

<details>
<summary>일반적인 질문이지만, 어떤 파드에 문제가 있는 것 같습니다. 정확히 무엇인지는 모릅니다. 어떻게 하시겠습니까?</summary><br><b>

파드 상태를 조사하는 것으로 시작합니다. `kubectl get pods` 명령을 사용할 수 있습니다(--all-namespaces는 시스템 네임스페이스의 파드에 대해).<br>

"Error" 상태를 본다면, `kubectl describe pod [name]` 명령을 실행하여 더 자세히 디버깅할 수 있습니다. 여전히 유용한 정보가 없다면 로그 추적을 위해 stern을 시도할 수 있습니다.<br>

파드 또는 시스템에 일시적인 문제가 있었다는 것을 알아낸 경우, 다음과 같이 파드를 재시작해볼 수 있습니다. `kubectl scale deployment [name] --replicas=0`<br>

복제본을 0으로 설정하면 프로세스가 중단됩니다. 이제 `kubectl scale deployment [name] --replicas=1`로 다시 시작합니다.
</b></details>

<details>
<summary>파드가 너무 많은 메모리를 사용할 때(제한을 초과할 때) 어떤 일이 발생하나요? (메모리 제한을 초과하는 경우)</summary><br><b>

종료될 후보가 됩니다.
</b></details>

<details>
<summary>롤백이 어떻게 작동하는지 자세히 설명하세요</summary><br><b>
</b></details>

<details>
<summary>다음 문장이 참인지 거짓인지 판별하시오. 메모리는 압축 가능한 리소스이므로, 컨테이너가 메모리 제한에 도달하더라도 계속 실행됩니다</summary><br><b>

거짓. CPU는 압축 가능한 리소스인 반면, 메모리는 압축 불가능한 리소스입니다 - 컨테이너가 메모리 제한에 도달하면 종료됩니다.
</b></details>

### Operators

<details>
<summary>Operator란 무엇인가요?</summary><br><b>

[여기](https://kubernetes.io/docs/concepts/extend-kubernetes/operator)에서 설명된 것처럼,

"Operators는 사용자 정의 리소스를 사용하여 애플리케이션 및 그 구성 요소를 관리하는 Kubernetes의 소프트웨어 확장입니다. Operators는 Kubernetes의 원칙을 따르며, 특히 제어 루프를 사용합니다."

더 간단한 말로, Operator는 Kubernetes의 사용자 정의 제어 루프로 생각할 수 있습니다.
</b></details>

<details>
<summary>왜 Operators가 필요한가요?</summary><br><b>

상태 비저장 애플리케이션을 관리하는 것은 상태 저장 애플리케이션을 관리하는 것만큼 간단하지 않습니다. 상태 비저장 애플리케이션에서는 모든 복제본에 대해 원하는 상태에 도달하고 업그레이드하는 것이 동일한 방식으로 처리됩니다. 상태 저장 애플리케이션에서는 각 복제본을 업그레이드하는 데 상태 저장 애플리케이션의 상태 저장 특성으로 인해 다른 처리가 필요할 수 있습니다. 각 복제본은 다른 상태에 있을 수 있습니다. 결과적으로, 상태 저장 애플리케이션을 관리하기 위해 종종 인간 운영자가 필요합니다. Kubernetes Operator는 이와 관련된 작업을 돕기 위해 존재합니다.

이는 또한 여러 Kubernetes 클러스터에서 표준 프로세스를 자동화하는 데 도움이 됩니다.
</b></details>

<details>
<summary>Operator는 어떤 구성 요소로 구성되어 있나요?</summary><br><b>

1. CRD (Custom Resource Definition) - Kubernetes 리소스(디플로이먼트, 파드, 서비스 등)에 익숙하실 겁니다. CRD도 리소스이지만, Operator를 개발하는 개발자가 정의하는 리소스입니다.
2. 컨트롤러 - CRD에 대해 실행되는 사용자 정의 제어 루프

</b></details>

<details>
<summary>CRD를 설명하세요</summary><br><b>

CRD는 Custom Resource Definitions입니다. 이는 사용자 정의 Kubernetes 구성 요소로, K8s API를 확장합니다.

TODO(abregman): add more info.

</b></details>

<details>
<summary>Operator는 어떻게 작동하나요?</summary><br><b>

이것은 일반적으로 Kubernetes에 의해 사용되는 제어 루프를 사용합니다. 이것은 애플리케이션 상태의 변화를 감시합니다. 차이점은 사용자 정의 제어 루프를 사용한다는 것입니다.

또한, CRD(사용자 정의 리소스 정의)를 사용하므로 기본적으로 Kubernetes API를 확장합니다.

</b></details>

<details>
<summary>다음 문장이 참인지 거짓인지 판별하시오. Kubernetes Operator는 상태 유지 애플리케이션에 사용됩니다</summary><br><b>

True
</b></details>

<details>
<summary>OLM(Operator Lifecycle Manager)이 무엇이며 어떻게 사용되는지 설명하십시오</summary><br><b>

</b></details>

<details>
<summary>Operator Framework이란 무엇인가요?</summary><br><b>

K8s 네이티브 애플리케이션을 관리하는 오픈 소스 툴킷으로, 자동화되고 효율적인 방식으로 운영자를 관리합니다.

</b></details>

<details>
<summary>Operator Framework는 어떤 구성 요소로 이루어져 있습니까?</summary><br><b>

1. Operator SDK - 개발자가 운영자를 만들 수 있게 해줍니다
2. Operator Lifecycle Manager - 운영자의 전체 수명주기를 설치, 업데이트 및 일반적으로 관리하는 데 도움을 줍니다
3. Operator Metering - 전문 서비스를 제공하는 운영자에 대한 사용 보고를 가능하게 합니다
4. 
</b></details>

<details>
<summary>Operator Lifecycle Manager에 대해 자세히 설명하십시오</summary><br><b>

이것은 Operator Framework의 일부로, 운영자의 수명주기를 관리하는 데 사용됩니다. 기본적으로 Kubernetes를 확장하여 사용자가 선언적 방식으로 운영자(설치, 업그레이드, ...)를 관리할 수 있게 합니다.

</b></details>

<details>
<summary>openshift-operator-lifecycle-manager 네임스페이스에는 무엇이 포함되어 있습니까?</summary><br><b>

이에는 다음이 포함됩니다:

  * catalog-operator - ClusterServiceVersions 리소스가 지정하는 리소스를 해결하고 설치합니다.
  * olm-operator - ClusterServiceVersion 리소스로 정의된 애플리케이션을 배포합니다

</b></details>

<details>
<summary>kubconfig란 무엇이며 어떻게 사용합니까?</summary><br><b>
  
kubeconfig 파일은 kubectl 커맨드라인 도구(또는 다른 클라이언트)와 함께 사용될 때 Kubernetes에 대한 접근을 구성하는 데 사용되는 파일입니다.
클러스터, 사용자, 네임스페이스 및 인증 메커니즘에 대한 정보를 정리하는 데 kubeconfig 파일을 사용합니다.
</b></details>

<details>
<summary>운영자를 생성하기 위해 Helm, Go 또는 다른 것을 사용하시겠습니까?</summary><br><b>
  
운영자의 범위와 성숙도에 따라 다릅니다. 주로 설치 및 업그레이드를 다루는 경우 Helm이 충분할 수 있습니다. 수명주기 관리, 인사이트 및 자동 조종을 원한다면 Go를 사용할 가능성이 높습니다.
</b></details>

<details>
<summary>운영자를 구축하기 위해 사용하는 도구나 프로젝트는 무엇입니까?</summary><br><b>

이것은 개인적인 경험과 취향에 더 기반을 두고 있습니다...

* Operator Framework
* Kubebuilder
* Controller Runtime
...
</b></details>

### Secrets

<details>
<summary>Kubernetes Secrets에 대해 설명하십시오</summary><br><b>

Secrets는 민감한 정보(비밀번호, SSH 키 등)를 저장하고 관리하는 데 사용됩니다.

</b></details>

<details>
<summary>키와 값으로 Secret을 생성하는 방법은 무엇입니까?</summary><br><b>

`kubectl create secret generic some-secret --from-literal=password='donttellmypassword'`

</b></details>

<details>
<summary>파일에서 Secret을 생성하는 방법은 무엇입니까?</summary><br><b>

`kubectl create secret generic some-secret --from-file=/some/file.txt`
</b></details>

<details>
<summary>Secret 파일에서 <code>type: Opaque</code>가 의미하는 것은 무엇입니까? 다른 타입은 무엇이 있습니까?</summary><br><b>

Opaque는 키-값 쌍에 대해 사용되는 기본 타입입니다.
</b></details>

<details>
<summary>다음 문장이 참인지 거짓인지 판별하시오. Secret 구성 요소에 데이터를 저장하면 자동으로 보안이 유지됩니다</summary><br><b>

거짓. "암호화"와 같은 일부 알려진 보안 메커니즘이 기본적으로 활성화되어 있지 않습니다.
</b></details>

<details>
<summary>다음 Secret 파일의 문제점은 무엇입니까:

```yaml
apiVersion: v1   
kind: Secret
metadata:
    name: some-secret
type: Opaque
data:
    password: mySecretPassword
```
</summary><br><b>

비밀번호가 암호화되지 않았습니다.
다음과 같이 실행해야 합니다: `echo -n 'mySecretPassword' | base64`를 실행하고 일반 텍스트를 사용하는 대신 결과를 파일에 붙여넣어야 합니다.

</b></details>

<details>
<summary>Deployment 파일의 다음 항목은 무엇을 의미하나요?

```yaml
spec:
  containers:
    - name: USER_PASSWORD
      valueFrom:
        secretKeyRef:
          name: some-secret
          key: password
```
</summary><br><b>

USER_PASSWORD 환경 변수는 "some-secret" 시크릿에 있는 'password' 키의 값을 저장합니다.
즉, Kubernetes 시크릿의 값을 참조합니다.

</b></details>

<details>
<summary>Git에 시크릿을 커밋하는 방법과 일반적으로 암호화된 시크릿을 사용하는 방법은 무엇인가요?</summary><br><b>

가능한 프로세스 중 하나는 다음과 같습니다.

1. Kubernetes 시크릿을 생성합니다(커밋하지는 않음).
2. 일부 타사 프로젝트(예: kubeseal)를 사용하여 암호화합니다.
3. 봉인/암호화된 시크릿을 적용합니다.
4. 봉인된 시크릿을 Git에 커밋합니다.
5. 시크릿이 필요한 애플리케이션을 배포하면 Bitnami Sealed 비밀 컨트롤러 등을 사용하여 자동으로 해독될 수 있습니다.
</b></details>

### Volumes

<details>
<summary>참인가 거짓인가? Kubernetes는 기본적으로 데이터 지속성을 제공하므로 Pod를 다시 시작하면 데이터가 저장됩니다.</summary><br><b>

거짓
</b></details>

<details>
<summary>"영구 볼륨"에 대해 설명하세요. 왜 필요한가요?</summary><br><b>

영구 볼륨을 사용하면 데이터를 저장할 수 있으므로 기본적으로 포드 수명 주기에 의존하지 않는 스토리지를 제공합니다.
</b></details>

<details>
<summary>참인가 거짓인가? Pod는 어느 노드에서나 다시 시작할 수 있으므로 모든 노드에서 영구 볼륨을 사용할 수 있어야 합니다.</summary><br><b>

참
</b></details>

<details>
<summary>영구 볼륨에는 어떤 유형이 있나요?</summary><br><b>

* NFS
* iSCSI
* CephFS
* ...
</b></details>

<details>
<summary>PertantVolumeClaim이란 무엇입니까?</summary><br><b>
</b></details>

<details>
<summary>볼륨 스냅샷 설명</summary><br><b>
  
볼륨 스냅샷을 사용하면 특정 시점에 볼륨의 복사본을 생성할 수 있습니다.
</b></details>

<details>
<summary>참인가 거짓인가? Kubernetes는 데이터 지속성을 관리합니다</summary><br><b>

거짓
</b></details>

<details>
<summary>스토리지 클래스를 설명하시오</summary><br><b>
</b></details>

<details>
<summary>"동적 프로비저닝" 및 "정적 프로비저닝" 설명</summary><br><b>
  
주요 차이점은 스토리지를 구성하려는 순간에 따라 다릅니다. 예를 들어 볼륨에 데이터를 미리 채워야 하는 경우 정적 프로비저닝을 선택합니다. 반면, 필요에 따라 볼륨을 생성해야 한다면 동적 프로비저닝을 선택하세요.
</b></details>

<details>
<summary>액세스 모드를 설명하시오</summary><br><b>
</b></details>

<details>
<summary>CSI 볼륨 복제란 무엇입니까?</summary><br><b>
</b></details>

<details>
<summary>"임시 볼륨"을 설명하시오</summary><br><b>
</b></details>

<details>
<summary>Kubernetes는 어떤 유형의 임시 볼륨을 지원하나요?</summary><br><b>
</b></details>

<details>
<summary>Reclaim policy란 무엇입니까?</summary><br><b>
</b></details>

<details>
<summary>Reclaim policy에는 어떤 것들이 있나요?</summary><br><b>

* Retain
* Recycle
* Delete
</b></details>

### 접근 제어

<details>
<summary>RBAC이란 무엇인가요?</summary><br><b>
 
Kubernetes의 RBAC는 특정 사용자 또는 사용자 그룹이 클러스터 또는 클러스터의 특정 네임스페이스에 있는 Kubernetes 개체와 상호 작용할 수 있는 방법을 정의하는 세분화된 특정 권한 집합을 구성할 수 있는 메커니즘입니다.
</b></details>

<details>
<summary><code>Role</code>과 <code>RoleBinding"</code> 오브젝트를 설명하세요</summary><br><b>
</b></details>

<details>
<summary><code>Role</code>과 <code>ClusterRole</code> 오브젝트의 차이점은 무엇인가요?</summary><br><b>
  
차이점은 Role은 네임스페이스 수준에서 사용되는 반면 ClusterRole은 클러스터 전체에 사용된다는 것입니다.
</b></details>

<details>
<summary>'서비스 계정'이 무엇인지, 어떤 시나리오에서 서비스 계정을 생성/사용하는지 설명하세요</summary><br><b>

[Kubernetes.io](https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account): "서비스 계정은 Pod에서 실행되는 프로세스에 대한 ID를 제공합니다."

언제 사용하는지에 대한 예:
이미지를 빌드하고 푸시해야 하는 파이프라인을 정의합니다. 푸시 이미지를 빌드할 수 있는 충분한 권한을 가지려면 해당 파이프라인에 충분한 권한이 있는 서비스 계정이 필요합니다.
</b></details>

<details>
<summary>포드를 생성하고 서비스 계정을 지정하지 않으면 어떻게 되나요?</summary><br><b>

포드는 기본 서비스 계정(포드가 실행 중인 네임스페이스)으로 자동 할당됩니다.
</b></details>

<details>
<summary>서비스 계정이 사용자 계정과 어떻게 다른지 설명</summary><br><b>

   - 사용자 계정은 전역적이지만 서비스 계정은 네임스페이스별로 고유합니다.
   - 사용자 계정은 인간 또는 클라이언트 프로세스를 위한 반면, 서비스 계정은 포드에서 실행되는 프로세스를 위한 것입니다.
</b></details>

<details>
<summary>서비스 계정을 나열하는 방법은 무엇입니까?</summary><br><b>

`kubectl get serviceaccounts`
</b></details>

<details>
<summary>"Security Context"에 대해 설명하시오.</summary><br><b>

[kubernetes.io](https://kubernetes.io/docs/tasks/configure-pod-container/security-context): "보안 컨텍스트는 포드 또는 컨테이너에 대한 권한 및 액세스 제어 설정을 정의합니다."
</b></details>

### Patterns



### CronJob

<details>
<summary>CronJob이 무엇이고 어떤 용도로 사용되는지 설명하세요.</summary><br><b>
  
CronJob은 반복 일정에 따라 작업을 생성합니다. 하나의 CronJob 개체는 crontab(cron 테이블) 파일의 한 줄과 같습니다. Cron 형식으로 작성된 지정된 일정에 따라 주기적으로 작업을 실행합니다.
</b></details>

<details>
<summary>다음 사양을 사용할 때 발생할 수 있는 문제와 해결 방법은 무엇입니까?

```yaml
apiVersion: batch/v1beta1
kind: CronJob
metadata:
  name: some-cron-job
spec:
  schedule: '*/1 * * * *'
  startingDeadlineSeconds: 10
  concurrencyPolicy: Allow
```
</summary><br><b>

크론 작업이 실패하면 "Allow"인 "concurrencyPolicy" 값으로 인해 다음 작업이 이전 작업을 대체하지 않습니다. 계속해서 새로운 작업이 생성되므로 결국 시스템은 실패한 크론 작업으로 가득 차게 됩니다.
이러한 문제를 방지하려면 "concurrencyPolicy" 값이 "Replace" 또는 "Forbid"여야 합니다.
</b></details>

<details>
<summary>다음 CronJob을 사용하면 어떤 문제가 발생할 수 있으며 어떻게 해결하나요?

```yaml
apiVersion: batch/v1beta1
kind: CronJob
metadata:
  name: "some-cron-job"
spec:
  schedule: '*/1 * * * *'
jobTemplate:
  spec:
    template:
      spec:
      restartPolicy: Never
      concurrencyPolicy: Forbid
      successfulJobsHistoryLimit: 1
      failedJobsHistoryLimit: 1
```
</summary><br><b>

템플릿 아래에 다음 줄을 배치합니다.

```yaml
concurrencyPolicy: Forbid
successfulJobsHistoryLimit: 1
failedJobsHistoryLimit: 1
```

결과적으로 이 구성은 cron job 사양의 일부가 아니므로 cron job에는 OOM과 같은 문제를 일으키고 잠재적으로 API 서버가 다운될 수 있는 제한이 없습니다.<br>
이 문제를 해결하려면 위 예의 "schedule" 지시어 위나 아래에 있는 cron job spec에 이 줄을 배치해야 합니다.
</b></details>

###  기타

<details>
<summary>명령형 관리와 선언적 관리 설명</summary><br><b>

</b></details>

<details>
<summary>Kubernetes 서비스 검색의 의미 설명</summary><br><b>
</b></details>

<details>
<summary>하나의 Kubernetes 클러스터와 이를 사용하려는 여러 팀이 있습니다. 클러스터에서 각 팀이 소비하는 리소스를 제한하고 싶습니다. 이를 위해 어떤 Kubernetes 개념을 사용하시겠습니까?</summary><br><b>

네임스페이스를 사용하면 리소스를 제한할 수 있으며 클러스터에서 작업할 때(예: 동일한 이름의 앱 생성) 팀 간에 충돌이 없는지 확인할 수 있습니다.
</b></details>

<details>
<summary>Kube 프록시의 기능</summary><br><b>
   Kube 프록시는 클러스터의 각 노드에서 실행되는 네트워크 프록시로, Kubernetes 서비스 개념의 일부를 구현합니다.
</b></details>

<details>
<summary>"Resources Quotas"은 무엇이며 어떻게 사용됩니까?</summary><br><b>
</b></details>

<details>
<summary>ConfigMap 설명</summary><br><b>

포드와 설정을 분리합니다.
설정은 언제든 변경해야 할 수 있는데, 애플리케이션을 다시 시작하거나 이미지를 다시 빌드하지 않고 ConfigMap을 변경해서 적용할 수 있어 유용합니다.

전반적으로 다음과 같은 경우에 좋습니다.
* 서로 다른 포드 간에 동일한 설정 공유
* 포드 설정을 외부에 저장
</b></details>

<details>
<summary>ConfigMap을 사용하는 방법</summary><br><b>

1. 만들기(키 및 값, 파일 또는 환경 파일에서)
2. 부착하세요. ConfigMap을 볼륨으로 마운트
</b></details>

<details>
<summary>참인가 거짓인가? 자격 증명과 같은 민감한 데이터는 ConfigMap에 저장해야 합니다</summary><br><b>

거짓. 시크릿을 사용하세요.
</b></details>

<details>
<summary>'Horizontal Pod Autoscaler'를 설명하시오</summary><br><b>

Kubernetes에서 HorizonPodAutoscaler는 수요에 맞게 워크로드를 자동으로 확장하기 위해 워크로드 리소스를 자동으로 업데이트합니다.
</b></details>

<details>
<summary>포드를 삭제하면 즉시 삭제되나요? (명령을 실행한 후 잠시 후)</summary><br><b>
</b></details>

<details>
<summary>클라우드 네이티브라는 것은 무엇을 의미하나요?</summary><br><b>
   클라우드 네이티브라는 용어는 클라우드 제공 모델이 제공하는 분산 컴퓨팅을 활용하기 위해 애플리케이션을 구축하고 실행하는 개념을 나타냅니다.
</b></details>

<details>
<summary>Kubernetes와 관련하여 인프라의 애완동물 및 가축 접근 방식을 설명합니다.</summary><br><b>
</b></details>

<details>
<summary>K8s에서 공개 URL을 통해 접근할 수 있는 컨테이너화된 웹 앱을 실행하는 방법을 설명하세요.</summary><br><b>
</b></details>

<details>
<summary>일부 애플리케이션에 더 이상 접근할 수 없는 경우 클러스터를 어떻게 트러블슈팅하시겠습니까?</summary><br><b>
</b></details>

<details>
<summary>Kubernetes 세계에는 어떤 CustomResourceDefinition이 있는지 설명하세요. 어떤 용도로 사용할 수 있나요?</summary><br><b>
</b></details>

<details>
<summary> Kubernetes에서 예약은 어떻게 작동하나요?</summary><br><b>

컨트롤 플레인 구성요소 kube-scheduler는 다음과 같은 질문을 합니다.
1. 무엇을 예약할 것인가? 포드 정의 사양을 이해하려고 시도합니다.
2. 어느 노드에 예약할 것인가? 포드를 회전시키기 위해 사용 가능한 리소스가 있는 최상의 노드를 결정하려고 시도합니다.
3. Pod를 특정 노드에 바인딩합니다.

자세한 내용은 [여기](https://www.youtube.com/watch?v=rDCWxkvPlAw)에서 확인하세요.
</b></details>

<details>
<summary> 라벨과 선택기는 어떻게 사용되나요?</summary><br><b>
</b></details>

<details>
<summary>QoS 클래스에는 어떤 것들이 있나요?</summary><br><b>

* Guaranteed
* Burstable
* BestEffort
</b></details>

<details>
<summary>레이블을 설명하세요. 그것들은 무엇이며 왜 사용합니까?</summary><br><b>
  
Kubernetes 레이블은 식별 메타데이터를 Kubernetes 객체와 연결할 수 있는 키-값 쌍입니다.
</b></details>

<details>
<summary>셀렉터를 설명하시오</summary><br><b>
</b></details>

<details>
<summary>Kubeconfig란 무엇입니까?</summary><br><b>
</b></details>

### Gatekeeper

<details>
<summary>게이트키퍼란 무엇인가요?</summary><br><b>

[Gatekeeper 문서](https://open-policy-agent.github.io/gatekeeper/website/docs): "Gatekeeper는 Open Policy Agent에 의해 실행되는 CRD 기반 정책을 시행하는 검증(변형 TBA) 웹훅입니다."
</b></details>

<details>
<summary>Gatekeeper 작동 방식을 설명하시오</summary><br><b>

Kubernetes 클러스터로 전송되는 모든 요청에서 Gatekeeper는 정책과 리소스를 OPA(Open Policy Agent)로 전송하여 정책을 위반하는지 확인합니다. 위반한다면 Gatekeeper는 정책 오류 메시지를 반환합니다. 정책을 위반하지 않으면 요청이 클러스터에 도달합니다.
</b></details>

### 정책 테스트

<details>
<summary>Conftest라는 게 무엇인가요?</summary><br><b>

Conftest를 사용하면 구조화된 파일에 대한 테스트를 작성할 수 있습니다. Kubernetes 리소스에 대한 테스트 라이브러리라고 생각하면 됩니다.<br>
CI 파이프라인이나 로컬 훅과 같은 테스트 환경에서 주로 사용됩니다.
</b></details>

<details>
<summary>Datree란 무엇인가요? Conftest와 어떻게 다른가요?</summary><br><b>

Conftest와 마찬가지로 정책 테스트 및 시행에 사용됩니다. 차이점은 기본 제공 정책이 있다는 것입니다.
</b></details>

### 헬름

<details>
<summary>What is Helm?</summary><br><b>

Package manager for Kubernetes. Basically the ability to package YAML files and distribute them to other users and apply them in the cluster(s).

As a concept it's quite common and can be found in many platforms and services. Think for example on package managers in operating systems. If you use Fedora/RHEL that would be dnf. If you use Ubuntu then, apt. If you don't use Linux, then a different question should be asked and it's why? but that's another topic :)
</b></details>

<details>
<summary>Why do we need Helm? What would be the use case for using it?</summary><br><b>

Sometimes when you would like to deploy a certain application to your cluster, you need to create multiple YAML files/components like: Secret, Service, ConfigMap, etc. This can be tedious task. So it would make sense to ease the process by introducing something that will allow us to share these bundle of YAMLs every time we would like to add an application to our cluster. This something is called Helm.

A common scenario is having multiple Kubernetes clusters (prod, dev, staging). Instead of individually applying different YAMLs in each cluster, it makes more sense to create one Chart and install it in every cluster.

Another scenario is, you would like to share what you've created with the community. For people and companies to easily deploy your application in their cluster.
</b></details>

<details>
<summary>"헬름 차트"에 대해 설명하시오</summary><br><b>

Helm Charts는 YAML 파일 묶음입니다. 리포지토리에서 사용하거나 직접 생성하여 리포지토리에 게시할 수 있는 번들입니다.
</b></details>

<details>
<summary>Helm도 Templating Engine이라고 합니다. 무슨 뜻인가요?</summary><br><b>

이는 애플리케이션이 여럿 있고 대체로 비슷한데, 설정 파일만 대동소이한 시나리오에 유용합니다. Helm을 사용하면 모든 항목에 대한 공통 청사진을 정의할 수 있으며 고정되지 않고 변경되는 값은 자리 표시자가 될 수 있습니다. 이를 템플릿 파일이라고 하며 이런 식으로 생겼습니다.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: {{ .Values.name }}
spec:
  containers:
  - name: {{ .Values.container.name }}
  image: {{ .Values.container.image }}
  port: {{ .Values.container.port }}
```

값 자체는 별도의 파일에 있습니다.

```yaml
name: some-app
container:
  name: some-app-container
  image: some-app-image
  port: 1991
```
</b></details>

<details>
<summary>Helm 템플릿 파일을 사용하는 사례에는 어떤 것이 있나요?</summary><br><b>

* 여러 다른 환경에 동일한 애플리케이션 배포
* CI/CD
</b></details>

<details>
<summary>Helm 차트 디렉토리 구조를 설명하시오</summary><br><b>
```dir
someChart/ -> 차트 이름
   Chart.yaml -> 차트의 메타 정보
   value.yaml -> 템플릿 파일의 값
   charts/ -> 차트 종속성
   templates/ -> 템플릿 파일 :)
```
</b></details>

<details>
<summary>Helm은 릴리즈 관리를 어떻게 지원하나요?</summary><br><b>

Helm을 사용하면 이전 버전의 차트로 업그레이드, 제거 및 롤백할 수 있습니다. Helm 버전 2에서는 "Tiller"라는 기능이 사용되었습니다만, 버전 3에서는 보안 문제로 제거되었습니다.
</b></details>

#### 명령어

<details>
<summary>차트는 어떻게 검색하나요?</summary><br><b>

`helm search hub [some_keyword]`
</b></details>

<details>
<summary>차트를 설치할 때 value.yaml 파일의 값을 재정의할 수 있나요?</summary><br><b>
예. 다른 값 파일을 전달할 수 있습니다.
`helm install --values=override-values.yaml [CHART_NAME]`

또는 명령줄에서 직접: `helm install --set some_key=some_value`
</b></details>

<details>
<summary>배포된 릴리즈를 어떻게 나열합니까?</summary><br><b>

`helm ls`나 `helm list`
</b></details>

<details>
<summary>롤백은 어떻게 하나요?</summary><br><b>

`helm rollback RELEASE_NAME REVISION_ID`
</b></details>

<details>
<summary>How to view revision history for a certain release?</summary><br><b>

`helm history RELEASE_NAME`
</b></details>

<details>
<summary>How to upgrade a release?</summary><br><b>

`helm upgrade RELEASE_NAME CHART_NAME`
</b></details>

### 보안

<details>
<summary>Kubernetes 클러스터와 관련한 보안 최선의 방법은 무엇입니까?</summary><br><b>

  * 서비스 간 안전한 통신 보장 (예를 들어, 상호 TLS를 제공하는 Istio 사용)
  * 다양한 리소스를 논리적 그룹에 따라 별도의 네임스페이스로 분리
  * 지원되는 컨테이너 런타임 사용 (Docker를 사용하는 경우 사용을 중단하세요. CRI-O를 엔진으로, CLI로는 podman을 고려해 보세요)
  * 클러스터의 변경 사항을 적절하게 테스트 (예: Kubernetes의 잘못된 구성을 방지하기 위해 Datree 사용 고려)
  * 클러스터에서 누가 무엇을 할 수 있는지 제한 (예를 들어, OPA 게이트키퍼 사용)
  * NetworkPolicy를 사용하여 네트워크 보안 적용
  * 위협 모니터링을 위해 도구 사용 고려 (예: Falco)
</b></details>

### 문제 해결 시나리오

<details>
<summary><code>kubectl get pods</code> 명령을 실행했을 때, "Pending" 상태의 Pods가 보입니다. 어떻게 하시겠습니까?</summary><br><b>

가능한 해결 방법 중 하나는 `kubectl describe pod <pod 이름>`을 실행하여 자세한 정보를 얻는 것입니다.<br>
다음 중 하나가 나타날 수 있습니다:
  * 클러스터가 가득 찼습니다. 이 경우 클러스터를 확장하세요.
  * ResourcesQuota 제한에 도달했습니다. 이 경우 해당 제한을 수정할 수 있습니다
  * PersistentVolumeClaim 마운트가 대기 중인지 확인하세요

위의 조치가 도움이 되지 않는다면, 명령어(`get pods`)를 `-o wide` 옵션과 함께 실행하여 노드가 할당되었는지 확인하세요. 할당되지 않았다면, 스케줄러에 문제가 있을 수 있습니다.
</b></details>

<details>
<summary>Kubernetes에서 Pod에 실행중인 애플리케이션에 사용자가 접근할 수 없을 때, 문제는 무엇일까요? 어떻게 확인할까요?</summary><br><b>

가능한 해결 방법 중 하나는 Pod 상태를 확인하는 것부터 시작하는 것입니다.
1. Pod가 대기 중인가요? 그렇다면 `kubectl describe pod <pod 이름>`으로 원인을 확인하세요.
TODO: 이 부분을 마무리...
</b></details>

### Istio

<details>
<summary>Istio란 무엇이며, 어떤 용도로 사용됩니까?</summary><br><b>
  
Istio는 기업이 어디에서든 분산된, 마이크로서비스 기반 앱을 운영할 수 있도록 도와주는 오픈 소스 서비스 메쉬입니다. Istio를 통해 기업은 마이크로서비스를 보안하고, 연결하며, 모니터링함으로써 기업 앱을 더 빠르고 안전하게 현대화할 수 있습니다.
</b></details>

### 컨트롤러

<details>
<summary>컨트롤러란 무엇입니까?</summary><br><b>

[Kubernetes.io](https://kubernetes.io/docs/concepts/architecture/controller): "Kubernetes에서 컨트롤러는 클러스터의 상태를 감시하고 필요에 따라 변경을 만들거나 요청하는 제어 루프입니다. 각 컨트롤러는 현재 클러스터 상태를 원하는 상태에 더 가깝게 이동하려고 시도합니다."
</b></details>

<details>
<summary>잘 알고 있는 두 가지 컨트롤러를 말해주세요</summary><br><b>

1. 노드 컨트롤러: 클러스터의 노드를 관리합니다. 이 컨트롤러는 노드의 건강을 모니터링하는 것을 포함해 여러 가지 책임이 있습니다. 갑자기 노드에 접근할 수 없게 되면 해당 노드에서 실행 중인 모든 파드를 대피시키고 노드 상태를 그에 따라 표시합니다.
2. 복제 컨트롤러: 실행되어야 하는 파드 복제본의 상태를 모니터링합니다. 실행되어야 하는 파드의 수가 실제로 실행 중인지 확인합니다.
</b></details>

<details>
<summary>다양한 컨트롤러를 실행하고 설치하는 데 책임이 있는 프로세스는 무엇입니까?</summary><br><b>

Kube-Controller-Manager
</b></details>

<details>
<summary>제어 루프란 무엇이며, 어떻게 작동합니까?</summary><br><b>

[여기](https://www.youtube.com/watch?v=i9V4oCa5f9I)에서 설명됩니다.
</b></details>

<details>
<summary>제어 루프의 모든 단계/단계는 무엇입니까?</summary><br><b>

- 관찰 - 클러스터의 현재 상태를 파악
- 차이점 파악 - 현재 상태와 원하는 상태 사이에 차이가 있는지 확인
- 행동 - 현재 클러스터 상태를 원하는 상태로 만듦 (기본적으로 차이가 없는 상태에 도달)
</b></details>

### 스케줄러

<details>
<summary>참 또는 거짓? 스케줄러는 파드가 실행될 노드를 결정하는 것과 실제로 실행하는 것 둘 다 책임이 있습니다</summary><br><b>

거짓. 스케줄러는 파드가 실행될 노드를 선택하는 책임이 있지만, 실제로 파드를 실행하는 것은 Kubelet입니다.
</b></details>

<details>
<summary>"node1"이라는 노드에 파드를 스케줄하는 방법은 무엇입니까?
</summary><br><b>

`k run some-pod --image=redix -o yaml --dry-run=client > pod.yaml`

`vi pod.yaml`하고 추가하세요:

```yaml
spec:
  nodeName: node1
```

`k apply -f pod.yaml`

참고: 클러스터에 node1이 없으면 포드는 '보류 중' 상태로 유지됩니다.
</b></details>

#### 노드 선호도

<상세>
<summary>노드 선호도를 사용하여 키가 "region"이고 값이 "asia" 또는 "emea"인 노드에서 예약하도록 Pod를 설정합니다.</summary><br><b>

`vi pod.yaml`

```yaml
affinity:
  nodeAffinity:
    requiredDuringSchedlingIgnoredDuringExecution:
      nodeSelectorTerms:
      - matchExpressions:
        - key: region
          operator: In
          values:
          - asia
          - emea
```
</b></details>

<details>
<summary>노드 어피니티를 사용하여 키가 'region'이고 값이 'neverland'인 노드에서는 포드를 예약하지 않도록 설정합니다.</summary><br><b>

`vi pod.yaml`

```yaml
affinity:
  nodeAffinity:
    requiredDuringSchedlingIgnoredDuringExecution:
      nodeSelectorTerms:
      - matchExpressions:
        - key: region
          operator: NotIn
          values:
          - neverland
```
</b></details>

<details>
<summary>참 또는 거짓? 노드 친화성 유형 "requiredDuringSchedlingIgnoredDuringExecution"을 사용하는 것은 스케줄러가 규칙을 충족하지 않으면 스케줄할 수 없음을 의미합니다</summary><br><b>

참
</b></details>

<details>
<summary>참 또는 거짓? 노드 친화성 유형 "preferredDuringSchedlingIgnoredDuringExecution"을 사용하는 것은 스케줄러가 규칙을 충족하지 않으면 스케줄할 수 없음을 의미합니다</summary><br><b>

거짓. 스케줄러는 요구 사항/규칙을 충족하는 노드를 찾으려고 하며, 찾지 못할 경우에도 파드를 스케줄합니다.
</b></details>

<details>
<summary>여러 스케줄러를 배포할 수 있나요?</summary><br><b>

네, 가능합니다. 다음과 비슷한 명령어로 다른 파드를 실행할 수 있습니다:

```yaml
spec:
  containers:
  - command:
    - kube-scheduler
    - --address=127.0.0.1
    - --leader-elect=true
    - --scheduler-name=some-custom-scheduler
...
```
</b></details>

<details>
<summary>여러 스케줄러가 있다고 가정했을 때, 주어진 파드에 어떤 스케줄러가 사용되었는지 어떻게 알 수 있나요?</summary><br><b>

`kubectl get events`를 실행하면 어떤 스케줄러가 사용되었는지 볼 수 있습니다.
</b></details>

<details>
<summary>새로운 파드를 실행하고자 하며, 커스텀 스케줄러에 의해 스케줄되기를 원합니다. 이를 달성하기 위해 어떻게 해야 하나요?</summary><br><b>

파드의 spec에 다음을 추가하세요:

```yaml
spec:
  schedulerName: some-custom-scheduler
```
</b></details>

### Taints

<details>
<summary>"master" 노드에 taint가 있는지 확인하세요</summary><br><b>

`kubectl describe no master | grep -i taints`
</b></details>

<details>
<summary>클러스터의 노드 중 하나에 "app" 키와 "web" 값 및 "NoSchedule" 효과의 taint를 생성하세요. 적용되었는지 확인하세요</summary><br><b>

`kubectl taint node minikube app=web:NoSchedule`

`kubectl describe no minikube | grep -i taints`
</b></details>

<details>
<summary>클러스터의 유일한 노드인 minikube에 <code>kubectl taint node minikube app=web:NoSchedule</code>를 적용한 후 <code>kubectl run some-pod --image=redis</code>를 실행했습니다. 무슨 일이 일어날까요?</summary><br><b>

클러스터의 유일한 노드에 "app=web"의 taint가 있기 때문에 파드는 "Pending" 상태에 머물게 됩니다.
</b></details>

<details>
<summary>클러스터의 유일한 노드인 minikube에 <code>kubectl taint node minikube app=web:NoSchedule</code>를 적용한 후 <code>kubectl run some-pod --image=redis</code>를 실행했지만 파드가 pending 상태에 있습니다. 이를 해결하려면 어떻게 해야 할까요?</summary><br><b>

`kubectl edit po some-pod`를 실행하고 다음을 추가하세요

```yaml
  - effect: NoSchedule
    key: app
    operator: Equal
    value: web
```

종료하고 저장하세요. 이제 파드는 Running 상태가 되어야 합니다.
</b></details>

<details>
<summary>클러스터의 노드 중 하나에서 기존의 taint를 제거하세요</summary><br><b>

`kubectl taint node minikube app=web:NoSchedule-`
</b></details>

<details>
<summary>taint의 효과는 무엇이 있으며, 각각을 설명하세요</summary><br><b>
```md
`NoSchedule`: 특정 노드에 리소스가 예약되는 것을 방지합니다.
`PreferNoSchedule`: 특정 노드(해당 taint가 적용된 노드)에 리소스를 예약하기 전에 다른 노드에 먼저 리소스를 예약하려고 합니다.
`NoExecute`: "NoSchedule"을 적용해도 이미 노드에서 실행 중인 파드(또는 다른 리소스)를 추방하지 않지만, "NoExecute"는 이미 실행 중인 리소스를 노드에서 추방할 것입니다.
```
</b></details>

### 리소스 제한

<details>
<summary>파드와 관련하여 리소스 제한을 지정하는 이유를 설명하세요</summary><br><b>

* 앱이 소비해야 하는 RAM 및/또는 CPU의 양을 알고 있으며, 그 이상은 유효하지 않습니다.
* 클러스터에서 모든 사람이 앱을 실행할 수 있도록 하고, 리소스가 하나의 애플리케이션 유형에만 사용되지 않도록 하고 싶습니다.
</b></details>

<details>
<summary>다음 문장이 참인지 거짓인지 판별하시오. 파드 수준에서 적용된 리소스 제한은, 제한이 2GB RAM이고 파드에 두 개의 컨테이너가 있으면 각각 1GB RAM입니다</summary><br><b>

거짓. 컨테이너별로 적용되며 파드별로 적용되지 않습니다.
</b></details>

#### 리소스 제한 - 명령어

<details>
<summary>클러스터의 파드 중 하나에 리소스 제한이 있는지 확인하세요</summary><br><b>

`kubectl describe po <POD_NAME> | grep -i limits`
</b></details>

<details>
<summary>"python" 이미지를 사용하여 "yay"라는 이름의 파드를 실행하고, 리소스 요청으로 64Mi 메모리와 250m CPU를 지정하세요</summary><br><b>

`kubectl run yay --image=python --dry-run=client -o yaml > pod.yaml`

`vi pod.yaml`

```yaml
spec:
  containers:
  - image: python
    imagePullPolicy: Always
    name: yay
    resources:
      requests:
        cpu: 250m
        memory: 64Mi
```

`kubectl apply -f pod.yaml`
</b></details>

<details>
<summary>"python" 이미지를 사용하여 "yay2"라는 Pod를 실행합니다. 64Mi 메모리와 250m CPU의 리소스 요청이 있고 제한은 128Mi 메모리와 500m CPU인지 확인하세요.</summary><br><b>

`kubectl run yay2 --image=python --dry-run=client -o yaml > pod.yaml`

`vi pod.yaml`

```yaml
spec:
  containers:
  - image: python
    imagePullPolicy: Always
    name: yay2
    resources:
      limits:
        cpu: 500m
        memory: 128Mi
      requests:
        cpu: 250m
        memory: 64Mi
```

`kubectl apply -f pod.yaml`
</b></details>

### 모니터링

<details>
<summary>Kubernetes와 관련하여 어떤 모니터링 솔루션에 익숙하십니까?</summary><br><b>

Kubernetes를 위한 다양한 종류의 모니터링 솔루션이 있습니다. 일부는 오픈 소스이고, 일부는 메모리 내에 있으며, 일부는 비용이 듭니다... 여기 간단한 목록이 있습니다:

* metrics-server: 메모리 내 오픈 소스 모니터링
* datadog: 유료
* prometheus: 오픈 소스 모니터링 솔루션

</b></details>

<details>
<summary>귀하가 사용 중인 모니터링 솔루션이 Kubernetes를 어떻게 모니터링하는지 설명해주세요.</summary><br><b>

이것은 당신이 사용하기로 선택한 것에 매우 달려 있습니다. 몇 가지 솔루션을 살펴보겠습니다:

* metrics-server: kubelet의 cAdvisor 구성 요소를 사용하여 클러스터와 그 리소스에 대한 정보를 검색하고 메모리 내에 저장하는 오픈 소스이며 무료 모니터링 솔루션입니다.
설치 후 일정 시간이 지나면 `kubectl top node` 및 `kubectl top pod`와 같은 명령어를 실행하여 노드, 파드 및 기타 리소스의 성능 메트릭을 볼 수 있습니다.

TODO: 모니터링 솔루션을 더 많이 추가

</b></details>

### Kustomize

<details>
<summary>Kustomize란 무엇입니까?</summary><br><b>
</b></details>

<details>
<summary>실제 사용 사례를 설명하며 Kustomize의 필요성을 설명하십시오</summary><br><b>

* 조직 내 여러 팀에서 사용하는 애플리케이션의 헬름 차트가 있고, 애플리케이션에 해당 팀 소유를 명시하는 주석을 추가할 필요가 있습니다
  * Kustomize 없이는 파일(이 경우 차트 템플릿)을 복사하고 필요한 특정 주석을 포함하도록 수정해야 합니다
  * Kustomize를 사용하면 전체 저장소나 파일을 복사할 필요가 없습니다
* 원본 파일을 수정하지 않고 앱에 변경/패치를 적용하라는 요청을 받았습니다
  * Kustomize를 사용하면 원본 앱 파일을 만질 필요 없이 이러한 사용자 정의를 정의하는 kustomization.yml 파일을 정의할 수 있습니다
</b></details>

<details>
<summary>Kustomize가 어떻게 작동하는지 고급 수준에서 설명하십시오</summary><br><b>

1. 원하는 앱의 폴더에 kustomization.yml 파일을 추가합니다.
   1. 수행하고자 하는 사용자 정의를 정의합니다
2. kustomization.yml이 있는 APP_PATH에서 `kustomize build APP_PATH`를 실행합니다
</b></details>

### Deployment Strategies

<details>
<summary>어떤 롤아웃/배포 전략을 알고 계십니까?</summary><br><b>

* 블루/그린 배포: 앱의 새 버전을 배포하면서 기존 버전이 계속 실행 중이고, 새 버전의 앱으로 트래픽을 리디렉션하기 시작합니다
* 카나리 배포: 앱의 새 버전을 배포하고 사용자/트래픽의 **일부**를 새 버전으로 리디렉션합니다. 새 버전으로의 이전이 훨씬 점진적입니다
</b></details>

<details>
<summary>블루/그린 배포/롤아웃을 자세히 설명하십시오</summary><br><b>

블루/그린 배포 단계:

1. 사용자의 트래픽이 로드 밸런서를 통해 현재 버전 1인 애플리케이션으로 오고 있습니다

사용자 -> 로드 밸런서 -> 앱 버전 1

2. 새로운 애플리케이션 버전 2가 배포됩니다(버전 1은 여전히 실행 중)

사용자 -> 로드 밸런서 -> 앱 버전 1
                          앱 버전 2

3. 버전 2가 제대로 실행되면 트래픽이 버전 1 대신 버전 2로 전환됩니다

사용자 -> 로드 밸런서     앱 버전 1
                       -> 앱 버전 2

4. 이전 버전을 제거하거나 사용자가 리디렉션되지 않도록 계속 실행하는 것은 팀이나 회사의 결정에 따릅니다

장점:
  * 언제든지 이전 버전으로 빠르게 롤백/전환할 수 있습니다
단점:
  * 새 버전에 문제가 있는 경우, 모든 사용자가 영향을 받습니다(일부가 아닌)

</b></details>

<details>
<summary>카나리 배포/롤아웃을 자세히 설명하십시오</summary><br><b>

카나리 배포 단계:

1. 사용자의 트래픽이 로드 밸런서를 통해 현재 버전 1인 애플리케이션으로 오고 있습니다

사용자 -> 로드 밸런서 -> 앱 버전 1

2. 새로운 애플리케이션 버전 2가 배포됩니다(버전 1은 여전히 실행 중) 그리고 트래픽의 일부가 새 버전으로 리디렉션됩니다

사용자 -> 로드 밸런서 ->(95% 트래픽) 앱 버전 1
                       ->(5% 트래픽) 앱 버전 2

3. 새 버전(2)이 잘 실행되면 더 많은 트래픽이 그것으로 리디렉션됩니다

사용자 -> 로드 밸런서 ->(70% 트래픽) 앱 버전 1
                       ->(30% 트래픽) 앱 버전 2

3. 모든 것이 잘 실행되면, 어느 시점에 모든 트래픽이 새 버전으로 리디렉션됩니다

사용자 -> 로드 밸런서 -> 앱 버전 2

장점:
  * 새로 배포된 앱 버전에 문제가 있으면 모든 사용자가 아닌 일부 사용자만 영향을 받습니다
단점:
  * 사용자 트래픽이 존재하는 생산 환경에서 새 버전을 테스트해야 합니다(그곳에서만 테스트 가능)

</b></details>

<details>
<summary>Kubernetes에서 카나리, 블루/그린과 같은 배포 전략을 구현하는 방법에 대해 알고 있는 것은 무엇입니까?</summary><br><b>

여러 가지 방법이 있습니다. 그 중 하나는 Argo Rollouts입니다.
</b></details>

### 시나리오

<details>
<summary>조직의 엔지니어가 자신의 팀 리소스만 Kubernetes에서 보고 싶다고 말했습니다. 그러나 실제로는 여러 다른 팀의 전체 조직 리소스를 볼 수 있습니다. 이를 다루기 위해 어떤 Kubernetes 개념을 사용할 수 있습니까?</summary><br><b>

네임스페이스. 더 많은 정보를 위해 다음의 [네임스페이스 질문 및 답변](#namespaces-use-cases)을 참조하십시오.
</b></details>

<details>
<summary>팀의 엔지니어가 Pod를 실행했지만 "CrashLoopBackOff"라는 상태를 보고 있습니다. 이것은 무엇을 의미하며 문제를 어떻게 식별합니까?</summary><br><b>

컨테이너가 실행에 실패했고(다양한 이유로), Kubernetes는 일정 지연(= BackOff 시간) 후에 Pod를 다시 실행하려고 시도합니다.

실패할 수 있는 몇 가지 이유:
  - 잘못된 구성 - 철자 오류, 지원되지 않는 값 등
  - 사용 가능한 리소스 없음 - 노드가 다운되었거나 PV가 마운트되지 않은 경우 등

디버깅 방법:

1. `kubectl describe pod POD_NAME`
   1. `State` (대기 중, CrashLoopBackOff 상태여야 함)와 `Last State`에 주목하세요. 이는 이전에 무슨 일이 발생했는지(왜 실패했는지)를 알려줄 것입니다.
2. `kubectl logs mypod` 실행
   1. 이는 정확한 출력을 제공해야 합니다.
   2. 특정 컨테이너에 대해서는 `-c CONTAINER_NAME`을 추가할 수 있습니다.
</b></details>

<details>
<summary>귀하의 조직에서 한 엔지니어가 클러스터의 노드 중 하나에서 특정 라벨이 있는 파드(Pods)가 예약되는 것을 방지하는 방법이 있는지 물어봅니다. 당신의 답변은 다음과 같습니다:</summary><br><b>

네, 우리는 다음 명령어를 사용하여 라벨 "app=web"이 있는 모든 리소스가 node1에 예약되지 않도록 할 수 있습니다: `kubectl taint node node1 app=web:NoSchedule`
</b></details>

<details>
<summary>귀하가 클러스터에서 사용 중인 리소스의 수를 제한하고 싶습니다. 예를 들어, 4개의 레플리카셋, 2개의 서비스 등을 넘지 않도록 하려면 어떻게 해야 할까요?</summary><br><b>

ResourceQuotas 사용
</b></details>

<!-- {% endraw %} -->

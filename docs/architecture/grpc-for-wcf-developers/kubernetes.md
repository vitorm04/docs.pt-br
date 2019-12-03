---
title: Kubernetes-gRPC para desenvolvedores do WCF
description: Executando ASP.NET Core serviços gRPC em um cluster kubernetes.
ms.date: 09/02/2019
ms.openlocfilehash: 22271343f8f0d0454469b2f35e717f5b7e939294
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711282"
---
# <a name="kubernetes"></a><span data-ttu-id="c3f4f-103">Kubernetes</span><span class="sxs-lookup"><span data-stu-id="c3f4f-103">Kubernetes</span></span>

<span data-ttu-id="c3f4f-104">Embora seja possível executar contêineres manualmente em hosts do Docker, para sistemas de produção confiáveis, é melhor usar um mecanismo de orquestração de contêiner para gerenciar várias instâncias em execução em vários servidores em um cluster.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-104">Although it's possible to run containers manually on Docker hosts, for reliable production systems it's better to use a container orchestration engine to manage multiple instances running across several servers in a cluster.</span></span> <span data-ttu-id="c3f4f-105">Há vários mecanismos de orquestração de contêiner disponíveis, incluindo kubernetes, Docker Swarm e Apache mesos.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-105">There are various container orchestration engines available, including Kubernetes, Docker Swarm, and Apache Mesos.</span></span> <span data-ttu-id="c3f4f-106">Mas desses mecanismos, o kubernetes está longe e distante do mais usado, portanto, será o foco deste capítulo.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-106">But of these engines, Kubernetes is far and away the most widely used, so it will be the focus of this chapter.</span></span>

<span data-ttu-id="c3f4f-107">O kubernetes inclui a seguinte funcionalidade:</span><span class="sxs-lookup"><span data-stu-id="c3f4f-107">Kubernetes includes the following functionality:</span></span>

- <span data-ttu-id="c3f4f-108">O **agendamento** executa contêineres em vários nós em um cluster, garantindo o uso equilibrado do recurso disponível, mantendo os contêineres em execução se houver interrupções e manipulando atualizações sem interrupção para novas versões de imagens ou novas configurações.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-108">**Scheduling** runs containers on multiple nodes within a cluster, ensuring balanced usage of the available resource, keeping containers running if there are outages, and handling rolling updates to new versions of images or new configurations.</span></span>
- <span data-ttu-id="c3f4f-109">As **verificações de integridade** monitoram contêineres para garantir o serviço contínuo.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-109">**Health checks** monitor containers to ensure continued service.</span></span>
- <span data-ttu-id="c3f4f-110">O **DNS & descoberta de serviço** manipula o roteamento entre serviços em um cluster.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-110">**DNS & service discovery** handles routing between services within a cluster.</span></span>
- <span data-ttu-id="c3f4f-111">A **entrada** expõe os serviços selecionados externamente e geralmente fornece balanceamento de carga entre instâncias desses serviços.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-111">**Ingress** exposes selected services externally and generally provides load-balancing across instances of those services.</span></span>
- <span data-ttu-id="c3f4f-112">O **Gerenciamento de recursos** anexa recursos externos, como armazenamento a contêineres.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-112">**Resource management** attaches external resources like storage to containers.</span></span>

<span data-ttu-id="c3f4f-113">Este capítulo detalha como implantar um serviço de ASP.NET Core gRPC e um site que consome o serviço em um cluster kubernetes.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-113">This chapter will detail how to deploy an ASP.NET Core gRPC service and a website that consumes the service into a Kubernetes cluster.</span></span> <span data-ttu-id="c3f4f-114">O aplicativo de exemplo usado está disponível no repositório [dotnet-Architecture/grpc-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) no github.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-114">The sample application used is available in the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="kubernetes-terminology"></a><span data-ttu-id="c3f4f-115">Terminologia do kubernetes</span><span class="sxs-lookup"><span data-stu-id="c3f4f-115">Kubernetes terminology</span></span>

<span data-ttu-id="c3f4f-116">O kubernetes usa a *configuração de estado desejado*: a API é usada para descrever objetos como *pods*, *implantações*e *Serviços*, e o *plano de controle* cuida da implementação do estado desejado em todos os *nós* em um *cluster*.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-116">Kubernetes uses *desired state configuration*: the API is used to describe objects like *Pods*, *Deployments*, and *Services*, and the *Control Plane* takes care of implementing the desired state across all the *nodes* in a *cluster*.</span></span> <span data-ttu-id="c3f4f-117">Um cluster kubernetes tem um nó *mestre* que executa a *API kubernetes*, com a qual você pode se comunicar de forma programática ou usando a ferramenta de linha de comando `kubectl`.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-117">A Kubernetes cluster has a *Master* node that runs the *Kubernetes API*, which you can communicate with programmatically or by using the `kubectl` command-line tool.</span></span> <span data-ttu-id="c3f4f-118">`kubectl` pode criar e gerenciar objetos por meio de argumentos de linha de comando, mas funciona melhor com arquivos YAML que contêm dados de declaração para objetos kubernetes.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-118">`kubectl` can create and manage objects through command-line arguments, but it works best with YAML files that contain declaration data for Kubernetes objects.</span></span>

### <a name="kubernetes-yaml-files"></a><span data-ttu-id="c3f4f-119">Arquivos kubernetes YAML</span><span class="sxs-lookup"><span data-stu-id="c3f4f-119">Kubernetes YAML files</span></span>

<span data-ttu-id="c3f4f-120">Cada arquivo kubernetes YAML terá pelo menos três propriedades de nível superior:</span><span class="sxs-lookup"><span data-stu-id="c3f4f-120">Every Kubernetes YAML file will have at least three top-level properties:</span></span>

```yaml
apiVersion: v1
kind: Namespace
metadata:
  # Object properties
```

<span data-ttu-id="c3f4f-121">A propriedade `apiVersion` é usada para especificar qual versão (e qual API) o arquivo se destina.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-121">The `apiVersion` property is used to specify which version (and which API) the file is intended for.</span></span> <span data-ttu-id="c3f4f-122">A propriedade `kind` especifica o tipo de objeto que o YAML representa.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-122">The `kind` property specifies the kind of object the YAML represents.</span></span> <span data-ttu-id="c3f4f-123">A propriedade `metadata` contém propriedades de objeto como `name`, `namespace`e `labels`.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-123">The `metadata` property contains object properties like `name`, `namespace`, and `labels`.</span></span>

<span data-ttu-id="c3f4f-124">A maioria dos arquivos kubernetes YAML também terá uma seção `spec` que descreve os recursos e a configuração necessários para criar o objeto.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-124">Most Kubernetes YAML files will also have a `spec` section that describes the resources and configuration necessary to create the object.</span></span>

### <a name="pods"></a><span data-ttu-id="c3f4f-125">Pods</span><span class="sxs-lookup"><span data-stu-id="c3f4f-125">Pods</span></span>

<span data-ttu-id="c3f4f-126">Pods são as unidades básicas de execução no kubernetes.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-126">Pods are the basic units of execution in Kubernetes.</span></span> <span data-ttu-id="c3f4f-127">Eles podem executar vários contêineres, mas também são usados para executar contêineres únicos.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-127">They can run multiple containers, but they're also used to run single containers.</span></span> <span data-ttu-id="c3f4f-128">O pod também inclui todos os recursos de armazenamento exigidos pelos contêineres e o endereço IP da rede.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-128">The pod also includes any storage resources required by the containers, and the network IP address.</span></span>

### <a name="services"></a><span data-ttu-id="c3f4f-129">Serviços</span><span class="sxs-lookup"><span data-stu-id="c3f4f-129">Services</span></span>

<span data-ttu-id="c3f4f-130">Os serviços são metaobjetos que descrevem pods (ou conjuntos de Pods) e fornecem uma maneira de acessá-los no cluster, como o mapeamento de um nome de serviço para um conjunto de endereços IP Pod usando o serviço DNS do cluster.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-130">Services are meta-objects that describe Pods (or sets of Pods) and provide a way to access them within the cluster, such as mapping a service name to a set of pod IP addresses by using the cluster DNS service.</span></span>

### <a name="deployments"></a><span data-ttu-id="c3f4f-131">Implantações</span><span class="sxs-lookup"><span data-stu-id="c3f4f-131">Deployments</span></span>

<span data-ttu-id="c3f4f-132">As implantações são os objetos de *estado desejado* para pods.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-132">Deployments are the *desired state* objects for Pods.</span></span> <span data-ttu-id="c3f4f-133">Se você criar um pod manualmente, ele não será reiniciado quando for encerrado.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-133">If you create a pod manually, it won't be restarted when it terminates.</span></span> <span data-ttu-id="c3f4f-134">As implantações são usadas para informar ao cluster quais pods e quantas réplicas desses pods devem estar em execução no momento atual.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-134">Deployments are used to tell the cluster which Pods, and how many replicas of those Pods, should be running at the present time.</span></span>

### <a name="other-objects"></a><span data-ttu-id="c3f4f-135">Outros objetos</span><span class="sxs-lookup"><span data-stu-id="c3f4f-135">Other objects</span></span>

<span data-ttu-id="c3f4f-136">Os pods, serviços e implantações são apenas três dos tipos de objetos mais básicos.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-136">Pods, Services, and Deployments are just three of the most basic object types.</span></span> <span data-ttu-id="c3f4f-137">Há dezenas de outros tipos de objeto que são gerenciados por clusters kubernetes.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-137">There are dozens of other object types that are managed by Kubernetes clusters.</span></span> <span data-ttu-id="c3f4f-138">Para obter mais informações, consulte a documentação de [conceitos do kubernetes](https://kubernetes.io/docs/concepts/) .</span><span class="sxs-lookup"><span data-stu-id="c3f4f-138">For more information, see the [Kubernetes Concepts](https://kubernetes.io/docs/concepts/) documentation.</span></span>

### <a name="namespaces"></a><span data-ttu-id="c3f4f-139">{1&gt;Namespaces&lt;1}</span><span class="sxs-lookup"><span data-stu-id="c3f4f-139">Namespaces</span></span>

<span data-ttu-id="c3f4f-140">Os clusters kubernetes são projetados para dimensionar para centenas ou milhares de nós e para executar números semelhantes de serviços.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-140">Kubernetes clusters are designed to scale to hundreds or thousands of nodes and to run similar numbers of services.</span></span> <span data-ttu-id="c3f4f-141">Para evitar conflitos entre nomes de objeto, os namespaces são usados para agrupar objetos juntos como parte de aplicativos maiores.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-141">To avoid clashes between object names, namespaces are used to group objects together as part of larger applications.</span></span> <span data-ttu-id="c3f4f-142">Os próprios serviços do kubernetes são executados em um namespace `default`.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-142">Kubernetes's own services run in a `default` namespace.</span></span> <span data-ttu-id="c3f4f-143">Todos os objetos de usuário devem ser criados em seus próprios namespaces para evitar possíveis conflitos com objetos padrão ou outros locatários no cluster.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-143">All user objects should be created in their own namespaces to avoid potential clashes with default objects or other tenants in the cluster.</span></span>

## <a name="get-started-with-kubernetes"></a><span data-ttu-id="c3f4f-144">Introdução ao kubernetes</span><span class="sxs-lookup"><span data-stu-id="c3f4f-144">Get started with Kubernetes</span></span>

<span data-ttu-id="c3f4f-145">Se você estiver executando o Docker desktop para Windows ou o Docker desktop para Mac, o kubernetes já estará disponível.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-145">If you're running Docker Desktop for Windows or Docker Desktop for Mac, Kubernetes is already available.</span></span> <span data-ttu-id="c3f4f-146">Basta habilitá-lo na seção **kubernetes** da janela **configurações** :</span><span class="sxs-lookup"><span data-stu-id="c3f4f-146">Just enable it in the **Kubernetes** section of the **Settings** window:</span></span>

![Habilitar kubernetes no Docker desktop](media/kubernetes/enable-kubernetes-docker-desktop.png)

<span data-ttu-id="c3f4f-148">Para executar um cluster kubernetes local no Linux, considere [minikube](https://github.com/kubernetes/minikube)ou [MicroK8s](https://microk8s.io/) se sua distribuição do Linux oferecer suporte a [snaps](https://snapcraft.io/).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-148">To run a local Kubernetes cluster on Linux, consider [minikube](https://github.com/kubernetes/minikube), or [MicroK8s](https://microk8s.io/) if your Linux distribution supports [snaps](https://snapcraft.io/).</span></span>

<span data-ttu-id="c3f4f-149">Para confirmar se o cluster está em execução e acessível, execute o comando `kubectl version`:</span><span class="sxs-lookup"><span data-stu-id="c3f4f-149">To confirm that your cluster is running and accessible, run the `kubectl version` command:</span></span>

```console
kubectl version
Client Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.6", GitCommit:"96fac5cd13a5dc064f7d9f4f23030a6aeface6cc", GitTreeState:"clean", BuildDate:"2019-08-19T11:13:49Z", GoVersion:"go1.12.9", Compiler:"gc", Platform:"windows/amd64"}
Server Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.6", GitCommit:"96fac5cd13a5dc064f7d9f4f23030a6aeface6cc", GitTreeState:"clean", BuildDate:"2019-08-19T11:05:16Z", GoVersion:"go1.12.9", Compiler:"gc", Platform:"linux/amd64"}
```

<span data-ttu-id="c3f4f-150">Neste exemplo, a CLI do `kubectl` e o servidor kubernetes estão executando a versão 1.14.6.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-150">In this example, both the `kubectl` CLI and the Kubernetes server are running version 1.14.6.</span></span> <span data-ttu-id="c3f4f-151">Cada versão do `kubectl` deve dar suporte à versão anterior e à próxima do servidor, de modo que `kubectl` 1,14 também deve funcionar com as versões 1,13 e 1,15 do servidor.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-151">Each version of `kubectl` is supposed to support the previous and next version of the server, so `kubectl` 1.14 should work with server versions 1.13 and 1.15 as well.</span></span>

## <a name="run-services-on-kubernetes"></a><span data-ttu-id="c3f4f-152">Executar serviços no kubernetes</span><span class="sxs-lookup"><span data-stu-id="c3f4f-152">Run services on Kubernetes</span></span>

<span data-ttu-id="c3f4f-153">O aplicativo de exemplo tem um diretório `kube` que contém três arquivos YAML.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-153">The sample application has a `kube` directory that contains three YAML files.</span></span> <span data-ttu-id="c3f4f-154">O arquivo de `namespace.yml` declara um namespace personalizado: `stocks`.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-154">The `namespace.yml` file declares a custom namespace: `stocks`.</span></span> <span data-ttu-id="c3f4f-155">O arquivo de `stockdata.yml` declara a implantação e o serviço para o aplicativo gRPC, e o arquivo de `stockweb.yml` declara a implantação e o serviço para um aplicativo Web MVC ASP.NET Core 3,0 que consome o serviço gRPC.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-155">The `stockdata.yml` file declares the Deployment and the Service for the gRPC application, and the `stockweb.yml` file declares the Deployment and Service for an ASP.NET Core 3.0 MVC web application that consumes the gRPC service.</span></span>

<span data-ttu-id="c3f4f-156">Para usar um arquivo de `YAML` com `kubectl`, execute o comando `apply -f`:</span><span class="sxs-lookup"><span data-stu-id="c3f4f-156">To use a `YAML` file with `kubectl`, run the `apply -f` command:</span></span>

```console
kubectl apply -f object.yml
```

<span data-ttu-id="c3f4f-157">O comando `apply` verificará a validade do arquivo YAML e exibirá todos os erros recebidos da API, mas não aguardará até que todos os objetos declarados no arquivo tenham sido criados, pois isso pode levar algum tempo.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-157">The `apply` command will check the validity of the YAML file and display any errors received from the API, but doesn't wait until all the objects declared in the file have been created because this can take some time.</span></span> <span data-ttu-id="c3f4f-158">Use o comando `kubectl get` com os tipos de objeto relevantes para verificar a criação de objetos no cluster.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-158">Use the `kubectl get` command with the relevant object types to check on object creation in the cluster.</span></span>

### <a name="the-namespace-declaration"></a><span data-ttu-id="c3f4f-159">A declaração de namespace</span><span class="sxs-lookup"><span data-stu-id="c3f4f-159">The namespace declaration</span></span>

<span data-ttu-id="c3f4f-160">A declaração de namespace é simples e requer apenas a atribuição de um `name`:</span><span class="sxs-lookup"><span data-stu-id="c3f4f-160">Namespace declaration is simple and requires only assigning a `name`:</span></span>

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: stocks
```

<span data-ttu-id="c3f4f-161">Use `kubectl` para aplicar o arquivo de `namespace.yml` e confirmar se o namespace foi criado com êxito:</span><span class="sxs-lookup"><span data-stu-id="c3f4f-161">Use `kubectl` to apply the `namespace.yml` file and to confirm the namespace is created successfully:</span></span>

```console
> kubectl apply -f namespace.yml
namespace/stocks created

> kubectl get namespaces
NAME              STATUS   AGE
stocks            Active   2m53s
```

### <a name="the-stockdata-application"></a><span data-ttu-id="c3f4f-162">O aplicativo StockData</span><span class="sxs-lookup"><span data-stu-id="c3f4f-162">The StockData application</span></span>

<span data-ttu-id="c3f4f-163">O arquivo `stockdata.yml` declara dois objetos: uma implantação e um serviço.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-163">The `stockdata.yml` file declares two objects: a Deployment and a Service.</span></span>

#### <a name="the-stockdata-deployment"></a><span data-ttu-id="c3f4f-164">A implantação do StockData</span><span class="sxs-lookup"><span data-stu-id="c3f4f-164">The StockData Deployment</span></span>

<span data-ttu-id="c3f4f-165">A parte de implantação do arquivo YAML fornece a `spec` para a implantação em si, incluindo o número de réplicas necessárias e um `template` para os objetos Pod a serem criados e gerenciados pela implantação.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-165">The Deployment part of the YAML file provides the `spec` for the deployment itself, including the number of replicas required, and a `template` for the Pod objects to be created and managed by the deployment.</span></span> <span data-ttu-id="c3f4f-166">Observe que os objetos de implantação são gerenciados pela API do `apps`, conforme especificado em `apiVersion`, em vez da API principal do kubernetes.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-166">Note that Deployment objects are managed by the `apps` API, as specified in `apiVersion`, rather than the main Kubernetes API.</span></span>

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: stockdata
  namespace: stocks
spec:
  selector:
    matchLabels:
      run: stockdata
  replicas: 1
  template:
    metadata:
      labels:
        run: stockdata
    spec:
      containers:
      - name: stockdata
        image: stockdata:1.0.0
        imagePullPolicy: Never
        resources:
          limits:
            cpu: 100m
            memory: 100Mi
        ports:
        - containerPort: 80
```

<span data-ttu-id="c3f4f-167">A propriedade `spec.selector` é usada para fazer a correspondência de pods com a implantação.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-167">The `spec.selector` property is used to match running Pods to the Deployment.</span></span> <span data-ttu-id="c3f4f-168">A propriedade de `metadata.labels` do pod deve corresponder à propriedade `matchLabels` ou a chamada à API falhará.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-168">The Pod's `metadata.labels` property must match the `matchLabels` property or the API call will fail.</span></span>

<span data-ttu-id="c3f4f-169">A seção `template.spec` declara o contêiner a ser executado.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-169">The `template.spec` section declares the container to be run.</span></span> <span data-ttu-id="c3f4f-170">Quando você estiver trabalhando com um cluster kubernetes local, como o fornecido pela área de trabalho do Docker, poderá especificar imagens que foram criadas localmente, desde que tenham uma marca de versão.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-170">When you're working with a local Kubernetes cluster, such as the one provided by Docker Desktop, you can specify images that were built locally as long as they have a version tag.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c3f4f-171">Por padrão, o kubernetes sempre verificará e tentará efetuar pull de uma nova imagem.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-171">By default, Kubernetes will always check for and try to pull a new image.</span></span> <span data-ttu-id="c3f4f-172">Se não conseguir localizar a imagem em nenhum de seus repositórios conhecidos, a criação do pod falhará.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-172">If it can't find the image in any of its known repositories, the Pod creation will fail.</span></span> <span data-ttu-id="c3f4f-173">Para trabalhar com imagens locais, defina o `imagePullPolicy` como `Never`.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-173">To work with local images, set the `imagePullPolicy` to `Never`.</span></span>

<span data-ttu-id="c3f4f-174">A propriedade `ports` especifica quais portas de contêiner devem ser publicadas no pod.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-174">The `ports` property specifies which container ports should be published on the Pod.</span></span> <span data-ttu-id="c3f4f-175">A imagem de `stockservice` executa o serviço na porta HTTP padrão, portanto, a porta 80 é publicada.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-175">The `stockservice` image runs the service on the standard HTTP port, so port 80 is published.</span></span>

<span data-ttu-id="c3f4f-176">A seção `resources` aplica limites de recursos ao contêiner em execução no pod.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-176">The `resources` section applies resource limits to the container running within the Pod.</span></span> <span data-ttu-id="c3f4f-177">Essa é uma boa prática porque impede que um pod individual consuma toda a CPU ou memória disponível em um nó.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-177">This is a good practice because it prevents an individual Pod from consuming all the available CPU or memory on a node.</span></span>

> [!NOTE]
> <span data-ttu-id="c3f4f-178">ASP.NET Core 3,0 foi otimizado e ajustado para ser executado em contêineres limitados por recursos.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-178">ASP.NET Core 3.0 has been optimized and tuned to run in resource-limited containers.</span></span> <span data-ttu-id="c3f4f-179">A imagem do Docker `dotnet/core/aspnet` define uma variável de ambiente para informar ao `dotnet` tempo de execução que ele está em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-179">The `dotnet/core/aspnet` Docker image sets an environment variable to tell the `dotnet` runtime that it's in a container.</span></span>

#### <a name="the-stockdata-service"></a><span data-ttu-id="c3f4f-180">O serviço StockData</span><span class="sxs-lookup"><span data-stu-id="c3f4f-180">The StockData Service</span></span>

<span data-ttu-id="c3f4f-181">A parte de serviço do arquivo YAML declara o serviço que fornece acesso ao pods dentro do cluster.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-181">The Service part of the YAML file declares the service that provides access to the Pods within the cluster.</span></span>

```yaml
apiVersion: v1
kind: Service
metadata:
  name: stockdata
  namespace: stocks
spec:
  ports:
  - port: 80
  selector:
    run: stockdata
```

<span data-ttu-id="c3f4f-182">O serviço `spec` usa a propriedade `selector` para corresponder à execução de `Pods`, nesse caso, procurando pods que têm um rótulo `run: stockdata`.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-182">The Service `spec` uses the `selector` property to match running `Pods`, in this case looking for Pods that have a label `run: stockdata`.</span></span> <span data-ttu-id="c3f4f-183">O `port` especificado em pods correspondentes é publicado pelo serviço nomeado.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-183">The specified `port` on matching Pods is published by the named service.</span></span> <span data-ttu-id="c3f4f-184">Outros pods em execução no namespace `stocks` podem acessar HTTP nesse serviço usando `http://stockdata` como o endereço.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-184">Other Pods running in the `stocks` namespace can access HTTP on this service by using `http://stockdata` as the address.</span></span> <span data-ttu-id="c3f4f-185">O pods em execução em outros namespaces pode usar o nome de host `http://stockdata.stocks`.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-185">Pods running in other namespaces can use the `http://stockdata.stocks` host name.</span></span> <span data-ttu-id="c3f4f-186">Você pode controlar o acesso ao serviço de namespace cruzado usando [as políticas de rede](https://kubernetes.io/docs/concepts/services-networking/network-policies/).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-186">You can control cross-namespace service access by using [Network Policies](https://kubernetes.io/docs/concepts/services-networking/network-policies/).</span></span>

#### <a name="deploy-the-stockdata-application"></a><span data-ttu-id="c3f4f-187">Implantar o aplicativo StockData</span><span class="sxs-lookup"><span data-stu-id="c3f4f-187">Deploy the StockData application</span></span>

<span data-ttu-id="c3f4f-188">Use `kubectl` para aplicar o arquivo de `stockdata.yml` e confirmar que a implantação e o serviço foram criados:</span><span class="sxs-lookup"><span data-stu-id="c3f4f-188">Use `kubectl` to apply the `stockdata.yml` file and confirm that the Deployment and Service were created:</span></span>

```console
> kubectl apply -f .\stockdata.yml
deployment.apps/stockdata created
service/stockdata created

> kubectl get deployment stockdata --namespace stocks
NAME        READY   UP-TO-DATE   AVAILABLE   AGE
stockdata   1/1     1            1           17s

> kubectl get service stockdata --namespace stocks
NAME        TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)   AGE
stockdata   ClusterIP   10.97.132.103   <none>        80/TCP    33s
```

### <a name="the-stockweb-application"></a><span data-ttu-id="c3f4f-189">O aplicativo StockWeb</span><span class="sxs-lookup"><span data-stu-id="c3f4f-189">The StockWeb application</span></span>

<span data-ttu-id="c3f4f-190">O arquivo de `stockweb.yml` declara a implantação e o serviço para o aplicativo MVC.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-190">The `stockweb.yml` file declares the Deployment and Service for the MVC application.</span></span>

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: stockweb
  namespace: stocks
spec:
  selector:
    matchLabels:
      run: stockweb
  replicas: 1
  template:
    metadata:
      labels:
        run: stockweb
    spec:
      containers:
      - name: stockweb
        image: stockweb:1.0.0
        imagePullPolicy: Never
        resources:
          limits:
            cpu: 100m
            memory: 100Mi
        ports:
        - containerPort: 80
        env:
        - name: StockData__Address
          value: "http://stockdata"
        - name: DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT
          value: "true"

---

apiVersion: v1
kind: Service
metadata:
  name: stockweb
  namespace: stocks
spec:
  type: NodePort
  ports:
  - port: 80
  selector:
    run: stockweb
```

#### <a name="environment-variables"></a><span data-ttu-id="c3f4f-191">Variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="c3f4f-191">Environment variables</span></span>

<span data-ttu-id="c3f4f-192">A seção `env` do objeto de implantação especifica as variáveis de ambiente a serem definidas no contêiner que está executando as imagens de `stockweb:1.0.0`.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-192">The `env` section of the Deployment object specifies environment variables to be set in the container that's running the `stockweb:1.0.0` images.</span></span>

<span data-ttu-id="c3f4f-193">A variável de ambiente **`StockData__Address`** será mapeada para o parâmetro de configuração `StockData:Address` graças ao provedor de configuração EnvironmentVariables.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-193">The **`StockData__Address`** environment variable will map to the `StockData:Address` configuration setting thanks to the EnvironmentVariables configuration provider.</span></span> <span data-ttu-id="c3f4f-194">Essa configuração usa sublinhados duplos entre nomes para separar seções.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-194">This setting uses double underscores between names to separate sections.</span></span> <span data-ttu-id="c3f4f-195">O endereço usa o nome do serviço do `stockdata`, que está em execução no mesmo namespace kubernetes.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-195">The address uses the service name of the `stockdata` Service, which is running in the same Kubernetes namespace.</span></span>

<span data-ttu-id="c3f4f-196">A variável de ambiente **`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** define uma opção <xref:System.AppContext> que permite conexões http/2 não criptografadas para <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-196">The **`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** environment variable sets an <xref:System.AppContext> switch that enables unencrypted HTTP/2 connections for <xref:System.Net.Http.HttpClient>.</span></span> <span data-ttu-id="c3f4f-197">Essa variável de ambiente faz a mesma coisa que definir a opção no código, como mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="c3f4f-197">This environment variable does the same thing as setting the switch in code, as shown here:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

<span data-ttu-id="c3f4f-198">Se você usar uma variável de ambiente para a opção, poderá alterar facilmente o contexto dependendo do contexto no qual o aplicativo está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-198">If you use an environment variable for the switch, you can easily change the context depending on the context in which the application is running.</span></span>

#### <a name="service-types"></a><span data-ttu-id="c3f4f-199">Tipos de serviço</span><span class="sxs-lookup"><span data-stu-id="c3f4f-199">Service types</span></span>

<span data-ttu-id="c3f4f-200">A propriedade `type: NodePort` é usada para tornar o aplicativo Web acessível de fora do cluster.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-200">The `type: NodePort` property is used to make the web application accessible from outside the cluster.</span></span> <span data-ttu-id="c3f4f-201">Esse tipo de propriedade faz com que o kubernetes publique a porta 80 no serviço em uma porta arbitrária nos soquetes de rede externa do cluster.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-201">This property type causes Kubernetes to publish port 80 on the Service to an arbitrary port on the cluster's external network sockets.</span></span> <span data-ttu-id="c3f4f-202">Você pode encontrar a porta atribuída usando o comando `kubectl get service`.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-202">You can find the assigned port by using the `kubectl get service` command.</span></span>

<span data-ttu-id="c3f4f-203">O serviço de `stockdata` não deve ser acessível de fora do cluster, portanto, ele usa o tipo padrão, `ClusterIP`.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-203">The `stockdata` Service shouldn't be accessible from outside the cluster, so it uses the default type, `ClusterIP`.</span></span>

<span data-ttu-id="c3f4f-204">Os sistemas de produção provavelmente usarão um balanceador de carga integrado para expor aplicativos públicos a consumidores externos.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-204">Production systems will most likely use an integrated load balancer to expose public applications to external consumers.</span></span> <span data-ttu-id="c3f4f-205">Os serviços expostos dessa maneira devem usar o tipo de `LoadBalancer`.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-205">Services exposed in this way should use the `LoadBalancer` type.</span></span>

<span data-ttu-id="c3f4f-206">Para obter mais informações sobre tipos de serviço, consulte a documentação [dos serviços de publicação do kubernetes](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) .</span><span class="sxs-lookup"><span data-stu-id="c3f4f-206">For more information on Service types, see the [Kubernetes Publishing Services](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) documentation.</span></span>

#### <a name="deploy-the-stockweb-application"></a><span data-ttu-id="c3f4f-207">Implantar o aplicativo StockWeb</span><span class="sxs-lookup"><span data-stu-id="c3f4f-207">Deploy the StockWeb application</span></span>

<span data-ttu-id="c3f4f-208">Use `kubectl` para aplicar o arquivo de `stockweb.yml` e confirmar que a implantação e o serviço foram criados:</span><span class="sxs-lookup"><span data-stu-id="c3f4f-208">Use `kubectl` to apply the `stockweb.yml` file and confirm that the Deployment and Service were created:</span></span>

```console
> kubectl apply -f .\stockweb.yml
deployment.apps/stockweb created
service/stockweb created

> kubectl get deployment stockweb --namespace stocks
NAME       READY   UP-TO-DATE   AVAILABLE   AGE
stockweb   1/1     1            1           8s

> kubectl get service stockweb --namespace stocks
NAME       TYPE       CLUSTER-IP     EXTERNAL-IP   PORT(S)        AGE
stockweb   NodePort   10.106.141.5   <none>        80:32564/TCP   13s
```

<span data-ttu-id="c3f4f-209">A saída do comando `get service` mostra que a porta HTTP foi publicada na porta 32564 na rede externa.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-209">The output of the `get service` command shows that the HTTP port has been published to port 32564 on the external network.</span></span> <span data-ttu-id="c3f4f-210">Para o Docker desktop, esse será o localhost.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-210">For Docker Desktop, this will be localhost.</span></span> <span data-ttu-id="c3f4f-211">Você pode acessar o aplicativo navegando até `http://localhost:32564`.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-211">You can access the application by browsing to `http://localhost:32564`.</span></span>

### <a name="test-the-application"></a><span data-ttu-id="c3f4f-212">Testar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="c3f4f-212">Test the application</span></span>

<span data-ttu-id="c3f4f-213">O aplicativo StockWeb exibe uma lista de ações de NASDAQ que são recuperadas de um serviço de solicitação-resposta simples.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-213">The StockWeb application displays a list of NASDAQ stocks that are retrieved from a simple request-reply service.</span></span> <span data-ttu-id="c3f4f-214">Para esta demonstração, cada linha também mostra a ID exclusiva da instância do serviço que a retornou.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-214">For this demonstration, each line also shows the unique ID of the Service instance that returned it.</span></span>

![Captura de tela StockWeb](media/kubernetes/stockweb-screenshot.png)

<span data-ttu-id="c3f4f-216">Se o número de réplicas do serviço de `stockdata` foi aumentado, talvez você espere que o valor do **servidor** seja alterado de linha para linha, mas, na verdade, todos os registros 100 sempre são retornados da mesma instância.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-216">If the number of replicas of the `stockdata` Service were increased, you might expect the **Server** value to change from line to line, but in fact all 100 records are always returned from the same instance.</span></span> <span data-ttu-id="c3f4f-217">Se você atualizar a página a cada poucos segundos, a ID do servidor permanecerá a mesma.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-217">If you refresh the page every few seconds, the server ID remains the same.</span></span> <span data-ttu-id="c3f4f-218">Por que isso acontece?</span><span class="sxs-lookup"><span data-stu-id="c3f4f-218">Why does this happen?</span></span> <span data-ttu-id="c3f4f-219">Há dois fatores em jogo aqui.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-219">There are two factors at play here.</span></span>

<span data-ttu-id="c3f4f-220">Primeiro, o sistema de descoberta de serviço kubernetes usa o balanceamento de carga Round Robin por padrão.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-220">First, the Kubernetes Service discovery system uses round-robin load balancing by default.</span></span> <span data-ttu-id="c3f4f-221">Na primeira vez que o servidor DNS for consultado, ele retornará o primeiro endereço IP correspondente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-221">The first time the DNS server is queried, it will return the first matching IP address for the Service.</span></span> <span data-ttu-id="c3f4f-222">Na próxima vez, ele retornará o próximo endereço IP na lista, e assim por diante, até o final.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-222">The next time, it will return the next IP address in the list, and so on, until the end.</span></span> <span data-ttu-id="c3f4f-223">Nesse ponto, ele faz um loop de volta para o início.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-223">At that point it loops back to the start.</span></span>

<span data-ttu-id="c3f4f-224">Em segundo lugar, o `HttpClient` usado para o cliente gRPC do aplicativo StockWeb é criado e gerenciado pelo [ASP.NET Core HttpClientFactory](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md), e uma única instância desse cliente é usada para cada chamada à página.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-224">Second, the `HttpClient` used for the StockWeb application's gRPC client is created and managed by the [ASP.NET Core HttpClientFactory](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md), and a single instance of this client is used for every call to the page.</span></span> <span data-ttu-id="c3f4f-225">O cliente faz apenas uma pesquisa DNS, de modo que todas as solicitações são roteadas para o mesmo endereço IP.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-225">The client only does one DNS lookup, so all requests are routed to the same IP address.</span></span> <span data-ttu-id="c3f4f-226">E como o `HttpClientHandler` é armazenado em cache por motivos de desempenho, várias solicitações em uma rápida *sucessão usarão o* mesmo endereço IP, até que a entrada DNS armazenada em cache expire ou a instância do manipulador seja descartada por algum motivo.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-226">And because the `HttpClientHandler` is cached for performance reasons, multiple requests in quick succession will *all* use the same IP address, until the cached DNS entry expires or the handler instance is disposed for some reason.</span></span>

<span data-ttu-id="c3f4f-227">O resultado é que, por padrão, as solicitações para um serviço gRPC não são balanceadas em todas as instâncias desse serviço no cluster.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-227">The result is that by default requests to a gRPC Service aren't balanced across all instances of that Service in the cluster.</span></span> <span data-ttu-id="c3f4f-228">Consumidores diferentes usarão instâncias diferentes, mas isso não garante uma boa distribuição de solicitações ou um uso balanceado de recursos.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-228">Different consumers will use different instances, but that doesn't guarantee a good distribution of requests or a balanced use of resources.</span></span>

<span data-ttu-id="c3f4f-229">O próximo capítulo, [malhas de serviço](service-mesh.md), resolverá esse problema.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-229">The next chapter, [Service meshes](service-mesh.md), will address this problem.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c3f4f-230">[Anterior](docker.md)
>[Próximo](service-mesh.md)</span><span class="sxs-lookup"><span data-stu-id="c3f4f-230">[Previous](docker.md)
[Next](service-mesh.md)</span></span>

---
title: Malhas de serviço-gRPC para desenvolvedores do WCF
description: Usar uma malha de serviço para rotear e balancear solicitações para serviços gRPC em um cluster kubernetes.
ms.date: 09/02/2019
ms.openlocfilehash: d20275082973f30bddbb342da90454401d4f019b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966962"
---
# <a name="service-meshes"></a><span data-ttu-id="d17e7-103">Malhas de serviço</span><span class="sxs-lookup"><span data-stu-id="d17e7-103">Service meshes</span></span>

<span data-ttu-id="d17e7-104">Uma malha de serviço é um componente de infraestrutura que assume o controle das solicitações de serviço de roteamento em uma rede.</span><span class="sxs-lookup"><span data-stu-id="d17e7-104">A service mesh is an infrastructure component that takes control of routing service requests within a network.</span></span> <span data-ttu-id="d17e7-105">As malhas de serviço podem lidar com todos os tipos de preocupações de nível de rede dentro de um cluster kubernetes, incluindo:</span><span class="sxs-lookup"><span data-stu-id="d17e7-105">Service meshes can handle all kinds of network-level concerns within a Kubernetes cluster, including:</span></span>

- <span data-ttu-id="d17e7-106">Descoberta de serviço</span><span class="sxs-lookup"><span data-stu-id="d17e7-106">Service discovery</span></span>
- <span data-ttu-id="d17e7-107">Balanceamento de carga</span><span class="sxs-lookup"><span data-stu-id="d17e7-107">Load balancing</span></span>
- <span data-ttu-id="d17e7-108">Tolerância a falhas</span><span class="sxs-lookup"><span data-stu-id="d17e7-108">Fault tolerance</span></span>
- <span data-ttu-id="d17e7-109">Criptografia</span><span class="sxs-lookup"><span data-stu-id="d17e7-109">Encryption</span></span>
- <span data-ttu-id="d17e7-110">Monitoramento</span><span class="sxs-lookup"><span data-stu-id="d17e7-110">Monitoring</span></span>

<span data-ttu-id="d17e7-111">As malhas do serviço kubernetes funcionam adicionando um contêiner extra, chamado *proxy sidecar*, a cada pod incluído na malha.</span><span class="sxs-lookup"><span data-stu-id="d17e7-111">Kubernetes service meshes work by adding an extra container, called a *sidecar proxy*, to each pod included in the mesh.</span></span> <span data-ttu-id="d17e7-112">O proxy assume o tratamento de todas as solicitações de rede de entrada e saída, permitindo que a configuração e o gerenciamento de rede sejam mantidos separados dos contêineres de aplicativos e, em muitos casos, sem a necessidade de qualquer alteração no código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d17e7-112">The proxy takes over handling all inbound and outbound network requests, allowing configuration and management of networking matters to be kept separate from the application containers and, in many cases, without requiring any changes to the application code.</span></span>

<span data-ttu-id="d17e7-113">Pegue o [exemplo do capítulo anterior](kubernetes.md#testing-the-application), em que as solicitações gRPC do aplicativo Web foram todas roteadas para uma única instância do serviço gRPC.</span><span class="sxs-lookup"><span data-stu-id="d17e7-113">Take the [previous chapter's example](kubernetes.md#testing-the-application), where the gRPC requests from the web application were all routed to a single instance of the gRPC service.</span></span> <span data-ttu-id="d17e7-114">Isso acontece porque o nome de host do serviço é resolvido para um endereço IP e esse endereço IP é armazenado em cache durante o tempo de vida da instância de `HttpClientHandler`.</span><span class="sxs-lookup"><span data-stu-id="d17e7-114">This happens because the service's hostname is resolved to an IP address, and that IP address is cached for the lifetime of the `HttpClientHandler` instance.</span></span> <span data-ttu-id="d17e7-115">Pode ser possível contornar isso tratando as pesquisas de DNS manualmente ou criando vários clientes, mas isso complicaria consideravelmente o código do aplicativo sem adicionar nenhum valor comercial ou de cliente.</span><span class="sxs-lookup"><span data-stu-id="d17e7-115">It might be possible to work around this by handling DNS lookups manually or creating multiple clients, but this would complicate the application code considerably without adding any business or customer value.</span></span>

<span data-ttu-id="d17e7-116">Usando uma malha de serviço, as solicitações do contêiner de aplicativo são enviadas para o proxy sidecar, que pode distribuí-las de forma inteligente em todas as instâncias do outro serviço.</span><span class="sxs-lookup"><span data-stu-id="d17e7-116">Using a service mesh, the requests from the application container are sent to the sidecar proxy, which can distribute them intelligently across all instances of the other service.</span></span> <span data-ttu-id="d17e7-117">A malha também pode:</span><span class="sxs-lookup"><span data-stu-id="d17e7-117">The mesh can also:</span></span>

- <span data-ttu-id="d17e7-118">Responda de forma direta às falhas de instâncias individuais de um serviço.</span><span class="sxs-lookup"><span data-stu-id="d17e7-118">Respond seamlessly to failures of individual instances of a service.</span></span>
- <span data-ttu-id="d17e7-119">Manipular semânticas de repetição para chamadas com falha ou tempos limite</span><span class="sxs-lookup"><span data-stu-id="d17e7-119">Handle retry semantics for failed calls or timeouts</span></span>
- <span data-ttu-id="d17e7-120">Redirecionar solicitações com falha para uma instância alternativa sem retornar ao aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="d17e7-120">Reroute failed requests to an alternate instance without returning to the client application at all.</span></span>

<span data-ttu-id="d17e7-121">A captura de tela a seguir mostra o aplicativo StockWeb em execução com a malha de serviço do Linkerd, sem alterações no código do aplicativo ou até mesmo a imagem do Docker que está sendo usada.</span><span class="sxs-lookup"><span data-stu-id="d17e7-121">The following screenshot shows the StockWeb application running with the Linkerd service mesh, with no changes to the application code, or even the Docker image being used.</span></span> <span data-ttu-id="d17e7-122">A única alteração necessária foi a adição de uma anotação à implantação nos arquivos YAML para os serviços de `stockdata` e `stockweb`.</span><span class="sxs-lookup"><span data-stu-id="d17e7-122">The only change required was the addition of an annotation to the Deployment in the YAML files for the `stockdata` and `stockweb` services.</span></span>

![StockWeb com malha de serviço](media/service-mesh/stockweb-servicemesh-screenshot.png)

<span data-ttu-id="d17e7-124">Você pode ver na coluna servidor que as solicitações do aplicativo StockWeb foram roteadas para ambas as réplicas do serviço StockData, apesar de serem originadas de uma única instância de `HttpClient` no código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d17e7-124">You can see from the Server column that the requests from the StockWeb application have been routed to both replicas of the StockData service, despite originating from a single `HttpClient` instance in the application code.</span></span> <span data-ttu-id="d17e7-125">Na verdade, se você examinar o código, verá que todas as solicitações de 100 para o serviço StockData são feitas simultaneamente usando a mesma instância de `HttpClient`, mas com a malha de serviço, essas solicitações serão balanceadas em todas as instâncias de serviço, no entanto, estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d17e7-125">In fact, if you review the code, you'll see that all 100 requests to the StockData service are made simultaneously using the same `HttpClient` instance, yet with the service mesh, those requests will be balanced across however many service instances are available.</span></span>

<span data-ttu-id="d17e7-126">As malhas de serviço se aplicam somente ao tráfego em um cluster.</span><span class="sxs-lookup"><span data-stu-id="d17e7-126">Service meshes only apply to traffic within a cluster.</span></span> <span data-ttu-id="d17e7-127">Para clientes externos, consulte [o próximo capítulo, balanceamento de carga](load-balancing.md).</span><span class="sxs-lookup"><span data-stu-id="d17e7-127">For external clients, see [the next chapter, Load Balancing](load-balancing.md).</span></span>

## <a name="service-mesh-options"></a><span data-ttu-id="d17e7-128">Opções de malha de serviço</span><span class="sxs-lookup"><span data-stu-id="d17e7-128">Service mesh options</span></span>

<span data-ttu-id="d17e7-129">Há três implementações de malha de serviço de uso geral disponíveis atualmente para uso com kubernetes: İSTİO, Linkerd e Consul Connect.</span><span class="sxs-lookup"><span data-stu-id="d17e7-129">There are three general-purpose service mesh implementations currently available for use with Kubernetes: Istio, Linkerd, and Consul Connect.</span></span> <span data-ttu-id="d17e7-130">Todos os três fornecem roteamento/proxy de solicitação, criptografia de tráfego, resiliência, autenticação de host para host e controle de tráfego.</span><span class="sxs-lookup"><span data-stu-id="d17e7-130">All three provide request routing/proxying, traffic encryption, resilience, host-to-host authentication, and traffic control.</span></span>

<span data-ttu-id="d17e7-131">Escolher uma malha de serviço depende de vários fatores:</span><span class="sxs-lookup"><span data-stu-id="d17e7-131">Choosing a service mesh depends multiple factors:</span></span>

- <span data-ttu-id="d17e7-132">Os requisitos específicos da organização em relação aos custos, conformidade, planos de suporte pagos e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="d17e7-132">The organization's specific requirements around costs, compliance, paid support plans, and so on.</span></span>
- <span data-ttu-id="d17e7-133">A natureza do cluster, seu tamanho, o número de serviços implantados e o volume de tráfego na rede de cluster.</span><span class="sxs-lookup"><span data-stu-id="d17e7-133">The nature of the cluster, its size, the number of services deployed, and the volume of traffic within the cluster network.</span></span>
- <span data-ttu-id="d17e7-134">Facilidade de implantar e gerenciar a malha e usá-la com serviços.</span><span class="sxs-lookup"><span data-stu-id="d17e7-134">Ease of deploying and managing the mesh and using it with services.</span></span>

<span data-ttu-id="d17e7-135">Mais informações sobre cada malha de serviço estão disponíveis em seus respectivos sites.</span><span class="sxs-lookup"><span data-stu-id="d17e7-135">More information on each service mesh is available from their respective websites.</span></span>

- [<span data-ttu-id="d17e7-136">**İSTİO** -İSTİO.Io</span><span class="sxs-lookup"><span data-stu-id="d17e7-136">**Istio** - istio.io</span></span>](https://istio.io)
- [<span data-ttu-id="d17e7-137">**Linkerd** -linkerd.Io</span><span class="sxs-lookup"><span data-stu-id="d17e7-137">**Linkerd** - linkerd.io</span></span>](https://linkerd.io)
- [<span data-ttu-id="d17e7-138">**Consul** -Consul.Io/mesh.html</span><span class="sxs-lookup"><span data-stu-id="d17e7-138">**Consul** - consul.io/mesh.html</span></span>](https://consul.io/mesh.html)

## <a name="example-add-linkerd-to-a-deployment"></a><span data-ttu-id="d17e7-139">Exemplo: Adicionar Linkerd a uma implantação</span><span class="sxs-lookup"><span data-stu-id="d17e7-139">Example: add Linkerd to a deployment</span></span>

<span data-ttu-id="d17e7-140">Neste exemplo, você aprenderá a usar a malha de serviço Linkerd com o aplicativo *StockKube* da [seção anterior](kubernetes.md).</span><span class="sxs-lookup"><span data-stu-id="d17e7-140">In this example, you'll learn how to use the Linkerd service mesh with the *StockKube* application from [the previous section](kubernetes.md).</span></span>
<span data-ttu-id="d17e7-141">Para seguir este exemplo, você precisará [instalar a CLI do Linkerd](https://linkerd.io/2/getting-started/#step-1-install-the-cli).</span><span class="sxs-lookup"><span data-stu-id="d17e7-141">To follow this example, you'll need to [install the Linkerd CLI](https://linkerd.io/2/getting-started/#step-1-install-the-cli).</span></span> <span data-ttu-id="d17e7-142">Os binários do Windows podem ser baixados na seção versões do GitHub; Certifique-se de usar a versão **estável** mais recente e não uma das versões de borda.</span><span class="sxs-lookup"><span data-stu-id="d17e7-142">Windows binaries can be downloaded from the GitHub releases section; make sure to use the most recent **stable** release and not one of the edge releases.</span></span>

<span data-ttu-id="d17e7-143">Com a CLI do Linkerd instalada, siga as instruções [*introdução* no site da Linkerd] para instalar os componentes do Linkerd no cluster do kubernetes.</span><span class="sxs-lookup"><span data-stu-id="d17e7-143">With the Linkerd CLI installed, follow the [*Getting Started* instructions on the Linkerd web site] to install the Linkerd components on your Kubernetes cluster.</span></span> <span data-ttu-id="d17e7-144">As instruções são diretas e a instalação deve levar apenas alguns minutos em uma instância de kubernetes local.</span><span class="sxs-lookup"><span data-stu-id="d17e7-144">The instructions are straight-forward and installation should only take a couple of minutes on a local Kubernetes instance.</span></span>

### <a name="add-linkerd-to-kubernetes-deployments"></a><span data-ttu-id="d17e7-145">Adicionar Linkerd a implantações do kubernetes</span><span class="sxs-lookup"><span data-stu-id="d17e7-145">Add Linkerd to Kubernetes deployments</span></span>

<span data-ttu-id="d17e7-146">A CLI do Linkerd fornece um comando `inject` para adicionar as seções e propriedades necessárias aos arquivos kubernetes.</span><span class="sxs-lookup"><span data-stu-id="d17e7-146">The Linkerd CLI provides an `inject` command to add the necessary sections and properties to Kubernetes files.</span></span> <span data-ttu-id="d17e7-147">Você pode executar o comando e gravar a saída em um novo arquivo.</span><span class="sxs-lookup"><span data-stu-id="d17e7-147">You can run the command and write the output to a new file.</span></span>

```console
linkerd inject stockdata.yml > stockdata-with-mesh.yml
linkerd inject stockweb.yml > stockweb-with-mesh.yml
```

<span data-ttu-id="d17e7-148">Você pode inspecionar os novos arquivos para ver quais alterações foram feitas.</span><span class="sxs-lookup"><span data-stu-id="d17e7-148">You can inspect the new files to see what changes have been made.</span></span> <span data-ttu-id="d17e7-149">Para objetos de implantação, uma anotação de metadados é adicionada para informar ao Linkerd para injetar um contêiner de proxy sidecar no pod quando ele é criado.</span><span class="sxs-lookup"><span data-stu-id="d17e7-149">For Deployment objects, a metadata annotation is added to tell Linkerd to inject a sidecar proxy container into the Pod when it's created.</span></span>

<span data-ttu-id="d17e7-150">Também é possível canalizar a saída do comando `linkerd inject` para `kubectl` diretamente.</span><span class="sxs-lookup"><span data-stu-id="d17e7-150">It's also possible to pipe the output of the `linkerd inject` command to `kubectl` directly.</span></span> <span data-ttu-id="d17e7-151">Os comandos a seguir funcionarão no PowerShell ou em qualquer shell do Linux.</span><span class="sxs-lookup"><span data-stu-id="d17e7-151">The following commands will work in PowerShell or any Linux shell.</span></span>

```console
linkerd inject stockdata.yml | kubectl apply -f -
linkerd inject stockweb.yml | kubectl apply -f -
```

### <a name="inspect-services-in-the-linkerd-dashboard"></a><span data-ttu-id="d17e7-152">Inspecionar serviços no painel do Linkerd</span><span class="sxs-lookup"><span data-stu-id="d17e7-152">Inspect services in the Linkerd dashboard</span></span>

<span data-ttu-id="d17e7-153">Inicie o painel do Linkerd usando a CLI do `linkerd`.</span><span class="sxs-lookup"><span data-stu-id="d17e7-153">Launch the Linkerd dashboard using the `linkerd` CLI.</span></span>

```console
linkerd dashboard
```

<span data-ttu-id="d17e7-154">O painel fornece informações detalhadas sobre todos os serviços que estão conectados à malha.</span><span class="sxs-lookup"><span data-stu-id="d17e7-154">The dashboard provides detailed information about all services that are connected to the mesh.</span></span>

![Painel do Linkerd mostrando aplicativos StockKube](media/service-mesh/linkerd-screenshot.png)

<span data-ttu-id="d17e7-156">Se você aumentar o número de réplicas do serviço StockData gRPC, conforme mostrado no exemplo a seguir, e atualizar a página StockWeb no navegador, verá uma mistura de IDs na coluna servidor, indicando que as solicitações estão sendo atendidas por todas as instâncias disponíveis .</span><span class="sxs-lookup"><span data-stu-id="d17e7-156">If you increase the number of replicas of the StockData gRPC service as shown in the following example, and refresh the StockWeb page in the browser, you should see a mix of IDs in the Server column, indicating that requests are being served by all the available instances.</span></span>

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
  replicas: 2 # Increase the target number of instances
  template:
    metadata:
      annotations:
        linkerd.io/inject: enabled
      creationTimestamp: null
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

>[!div class="step-by-step"]
><span data-ttu-id="d17e7-157">[Anterior](kubernetes.md)
>[Próximo](load-balancing.md)</span><span class="sxs-lookup"><span data-stu-id="d17e7-157">[Previous](kubernetes.md)
[Next](load-balancing.md)</span></span>

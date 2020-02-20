---
title: Malhas de serviço-gRPC para desenvolvedores do WCF
description: Usar uma malha de serviço para rotear e balancear solicitações para serviços gRPC em um cluster kubernetes.
ms.date: 09/02/2019
ms.openlocfilehash: a29d6893e585c7eb60c847cef0149afeeaebcdab
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503391"
---
# <a name="service-meshes"></a><span data-ttu-id="00596-103">Malhas de serviço</span><span class="sxs-lookup"><span data-stu-id="00596-103">Service meshes</span></span>

<span data-ttu-id="00596-104">Uma malha de serviço é um componente de infraestrutura que assume o controle das solicitações de serviço de roteamento em uma rede.</span><span class="sxs-lookup"><span data-stu-id="00596-104">A service mesh is an infrastructure component that takes control of routing service requests within a network.</span></span> <span data-ttu-id="00596-105">As malhas de serviço podem lidar com todos os tipos de preocupações de nível de rede dentro de um cluster kubernetes, incluindo:</span><span class="sxs-lookup"><span data-stu-id="00596-105">Service meshes can handle all kinds of network-level concerns within a Kubernetes cluster, including:</span></span>

- <span data-ttu-id="00596-106">Descoberta de serviço</span><span class="sxs-lookup"><span data-stu-id="00596-106">Service discovery</span></span>
- <span data-ttu-id="00596-107">Balanceamento de carga</span><span class="sxs-lookup"><span data-stu-id="00596-107">Load balancing</span></span>
- <span data-ttu-id="00596-108">Tolerância a falhas</span><span class="sxs-lookup"><span data-stu-id="00596-108">Fault tolerance</span></span>
- <span data-ttu-id="00596-109">Criptografia</span><span class="sxs-lookup"><span data-stu-id="00596-109">Encryption</span></span>
- <span data-ttu-id="00596-110">Monitoramento</span><span class="sxs-lookup"><span data-stu-id="00596-110">Monitoring</span></span>

<span data-ttu-id="00596-111">As malhas do serviço kubernetes funcionam adicionando um contêiner extra, chamado *proxy sidecar*, a cada pod incluído na malha.</span><span class="sxs-lookup"><span data-stu-id="00596-111">Kubernetes service meshes work by adding an extra container, called a *sidecar proxy*, to each pod included in the mesh.</span></span> <span data-ttu-id="00596-112">O proxy assume o tratamento de todas as solicitações de rede de entrada e saída.</span><span class="sxs-lookup"><span data-stu-id="00596-112">The proxy takes over handling all inbound and outbound network requests.</span></span> <span data-ttu-id="00596-113">Em seguida, você pode manter a configuração e o gerenciamento de redes de rede separadas dos contêineres de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="00596-113">You can then keep configuration and management of networking matters separate from the application containers.</span></span> <span data-ttu-id="00596-114">Em muitos casos, essa separação não requer nenhuma alteração no código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="00596-114">In many cases, this separation doesn't require any changes to the application code.</span></span>

<span data-ttu-id="00596-115">No [exemplo do capítulo anterior](kubernetes.md#test-the-application), as solicitações gRPC do aplicativo Web foram todas roteadas para uma única instância do serviço gRPC.</span><span class="sxs-lookup"><span data-stu-id="00596-115">In the [previous chapter's example](kubernetes.md#test-the-application), the gRPC requests from the web application were all routed to a single instance of the gRPC service.</span></span> <span data-ttu-id="00596-116">Isso acontece porque o nome do host do serviço é resolvido para um endereço IP e esse endereço IP é armazenado em cache durante o tempo de vida da instância de `HttpClientHandler`.</span><span class="sxs-lookup"><span data-stu-id="00596-116">This happens because the service's host name is resolved to an IP address, and that IP address is cached for the lifetime of the `HttpClientHandler` instance.</span></span> <span data-ttu-id="00596-117">Pode ser possível contornar isso tratando as pesquisas de DNS manualmente ou criando vários clientes.</span><span class="sxs-lookup"><span data-stu-id="00596-117">It might be possible to work around this by handling DNS lookups manually or creating multiple clients.</span></span> <span data-ttu-id="00596-118">Mas essa solução alternativa complicaria o código do aplicativo sem adicionar nenhum valor comercial ou de cliente.</span><span class="sxs-lookup"><span data-stu-id="00596-118">But this workaround would complicate the application code without adding any business or customer value.</span></span>

<span data-ttu-id="00596-119">Quando você usa uma malha de serviço, as solicitações do contêiner de aplicativo são enviadas para o proxy sidecar.</span><span class="sxs-lookup"><span data-stu-id="00596-119">When you use a service mesh, the requests from the application container are sent to the sidecar proxy.</span></span> <span data-ttu-id="00596-120">O proxy sidecar pode então distribuí-los de forma inteligente em todas as instâncias do outro serviço.</span><span class="sxs-lookup"><span data-stu-id="00596-120">The sidecar proxy can then distribute them intelligently across all instances of the other service.</span></span> <span data-ttu-id="00596-121">A malha também pode:</span><span class="sxs-lookup"><span data-stu-id="00596-121">The mesh can also:</span></span>

- <span data-ttu-id="00596-122">Responda de forma direta às falhas de instâncias individuais de um serviço.</span><span class="sxs-lookup"><span data-stu-id="00596-122">Respond seamlessly to failures of individual instances of a service.</span></span>
- <span data-ttu-id="00596-123">Manipule a semântica de repetição para chamadas com falha ou tempos limite.</span><span class="sxs-lookup"><span data-stu-id="00596-123">Handle retry semantics for failed calls or timeouts.</span></span>
- <span data-ttu-id="00596-124">Redirecionar solicitações com falha para uma instância alternativa sem retornar ao aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="00596-124">Reroute failed requests to an alternate instance without returning to the client application.</span></span>

<span data-ttu-id="00596-125">A captura de tela a seguir mostra o aplicativo StockWeb em execução com a malha de serviço do Linkerd.</span><span class="sxs-lookup"><span data-stu-id="00596-125">The following screenshot shows the StockWeb application running with the Linkerd service mesh.</span></span> <span data-ttu-id="00596-126">Não há nenhuma alteração no código do aplicativo e a imagem do Docker não está sendo usada.</span><span class="sxs-lookup"><span data-stu-id="00596-126">There are no changes to the application code, and the Docker image isn't being used.</span></span> <span data-ttu-id="00596-127">A única alteração necessária foi a adição de uma anotação à implantação nos arquivos YAML para os serviços de `stockdata` e `stockweb`.</span><span class="sxs-lookup"><span data-stu-id="00596-127">The only change required was the addition of an annotation to the deployment in the YAML files for the `stockdata` and `stockweb` services.</span></span>

![StockWeb com malha de serviço](media/service-mesh/stockweb-servicemesh-screenshot.png)

<span data-ttu-id="00596-129">Você pode ver na coluna **servidor** que as solicitações do aplicativo StockWeb foram roteadas para ambas as réplicas do serviço StockData, apesar de serem originadas de uma única instância de `HttpClient` no código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="00596-129">You can see from the **Server** column that the requests from the StockWeb application have been routed to both replicas of the StockData service, despite originating from a single `HttpClient` instance in the application code.</span></span> <span data-ttu-id="00596-130">Na verdade, se você examinar o código, verá que todas as solicitações de 100 para o serviço StockData são feitas simultaneamente usando a mesma instância de `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="00596-130">In fact, if you review the code, you'll see that all 100 requests to the StockData service are made simultaneously by using the same `HttpClient` instance.</span></span> <span data-ttu-id="00596-131">Com a malha de serviço, essas solicitações serão balanceadas em todas as instâncias de serviço, no entanto, estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="00596-131">With the service mesh, those requests will be balanced across however many service instances are available.</span></span>

<span data-ttu-id="00596-132">As malhas de serviço aplicam-se somente ao tráfego em um cluster.</span><span class="sxs-lookup"><span data-stu-id="00596-132">Service meshes apply only to traffic within a cluster.</span></span> <span data-ttu-id="00596-133">Para clientes externos, consulte o próximo capítulo, [balanceamento de carga](load-balancing.md).</span><span class="sxs-lookup"><span data-stu-id="00596-133">For external clients, see the next chapter, [Load Balancing](load-balancing.md).</span></span>

## <a name="service-mesh-options"></a><span data-ttu-id="00596-134">Opções de malha de serviço</span><span class="sxs-lookup"><span data-stu-id="00596-134">Service mesh options</span></span>

<span data-ttu-id="00596-135">Três implementações de malha de serviço de uso geral estão disponíveis atualmente para uso com kubernetes: [İSTİO](https://istio.io), [Linkerd](https://linkerd.io)e [Consul Connect](https://consul.io/mesh.html).</span><span class="sxs-lookup"><span data-stu-id="00596-135">Three general-purpose service mesh implementations are currently available for use with Kubernetes: [Istio](https://istio.io), [Linkerd](https://linkerd.io), and [Consul Connect](https://consul.io/mesh.html).</span></span> <span data-ttu-id="00596-136">Todos os três fornecem roteamento/proxy de solicitação, criptografia de tráfego, resiliência, autenticação de host para host e controle de tráfego.</span><span class="sxs-lookup"><span data-stu-id="00596-136">All three provide request routing/proxying, traffic encryption, resilience, host-to-host authentication, and traffic control.</span></span>

<span data-ttu-id="00596-137">Escolher uma malha de serviço depende de vários fatores:</span><span class="sxs-lookup"><span data-stu-id="00596-137">Choosing a service mesh depends on multiple factors:</span></span>

- <span data-ttu-id="00596-138">Os requisitos específicos da organização em relação aos custos, conformidade, planos de suporte pagos e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="00596-138">The organization's specific requirements around costs, compliance, paid support plans, and so on.</span></span>
- <span data-ttu-id="00596-139">A natureza do cluster, seu tamanho, o número de serviços implantados e o volume de tráfego na rede de cluster.</span><span class="sxs-lookup"><span data-stu-id="00596-139">The nature of the cluster, its size, the number of services deployed, and the volume of traffic within the cluster network.</span></span>
- <span data-ttu-id="00596-140">Facilidade de implantar e gerenciar a malha e usá-la com serviços.</span><span class="sxs-lookup"><span data-stu-id="00596-140">Ease of deploying and managing the mesh and using it with services.</span></span>

## <a name="example-add-linkerd-to-a-deployment"></a><span data-ttu-id="00596-141">Exemplo: Adicionar Linkerd a uma implantação</span><span class="sxs-lookup"><span data-stu-id="00596-141">Example: Add Linkerd to a deployment</span></span>

<span data-ttu-id="00596-142">Neste exemplo, você aprenderá a usar a malha de serviço Linkerd com o aplicativo *StockKube* da [seção anterior](kubernetes.md).</span><span class="sxs-lookup"><span data-stu-id="00596-142">In this example, you'll learn how to use the Linkerd service mesh with the *StockKube* application from [the previous section](kubernetes.md).</span></span>
<span data-ttu-id="00596-143">Para seguir este exemplo, você precisará [instalar a CLI do Linkerd](https://linkerd.io/2/getting-started/#step-1-install-the-cli).</span><span class="sxs-lookup"><span data-stu-id="00596-143">To follow this example, you'll need to [install the Linkerd CLI](https://linkerd.io/2/getting-started/#step-1-install-the-cli).</span></span> <span data-ttu-id="00596-144">Você pode baixar binários do Windows na seção que lista as versões do GitHub.</span><span class="sxs-lookup"><span data-stu-id="00596-144">You can download Windows binaries from the section that lists GitHub releases.</span></span> <span data-ttu-id="00596-145">Certifique-se de usar a versão *estável* mais recente e não uma das versões de borda.</span><span class="sxs-lookup"><span data-stu-id="00596-145">Be sure to use the most recent *stable* release and not one of the edge releases.</span></span>

<span data-ttu-id="00596-146">Com a CLI do Linkerd instalada, siga as instruções de [introdução](https://linkerd.io/2/getting-started/index.html) para instalar os componentes do Linkerd no cluster do kubernetes.</span><span class="sxs-lookup"><span data-stu-id="00596-146">With the Linkerd CLI installed, follow the [Getting Started](https://linkerd.io/2/getting-started/index.html) instructions to install the Linkerd components on your Kubernetes cluster.</span></span> <span data-ttu-id="00596-147">As instruções são simples e a instalação deve levar apenas alguns minutos em uma instância de kubernetes local.</span><span class="sxs-lookup"><span data-stu-id="00596-147">The instructions are straightforward, and installation should take only a couple of minutes on a local Kubernetes instance.</span></span>

### <a name="add-linkerd-to-kubernetes-deployments"></a><span data-ttu-id="00596-148">Adicionar Linkerd a implantações do kubernetes</span><span class="sxs-lookup"><span data-stu-id="00596-148">Add Linkerd to Kubernetes deployments</span></span>

<span data-ttu-id="00596-149">A CLI do Linkerd fornece um comando `inject` para adicionar as seções e propriedades necessárias aos arquivos kubernetes.</span><span class="sxs-lookup"><span data-stu-id="00596-149">The Linkerd CLI provides an `inject` command to add the necessary sections and properties to Kubernetes files.</span></span> <span data-ttu-id="00596-150">Você pode executar o comando e gravar a saída em um novo arquivo.</span><span class="sxs-lookup"><span data-stu-id="00596-150">You can run the command and write the output to a new file.</span></span>

```console
linkerd inject stockdata.yml > stockdata-with-mesh.yml
linkerd inject stockweb.yml > stockweb-with-mesh.yml
```

<span data-ttu-id="00596-151">Você pode inspecionar os novos arquivos para ver quais alterações foram feitas.</span><span class="sxs-lookup"><span data-stu-id="00596-151">You can inspect the new files to see what changes have been made.</span></span> <span data-ttu-id="00596-152">Para objetos de implantação, uma anotação de metadados é adicionada para informar ao Linkerd para injetar um contêiner de proxy sidecar no pod quando ele é criado.</span><span class="sxs-lookup"><span data-stu-id="00596-152">For deployment objects, a metadata annotation is added to tell Linkerd to inject a sidecar proxy container into the pod when it's created.</span></span>

<span data-ttu-id="00596-153">Também é possível canalizar a saída do comando `linkerd inject` para `kubectl` diretamente.</span><span class="sxs-lookup"><span data-stu-id="00596-153">It's also possible to pipe the output of the `linkerd inject` command to `kubectl` directly.</span></span> <span data-ttu-id="00596-154">Os comandos a seguir funcionarão no PowerShell ou em qualquer shell do Linux.</span><span class="sxs-lookup"><span data-stu-id="00596-154">The following commands will work in PowerShell or any Linux shell.</span></span>

```console
linkerd inject stockdata.yml | kubectl apply -f -
linkerd inject stockweb.yml | kubectl apply -f -
```

### <a name="inspect-services-in-the-linkerd-dashboard"></a><span data-ttu-id="00596-155">Inspecionar serviços no painel do Linkerd</span><span class="sxs-lookup"><span data-stu-id="00596-155">Inspect services in the Linkerd dashboard</span></span>

<span data-ttu-id="00596-156">Abra o painel do Linkerd usando a CLI do `linkerd`.</span><span class="sxs-lookup"><span data-stu-id="00596-156">Open the Linkerd dashboard by using the `linkerd` CLI.</span></span>

```console
linkerd dashboard
```

<span data-ttu-id="00596-157">O painel fornece informações detalhadas sobre todos os serviços que estão conectados à malha.</span><span class="sxs-lookup"><span data-stu-id="00596-157">The dashboard provides detailed information about all services that are connected to the mesh.</span></span>

![Painel do Linkerd mostrando aplicativos StockKube](media/service-mesh/linkerd-screenshot.png)

<span data-ttu-id="00596-159">Se você aumentar o número de réplicas do serviço StockData gRPC, conforme mostrado no exemplo a seguir, e atualizar a página StockWeb no navegador, você deverá ver uma mistura de IDs na coluna **servidor** .</span><span class="sxs-lookup"><span data-stu-id="00596-159">If you increase the number of replicas of the StockData gRPC service as shown in the following example, and refresh the StockWeb page in the browser, you should see a mix of IDs in the **Server** column.</span></span> <span data-ttu-id="00596-160">Essa combinação indica que todas as instâncias disponíveis estão atendendo a solicitações.</span><span class="sxs-lookup"><span data-stu-id="00596-160">This mix indicates that all the available instances are serving requests.</span></span>

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
><span data-ttu-id="00596-161">[Anterior](kubernetes.md)
>[Próximo](load-balancing.md)</span><span class="sxs-lookup"><span data-stu-id="00596-161">[Previous](kubernetes.md)
[Next](load-balancing.md)</span></span>

---
title: Comunicação resiliente
description: Arquitetando aplicativos .NET nativos da nuvem para o Azure | Comunicação resiliente
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 33e4c03c1f3d8c01f72c588326fbb0bdfa512cdd
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613740"
---
# <a name="resilient-communications"></a><span data-ttu-id="230c1-103">Comunicações resilientes</span><span class="sxs-lookup"><span data-stu-id="230c1-103">Resilient communications</span></span>

<span data-ttu-id="230c1-104">Em todo este livro, adotamos uma abordagem arquitetônica baseada em microserviço.</span><span class="sxs-lookup"><span data-stu-id="230c1-104">Throughout this book, we've embraced a microservice-based architectural approach.</span></span> <span data-ttu-id="230c1-105">Embora essa arquitetura forneça benefícios importantes, ela apresenta muitos desafios:</span><span class="sxs-lookup"><span data-stu-id="230c1-105">While such an architecture provides important benefits, it presents many challenges:</span></span>

- <span data-ttu-id="230c1-106">*Comunicação de rede fora do processo.*</span><span class="sxs-lookup"><span data-stu-id="230c1-106">*Out-of-process network communication.*</span></span> <span data-ttu-id="230c1-107">Cada microserviço se comunica em um protocolo de rede que apresenta congestionamento de rede, latência e falhas transitórias.</span><span class="sxs-lookup"><span data-stu-id="230c1-107">Each microservice communicates over a network protocol that introduces network congestion, latency, and transient faults.</span></span>

- <span data-ttu-id="230c1-108">*Descoberta de serviço.*</span><span class="sxs-lookup"><span data-stu-id="230c1-108">*Service discovery.*</span></span> <span data-ttu-id="230c1-109">Como os microserviços detectam e se comunicam uns com os outros ao serem executados em um cluster de computadores com seus próprios endereços IP e portas?</span><span class="sxs-lookup"><span data-stu-id="230c1-109">How do microservices discover and communicate with each other when running across a cluster of machines with their own IP addresses and ports?</span></span>

- <span data-ttu-id="230c1-110">*Resiliência.*</span><span class="sxs-lookup"><span data-stu-id="230c1-110">*Resiliency.*</span></span> <span data-ttu-id="230c1-111">Como gerenciar falhas de curta duração e manter o sistema estável?</span><span class="sxs-lookup"><span data-stu-id="230c1-111">How do you manage short-lived failures and keep the system stable?</span></span>

- <span data-ttu-id="230c1-112">*Balanceamento de carga.*</span><span class="sxs-lookup"><span data-stu-id="230c1-112">*Load balancing.*</span></span> <span data-ttu-id="230c1-113">Como o tráfego de entrada é distribuído entre várias instâncias de um microserviço?</span><span class="sxs-lookup"><span data-stu-id="230c1-113">How does inbound traffic get distributed across multiple instances of a microservice?</span></span>

- <span data-ttu-id="230c1-114">*Segurança.*</span><span class="sxs-lookup"><span data-stu-id="230c1-114">*Security.*</span></span> <span data-ttu-id="230c1-115">Como as questões de segurança, como criptografia de nível de transporte e gerenciamento de certificados, são impostas?</span><span class="sxs-lookup"><span data-stu-id="230c1-115">How are security concerns such as transport-level encryption and certificate management enforced?</span></span>

- <span data-ttu-id="230c1-116">*Monitoramento distribuído.*</span><span class="sxs-lookup"><span data-stu-id="230c1-116">*Distributed Monitoring.*</span></span> <span data-ttu-id="230c1-117">-Como correlacionar e capturar a rastreabilidade e o monitoramento de uma única solicitação entre vários microservices de consumo?</span><span class="sxs-lookup"><span data-stu-id="230c1-117">- How do you correlate and capture traceability and monitoring for a single request across multiple consuming microservices?</span></span>

<span data-ttu-id="230c1-118">Você pode resolver essas preocupações com diferentes bibliotecas e estruturas, mas a implementação pode ser cara, complexa e demorada.</span><span class="sxs-lookup"><span data-stu-id="230c1-118">You can address these concerns with different libraries and frameworks, but the implementation can be expensive, complex, and time-consuming.</span></span> <span data-ttu-id="230c1-119">Você também acaba com preocupações com a infraestrutura associada à lógica de negócios.</span><span class="sxs-lookup"><span data-stu-id="230c1-119">You also end up with infrastructure concerns coupled to business logic.</span></span>

## <a name="service-mesh"></a><span data-ttu-id="230c1-120">Malha de serviço</span><span class="sxs-lookup"><span data-stu-id="230c1-120">Service mesh</span></span>

<span data-ttu-id="230c1-121">Uma abordagem melhor é uma tecnologia em evolução chamada *malha de serviço*.</span><span class="sxs-lookup"><span data-stu-id="230c1-121">A better approach is an evolving technology entitled *Service Mesh*.</span></span> <span data-ttu-id="230c1-122">Uma [malha de serviço](https://www.nginx.com/blog/what-is-a-service-mesh/) é uma camada de infraestrutura configurável com recursos internos para lidar com a comunicação do serviço e os outros desafios mencionados acima.</span><span class="sxs-lookup"><span data-stu-id="230c1-122">A [service mesh](https://www.nginx.com/blog/what-is-a-service-mesh/) is a configurable infrastructure layer with built-in capabilities to handle service communication and the other challenges mentioned above.</span></span> <span data-ttu-id="230c1-123">Ele dissocia essas preocupações movendo-as para um proxy de serviço.</span><span class="sxs-lookup"><span data-stu-id="230c1-123">It decouples these concerns by moving them into a service proxy.</span></span> <span data-ttu-id="230c1-124">O proxy é implantado em um processo separado (chamado de [sidecar](https://docs.microsoft.com/azure/architecture/patterns/sidecar)) para fornecer isolamento do código comercial.</span><span class="sxs-lookup"><span data-stu-id="230c1-124">The proxy is deployed into a separate process (called a [sidecar](https://docs.microsoft.com/azure/architecture/patterns/sidecar)) to provide isolation from business code.</span></span> <span data-ttu-id="230c1-125">No entanto, o sidecar está vinculado ao serviço – ele é criado com ele e compartilha seu ciclo de vida.</span><span class="sxs-lookup"><span data-stu-id="230c1-125">However, the sidecar is linked to the service - it's created with it and shares its lifecycle.</span></span> <span data-ttu-id="230c1-126">A Figura 6-7 mostra esse cenário.</span><span class="sxs-lookup"><span data-stu-id="230c1-126">Figure 6-7 shows this scenario.</span></span>

![Malha de serviço com um carro lateral](./media/service-mesh-with-side-car.png)

<span data-ttu-id="230c1-128">**Figura 6-7**.</span><span class="sxs-lookup"><span data-stu-id="230c1-128">**Figure 6-7**.</span></span> <span data-ttu-id="230c1-129">Malha de serviço com um carro lateral</span><span class="sxs-lookup"><span data-stu-id="230c1-129">Service mesh with a side car</span></span>

<span data-ttu-id="230c1-130">Na figura anterior, observe como o proxy intercepta e gerencia a comunicação entre os microserviços e o cluster.</span><span class="sxs-lookup"><span data-stu-id="230c1-130">In the previous figure, note how the proxy intercepts and manages communication among the microservices and the cluster.</span></span>

<span data-ttu-id="230c1-131">Uma malha de serviço é dividida logicamente em dois componentes diferentes: um [plano de dados](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) e um [plano de controle](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc).</span><span class="sxs-lookup"><span data-stu-id="230c1-131">A service mesh is logically split into two disparate components: A [data plane](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) and [control plane](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc).</span></span> <span data-ttu-id="230c1-132">A Figura 6-8 mostra esses componentes e suas responsabilidades.</span><span class="sxs-lookup"><span data-stu-id="230c1-132">Figure 6-8 shows these components and their responsibilities.</span></span>

![Controle de malha de serviço e plano de dados](./media/istio-control-and-data-plane.png)

<span data-ttu-id="230c1-134">**Figura 6-8.**</span><span class="sxs-lookup"><span data-stu-id="230c1-134">**Figure 6-8.**</span></span> <span data-ttu-id="230c1-135">Controle de malha de serviço e plano de dados</span><span class="sxs-lookup"><span data-stu-id="230c1-135">Service mesh control and data plane</span></span>

<span data-ttu-id="230c1-136">Uma vez configurado, uma malha de serviço é altamente funcional.</span><span class="sxs-lookup"><span data-stu-id="230c1-136">Once configured, a service mesh is highly functional.</span></span> <span data-ttu-id="230c1-137">Ele pode recuperar um pool correspondente de instâncias de um ponto de extremidade de descoberta de serviço.</span><span class="sxs-lookup"><span data-stu-id="230c1-137">It can retrieve a corresponding pool of instances from a service discovery endpoint.</span></span> <span data-ttu-id="230c1-138">Em seguida, a malha pode enviar uma solicitação para uma instância específica, registrando a latência e o tipo de resposta do resultado.</span><span class="sxs-lookup"><span data-stu-id="230c1-138">The mesh can then send a request to a specific instance, recording the latency and response type of the result.</span></span> <span data-ttu-id="230c1-139">Uma malha pode escolher a instância mais provável de retornar uma resposta rápida com base em vários fatores, incluindo sua latência observada para solicitações recentes.</span><span class="sxs-lookup"><span data-stu-id="230c1-139">A mesh can choose the instance most likely to return a fast response based on many factors, including its observed latency for recent requests.</span></span>

<span data-ttu-id="230c1-140">Se uma instância não estiver respondendo ou falhar, a malha tentará novamente a solicitação em outra instância.</span><span class="sxs-lookup"><span data-stu-id="230c1-140">If an instance is unresponsive or fails, the mesh will retry the request on another instance.</span></span> <span data-ttu-id="230c1-141">Se ele retornar erros, uma malha removerá a instância do pool de balanceamento de carga e a redefinirá após o reparo.</span><span class="sxs-lookup"><span data-stu-id="230c1-141">If it returns errors, a mesh will evict the instance from the load-balancing pool and restate it after it heals.</span></span> <span data-ttu-id="230c1-142">Se uma solicitação atingir o tempo limite, uma malha poderá falhar e, em seguida, repetir a solicitação.</span><span class="sxs-lookup"><span data-stu-id="230c1-142">If a request times out, a mesh can fail and then retry the request.</span></span> <span data-ttu-id="230c1-143">Uma malha captura e emite métricas e rastreamento distribuído para um sistema de métricas centralizado.</span><span class="sxs-lookup"><span data-stu-id="230c1-143">A mesh captures and emits metrics and distributed tracing to a centralized metrics system.</span></span>

## <a name="istio-and-envoy"></a><span data-ttu-id="230c1-144">İSTİO e Envoy</span><span class="sxs-lookup"><span data-stu-id="230c1-144">Istio and Envoy</span></span>

<span data-ttu-id="230c1-145">Embora algumas opções de malha de serviço existam atualmente, a [İSTİO](https://istio.io/docs/concepts/what-is-istio/) é a mais popular no momento da elaboração deste artigo.</span><span class="sxs-lookup"><span data-stu-id="230c1-145">While a few service mesh options currently exist, [Istio](https://istio.io/docs/concepts/what-is-istio/) is the most popular at the time of this writing.</span></span> <span data-ttu-id="230c1-146">İSTİO é uma joint venture da IBM, do Google e do lyft.</span><span class="sxs-lookup"><span data-stu-id="230c1-146">Istio is a joint venture from IBM, Google, and Lyft.</span></span> <span data-ttu-id="230c1-147">É uma oferta de código-fonte aberto que pode ser integrada a um aplicativo distribuído novo ou existente.</span><span class="sxs-lookup"><span data-stu-id="230c1-147">It's an open-source offering that can be integrated into a new or existing distributed application.</span></span> <span data-ttu-id="230c1-148">A tecnologia fornece uma solução consistente e completa para proteger, conectar e monitorar os microserviços.</span><span class="sxs-lookup"><span data-stu-id="230c1-148">The technology provides a consistent and complete solution to secure, connect, and monitor microservices.</span></span> <span data-ttu-id="230c1-149">Seus recursos incluem:</span><span class="sxs-lookup"><span data-stu-id="230c1-149">Its features include:</span></span>

- <span data-ttu-id="230c1-150">Proteja a comunicação entre serviços em um cluster com autenticação e autorização baseadas em identidade forte.</span><span class="sxs-lookup"><span data-stu-id="230c1-150">Secure service-to-service communication in a cluster with strong identity-based authentication and authorization.</span></span>
- <span data-ttu-id="230c1-151">Balanceamento de carga automático para tráfego HTTP, [gRPC](https://grpc.io/), WebSocket e TCP.</span><span class="sxs-lookup"><span data-stu-id="230c1-151">Automatic load balancing for HTTP, [gRPC](https://grpc.io/), WebSocket, and TCP traffic.</span></span>
- <span data-ttu-id="230c1-152">Controle refinado do comportamento de tráfego com regras de roteamento avançadas, repetições, failovers e injeção de falha.</span><span class="sxs-lookup"><span data-stu-id="230c1-152">Fine-grained control of traffic behavior with rich routing rules, retries, failovers, and fault injection.</span></span>
- <span data-ttu-id="230c1-153">Uma camada de política conectável e uma API de configuração que dão suporte a controles de acesso, limites de taxa e cotas.</span><span class="sxs-lookup"><span data-stu-id="230c1-153">A pluggable policy layer and configuration API supporting access controls, rate limits, and quotas.</span></span>
- <span data-ttu-id="230c1-154">Métricas, logs e rastreamentos automáticos para todo o tráfego em um cluster, incluindo a entrada e saída do cluster.</span><span class="sxs-lookup"><span data-stu-id="230c1-154">Automatic metrics, logs, and traces for all traffic within a cluster, including cluster ingress and egress.</span></span>

<span data-ttu-id="230c1-155">Um componente fundamental para uma implementação de İSTİO é um serviço de proxy intitulado The [Envoy proxy](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy).</span><span class="sxs-lookup"><span data-stu-id="230c1-155">A key component for an Istio implementation is a proxy service entitled the [Envoy proxy](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy).</span></span> <span data-ttu-id="230c1-156">Ele é executado junto com cada serviço e fornece uma base independente de plataforma para os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="230c1-156">It runs alongside each service and provides a platform-agnostic foundation for the following features:</span></span>

- <span data-ttu-id="230c1-157">Descoberta dinâmica de serviço.</span><span class="sxs-lookup"><span data-stu-id="230c1-157">Dynamic service discovery.</span></span>
- <span data-ttu-id="230c1-158">Balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="230c1-158">Load balancing.</span></span>
- <span data-ttu-id="230c1-159">Término do TLS.</span><span class="sxs-lookup"><span data-stu-id="230c1-159">TLS termination.</span></span>
- <span data-ttu-id="230c1-160">Proxies HTTP e gRPC.</span><span class="sxs-lookup"><span data-stu-id="230c1-160">HTTP and gRPC proxies.</span></span>
- <span data-ttu-id="230c1-161">Resiliência do disjuntor.</span><span class="sxs-lookup"><span data-stu-id="230c1-161">Circuit breaker resiliency.</span></span>
- <span data-ttu-id="230c1-162">Verificações de integridade.</span><span class="sxs-lookup"><span data-stu-id="230c1-162">Health checks.</span></span>
- <span data-ttu-id="230c1-163">Atualizações sem interrupção com implantações do [canário](https://martinfowler.com/bliki/CanaryRelease.html) .</span><span class="sxs-lookup"><span data-stu-id="230c1-163">Rolling updates with [canary](https://martinfowler.com/bliki/CanaryRelease.html) deployments.</span></span>

<span data-ttu-id="230c1-164">Conforme discutido anteriormente, o Envoy é implantado como um sidecar para cada microserviço no cluster.</span><span class="sxs-lookup"><span data-stu-id="230c1-164">As previously discussed, Envoy is deployed as a sidecar to each microservice in the cluster.</span></span>

## <a name="integration-with-azure-kubernetes-services"></a><span data-ttu-id="230c1-165">Integração com os serviços Kubernetess do Azure</span><span class="sxs-lookup"><span data-stu-id="230c1-165">Integration with Azure Kubernetes Services</span></span>

<span data-ttu-id="230c1-166">A nuvem do Azure adota o İSTİO e fornece suporte direto para ele nos serviços Kubernetess do Azure.</span><span class="sxs-lookup"><span data-stu-id="230c1-166">The Azure cloud embraces Istio and provides direct support for it within Azure Kubernetes Services.</span></span> <span data-ttu-id="230c1-167">Os links a seguir podem ajudá-lo a começar:</span><span class="sxs-lookup"><span data-stu-id="230c1-167">The following links can help you get started:</span></span>

- [<span data-ttu-id="230c1-168">Instalando o İSTİO no AKS</span><span class="sxs-lookup"><span data-stu-id="230c1-168">Installing Istio in AKS</span></span>](https://docs.microsoft.com/azure/aks/istio-install)
- [<span data-ttu-id="230c1-169">Usando AKS e İSTİO</span><span class="sxs-lookup"><span data-stu-id="230c1-169">Using AKS and Istio</span></span>](https://docs.microsoft.com/azure/aks/istio-scenario-routing)

### <a name="references"></a><span data-ttu-id="230c1-170">Referências</span><span class="sxs-lookup"><span data-stu-id="230c1-170">References</span></span>

- [<span data-ttu-id="230c1-171">Polly</span><span class="sxs-lookup"><span data-stu-id="230c1-171">Polly</span></span>](http://www.thepollyproject.org/)

- [<span data-ttu-id="230c1-172">Padrão de repetição</span><span class="sxs-lookup"><span data-stu-id="230c1-172">Retry pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/retry)

- [<span data-ttu-id="230c1-173">Padrão de disjuntor</span><span class="sxs-lookup"><span data-stu-id="230c1-173">Circuit Breaker pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)

- [<span data-ttu-id="230c1-174">White paper sobre resiliência no Azure</span><span class="sxs-lookup"><span data-stu-id="230c1-174">Resilience in Azure whitepaper</span></span>](https://azure.microsoft.com/mediahandler/files/resourcefiles/resilience-in-azure-whitepaper/Resilience%20in%20Azure.pdf)

- [<span data-ttu-id="230c1-175">latência de rede</span><span class="sxs-lookup"><span data-stu-id="230c1-175">network latency</span></span>](https://www.techopedia.com/definition/8553/network-latency)

- [<span data-ttu-id="230c1-176">Redundância</span><span class="sxs-lookup"><span data-stu-id="230c1-176">Redundancy</span></span>](https://docs.microsoft.com/azure/architecture/guide/design-principles/redundancy)

- [<span data-ttu-id="230c1-177">replicação geográfica</span><span class="sxs-lookup"><span data-stu-id="230c1-177">geo-replication</span></span>](https://docs.microsoft.com/azure/sql-database/sql-database-active-geo-replication)

- [<span data-ttu-id="230c1-178">Gerenciador de Tráfego do Azure</span><span class="sxs-lookup"><span data-stu-id="230c1-178">Azure Traffic Manager</span></span>](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)

- [<span data-ttu-id="230c1-179">Diretrizes de dimensionamento automático</span><span class="sxs-lookup"><span data-stu-id="230c1-179">Autoscaling guidance</span></span>](https://docs.microsoft.com/azure/architecture/best-practices/auto-scaling)

- [<span data-ttu-id="230c1-180">İSTİO</span><span class="sxs-lookup"><span data-stu-id="230c1-180">Istio</span></span>](https://istio.io/docs/concepts/what-is-istio/)

- [<span data-ttu-id="230c1-181">Proxy Envoy</span><span class="sxs-lookup"><span data-stu-id="230c1-181">Envoy proxy</span></span>](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy)

>[!div class="step-by-step"]
><span data-ttu-id="230c1-182">[Anterior](infrastructure-resiliency-azure.md) 
> [Avançar](monitoring-health.md)</span><span class="sxs-lookup"><span data-stu-id="230c1-182">[Previous](infrastructure-resiliency-azure.md)
[Next](monitoring-health.md)</span></span>

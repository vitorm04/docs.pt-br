---
title: Balanceamento de carga gRPC-gRPC para desenvolvedores do WCF
description: Escolhendo um balanceador de carga para trabalhar com os serviços gRPCs.
ms.date: 09/02/2019
ms.openlocfilehash: 070fc7fda73988302d15c8cec12b1ac359641317
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967447"
---
# <a name="load-balancing-grpc"></a><span data-ttu-id="88ccf-103">GRPC de balanceamento de carga</span><span class="sxs-lookup"><span data-stu-id="88ccf-103">Load balancing gRPC</span></span>

<span data-ttu-id="88ccf-104">Uma implantação típica de um aplicativo gRPC inclui várias instâncias idênticas do serviço, fornecendo resiliência e escalabilidade horizontal.</span><span class="sxs-lookup"><span data-stu-id="88ccf-104">A typical deployment of a gRPC application includes a number of identical instances of the service, providing resilience and horizontal scalability.</span></span> <span data-ttu-id="88ccf-105">Balanceamento de carga de solicitações de entrada distribuídas entre essas instâncias para fornecer uso total de todos os recursos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="88ccf-105">Load balancing distributed incoming requests across these instances to provide full usage of all available resources.</span></span> <span data-ttu-id="88ccf-106">Para tornar esse balanceamento de carga invisível para o cliente, é comum usar um servidor de balanceador de carga proxy para lidar com solicitações de clientes e roteá-las para instâncias de back-end.</span><span class="sxs-lookup"><span data-stu-id="88ccf-106">To make this load balancing invisible to the client, it's common to use a proxy load balancer server to handle requests from clients and route them to back-end instances.</span></span>

<span data-ttu-id="88ccf-107">Os balanceadores de carga são classificados de acordo com a *camada* em que operam.</span><span class="sxs-lookup"><span data-stu-id="88ccf-107">Load balancers are classified according to the *layer* they operate on.</span></span> <span data-ttu-id="88ccf-108">Os balanceadores de carga de camada 4 funcionam no nível de *transporte* , por exemplo, com soquetes TCP, conexões e pacotes.</span><span class="sxs-lookup"><span data-stu-id="88ccf-108">Layer 4 load balancers work on the *transport* level, for example, with TCP sockets, connections and packets.</span></span> <span data-ttu-id="88ccf-109">Os balanceadores de carga de camada 7 funcionam no nível do *aplicativo* , manipulando especificamente solicitações HTTP/2 para aplicativos gRPC.</span><span class="sxs-lookup"><span data-stu-id="88ccf-109">Layer 7 load balancers work at the *application* level, specifically handling HTTP/2 requests for gRPC applications.</span></span>

## <a name="l4-load-balancers"></a><span data-ttu-id="88ccf-110">Balanceadores de carga L4</span><span class="sxs-lookup"><span data-stu-id="88ccf-110">L4 load balancers</span></span>

<span data-ttu-id="88ccf-111">Um balanceador de carga L4 aceita uma solicitação de conexão TCP de um cliente, abre outra conexão com uma das instâncias de back-end e copia dados entre as duas conexões sem processamento real.</span><span class="sxs-lookup"><span data-stu-id="88ccf-111">An L4 load balancer accepts a TCP connection request from a client, opens another connection to one of the back-end instances, and copies data between the two connections with no real processing.</span></span> <span data-ttu-id="88ccf-112">O L4 oferece excelente desempenho e baixa latência, mas muito pouco controle ou inteligência.</span><span class="sxs-lookup"><span data-stu-id="88ccf-112">L4 offers excellent performance and low latency, but very little control or intelligence.</span></span> <span data-ttu-id="88ccf-113">Desde que o cliente mantenha a conexão aberta, todas as solicitações serão direcionadas para a mesma instância de back-end.</span><span class="sxs-lookup"><span data-stu-id="88ccf-113">As long as the client keeps the connection open, all requests will be directed to the same back-end instance.</span></span>

<span data-ttu-id="88ccf-114">Um exemplo de um balanceador de carga L4 é o [Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/).</span><span class="sxs-lookup"><span data-stu-id="88ccf-114">An example of an L4 load balancer is the [Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/).</span></span>

## <a name="l7-load-balancers"></a><span data-ttu-id="88ccf-115">Balanceadores de carga L7</span><span class="sxs-lookup"><span data-stu-id="88ccf-115">L7 load balancers</span></span>

<span data-ttu-id="88ccf-116">Um balanceador de carga L7 analisa as solicitações HTTP/2 de entrada e as passa para as instâncias de back-end em uma base solicitação por solicitação, independentemente de quanto tempo a conexão é mantida pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="88ccf-116">An L7 load balancer parses incoming HTTP/2 requests and passes them on to back-end instances on a request-by-request basis, no matter how long the connection is held by the client.</span></span>

<span data-ttu-id="88ccf-117">Exemplos de balanceadores de carga L7 incluem:</span><span class="sxs-lookup"><span data-stu-id="88ccf-117">Examples of L7 load balancers include:</span></span>

- [<span data-ttu-id="88ccf-118">Nginx</span><span class="sxs-lookup"><span data-stu-id="88ccf-118">Nginx</span></span>](https://www.nginx.com/)
- [<span data-ttu-id="88ccf-119">HAproxy</span><span class="sxs-lookup"><span data-stu-id="88ccf-119">HAproxy</span></span>](https://www.haproxy.com/)
- [<span data-ttu-id="88ccf-120">Traefik</span><span class="sxs-lookup"><span data-stu-id="88ccf-120">Traefik</span></span>](https://traefik.io/)

<span data-ttu-id="88ccf-121">Como regra prática, os balanceadores de carga L7 são a melhor opção para gRPC e outros aplicativos HTTP/2 (e para aplicativos HTTP geralmente, de fato).</span><span class="sxs-lookup"><span data-stu-id="88ccf-121">As a rule of thumb, L7 load balancers are the best choice for gRPC and other HTTP/2 applications (and for HTTP applications generally, in fact).</span></span> <span data-ttu-id="88ccf-122">Os balanceadores de carga L4 *funcionarão* com aplicativos gRPC, mas são principalmente úteis quando baixa latência e baixa sobrecarga são de extrema importância.</span><span class="sxs-lookup"><span data-stu-id="88ccf-122">L4 load balancers will *work* with gRPC applications, but are primarily useful when low latency and low overhead are of paramount importance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="88ccf-123">No momento da redação deste artigo, nem todos os balanceadores de carga L7 dão suporte a todas as partes da especificação HTTP/2 exigidas pelos serviços gRPCs, como cabeçalhos à direita.</span><span class="sxs-lookup"><span data-stu-id="88ccf-123">At the time of this writing, not all L7 load balancers support all parts of the HTTP/2 specification required by gRPC services, such as trailing headers.</span></span>

<span data-ttu-id="88ccf-124">Ao usar a criptografia TLS, os balanceadores de carga podem encerrar a conexão TLS e passar solicitações não criptografadas para o aplicativo de back-end ou passar a solicitação criptografada ao longo do.</span><span class="sxs-lookup"><span data-stu-id="88ccf-124">When using TLS encryption, load balancers can terminate the TLS connection and pass unencrypted requests to the back-end application, or pass the encrypted request along.</span></span> <span data-ttu-id="88ccf-125">De qualquer forma, o balanceador de carga precisará ser configurado com a chave pública e privada do servidor para que ele possa descriptografar solicitações de processamento.</span><span class="sxs-lookup"><span data-stu-id="88ccf-125">Either way, the load balancer will need to be configured with the server's public and private key, so that it can decrypt requests for processing.</span></span>

<span data-ttu-id="88ccf-126">Consulte a documentação do balanceador de carga preferencial para descobrir como configurá-lo para lidar com solicitações HTTP/2 com seus serviços de back-end.</span><span class="sxs-lookup"><span data-stu-id="88ccf-126">Refer to the documentation for your preferred load balancer to find out how to configure it to handle HTTP/2 requests with your back-end services.</span></span>

## <a name="load-balancing-within-kubernetes"></a><span data-ttu-id="88ccf-127">Balanceamento de carga dentro de kubernetes</span><span class="sxs-lookup"><span data-stu-id="88ccf-127">Load balancing within Kubernetes</span></span>

<span data-ttu-id="88ccf-128">Consulte [a seção sobre malhas de serviço](service-mesh.md) para obter uma discussão sobre o balanceamento de carga entre serviços internos no kubernetes.</span><span class="sxs-lookup"><span data-stu-id="88ccf-128">See [the section on Service Meshes](service-mesh.md) for a discussion of load balancing across internal services on Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="88ccf-129">[Anterior](service-mesh.md)
>[Próximo](application-performance-management.md)</span><span class="sxs-lookup"><span data-stu-id="88ccf-129">[Previous](service-mesh.md)
[Next](application-performance-management.md)</span></span>

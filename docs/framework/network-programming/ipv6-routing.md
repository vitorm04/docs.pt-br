---
title: Roteamento IPv6
ms.date: 03/30/2017
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
ms.openlocfilehash: 0f0fbce84caf096770e49ab47fb1de5b23b44b33
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136676"
---
# <a name="ipv6-routing"></a><span data-ttu-id="79619-102">Roteamento IPv6</span><span class="sxs-lookup"><span data-stu-id="79619-102">IPv6 Routing</span></span>
<span data-ttu-id="79619-103">Um mecanismo de roteamento flexível é uma vantagem do IPv6.</span><span class="sxs-lookup"><span data-stu-id="79619-103">A flexible routing mechanism is a benefit of IPv6.</span></span> <span data-ttu-id="79619-104">Devido à maneira que as IDs de rede IPv4 foram e são alocadas, grandes tabelas de roteamento precisam ser mantidas pelos roteadores que estão nos backbones da Internet.</span><span class="sxs-lookup"><span data-stu-id="79619-104">Due to the way in which IPv4 network IDs were and are allocated, large routing tables need to be maintained by the routers that are on the Internet backbones.</span></span> <span data-ttu-id="79619-105">Esses roteadores devem saber todas as rotas para encaminhar pacotes que são potencialmente direcionados para qualquer nó na Internet.</span><span class="sxs-lookup"><span data-stu-id="79619-105">These routers must know all the routes in order to forward packets that are potentially directed to any node on the Internet.</span></span> <span data-ttu-id="79619-106">Com sua capacidade de agregar endereços, o IPv6 permite endereçamento flexível e reduz consideravelmente o tamanho das tabelas de roteamento.</span><span class="sxs-lookup"><span data-stu-id="79619-106">With its ability to aggregate addresses, IPv6 allows flexible addressing and drastically reduces the size of routing tables.</span></span> <span data-ttu-id="79619-107">Nessa nova arquitetura de endereçamento, os roteadores intermediários devem controlar apenas a parte local de sua rede para encaminhar as mensagens corretamente.</span><span class="sxs-lookup"><span data-stu-id="79619-107">In this new addressing architecture, intermediate routers must keep track only of the local portion of their network in order to forward the messages appropriately.</span></span>  
  
## <a name="neighbor-discovery"></a><span data-ttu-id="79619-108">Descoberta de vizinhos</span><span class="sxs-lookup"><span data-stu-id="79619-108">Neighbor Discovery</span></span>  
 <span data-ttu-id="79619-109">Estes são alguns dos recursos fornecidos pela descoberta de vizinhos:</span><span class="sxs-lookup"><span data-stu-id="79619-109">Some of the features provided by Neighbor Discovery are:</span></span>  
  
-   <span data-ttu-id="79619-110">Descoberta de roteador.</span><span class="sxs-lookup"><span data-stu-id="79619-110">Router discovery.</span></span> <span data-ttu-id="79619-111">Isso permite que os hosts identifiquem os roteadores locais.</span><span class="sxs-lookup"><span data-stu-id="79619-111">This allows hosts to identify local routers.</span></span>  
  
-   <span data-ttu-id="79619-112">Resolução de endereço.</span><span class="sxs-lookup"><span data-stu-id="79619-112">Address resolution.</span></span> <span data-ttu-id="79619-113">Isso permite que os nós resolvam um endereço de camada de link para um endereço de próximo salto correspondente (uma substituição para o protocolo de resolução de endereço [ARP]).</span><span class="sxs-lookup"><span data-stu-id="79619-113">This allows nodes to resolve a link-layer address for a corresponding next-hop address (a replacement for Address Resolution Protocol [ARP]).</span></span>  
  
-   <span data-ttu-id="79619-114">Configuração automática de endereço.</span><span class="sxs-lookup"><span data-stu-id="79619-114">Address auto-configuration.</span></span> <span data-ttu-id="79619-115">Isso permite que os hosts configurem automaticamente os endereços locais e globais de sites.</span><span class="sxs-lookup"><span data-stu-id="79619-115">This allows hosts to automatically configure site-local and global addresses.</span></span>  
  
 <span data-ttu-id="79619-116">A descoberta de vizinho usa protocolo ICMP para mensagens IPv6 (ICMPv6) que incluem:</span><span class="sxs-lookup"><span data-stu-id="79619-116">Neighbor Discovery uses Internet Control Message Protocol for IPv6 (ICMPv6) messages that include:</span></span>  
  
-   <span data-ttu-id="79619-117">Anúncio de roteador.</span><span class="sxs-lookup"><span data-stu-id="79619-117">Router advertisement.</span></span> <span data-ttu-id="79619-118">Enviado por um roteador psudoperiodicamente ou em resposta a uma solicitação de roteador.</span><span class="sxs-lookup"><span data-stu-id="79619-118">Sent by a router on a pseudo-periodic basis or in response to a router solicitation.</span></span> <span data-ttu-id="79619-119">Os roteadores IPv6 usam anúncios de roteador para anunciar a própria disponibilidade, prefixos de endereço e outros parâmetros.</span><span class="sxs-lookup"><span data-stu-id="79619-119">IPv6 routers use router advertisements to advertise their availability, address prefixes, and other parameters.</span></span>  
  
-   <span data-ttu-id="79619-120">Solicitação de roteador.</span><span class="sxs-lookup"><span data-stu-id="79619-120">Router solicitation.</span></span> <span data-ttu-id="79619-121">Enviada por um host para solicitar que os roteadores no link enviem um anúncio de roteador imediatamente.</span><span class="sxs-lookup"><span data-stu-id="79619-121">Sent by a host to request that routers on the link send a router advertisement immediately.</span></span>  
  
-   <span data-ttu-id="79619-122">Solicitação de vizinho.</span><span class="sxs-lookup"><span data-stu-id="79619-122">Neighbor solicitation.</span></span> <span data-ttu-id="79619-123">Enviado por nós para resolução de endereço, para detecção de endereço duplicado ou para verificar se um vizinho ainda pode ser acessado.</span><span class="sxs-lookup"><span data-stu-id="79619-123">Sent by nodes for address resolution, duplicate address detection, or to verify that a neighbor is still reachable.</span></span>  
  
-   <span data-ttu-id="79619-124">Anúncio de vizinho.</span><span class="sxs-lookup"><span data-stu-id="79619-124">Neighbor advertisement.</span></span> <span data-ttu-id="79619-125">Enviado por nós para responder a uma solicitação de vizinho ou para notificar vizinhos de uma alteração no endereço de camada de link.</span><span class="sxs-lookup"><span data-stu-id="79619-125">Sent by nodes to respond to a neighbor solicitation or to notify neighbors of a change in link-layer address.</span></span>  
  
-   <span data-ttu-id="79619-126">Redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="79619-126">Redirect.</span></span> <span data-ttu-id="79619-127">Enviado por roteadores a fim de indicar um melhor endereço de próximo salto para um destino específico para um nó de envio.</span><span class="sxs-lookup"><span data-stu-id="79619-127">Sent by routers to indicate a better next-hop address to a particular destination for a sending node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79619-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79619-128">See also</span></span>

- [<span data-ttu-id="79619-129">Protocolo da Internet Versão 6</span><span class="sxs-lookup"><span data-stu-id="79619-129">Internet Protocol Version 6</span></span>](../../../docs/framework/network-programming/internet-protocol-version-6.md)
- [<span data-ttu-id="79619-130">Soquetes</span><span class="sxs-lookup"><span data-stu-id="79619-130">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)

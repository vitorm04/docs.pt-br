---
title: "Configuração automática de endereço IPv6"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 581c1d21-1013-43a3-bf3e-2d9ead62b79c
caps.latest.revision: "5"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: b116e3aa88f919b850d6f79754d25ee10ac974f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ipv6-auto-configuration"></a><span data-ttu-id="544bf-102">Configuração automática de endereço IPv6</span><span class="sxs-lookup"><span data-stu-id="544bf-102">IPv6 Auto-Configuration</span></span>
<span data-ttu-id="544bf-103">Uma meta importante para IPv6 é dar suporte a Plug and Play de nó.</span><span class="sxs-lookup"><span data-stu-id="544bf-103">One important goal for IPv6 is to support node Plug and Play.</span></span> <span data-ttu-id="544bf-104">Ou seja, deve ser possível conectar um nó a uma rede IPv6 de modo que ele seja configurado automaticamente sem intervenção humana.</span><span class="sxs-lookup"><span data-stu-id="544bf-104">That is, it should be possible to plug a node into an IPv6 network and have it automatically configured without any human intervention.</span></span>  
  
## <a name="type-of-auto-configuration"></a><span data-ttu-id="544bf-105">Tipo de configuração automática</span><span class="sxs-lookup"><span data-stu-id="544bf-105">Type of Auto-Configuration</span></span>  
 <span data-ttu-id="544bf-106">O IPv6 dá suporte aos seguintes tipos de configuração automática:</span><span class="sxs-lookup"><span data-stu-id="544bf-106">IPv6 supports the following types of auto-configuration:</span></span>  
  
-   <span data-ttu-id="544bf-107">**Configuração automática com estado**.</span><span class="sxs-lookup"><span data-stu-id="544bf-107">**Stateful auto-configuration**.</span></span> <span data-ttu-id="544bf-108">Esse tipo de configuração requer um certo nível de intervenção humana, porque é necessário um protocolo DHCP para servidor IPv6 (DHCPv6) para a instalação e administração dos nós.</span><span class="sxs-lookup"><span data-stu-id="544bf-108">This type of configuration requires a certain level of human intervention because it needs a Dynamic Host Configuration Protocol for IPv6 (DHCPv6) server for the installation and administration of the nodes.</span></span> <span data-ttu-id="544bf-109">O servidor DHCPv6 mantém uma lista de nós para os quais ele fornece informações de configuração.</span><span class="sxs-lookup"><span data-stu-id="544bf-109">The DHCPv6 server keeps a list of nodes to which it supplies configuration information.</span></span> <span data-ttu-id="544bf-110">Ele também mantém informações de estado para que o servidor saiba quanto tempo cada endereço está em uso e quando ele pode estar disponível para reatribuição.</span><span class="sxs-lookup"><span data-stu-id="544bf-110">It also maintains state information so the server knows how long each address is in use, and when it might be available for reassignment.</span></span>  
  
-   <span data-ttu-id="544bf-111">**Configuração automática sem monitoração de estado**.</span><span class="sxs-lookup"><span data-stu-id="544bf-111">**Stateless auto-configuration**.</span></span> <span data-ttu-id="544bf-112">Esse tipo de configuração é adequado para indivíduos e pequenas empresas.</span><span class="sxs-lookup"><span data-stu-id="544bf-112">This type of configuration is suitable for small organizations and individuals.</span></span> <span data-ttu-id="544bf-113">Nesse caso, cada host determina seus endereços com base no conteúdo de anúncios de roteador recebidos.</span><span class="sxs-lookup"><span data-stu-id="544bf-113">In this case, each host determines its addresses from the contents of received router advertisements.</span></span> <span data-ttu-id="544bf-114">Usando o padrão IEEE EUI-64 para definir a parte de ID de rede do endereço, é razoável pressupor a exclusividade do endereço de host no link.</span><span class="sxs-lookup"><span data-stu-id="544bf-114">Using the IEEE EUI-64 standard to define the network ID portion of the address, it is reasonable to assume the uniqueness of the host address on the link.</span></span>  
  
 <span data-ttu-id="544bf-115">Independentemente de como o endereço é determinado, o nó deve verificar se seu endereço potencial é exclusivo para o link local.</span><span class="sxs-lookup"><span data-stu-id="544bf-115">Regardless of how the address is determined, the node must verify that its potential address is unique to the local link.</span></span> <span data-ttu-id="544bf-116">Isso é feito enviando uma mensagem de solicitação de vizinho para o endereço potencial.</span><span class="sxs-lookup"><span data-stu-id="544bf-116">This is done by sending a neighbor solicitation message to the potential address.</span></span> <span data-ttu-id="544bf-117">Se o nó receber alguma resposta, ele saberá que o endereço já está em uso e deverá determinar outro endereço.</span><span class="sxs-lookup"><span data-stu-id="544bf-117">If the node receives any response, it knows that the address is already in use and must determine another address.</span></span>  
  
## <a name="ipv6-mobility"></a><span data-ttu-id="544bf-118">Mobilidade IPv6</span><span class="sxs-lookup"><span data-stu-id="544bf-118">IPv6 Mobility</span></span>  
 <span data-ttu-id="544bf-119">A proliferação de dispositivos móveis introduziu um novo requisito: um dispositivo deve ser capaz de alterar os locais na Internet IPv6 arbitrariamente e ainda manter as conexões existentes.</span><span class="sxs-lookup"><span data-stu-id="544bf-119">The proliferation of mobile devices has introduced a new requirement: A device must be able to arbitrarily change locations on the IPv6 Internet and still maintain existing connections.</span></span> <span data-ttu-id="544bf-120">Para fornecer essa funcionalidade, um endereço residencial é atribuído a um nó móvel, endereço no qual ele sempre pode ser alcançado.</span><span class="sxs-lookup"><span data-stu-id="544bf-120">To provide this functionality, a mobile node is assigned a home address at which it can always be reached.</span></span> <span data-ttu-id="544bf-121">Quando o nó móvel está no endereço residencial, ele se conecta ao link residencial e usa seu endereço residencial.</span><span class="sxs-lookup"><span data-stu-id="544bf-121">When the mobile node is at home, it connects to the home link and uses its home address.</span></span> <span data-ttu-id="544bf-122">Quando o nó móvel está longe do endereço residencial, um agente, que geralmente é um roteador, retransmite mensagens entre o nó móvel e os nós com os quais ele está se comunicando.</span><span class="sxs-lookup"><span data-stu-id="544bf-122">When the mobile node is away from home, a home agent, which is usually a router, relays messages between the mobile node and nodes with which it is communicating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="544bf-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="544bf-123">See Also</span></span>  
 [<span data-ttu-id="544bf-124">Protocolo IP versão 6</span><span class="sxs-lookup"><span data-stu-id="544bf-124">Internet Protocol Version 6</span></span>](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [<span data-ttu-id="544bf-125">Soquetes</span><span class="sxs-lookup"><span data-stu-id="544bf-125">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)

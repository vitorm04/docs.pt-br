---
title: "Configuração automática de endereço IPv6"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 581c1d21-1013-43a3-bf3e-2d9ead62b79c
caps.latest.revision: 5
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c46d4b8f6b9e3620c313e9737b556a6050da0126
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="ipv6-auto-configuration"></a><span data-ttu-id="b304b-102">Configuração automática de endereço IPv6</span><span class="sxs-lookup"><span data-stu-id="b304b-102">IPv6 Auto-Configuration</span></span>
<span data-ttu-id="b304b-103">Uma meta importante para IPv6 é dar suporte a Plug and Play de nó.</span><span class="sxs-lookup"><span data-stu-id="b304b-103">One important goal for IPv6 is to support node Plug and Play.</span></span> <span data-ttu-id="b304b-104">Ou seja, deve ser possível conectar um nó a uma rede IPv6 de modo que ele seja configurado automaticamente sem intervenção humana.</span><span class="sxs-lookup"><span data-stu-id="b304b-104">That is, it should be possible to plug a node into an IPv6 network and have it automatically configured without any human intervention.</span></span>  
  
## <a name="type-of-auto-configuration"></a><span data-ttu-id="b304b-105">Tipo de configuração automática</span><span class="sxs-lookup"><span data-stu-id="b304b-105">Type of Auto-Configuration</span></span>  
 <span data-ttu-id="b304b-106">O IPv6 dá suporte aos seguintes tipos de configuração automática:</span><span class="sxs-lookup"><span data-stu-id="b304b-106">IPv6 supports the following types of auto-configuration:</span></span>  
  
-   <span data-ttu-id="b304b-107">**Configuração automática com estado**.</span><span class="sxs-lookup"><span data-stu-id="b304b-107">**Stateful auto-configuration**.</span></span> <span data-ttu-id="b304b-108">Esse tipo de configuração requer um certo nível de intervenção humana, porque é necessário um protocolo DHCP para servidor IPv6 (DHCPv6) para a instalação e administração dos nós.</span><span class="sxs-lookup"><span data-stu-id="b304b-108">This type of configuration requires a certain level of human intervention because it needs a Dynamic Host Configuration Protocol for IPv6 (DHCPv6) server for the installation and administration of the nodes.</span></span> <span data-ttu-id="b304b-109">O servidor DHCPv6 mantém uma lista de nós para os quais ele fornece informações de configuração.</span><span class="sxs-lookup"><span data-stu-id="b304b-109">The DHCPv6 server keeps a list of nodes to which it supplies configuration information.</span></span> <span data-ttu-id="b304b-110">Ele também mantém informações de estado para que o servidor saiba quanto tempo cada endereço está em uso e quando ele pode estar disponível para reatribuição.</span><span class="sxs-lookup"><span data-stu-id="b304b-110">It also maintains state information so the server knows how long each address is in use, and when it might be available for reassignment.</span></span>  
  
-   <span data-ttu-id="b304b-111">**Configuração automática sem monitoração de estado**.</span><span class="sxs-lookup"><span data-stu-id="b304b-111">**Stateless auto-configuration**.</span></span> <span data-ttu-id="b304b-112">Esse tipo de configuração é adequado para indivíduos e pequenas empresas.</span><span class="sxs-lookup"><span data-stu-id="b304b-112">This type of configuration is suitable for small organizations and individuals.</span></span> <span data-ttu-id="b304b-113">Nesse caso, cada host determina seus endereços com base no conteúdo de anúncios de roteador recebidos.</span><span class="sxs-lookup"><span data-stu-id="b304b-113">In this case, each host determines its addresses from the contents of received router advertisements.</span></span> <span data-ttu-id="b304b-114">Usando o padrão IEEE EUI-64 para definir a parte de ID de rede do endereço, é razoável pressupor a exclusividade do endereço de host no link.</span><span class="sxs-lookup"><span data-stu-id="b304b-114">Using the IEEE EUI-64 standard to define the network ID portion of the address, it is reasonable to assume the uniqueness of the host address on the link.</span></span>  
  
 <span data-ttu-id="b304b-115">Independentemente de como o endereço é determinado, o nó deve verificar se seu endereço potencial é exclusivo para o link local.</span><span class="sxs-lookup"><span data-stu-id="b304b-115">Regardless of how the address is determined, the node must verify that its potential address is unique to the local link.</span></span> <span data-ttu-id="b304b-116">Isso é feito enviando uma mensagem de solicitação de vizinho para o endereço potencial.</span><span class="sxs-lookup"><span data-stu-id="b304b-116">This is done by sending a neighbor solicitation message to the potential address.</span></span> <span data-ttu-id="b304b-117">Se o nó receber alguma resposta, ele saberá que o endereço já está em uso e deverá determinar outro endereço.</span><span class="sxs-lookup"><span data-stu-id="b304b-117">If the node receives any response, it knows that the address is already in use and must determine another address.</span></span>  
  
## <a name="ipv6-mobility"></a><span data-ttu-id="b304b-118">Mobilidade IPv6</span><span class="sxs-lookup"><span data-stu-id="b304b-118">IPv6 Mobility</span></span>  
 <span data-ttu-id="b304b-119">A proliferação de dispositivos móveis introduziu um novo requisito: um dispositivo deve ser capaz de alterar os locais na Internet IPv6 arbitrariamente e ainda manter as conexões existentes.</span><span class="sxs-lookup"><span data-stu-id="b304b-119">The proliferation of mobile devices has introduced a new requirement: A device must be able to arbitrarily change locations on the IPv6 Internet and still maintain existing connections.</span></span> <span data-ttu-id="b304b-120">Para fornecer essa funcionalidade, um endereço residencial é atribuído a um nó móvel, endereço no qual ele sempre pode ser alcançado.</span><span class="sxs-lookup"><span data-stu-id="b304b-120">To provide this functionality, a mobile node is assigned a home address at which it can always be reached.</span></span> <span data-ttu-id="b304b-121">Quando o nó móvel está no endereço residencial, ele se conecta ao link residencial e usa seu endereço residencial.</span><span class="sxs-lookup"><span data-stu-id="b304b-121">When the mobile node is at home, it connects to the home link and uses its home address.</span></span> <span data-ttu-id="b304b-122">Quando o nó móvel está longe do endereço residencial, um agente, que geralmente é um roteador, retransmite mensagens entre o nó móvel e os nós com os quais ele está se comunicando.</span><span class="sxs-lookup"><span data-stu-id="b304b-122">When the mobile node is away from home, a home agent, which is usually a router, relays messages between the mobile node and nodes with which it is communicating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b304b-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b304b-123">See Also</span></span>  
 <span data-ttu-id="b304b-124">[Protocolo IP versão 6](../../../docs/framework/network-programming/internet-protocol-version-6.md) </span><span class="sxs-lookup"><span data-stu-id="b304b-124">[Internet Protocol Version 6](../../../docs/framework/network-programming/internet-protocol-version-6.md) </span></span>  
 [<span data-ttu-id="b304b-125">Soquetes</span><span class="sxs-lookup"><span data-stu-id="b304b-125">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)


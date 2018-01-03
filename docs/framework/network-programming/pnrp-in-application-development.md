---
title: PNRP no desenvolvimento do aplicativo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d11f1b284ebb4e4a44d1dad442f727692fa26ffa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="pnrp-in-application-development"></a><span data-ttu-id="5e712-102">PNRP no desenvolvimento do aplicativo</span><span class="sxs-lookup"><span data-stu-id="5e712-102">PNRP in Application Development</span></span>
<span data-ttu-id="5e712-103">No o Windows Vista, os aplicativos de rede podem acessar funções de publicação e de resolução de nomes por meio de uma API (interface de programação de aplicativo) PNRP simplificada.</span><span class="sxs-lookup"><span data-stu-id="5e712-103">In Windows Vista, networking applications can access name publication and resolution functions through a simplified PNRP application programming interface (API).</span></span>  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a><span data-ttu-id="5e712-104">Implementando o protocolo PNRP</span><span class="sxs-lookup"><span data-stu-id="5e712-104">Implementing the Peer Name Resolution Protocol</span></span>  
 <span data-ttu-id="5e712-105">Com a API PNRP simplificada, nuvens não são especificadas explicitamente para registrar o nome e endereços; o componente PNRP determina automaticamente as nuvens apropriadas ingressar e os endereços para publicar dentro delas.</span><span class="sxs-lookup"><span data-stu-id="5e712-105">With the simplified PNRP API, clouds are not explicitly specified to register the name and addresses; the PNRP component automatically determines the appropriate clouds to join and the addresses to publish within the clouds.</span></span>  
  
 <span data-ttu-id="5e712-106">Para proporcionar uma resolução de nomes PNRP simplificada no Windows Vista, os nomes PNRP agora estão integrados à função getaddrinfo() do Windows Sockets.</span><span class="sxs-lookup"><span data-stu-id="5e712-106">For highly simplified PNRP name resolution in Windows Vista, PNRP names are now integrated into the getaddrinfo() Windows Sockets function.</span></span> <span data-ttu-id="5e712-107">Para usar o PNRP para solucionar um nome para um endereço IPv6, os aplicativos podem usar a função getaddrinfo() para solucionar o FQDN (nome de domínio totalmente qualificado) nome.prnp.net, no qual nome é o nome do par que está sendo resolvido.</span><span class="sxs-lookup"><span data-stu-id="5e712-107">To use PNRP to resolve a name to an IPv6 address, applications can use the getaddrinfo() function to resolve the Fully Qualified Domain Name (FQDN) name.prnp.net, in which name is peer name being resolved.</span></span> <span data-ttu-id="5e712-108">O domínio pnrp.net é um domínio reservado no Windows Vista para a resolução de nomes PNRP.</span><span class="sxs-lookup"><span data-stu-id="5e712-108">The pnrp.net domain is a reserved domain in Windows Vista for PNRP name resolution.</span></span>  
  
 <span data-ttu-id="5e712-109">A mensagem passando entre aplicativos PeerToPeer ainda é manipulada pelo arquiteturas subjacentes, como PeerChannel e [Dados Grandes e Streaming](http://go.microsoft.com/fwlink/?LinkID=179652) de WCF.</span><span class="sxs-lookup"><span data-stu-id="5e712-109">Message passing between PeerToPeer applications is still handled by underlying architectures such as PeerChannel and WCF [Large Data and Streaming](http://go.microsoft.com/fwlink/?LinkID=179652).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e712-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e712-110">See Also</span></span>  
 <xref:System.Net.PeerToPeer>

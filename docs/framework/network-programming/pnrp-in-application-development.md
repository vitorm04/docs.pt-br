---
title: PNRP no desenvolvimento do aplicativo
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
ms.openlocfilehash: b19138c43185f4d31bef4fe67af48f89dc03eba4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50180427"
---
# <a name="pnrp-in-application-development"></a><span data-ttu-id="5d3cb-102">PNRP no desenvolvimento do aplicativo</span><span class="sxs-lookup"><span data-stu-id="5d3cb-102">PNRP in Application Development</span></span>
<span data-ttu-id="5d3cb-103">No o Windows Vista, os aplicativos de rede podem acessar funções de publicação e de resolução de nomes por meio de uma API (interface de programação de aplicativo) PNRP simplificada.</span><span class="sxs-lookup"><span data-stu-id="5d3cb-103">In Windows Vista, networking applications can access name publication and resolution functions through a simplified PNRP application programming interface (API).</span></span>  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a><span data-ttu-id="5d3cb-104">Implementando o protocolo PNRP</span><span class="sxs-lookup"><span data-stu-id="5d3cb-104">Implementing the Peer Name Resolution Protocol</span></span>  
 <span data-ttu-id="5d3cb-105">Com a API PNRP simplificada, nuvens não são especificadas explicitamente para registrar o nome e endereços; o componente PNRP determina automaticamente as nuvens apropriadas ingressar e os endereços para publicar dentro delas.</span><span class="sxs-lookup"><span data-stu-id="5d3cb-105">With the simplified PNRP API, clouds are not explicitly specified to register the name and addresses; the PNRP component automatically determines the appropriate clouds to join and the addresses to publish within the clouds.</span></span>  
  
 <span data-ttu-id="5d3cb-106">Para proporcionar uma resolução de nomes PNRP simplificada no Windows Vista, os nomes PNRP agora estão integrados à função getaddrinfo() do Windows Sockets.</span><span class="sxs-lookup"><span data-stu-id="5d3cb-106">For highly simplified PNRP name resolution in Windows Vista, PNRP names are now integrated into the getaddrinfo() Windows Sockets function.</span></span> <span data-ttu-id="5d3cb-107">Para usar o PNRP para solucionar um nome para um endereço IPv6, os aplicativos podem usar a função getaddrinfo() para solucionar o FQDN (nome de domínio totalmente qualificado) nome.prnp.net, no qual nome é o nome do par que está sendo resolvido.</span><span class="sxs-lookup"><span data-stu-id="5d3cb-107">To use PNRP to resolve a name to an IPv6 address, applications can use the getaddrinfo() function to resolve the Fully Qualified Domain Name (FQDN) name.prnp.net, in which name is peer name being resolved.</span></span> <span data-ttu-id="5d3cb-108">O domínio pnrp.net é um domínio reservado no Windows Vista para a resolução de nomes PNRP.</span><span class="sxs-lookup"><span data-stu-id="5d3cb-108">The pnrp.net domain is a reserved domain in Windows Vista for PNRP name resolution.</span></span>  
  
 <span data-ttu-id="5d3cb-109">A mensagem passando entre aplicativos PeerToPeer ainda é manipulada pelo arquiteturas subjacentes, como PeerChannel e [Dados Grandes e Streaming](https://go.microsoft.com/fwlink/?LinkID=179652) de WCF.</span><span class="sxs-lookup"><span data-stu-id="5d3cb-109">Message passing between PeerToPeer applications is still handled by underlying architectures such as PeerChannel and WCF [Large Data and Streaming](https://go.microsoft.com/fwlink/?LinkID=179652).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d3cb-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d3cb-110">See Also</span></span>  
 <xref:System.Net.PeerToPeer>

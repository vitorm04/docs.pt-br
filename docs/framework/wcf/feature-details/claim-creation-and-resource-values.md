---
title: Valores de recursos e criação de declarações
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], creation and resource values
ms.assetid: 30431f76-cbe7-4bad-bad7-8e43e23a82d4
ms.openlocfilehash: fabd0a2606560d99174e5ad28940c3b59ee689d9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587047"
---
# <a name="claim-creation-and-resource-values"></a><span data-ttu-id="fa54c-102">Valores de recursos e criação de declarações</span><span class="sxs-lookup"><span data-stu-id="fa54c-102">Claim Creation and Resource Values</span></span>
<span data-ttu-id="fa54c-103">A <xref:System.IdentityModel.Claims.Claim> classe fornece vários métodos para criar instâncias de tipos de declarações internas.</span><span class="sxs-lookup"><span data-stu-id="fa54c-103">The <xref:System.IdentityModel.Claims.Claim> class provides several methods for creating instances of built-in claims types.</span></span> <span data-ttu-id="fa54c-104">Desses métodos, o seguinte não executa nenhuma verificação semântica ou de formato no recurso fornecido:</span><span class="sxs-lookup"><span data-stu-id="fa54c-104">Of these methods, the following perform no semantic or format checking on the supplied resource:</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateDnsClaim%2A>  
  
- <span data-ttu-id="fa54c-105"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A>(não verifica o comprimento ou o conteúdo da matriz de bytes)</span><span class="sxs-lookup"><span data-stu-id="fa54c-105"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateNameClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateSpnClaim%2A>  
  
- <span data-ttu-id="fa54c-106"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A>(não verifica o comprimento ou o conteúdo da matriz de bytes)</span><span class="sxs-lookup"><span data-stu-id="fa54c-106"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateUpnClaim%2A>  
  
 <span data-ttu-id="fa54c-107">Deve-se ter cuidado ao chamar os métodos acima para garantir que os valores de recurso passados sejam do formato correto ou contenham o tipo correto de informação (ou ambos).</span><span class="sxs-lookup"><span data-stu-id="fa54c-107">Care should be taken when calling the above methods to ensure that the resource values passed in are of the correct format or contain the correct kind of information (or both).</span></span>  
  
 <span data-ttu-id="fa54c-108">Os métodos a seguir usam tipos específicos:</span><span class="sxs-lookup"><span data-stu-id="fa54c-108">The following methods take specific types:</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateDenyOnlyWindowsSidClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateMailAddressClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateRsaClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateUriClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateWindowsSidClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateX500DistinguishedNameClaim%2A>  
  
## <a name="see-also"></a><span data-ttu-id="fa54c-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa54c-109">See also</span></span>

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.ClaimSet>
- [<span data-ttu-id="fa54c-110">Gerenciamento de declarações e autorizações com o modelo de identidade</span><span class="sxs-lookup"><span data-stu-id="fa54c-110">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)

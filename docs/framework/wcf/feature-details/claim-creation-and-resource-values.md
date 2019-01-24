---
title: Valores de recursos e criação de declarações
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], creation and resource values
ms.assetid: 30431f76-cbe7-4bad-bad7-8e43e23a82d4
ms.openlocfilehash: ca1bb8ccbc77e2b026a65a9cef56118e8b86dbb3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704063"
---
# <a name="claim-creation-and-resource-values"></a><span data-ttu-id="8da15-102">Valores de recursos e criação de declarações</span><span class="sxs-lookup"><span data-stu-id="8da15-102">Claim Creation and Resource Values</span></span>
<span data-ttu-id="8da15-103">O <xref:System.IdentityModel.Claims.Claim> classe fornece vários métodos para criar instâncias de internos de tipos de declarações.</span><span class="sxs-lookup"><span data-stu-id="8da15-103">The <xref:System.IdentityModel.Claims.Claim> class provides several methods for creating instances of built-in claims types.</span></span> <span data-ttu-id="8da15-104">Esses métodos, o seguinte executar semântico não ou formatar a verificação de recurso fornecido:</span><span class="sxs-lookup"><span data-stu-id="8da15-104">Of these methods, the following perform no semantic or format checking on the supplied resource:</span></span>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateDnsClaim%2A>  
  
-   <span data-ttu-id="8da15-105"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (não verifica o comprimento ou o conteúdo da matriz de bytes)</span><span class="sxs-lookup"><span data-stu-id="8da15-105"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateNameClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateSpnClaim%2A>  
  
-   <span data-ttu-id="8da15-106"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (não verifica o comprimento ou o conteúdo da matriz de bytes)</span><span class="sxs-lookup"><span data-stu-id="8da15-106"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateUpnClaim%2A>  
  
 <span data-ttu-id="8da15-107">Tome cuidado ao chamar os métodos acima para garantir que o recurso de valores passados estão no formato correto ou conter o tipo correto de informações (ou ambos).</span><span class="sxs-lookup"><span data-stu-id="8da15-107">Care should be taken when calling the above methods to ensure that the resource values passed in are of the correct format or contain the correct kind of information (or both).</span></span>  
  
 <span data-ttu-id="8da15-108">Os seguintes métodos recebem tipos específicos:</span><span class="sxs-lookup"><span data-stu-id="8da15-108">The following methods take specific types:</span></span>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateDenyOnlyWindowsSidClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateMailAddressClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateRsaClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateUriClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateWindowsSidClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateX500DistinguishedNameClaim%2A>  
  
## <a name="see-also"></a><span data-ttu-id="8da15-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8da15-109">See also</span></span>
- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.ClaimSet>
- [<span data-ttu-id="8da15-110">Gerenciando reivindicações e autorização com o modelo de identidade</span><span class="sxs-lookup"><span data-stu-id="8da15-110">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)

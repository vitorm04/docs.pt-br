---
title: <claimTypeRequirements> para <message>
ms.date: 03/30/2017
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
ms.openlocfilehash: e70b036fddbc706c8c16de9a0834140f600aa5ef
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173790"
---
# <a name="claimtyperequirements-for-message"></a><span data-ttu-id="fabd8-102">\<claimTypeRequirements> para \<message></span><span class="sxs-lookup"><span data-stu-id="fabd8-102">\<claimTypeRequirements> for \<message></span></span>

<span data-ttu-id="fabd8-103">Especifica uma coleção de tipos de declaração necessários.</span><span class="sxs-lookup"><span data-stu-id="fabd8-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="fabd8-104">A coleção é usada pelo serviço para especificar quaisquer declarações obrigatórias e opcionais que devem estar no token emitido que o cliente usa para acessar o serviço.</span><span class="sxs-lookup"><span data-stu-id="fabd8-104">The collection is used by the service to specify any required and optional claims which must be in the issued token the client uses to access the service.</span></span> <span data-ttu-id="fabd8-105">O serviço expõe os tipos de declaração necessários nos metadados se a publicação WSDL estiver habilitada, mas o WCF não exigir que o token emitido contenha os tipos de declaração especificados.</span><span class="sxs-lookup"><span data-stu-id="fabd8-105">The service exposes the required claim types in metadata if WSDL publishing is enabled but WCF does not require the issued token contain the specified claim types.</span></span> <span data-ttu-id="fabd8-106">Os serviços que desejam impor os tipos de declaração necessários estão presentes devem usar a política de autorização.</span><span class="sxs-lookup"><span data-stu-id="fabd8-106">Services wishing to enforce required claim types are present should do using authorization policy.</span></span>  
  
 <span data-ttu-id="fabd8-107">Em clientes federados, essa coleção contém a lista de declarações obrigatórias e opcionais que são enviadas para o serviço de token de segurança na solicitação do cliente para um token emitido.</span><span class="sxs-lookup"><span data-stu-id="fabd8-107">On federated clients, this collection contains the list of required and optional claims which is sent to the security token service in the client’s request for an issued token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fabd8-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="fabd8-108">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>

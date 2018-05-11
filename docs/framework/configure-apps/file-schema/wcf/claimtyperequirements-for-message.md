---
title: '&lt;claimTypeRequirements&gt; de &lt;mensagem&gt;'
ms.date: 03/30/2017
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
ms.openlocfilehash: f4460311f5478f441b819bc8a48540d6feea69b1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltclaimtyperequirementsgt-for-ltmessagegt"></a><span data-ttu-id="b471a-102">&lt;claimTypeRequirements&gt; de &lt;mensagem&gt;</span><span class="sxs-lookup"><span data-stu-id="b471a-102">&lt;claimTypeRequirements&gt; for &lt;message&gt;</span></span>
<span data-ttu-id="b471a-103">Especifica uma coleção de tipos de declaração necessária.</span><span class="sxs-lookup"><span data-stu-id="b471a-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="b471a-104">A coleção é usada pelo serviço para especificar quaisquer declarações obrigatórias e opcionais que deverá ser o token emitido que o cliente usa para acessar o serviço.</span><span class="sxs-lookup"><span data-stu-id="b471a-104">The collection is used by the service to specify any required and optional claims which must be in the issued token the client uses to access the service.</span></span> <span data-ttu-id="b471a-105">O serviço expõe os tipos de declaração necessária nos metadados se a publicação de WSDL está habilitada, mas WCF não exige que o token emitido contêm os tipos de declaração especificada.</span><span class="sxs-lookup"><span data-stu-id="b471a-105">The service exposes the required claim types in metadata if WSDL publishing is enabled but WCF does not require the issued token contain the specified claim types.</span></span> <span data-ttu-id="b471a-106">Serviços que deseja impor existem tipos de declaração necessária devem ser feito usando a política de autorização.</span><span class="sxs-lookup"><span data-stu-id="b471a-106">Services wishing to enforce required claim types are present should do using authorization policy.</span></span>  
  
 <span data-ttu-id="b471a-107">Em clientes federados, essa coleção contém a lista de declarações obrigatórias e opcionais que é enviada para o serviço de token de segurança na solicitação do cliente para um token emitido.</span><span class="sxs-lookup"><span data-stu-id="b471a-107">On federated clients, this collection contains the list of required and optional claims which is sent to the security token service in the client’s request for an issued token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b471a-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b471a-108">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>

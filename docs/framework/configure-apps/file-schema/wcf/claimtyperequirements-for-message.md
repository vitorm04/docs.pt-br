---
title: <claimTypeRequirements> para <message>
ms.date: 03/30/2017
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
ms.openlocfilehash: 9cf77f6c026df5f78cc8ae6e6783e91f1c86e282
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367440"
---
# <a name="claimtyperequirements-for-message"></a><span data-ttu-id="a89fd-102">\<claimTypeRequirements > para \<mensagem ></span><span class="sxs-lookup"><span data-stu-id="a89fd-102">\<claimTypeRequirements> for \<message></span></span>
<span data-ttu-id="a89fd-103">Especifica uma coleção de tipos de declaração exigidos.</span><span class="sxs-lookup"><span data-stu-id="a89fd-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="a89fd-104">A coleção é usada pelo serviço para especificar quaisquer declarações obrigatórias e opcionais que devem ser no token emitido, que o cliente usa para acessar o serviço.</span><span class="sxs-lookup"><span data-stu-id="a89fd-104">The collection is used by the service to specify any required and optional claims which must be in the issued token the client uses to access the service.</span></span> <span data-ttu-id="a89fd-105">O serviço expõe os tipos de declaração necessária nos metadados se a publicação de WSDL está habilitada, mas o WCF não exige o token emitido contêm os tipos de declaração especificado.</span><span class="sxs-lookup"><span data-stu-id="a89fd-105">The service exposes the required claim types in metadata if WSDL publishing is enabled but WCF does not require the issued token contain the specified claim types.</span></span> <span data-ttu-id="a89fd-106">Serviços que desejam impor declaração necessária tipos estão presentes devem fazer usando a política de autorização.</span><span class="sxs-lookup"><span data-stu-id="a89fd-106">Services wishing to enforce required claim types are present should do using authorization policy.</span></span>  
  
 <span data-ttu-id="a89fd-107">Em clientes federados, essa coleção contém a lista de declarações obrigatórias e opcionais que é enviada para o serviço de token de segurança na solicitação do cliente para um token emitido.</span><span class="sxs-lookup"><span data-stu-id="a89fd-107">On federated clients, this collection contains the list of required and optional claims which is sent to the security token service in the client’s request for an issued token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a89fd-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a89fd-108">See also</span></span>
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>

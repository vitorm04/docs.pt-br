---
title: <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 5b367489-54d7-408b-8f56-cb157dd68eaf
ms.openlocfilehash: 38d123a53b344ff1e4d781115093d0d1de5ae679
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926457"
---
# <a name="authorizationpolicies"></a><span data-ttu-id="bbcfc-101">\<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="bbcfc-101">\<authorizationPolicies></span></span>
<span data-ttu-id="bbcfc-102">Esta seção de configuração contém uma coleção de tipos de política de autorização, que podem ser `add` adicionados usando a palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="bbcfc-102">This configuration section contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="bbcfc-103">Cada política de autorização contém um único `policyType` atributo necessário que é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="bbcfc-103">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="bbcfc-104">O atributo especifica uma política de autorização, que permite a transformação de um conjunto de declarações de entrada em outro conjunto de declarações.</span><span class="sxs-lookup"><span data-stu-id="bbcfc-104">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="bbcfc-105">Controle de acesso pode ser concedido ou negado com base nisso.</span><span class="sxs-lookup"><span data-stu-id="bbcfc-105">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="bbcfc-106">Para obter mais informações sobre como funciona uma diretiva de autorização <xref:System.IdentityModel.Policy.IAuthorizationPolicy> , consulte e [política de autorização](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="bbcfc-106">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbcfc-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bbcfc-107">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="bbcfc-108">Autorizando o acesso a operações de serviço</span><span class="sxs-lookup"><span data-stu-id="bbcfc-108">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="bbcfc-109">Como: Criar um Gerenciador de autorização personalizado para um serviço</span><span class="sxs-lookup"><span data-stu-id="bbcfc-109">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="bbcfc-110">\<add></span><span class="sxs-lookup"><span data-stu-id="bbcfc-110">\<add></span></span>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="bbcfc-111">Política de autorização</span><span class="sxs-lookup"><span data-stu-id="bbcfc-111">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)

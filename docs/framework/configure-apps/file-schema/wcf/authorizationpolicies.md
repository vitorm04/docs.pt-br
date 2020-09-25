---
title: <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 5b367489-54d7-408b-8f56-cb157dd68eaf
ms.openlocfilehash: 7d8eb27b8a569b1ca6b65a7c8c70c6fb82f701a4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201571"
---
# \<authorizationPolicies>

<span data-ttu-id="f44e1-101">Esta seção de configuração contém uma coleção de tipos de política de autorização, que podem ser adicionados usando a `add` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="f44e1-101">This configuration section contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="f44e1-102">Cada política de autorização contém um único `policyType` atributo necessário que é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f44e1-102">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="f44e1-103">O atributo especifica uma política de autorização, que permite a transformação de um conjunto de declarações de entrada em outro conjunto de declarações.</span><span class="sxs-lookup"><span data-stu-id="f44e1-103">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="f44e1-104">Controle de acesso pode ser concedido ou negado com base nisso.</span><span class="sxs-lookup"><span data-stu-id="f44e1-104">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="f44e1-105">Para obter mais informações sobre como funciona uma diretiva de autorização, consulte <xref:System.IdentityModel.Policy.IAuthorizationPolicy> e [política de autorização](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="f44e1-105">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f44e1-106">Veja também</span><span class="sxs-lookup"><span data-stu-id="f44e1-106">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="f44e1-107">Autorizando o acesso às operações de serviço</span><span class="sxs-lookup"><span data-stu-id="f44e1-107">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="f44e1-108">Como: criar gerenciador de autorização personalizado para um serviço</span><span class="sxs-lookup"><span data-stu-id="f44e1-108">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<add>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="f44e1-109">Política de autorização</span><span class="sxs-lookup"><span data-stu-id="f44e1-109">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)

---
title: "Como examinar o contexto de segurança"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceSecurityContext class
- WCF, security
- Claimset class
ms.assetid: 389b5a57-4175-4bc0-ada0-fc750d51149f
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 4d6852a3162b3a8666c711d455e72517a91c4477
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-examine-the-security-context"></a><span data-ttu-id="ba672-102">Como examinar o contexto de segurança</span><span class="sxs-lookup"><span data-stu-id="ba672-102">How to: Examine the Security Context</span></span>
<span data-ttu-id="ba672-103">Ao programar [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] services, o contexto de segurança permite que você determine os detalhes sobre as credenciais de cliente e as declarações usadas para autenticar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="ba672-103">When programming [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] services, the service security context enables you to determine details about the client credentials and claims used to authenticate with the service.</span></span> <span data-ttu-id="ba672-104">Isso é feito por meio das propriedades da <xref:System.ServiceModel.ServiceSecurityContext> classe.</span><span class="sxs-lookup"><span data-stu-id="ba672-104">This is done by using the properties of the <xref:System.ServiceModel.ServiceSecurityContext> class.</span></span>  
  
 <span data-ttu-id="ba672-105">Por exemplo, você pode recuperar a identidade do cliente atual usando o <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> ou <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="ba672-105">For example, you can retrieve the identity of the current client by using the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> or the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property.</span></span> <span data-ttu-id="ba672-106">Para determinar se o cliente é anônimo, use o <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="ba672-106">To determine whether the client is anonymous, use the <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> property.</span></span>  
  
 <span data-ttu-id="ba672-107">Você também pode determinar quais declarações estão sendo feitas em nome do cliente pela iteração através da coleção de declarações de <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="ba672-107">You can also determine what claims are being made on behalf of the client by iterating through the collection of claims in the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
### <a name="to-get-the-current-security-context"></a><span data-ttu-id="ba672-108">Para obter o contexto de segurança atual</span><span class="sxs-lookup"><span data-stu-id="ba672-108">To get the current security context</span></span>  
  
-   <span data-ttu-id="ba672-109">Acessar a propriedade estática <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> para obter o contexto de segurança atual.</span><span class="sxs-lookup"><span data-stu-id="ba672-109">Access the static property <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> to get the current security context.</span></span> <span data-ttu-id="ba672-110">Examine as propriedades do contexto atual da referência.</span><span class="sxs-lookup"><span data-stu-id="ba672-110">Examine any of the properties of the current context from the reference.</span></span>  
  
### <a name="to-determine-the-identity-of-the-caller"></a><span data-ttu-id="ba672-111">Para determinar a identidade do chamador</span><span class="sxs-lookup"><span data-stu-id="ba672-111">To determine the identity of the caller</span></span>  
  
1.  <span data-ttu-id="ba672-112">Imprimir o valor de <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> e <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="ba672-112">Print the value of the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> properties.</span></span>  
  
### <a name="to-parse-the-claims-of-a-caller"></a><span data-ttu-id="ba672-113">Para analisar as declarações de um chamador</span><span class="sxs-lookup"><span data-stu-id="ba672-113">To parse the claims of a caller</span></span>  
  
1.  <span data-ttu-id="ba672-114">Retornar atuais <xref:System.IdentityModel.Policy.AuthorizationContext> classe.</span><span class="sxs-lookup"><span data-stu-id="ba672-114">Return the current <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span> <span data-ttu-id="ba672-115">Use o <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> propriedade para retornar o contexto de segurança atual, em seguida, retornar o `AuthorizationContext` usando o <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="ba672-115">Use the <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> property to return the current service security context, then return the `AuthorizationContext` using the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
2.  <span data-ttu-id="ba672-116">Analisar a coleção de <xref:System.IdentityModel.Claims.ClaimSet> objetos retornados pelo <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> propriedade o <xref:System.IdentityModel.Policy.AuthorizationContext> classe.</span><span class="sxs-lookup"><span data-stu-id="ba672-116">Parse the collection of <xref:System.IdentityModel.Claims.ClaimSet> objects returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba672-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ba672-117">Example</span></span>  
 <span data-ttu-id="ba672-118">O exemplo a seguir imprime os valores da <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> e <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> propriedades de contexto de segurança atual e o <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> propriedade, o valor do recurso de declaração e o <xref:System.IdentityModel.Claims.Claim.Right%2A> propriedade de cada declaração na segurança atual contexto.</span><span class="sxs-lookup"><span data-stu-id="ba672-118">The following example prints the values of the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> properties of the current security context and the <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> property, the resource value of the claim, and the <xref:System.IdentityModel.Claims.Claim.Right%2A> property of every claim in the current security context.</span></span>  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ba672-119">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="ba672-119">Compiling the Code</span></span>  
 <span data-ttu-id="ba672-120">O código usa os namespaces a seguir:</span><span class="sxs-lookup"><span data-stu-id="ba672-120">The code uses the following namespaces:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.IdentityModel.Policy>  
  
-   <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a><span data-ttu-id="ba672-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba672-121">See Also</span></span>  
 [<span data-ttu-id="ba672-122">Protegendo serviços</span><span class="sxs-lookup"><span data-stu-id="ba672-122">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="ba672-123">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="ba672-123">Service Identity and Authentication</span></span>](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)

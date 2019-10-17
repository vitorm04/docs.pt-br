---
title: Como examinar o contexto de segurança
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceSecurityContext class
- WCF, security
- Claimset class
ms.assetid: 389b5a57-4175-4bc0-ada0-fc750d51149f
ms.openlocfilehash: 328d47a583a4f047fd54589a82d339de2cb1a16f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320984"
---
# <a name="how-to-examine-the-security-context"></a><span data-ttu-id="b6348-102">Como examinar o contexto de segurança</span><span class="sxs-lookup"><span data-stu-id="b6348-102">How to: Examine the Security Context</span></span>
<span data-ttu-id="b6348-103">Ao programar serviços Windows Communication Foundation (WCF), o contexto de segurança do serviço permite que você determine detalhes sobre as credenciais do cliente e as declarações usadas para autenticar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="b6348-103">When programming Windows Communication Foundation (WCF) services, the service security context enables you to determine details about the client credentials and claims used to authenticate with the service.</span></span> <span data-ttu-id="b6348-104">Isso é feito usando as propriedades da classe <xref:System.ServiceModel.ServiceSecurityContext>.</span><span class="sxs-lookup"><span data-stu-id="b6348-104">This is done by using the properties of the <xref:System.ServiceModel.ServiceSecurityContext> class.</span></span>  
  
 <span data-ttu-id="b6348-105">Por exemplo, você pode recuperar a identidade do cliente atual usando o <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> ou a propriedade <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="b6348-105">For example, you can retrieve the identity of the current client by using the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> or the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property.</span></span> <span data-ttu-id="b6348-106">Para determinar se o cliente é anônimo, use a propriedade <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A>.</span><span class="sxs-lookup"><span data-stu-id="b6348-106">To determine whether the client is anonymous, use the <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> property.</span></span>  
  
 <span data-ttu-id="b6348-107">Você também pode determinar quais declarações estão sendo feitas em nome do cliente Iterando pela coleção de declarações na propriedade <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A>.</span><span class="sxs-lookup"><span data-stu-id="b6348-107">You can also determine what claims are being made on behalf of the client by iterating through the collection of claims in the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
### <a name="to-get-the-current-security-context"></a><span data-ttu-id="b6348-108">Para obter o contexto de segurança atual</span><span class="sxs-lookup"><span data-stu-id="b6348-108">To get the current security context</span></span>  
  
- <span data-ttu-id="b6348-109">Acesse a propriedade estática <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> para obter o contexto de segurança atual.</span><span class="sxs-lookup"><span data-stu-id="b6348-109">Access the static property <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> to get the current security context.</span></span> <span data-ttu-id="b6348-110">Examine qualquer uma das propriedades do contexto atual da referência.</span><span class="sxs-lookup"><span data-stu-id="b6348-110">Examine any of the properties of the current context from the reference.</span></span>  
  
### <a name="to-determine-the-identity-of-the-caller"></a><span data-ttu-id="b6348-111">Para determinar a identidade do chamador</span><span class="sxs-lookup"><span data-stu-id="b6348-111">To determine the identity of the caller</span></span>  
  
1. <span data-ttu-id="b6348-112">Imprima o valor das propriedades <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> e <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="b6348-112">Print the value of the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> properties.</span></span>  
  
### <a name="to-parse-the-claims-of-a-caller"></a><span data-ttu-id="b6348-113">Para analisar as declarações de um chamador</span><span class="sxs-lookup"><span data-stu-id="b6348-113">To parse the claims of a caller</span></span>  
  
1. <span data-ttu-id="b6348-114">Retornar a classe <xref:System.IdentityModel.Policy.AuthorizationContext> atual.</span><span class="sxs-lookup"><span data-stu-id="b6348-114">Return the current <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span> <span data-ttu-id="b6348-115">Use a propriedade <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> para retornar o contexto de segurança do serviço atual e, em seguida, retorne o `AuthorizationContext` usando a propriedade <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A>.</span><span class="sxs-lookup"><span data-stu-id="b6348-115">Use the <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> property to return the current service security context, then return the `AuthorizationContext` using the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
2. <span data-ttu-id="b6348-116">Analise a coleção de objetos <xref:System.IdentityModel.Claims.ClaimSet> retornados pela propriedade <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> da classe <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="b6348-116">Parse the collection of <xref:System.IdentityModel.Claims.ClaimSet> objects returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6348-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b6348-117">Example</span></span>  
 <span data-ttu-id="b6348-118">O exemplo a seguir imprime os valores das propriedades <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> e <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> do contexto de segurança atual e a propriedade <xref:System.IdentityModel.Claims.Claim.ClaimType%2A>, o valor do recurso da declaração e a propriedade <xref:System.IdentityModel.Claims.Claim.Right%2A> de cada declaração no contexto de segurança atual.</span><span class="sxs-lookup"><span data-stu-id="b6348-118">The following example prints the values of the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> properties of the current security context and the <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> property, the resource value of the claim, and the <xref:System.IdentityModel.Claims.Claim.Right%2A> property of every claim in the current security context.</span></span>  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b6348-119">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="b6348-119">Compiling the Code</span></span>  
 <span data-ttu-id="b6348-120">O código usa os seguintes namespaces:</span><span class="sxs-lookup"><span data-stu-id="b6348-120">The code uses the following namespaces:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.IdentityModel.Policy>  
  
- <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a><span data-ttu-id="b6348-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b6348-121">See also</span></span>

- [<span data-ttu-id="b6348-122">Protegendo serviços</span><span class="sxs-lookup"><span data-stu-id="b6348-122">Securing Services</span></span>](securing-services.md)
- [<span data-ttu-id="b6348-123">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="b6348-123">Service Identity and Authentication</span></span>](./feature-details/service-identity-and-authentication.md)

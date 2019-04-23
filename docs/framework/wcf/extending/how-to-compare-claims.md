---
title: 'Como: comparar declarações'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], comparing
- claims [WCF]
ms.assetid: 0c4ec84d-53df-408f-8953-9bc437f56c28
ms.openlocfilehash: 932ad347730b35a936e040e116e5aa6af36cd3dc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343305"
---
# <a name="how-to-compare-claims"></a><span data-ttu-id="e15a5-102">Como: comparar declarações</span><span class="sxs-lookup"><span data-stu-id="e15a5-102">How to: Compare Claims</span></span>
<span data-ttu-id="e15a5-103">A infraestrutura do modelo de identidade no Windows Communication Foundation (WCF) é usada para executar a verificação de autorização.</span><span class="sxs-lookup"><span data-stu-id="e15a5-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) is used to perform authorization checking.</span></span> <span data-ttu-id="e15a5-104">Dessa forma, uma tarefa comum é comparar declarações no contexto de autorização para as declarações necessárias para executar a ação solicitada ou acessar o recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="e15a5-104">As such, a common task is to compare claims in the authorization context to the claims required to perform the requested action or access the requested resource.</span></span> <span data-ttu-id="e15a5-105">Este tópico descreve como comparar declarações, incluindo tipos de declaração internas e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="e15a5-105">This topic describes how to compare claims, including built-in and custom claim types.</span></span> <span data-ttu-id="e15a5-106">Para obter mais informações sobre a infraestrutura do modelo de identidade, consulte [Gerenciando reivindicações e autorização com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="e15a5-106">For more information about the Identity Model infrastructure, see [Managing Claims and Authorization with the Identity Model](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span></span>  
  
 <span data-ttu-id="e15a5-107">Comparação de declaração envolve comparando as três partes de uma declaração (tipo, certo e recursos) contra as mesmas partes em outra declaração para ver se elas são iguais.</span><span class="sxs-lookup"><span data-stu-id="e15a5-107">Claim comparison involves comparing the three parts of a claim (type, right, and resource) against the same parts in another claim to see if they are equal.</span></span> <span data-ttu-id="e15a5-108">Consulte o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e15a5-108">See the following example.</span></span>  
  
 [!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
 [!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]  
  
 <span data-ttu-id="e15a5-109">Ambas as declarações têm um tipo de declaração de <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, um direito de <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>e um recurso da cadeia de caracteres "alguém".</span><span class="sxs-lookup"><span data-stu-id="e15a5-109">Both claims have a claim type of <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, a right of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, and a resource of the string "someone".</span></span> <span data-ttu-id="e15a5-110">Como todas as três partes da declaração forem iguais, as declarações em si são iguais.</span><span class="sxs-lookup"><span data-stu-id="e15a5-110">As all three parts of the claim are equal, the claims themselves are equal.</span></span>  
  
 <span data-ttu-id="e15a5-111">Os tipos de declaração internos são comparados usando o <xref:System.IdentityModel.Claims.Claim.Equals%2A> método.</span><span class="sxs-lookup"><span data-stu-id="e15a5-111">The built-in claim types are compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="e15a5-112">Código de comparação de declaração específico seja usado quando necessário.</span><span class="sxs-lookup"><span data-stu-id="e15a5-112">Claim-specific comparison code is used where necessary.</span></span> <span data-ttu-id="e15a5-113">Por exemplo, considerando as seguintes declarações de nome principal (UPN) do dois usuário:</span><span class="sxs-lookup"><span data-stu-id="e15a5-113">For example, given the following two user principal name (UPN) claims:</span></span>  
  
 [!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
 [!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]  
  
 <span data-ttu-id="e15a5-114">o código de comparação no <xref:System.IdentityModel.Claims.Claim.Equals%2A> retorn `true`, assumindo `example\someone` identifica o mesmo usuário de domínio que "someone@example.com".</span><span class="sxs-lookup"><span data-stu-id="e15a5-114">the comparison code in the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method returns `true`, assuming `example\someone` identifies the same domain user as "someone@example.com".</span></span>  
  
 <span data-ttu-id="e15a5-115">Tipos de declaração personalizada também podem ser comparados usando o <xref:System.IdentityModel.Claims.Claim.Equals%2A> método.</span><span class="sxs-lookup"><span data-stu-id="e15a5-115">Custom claim types can also be compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="e15a5-116">No entanto, em casos em que o tipo retornado pelo <xref:System.IdentityModel.Claims.Claim.Resource%2A> propriedade da declaração é algo diferente de um tipo primitivo, o <xref:System.IdentityModel.Claims.Claim.Equals%2A> retorna `true` somente se os valores retornados pelo `Resource` propriedades são iguais de acordo com o <xref:System.IdentityModel.Claims.Claim.Equals%2A> método.</span><span class="sxs-lookup"><span data-stu-id="e15a5-116">However, in cases where the type returned by the <xref:System.IdentityModel.Claims.Claim.Resource%2A> property of the claim is something other than a primitive type, the <xref:System.IdentityModel.Claims.Claim.Equals%2A> returns `true` only if the values returned by the `Resource` properties are equal according to the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="e15a5-117">Em casos em que isso não é apropriado, o tipo personalizado retornado pela `Resource` propriedade deve substituir o <xref:System.IdentityModel.Claims.Claim.Equals%2A> e <xref:System.Object.GetHashCode%2A> métodos para executar qualquer processamento personalizado é necessário.</span><span class="sxs-lookup"><span data-stu-id="e15a5-117">In cases where this is not appropriate, the custom type returned by the `Resource` property should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods to perform whatever custom processing is necessary.</span></span>  
  
### <a name="comparing-built-in-claims"></a><span data-ttu-id="e15a5-118">Comparar declarações internas</span><span class="sxs-lookup"><span data-stu-id="e15a5-118">Comparing built-in claims</span></span>  
  
1. <span data-ttu-id="e15a5-119">Considerando duas instâncias do <xref:System.IdentityModel.Claims.Claim> classe, use o <xref:System.IdentityModel.Claims.Claim.Equals%2A> para fazer a comparação, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e15a5-119">Given two instances of the <xref:System.IdentityModel.Claims.Claim> class, use the <xref:System.IdentityModel.Claims.Claim.Equals%2A> to make the comparison, as shown in the following code.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]  
  
### <a name="comparing-custom-claims-with-primitive-resource-types"></a><span data-ttu-id="e15a5-120">Comparando as declarações personalizadas com tipos primitivos de recurso</span><span class="sxs-lookup"><span data-stu-id="e15a5-120">Comparing custom claims with primitive resource types</span></span>  
  
1. <span data-ttu-id="e15a5-121">Para declarações personalizadas com tipos de recurso primitivo, comparação pode ser executada como para declarações internas, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e15a5-121">For custom claims with primitive resource types, comparison can be performed as for built-in claims, as shown in the following code.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]  
  
2. <span data-ttu-id="e15a5-122">Para as declarações personalizadas com a estrutura ou classe com base em tipos de recursos, o tipo de recurso devem substituir o <xref:System.IdentityModel.Claims.Claim.Equals%2A> método.</span><span class="sxs-lookup"><span data-stu-id="e15a5-122">For custom claims with structure or class based resource types, the resource type should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span>  
  
3. <span data-ttu-id="e15a5-123">Primeiro, verifique se o `obj` parâmetro é `null`e nesse caso, retornar `false`.</span><span class="sxs-lookup"><span data-stu-id="e15a5-123">First check whether the `obj` parameter is `null`, and if so, return `false`.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]  
  
4. <span data-ttu-id="e15a5-124">Em seguida chame <xref:System.Object.ReferenceEquals%2A> e passe `this` e `obj` como parâmetros.</span><span class="sxs-lookup"><span data-stu-id="e15a5-124">Next call <xref:System.Object.ReferenceEquals%2A> and pass `this` and `obj` as parameters.</span></span> <span data-ttu-id="e15a5-125">Se ele retornar `true`, em seguida, retorne `true`.</span><span class="sxs-lookup"><span data-stu-id="e15a5-125">If it returns `true`, then return `true`.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]  
  
5. <span data-ttu-id="e15a5-126">Em seguida, tentar atribuir `obj` a uma variável local do tipo de classe.</span><span class="sxs-lookup"><span data-stu-id="e15a5-126">Next attempt to assign `obj` to a local variable of the class type.</span></span> <span data-ttu-id="e15a5-127">Se isso falhar, a referência é `null`.</span><span class="sxs-lookup"><span data-stu-id="e15a5-127">If this fails, the reference is `null`.</span></span> <span data-ttu-id="e15a5-128">Nesses casos, retornar `false`.</span><span class="sxs-lookup"><span data-stu-id="e15a5-128">In such cases, return `false`.</span></span>  
  
6. <span data-ttu-id="e15a5-129">Execute a comparação personalizada necessária comparar corretamente a declaração atual para a declaração fornecida.</span><span class="sxs-lookup"><span data-stu-id="e15a5-129">Perform the custom comparison necessary to correctly compare the current claim to the provided claim.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e15a5-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e15a5-130">Example</span></span>  
 <span data-ttu-id="e15a5-131">O exemplo a seguir mostra uma comparação de declarações personalizadas em que o recurso da declaração é um tipo não primitivo.</span><span class="sxs-lookup"><span data-stu-id="e15a5-131">The following example shows a comparison of custom claims where the claim resource is a non-primitive type.</span></span>  
  
 [!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
 [!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="e15a5-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e15a5-132">See also</span></span>

- [<span data-ttu-id="e15a5-133">Gerenciando reivindicações e autorização com o modelo de identidade</span><span class="sxs-lookup"><span data-stu-id="e15a5-133">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [<span data-ttu-id="e15a5-134">Como: Criar uma declaração personalizada</span><span class="sxs-lookup"><span data-stu-id="e15a5-134">How to: Create a Custom Claim</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)

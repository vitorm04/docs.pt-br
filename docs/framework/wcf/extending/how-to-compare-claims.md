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
ms.openlocfilehash: 29254bd661e72b926b21695ccb646480c53b5475
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797100"
---
# <a name="how-to-compare-claims"></a><span data-ttu-id="744dc-102">Como: comparar declarações</span><span class="sxs-lookup"><span data-stu-id="744dc-102">How to: Compare Claims</span></span>

<span data-ttu-id="744dc-103">A infraestrutura do modelo de identidade no Windows Communication Foundation (WCF) é usada para executar a verificação de autorização.</span><span class="sxs-lookup"><span data-stu-id="744dc-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) is used to perform authorization checking.</span></span> <span data-ttu-id="744dc-104">Dessa forma, uma tarefa comum é comparar as declarações no contexto de autorização com as declarações necessárias para executar a ação solicitada ou acessar o recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="744dc-104">As such, a common task is to compare claims in the authorization context to the claims required to perform the requested action or access the requested resource.</span></span> <span data-ttu-id="744dc-105">Este tópico descreve como comparar declarações, incluindo tipos de declaração internos e personalizados.</span><span class="sxs-lookup"><span data-stu-id="744dc-105">This topic describes how to compare claims, including built-in and custom claim types.</span></span> <span data-ttu-id="744dc-106">Para obter mais informações sobre a infraestrutura do modelo de identidade, consulte [Gerenciando declarações e autorização com o modelo de identidade](../feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="744dc-106">For more information about the Identity Model infrastructure, see [Managing Claims and Authorization with the Identity Model](../feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span></span>

<span data-ttu-id="744dc-107">A comparação de declarações envolve comparar as três partes de uma declaração (tipo, direito e recurso) com as mesmas partes em outra declaração para ver se elas são iguais.</span><span class="sxs-lookup"><span data-stu-id="744dc-107">Claim comparison involves comparing the three parts of a claim (type, right, and resource) against the same parts in another claim to see if they are equal.</span></span> <span data-ttu-id="744dc-108">Consulte o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="744dc-108">See the following example.</span></span>

[!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
[!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]

<span data-ttu-id="744dc-109">Ambas as declarações têm um tipo de <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>declaração de, um <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>direito de e um recurso da cadeia de caracteres "alguém".</span><span class="sxs-lookup"><span data-stu-id="744dc-109">Both claims have a claim type of <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, a right of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, and a resource of the string "someone".</span></span> <span data-ttu-id="744dc-110">Como todas as três partes da declaração são iguais, as próprias declarações são iguais.</span><span class="sxs-lookup"><span data-stu-id="744dc-110">As all three parts of the claim are equal, the claims themselves are equal.</span></span>

<span data-ttu-id="744dc-111">Os tipos de declaração internos são comparados usando <xref:System.IdentityModel.Claims.Claim.Equals%2A> o método.</span><span class="sxs-lookup"><span data-stu-id="744dc-111">The built-in claim types are compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="744dc-112">O código de comparação específico da declaração é usado quando necessário.</span><span class="sxs-lookup"><span data-stu-id="744dc-112">Claim-specific comparison code is used where necessary.</span></span> <span data-ttu-id="744dc-113">Por exemplo, considerando as duas declarações de UPN (nome principal de usuário) a seguir:</span><span class="sxs-lookup"><span data-stu-id="744dc-113">For example, given the following two user principal name (UPN) claims:</span></span>

[!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
[!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]

<span data-ttu-id="744dc-114">o código de comparação no <xref:System.IdentityModel.Claims.Claim.Equals%2A> método retorna `true`, supondo `example\someone` que identifique o mesmo usuário desomeone@example.comdomínio que "".</span><span class="sxs-lookup"><span data-stu-id="744dc-114">the comparison code in the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method returns `true`, assuming `example\someone` identifies the same domain user as "someone@example.com".</span></span>

<span data-ttu-id="744dc-115">Os tipos de declaração personalizados também podem ser comparados usando o <xref:System.IdentityModel.Claims.Claim.Equals%2A> método.</span><span class="sxs-lookup"><span data-stu-id="744dc-115">Custom claim types can also be compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="744dc-116">No entanto, nos casos em que o tipo <xref:System.IdentityModel.Claims.Claim.Resource%2A> retornado pela propriedade da declaração for algo diferente de um tipo primitivo, <xref:System.IdentityModel.Claims.Claim.Equals%2A> o `true` retornará somente se os valores retornados pelas `Resource` propriedades forem iguais, de acordo com o <xref:System.IdentityModel.Claims.Claim.Equals%2A> método.</span><span class="sxs-lookup"><span data-stu-id="744dc-116">However, in cases where the type returned by the <xref:System.IdentityModel.Claims.Claim.Resource%2A> property of the claim is something other than a primitive type, the <xref:System.IdentityModel.Claims.Claim.Equals%2A> returns `true` only if the values returned by the `Resource` properties are equal according to the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="744dc-117">Nos casos em que isso não for apropriado, o tipo personalizado retornado pela `Resource` Propriedade deverá substituir os <xref:System.IdentityModel.Claims.Claim.Equals%2A> métodos <xref:System.Object.GetHashCode%2A> e para executar qualquer processamento personalizado necessário.</span><span class="sxs-lookup"><span data-stu-id="744dc-117">In cases where this is not appropriate, the custom type returned by the `Resource` property should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods to perform whatever custom processing is necessary.</span></span>

## <a name="comparing-built-in-claims"></a><span data-ttu-id="744dc-118">Comparando declarações internas</span><span class="sxs-lookup"><span data-stu-id="744dc-118">Comparing built-in claims</span></span>

1. <span data-ttu-id="744dc-119">Dadas duas instâncias da <xref:System.IdentityModel.Claims.Claim> classe, use o <xref:System.IdentityModel.Claims.Claim.Equals%2A> para fazer a comparação, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="744dc-119">Given two instances of the <xref:System.IdentityModel.Claims.Claim> class, use the <xref:System.IdentityModel.Claims.Claim.Equals%2A> to make the comparison, as shown in the following code.</span></span>

     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]

### <a name="comparing-custom-claims-with-primitive-resource-types"></a><span data-ttu-id="744dc-120">Comparando declarações personalizadas com tipos de recursos primitivos</span><span class="sxs-lookup"><span data-stu-id="744dc-120">Comparing custom claims with primitive resource types</span></span>

1. <span data-ttu-id="744dc-121">Para declarações personalizadas com tipos de recursos primitivos, a comparação pode ser executada como para declarações internas, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="744dc-121">For custom claims with primitive resource types, comparison can be performed as for built-in claims, as shown in the following code.</span></span>

     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]

2. <span data-ttu-id="744dc-122">Para declarações personalizadas com tipos de recursos baseados em classe ou estrutura, o tipo de recurso <xref:System.IdentityModel.Claims.Claim.Equals%2A> deve substituir o método.</span><span class="sxs-lookup"><span data-stu-id="744dc-122">For custom claims with structure or class based resource types, the resource type should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span>

3. <span data-ttu-id="744dc-123">Primeiro, verifique se `obj` o parâmetro `null`é e, em caso afirmativo, retornar `false`.</span><span class="sxs-lookup"><span data-stu-id="744dc-123">First check whether the `obj` parameter is `null`, and if so, return `false`.</span></span>

     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]

4. <span data-ttu-id="744dc-124">Parâmetros de <xref:System.Object.ReferenceEquals%2A> próxima chamada `this` e `obj` Pass e as.</span><span class="sxs-lookup"><span data-stu-id="744dc-124">Next call <xref:System.Object.ReferenceEquals%2A> and pass `this` and `obj` as parameters.</span></span> <span data-ttu-id="744dc-125">Se retornar `true`, retorne. `true`</span><span class="sxs-lookup"><span data-stu-id="744dc-125">If it returns `true`, then return `true`.</span></span>

     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]

5. <span data-ttu-id="744dc-126">A próxima tentativa de `obj` atribuir a uma variável local do tipo de classe.</span><span class="sxs-lookup"><span data-stu-id="744dc-126">Next attempt to assign `obj` to a local variable of the class type.</span></span> <span data-ttu-id="744dc-127">Se isso falhar, a referência será `null`.</span><span class="sxs-lookup"><span data-stu-id="744dc-127">If this fails, the reference is `null`.</span></span> <span data-ttu-id="744dc-128">Nesses casos, retorne `false`.</span><span class="sxs-lookup"><span data-stu-id="744dc-128">In such cases, return `false`.</span></span>

6. <span data-ttu-id="744dc-129">Execute a comparação personalizada necessária para comparar corretamente a declaração atual com a declaração fornecida.</span><span class="sxs-lookup"><span data-stu-id="744dc-129">Perform the custom comparison necessary to correctly compare the current claim to the provided claim.</span></span>

## <a name="example"></a><span data-ttu-id="744dc-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="744dc-130">Example</span></span>

<span data-ttu-id="744dc-131">O exemplo a seguir mostra uma comparação de declarações personalizadas em que o recurso de declaração é um tipo não primitivo.</span><span class="sxs-lookup"><span data-stu-id="744dc-131">The following example shows a comparison of custom claims where the claim resource is a non-primitive type.</span></span>

[!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
[!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]

## <a name="see-also"></a><span data-ttu-id="744dc-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="744dc-132">See also</span></span>

- [<span data-ttu-id="744dc-133">Gerenciando reivindicações e autorização com o modelo de identidade</span><span class="sxs-lookup"><span data-stu-id="744dc-133">Managing Claims and Authorization with the Identity Model</span></span>](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [<span data-ttu-id="744dc-134">Como: Criar uma declaração personalizada</span><span class="sxs-lookup"><span data-stu-id="744dc-134">How to: Create a Custom Claim</span></span>](how-to-create-a-custom-claim.md)

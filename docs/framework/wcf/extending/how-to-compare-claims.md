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
# <a name="how-to-compare-claims"></a>Como: comparar declarações

A infraestrutura do modelo de identidade no Windows Communication Foundation (WCF) é usada para executar a verificação de autorização. Dessa forma, uma tarefa comum é comparar as declarações no contexto de autorização com as declarações necessárias para executar a ação solicitada ou acessar o recurso solicitado. Este tópico descreve como comparar declarações, incluindo tipos de declaração internos e personalizados. Para obter mais informações sobre a infraestrutura do modelo de identidade, consulte [Gerenciando declarações e autorização com o modelo de identidade](../feature-details/managing-claims-and-authorization-with-the-identity-model.md).

A comparação de declarações envolve comparar as três partes de uma declaração (tipo, direito e recurso) com as mesmas partes em outra declaração para ver se elas são iguais. Consulte o exemplo a seguir.

[!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
[!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]

Ambas as declarações têm um tipo de <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>declaração de, um <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>direito de e um recurso da cadeia de caracteres "alguém". Como todas as três partes da declaração são iguais, as próprias declarações são iguais.

Os tipos de declaração internos são comparados usando <xref:System.IdentityModel.Claims.Claim.Equals%2A> o método. O código de comparação específico da declaração é usado quando necessário. Por exemplo, considerando as duas declarações de UPN (nome principal de usuário) a seguir:

[!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
[!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]

o código de comparação no <xref:System.IdentityModel.Claims.Claim.Equals%2A> método retorna `true`, supondo `example\someone` que identifique o mesmo usuário desomeone@example.comdomínio que "".

Os tipos de declaração personalizados também podem ser comparados usando o <xref:System.IdentityModel.Claims.Claim.Equals%2A> método. No entanto, nos casos em que o tipo <xref:System.IdentityModel.Claims.Claim.Resource%2A> retornado pela propriedade da declaração for algo diferente de um tipo primitivo, <xref:System.IdentityModel.Claims.Claim.Equals%2A> o `true` retornará somente se os valores retornados pelas `Resource` propriedades forem iguais, de acordo com o <xref:System.IdentityModel.Claims.Claim.Equals%2A> método. Nos casos em que isso não for apropriado, o tipo personalizado retornado pela `Resource` Propriedade deverá substituir os <xref:System.IdentityModel.Claims.Claim.Equals%2A> métodos <xref:System.Object.GetHashCode%2A> e para executar qualquer processamento personalizado necessário.

## <a name="comparing-built-in-claims"></a>Comparando declarações internas

1. Dadas duas instâncias da <xref:System.IdentityModel.Claims.Claim> classe, use o <xref:System.IdentityModel.Claims.Claim.Equals%2A> para fazer a comparação, conforme mostrado no código a seguir.

     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]

### <a name="comparing-custom-claims-with-primitive-resource-types"></a>Comparando declarações personalizadas com tipos de recursos primitivos

1. Para declarações personalizadas com tipos de recursos primitivos, a comparação pode ser executada como para declarações internas, conforme mostrado no código a seguir.

     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]

2. Para declarações personalizadas com tipos de recursos baseados em classe ou estrutura, o tipo de recurso <xref:System.IdentityModel.Claims.Claim.Equals%2A> deve substituir o método.

3. Primeiro, verifique se `obj` o parâmetro `null`é e, em caso afirmativo, retornar `false`.

     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]

4. Parâmetros de <xref:System.Object.ReferenceEquals%2A> próxima chamada `this` e `obj` Pass e as. Se retornar `true`, retorne. `true`

     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]

5. A próxima tentativa de `obj` atribuir a uma variável local do tipo de classe. Se isso falhar, a referência será `null`. Nesses casos, retorne `false`.

6. Execute a comparação personalizada necessária para comparar corretamente a declaração atual com a declaração fornecida.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra uma comparação de declarações personalizadas em que o recurso de declaração é um tipo não primitivo.

[!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
[!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]

## <a name="see-also"></a>Consulte também

- [Gerenciando reivindicações e autorização com o modelo de identidade](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Como: Criar uma declaração personalizada](how-to-create-a-custom-claim.md)

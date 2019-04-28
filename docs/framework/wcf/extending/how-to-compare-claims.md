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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857748"
---
# <a name="how-to-compare-claims"></a>Como: comparar declarações
A infraestrutura do modelo de identidade no Windows Communication Foundation (WCF) é usada para executar a verificação de autorização. Dessa forma, uma tarefa comum é comparar declarações no contexto de autorização para as declarações necessárias para executar a ação solicitada ou acessar o recurso solicitado. Este tópico descreve como comparar declarações, incluindo tipos de declaração internas e personalizadas. Para obter mais informações sobre a infraestrutura do modelo de identidade, consulte [Gerenciando reivindicações e autorização com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).  
  
 Comparação de declaração envolve comparando as três partes de uma declaração (tipo, certo e recursos) contra as mesmas partes em outra declaração para ver se elas são iguais. Consulte o exemplo a seguir.  
  
 [!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
 [!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]  
  
 Ambas as declarações têm um tipo de declaração de <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, um direito de <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>e um recurso da cadeia de caracteres "alguém". Como todas as três partes da declaração forem iguais, as declarações em si são iguais.  
  
 Os tipos de declaração internos são comparados usando o <xref:System.IdentityModel.Claims.Claim.Equals%2A> método. Código de comparação de declaração específico seja usado quando necessário. Por exemplo, considerando as seguintes declarações de nome principal (UPN) do dois usuário:  
  
 [!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
 [!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]  
  
 o código de comparação no <xref:System.IdentityModel.Claims.Claim.Equals%2A> retorn `true`, assumindo `example\someone` identifica o mesmo usuário de domínio que "someone@example.com".  
  
 Tipos de declaração personalizada também podem ser comparados usando o <xref:System.IdentityModel.Claims.Claim.Equals%2A> método. No entanto, em casos em que o tipo retornado pelo <xref:System.IdentityModel.Claims.Claim.Resource%2A> propriedade da declaração é algo diferente de um tipo primitivo, o <xref:System.IdentityModel.Claims.Claim.Equals%2A> retorna `true` somente se os valores retornados pelo `Resource` propriedades são iguais de acordo com o <xref:System.IdentityModel.Claims.Claim.Equals%2A> método. Em casos em que isso não é apropriado, o tipo personalizado retornado pela `Resource` propriedade deve substituir o <xref:System.IdentityModel.Claims.Claim.Equals%2A> e <xref:System.Object.GetHashCode%2A> métodos para executar qualquer processamento personalizado é necessário.  
  
### <a name="comparing-built-in-claims"></a>Comparar declarações internas  
  
1. Considerando duas instâncias do <xref:System.IdentityModel.Claims.Claim> classe, use o <xref:System.IdentityModel.Claims.Claim.Equals%2A> para fazer a comparação, conforme mostrado no código a seguir.  
  
     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]  
  
### <a name="comparing-custom-claims-with-primitive-resource-types"></a>Comparando as declarações personalizadas com tipos primitivos de recurso  
  
1. Para declarações personalizadas com tipos de recurso primitivo, comparação pode ser executada como para declarações internas, conforme mostrado no código a seguir.  
  
     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]  
  
2. Para as declarações personalizadas com a estrutura ou classe com base em tipos de recursos, o tipo de recurso devem substituir o <xref:System.IdentityModel.Claims.Claim.Equals%2A> método.  
  
3. Primeiro, verifique se o `obj` parâmetro é `null`e nesse caso, retornar `false`.  
  
     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]  
  
4. Em seguida chame <xref:System.Object.ReferenceEquals%2A> e passe `this` e `obj` como parâmetros. Se ele retornar `true`, em seguida, retorne `true`.  
  
     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]  
  
5. Em seguida, tentar atribuir `obj` a uma variável local do tipo de classe. Se isso falhar, a referência é `null`. Nesses casos, retornar `false`.  
  
6. Execute a comparação personalizada necessária comparar corretamente a declaração atual para a declaração fornecida.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma comparação de declarações personalizadas em que o recurso da declaração é um tipo não primitivo.  
  
 [!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
 [!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]  
  
## <a name="see-also"></a>Consulte também

- [Gerenciando reivindicações e autorização com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Como: Criar uma declaração personalizada](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)

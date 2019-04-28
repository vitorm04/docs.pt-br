---
title: Encontrando declarações em um ClaimSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], finding in a claimset
- claims [WCF]
ms.assetid: a76ce107-aeb3-47d0-bfa9-134c53664e20
ms.openlocfilehash: 42e6ee682220913f872da337eb41f6c290082988
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61856397"
---
# <a name="finding-claims-in-a-claimset"></a>Encontrando declarações em um ClaimSet
Examinando o conteúdo de um <xref:System.IdentityModel.Claims.ClaimSet> para determinados tipos de declarações é uma tarefa comum ao usar a autorização baseada em declarações. Para examinar uma <xref:System.IdentityModel.Claims.ClaimSet> quanto à presença de declarações específicas, use o <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> método. Esse método fornece melhor desempenho que iterando diretamente o <xref:System.IdentityModel.Claims.ClaimSet>. O exemplo a seguir demonstra esse uso. Observe que o `claimType` e `claimRight` parâmetros podem ser `null`. Nesse caso, os parâmetros serão corresponde a todos os tipos de declaração e de declaração de direitos.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a>Consulte também

- [Gerenciando reivindicações e autorização com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)

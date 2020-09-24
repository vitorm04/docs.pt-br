---
title: Expressões constantes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
ms.openlocfilehash: 163f73a7682d444214caa213751cb35f8f0e8743
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153034"
---
# <a name="constant-expressions"></a>Expressões constantes

Uma expressão constante consiste em um valor constante. Os valores constantes são convertidos diretamente às expressões constantes da árvore de comando, sem nenhuma conversão no cliente. Isso inclui as expressões que levam a um valor constante. Portanto, o comportamento da fonte de dados deve ser esperado para todas as expressões que envolvem constantes. Isso pode levar ao comportamento que difere do comportamento de CLR.  
  
 O exemplo a seguir mostra uma expressão constante que é avaliada no servidor.  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 LINQ to Entities não dá suporte ao uso de uma classe de usuário como uma constante. No entanto, uma referência de propriedade em uma classe de usuário é considerada uma constante, e será convertida em uma expressão constante de árvore de comando e executada na fonte de dados.  
  
## <a name="see-also"></a>Confira também

- [Expressões em consultas LINQ to Entities](expressions-in-linq-to-entities-queries.md)

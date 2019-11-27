---
title: Cláusula Distinct
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: 94471898807ef4552564c3e01465f2b2f6211d0c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335374"
---
# <a name="distinct-clause-visual-basic"></a>Cláusula Distinct (Visual Basic)
Restringe os valores da variável de intervalo atual para eliminar valores duplicados em cláusulas de consulta subsequentes.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a>Comentários  
 Você pode usar a cláusula `Distinct` para retornar uma lista de itens exclusivos. A cláusula `Distinct` faz com que a consulta ignore resultados de consulta duplicados. A cláusula `Distinct` se aplica a valores duplicados para todos os campos de retorno especificados pela cláusula `Select`. Se nenhuma cláusula de `Select` for especificada, a cláusula `Distinct` será aplicada à variável de intervalo para a consulta identificada na cláusula `From`. Se a variável de intervalo não for um tipo imutável, a consulta irá ignorar apenas um resultado de consulta se todos os membros do tipo corresponderem a um resultado de consulta existente.  
  
## <a name="example"></a>Exemplo  
 A expressão de consulta a seguir une uma lista de clientes e uma lista de pedidos de clientes. A cláusula `Distinct` está incluída para retornar uma lista de nomes de clientes e datas de pedido exclusivos.  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a>Consulte também

- [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Consultas](../../../visual-basic/language-reference/queries/index.md)
- [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)

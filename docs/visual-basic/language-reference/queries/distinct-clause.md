---
title: Cláusula Distinct (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: 4b0ce12f6361d3dc6e5cc3601e96fc3a9bcf3841
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="distinct-clause-visual-basic"></a>Cláusula Distinct (Visual Basic)
Restringe os valores da variável de intervalo atual para eliminar valores duplicados nas cláusulas de consulta subsequentes.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Distinct  
```  
  
## <a name="remarks"></a>Comentários  
 Você pode usar o `Distinct` cláusula para retornar uma lista de itens exclusivos. O `Distinct` cláusula faz com que a consulta ignorar resultados de consulta duplicados. O `Distinct` cláusula se aplica a valores duplicados para todos os campos especificados de retorno de `Select` cláusula. Se nenhum `Select` cláusula for especificada, o `Distinct` cláusula é aplicada à variável de intervalo para a consulta identificada no `From` cláusula. Se a variável de intervalo não é um tipo imutável, a consulta irá ignorar apenas um resultado de consulta se todos os membros do tipo correspondem a um resultado de consulta existente.  
  
## <a name="example"></a>Exemplo  
 A expressão de consulta a seguir associa uma lista de clientes e uma lista de pedidos de clientes. O `Distinct` cláusula é incluída para retornar uma lista de nomes exclusivos de clientes e datas de pedido.  
  
 [!code-vb[VbSimpleQuerySamples#20](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)  
 [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)

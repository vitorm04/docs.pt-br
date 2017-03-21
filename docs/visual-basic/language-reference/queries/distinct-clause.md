---
title: "Cláusula DISTINCT (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryDistinct
dev_langs:
- VB
helpviewer_keywords:
- Distinct clause
- Distinct statement
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
caps.latest.revision: 15
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4e0075a410e9291971308a8cbb1c9c7570b935e4
ms.lasthandoff: 03/13/2017

---
# <a name="distinct-clause-visual-basic"></a>Cláusula Distinct (Visual Basic)
Restringe os valores da variável range atual para eliminar valores duplicados nas cláusulas de consulta subsequentes.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Distinct  
```  
  
## <a name="remarks"></a>Comentários  
 Você pode usar o `Distinct` cláusula para retornar uma lista de itens exclusivos. O `Distinct` cláusula faz a consulta ignorar resultados de consulta duplicados. O `Distinct` cláusula aplica-se a valores duplicados para todos os campos de retorno especificados pelo `Select` cláusula. Se nenhum `Select` cláusula for especificada, o `Distinct` cláusula é aplicada à variável de intervalo para a consulta identificada no `From` cláusula. Se a variável de intervalo não é um tipo imutável, a consulta irá apenas ignorar um resultado de consulta se todos os membros do tipo correspondem a um resultado de consulta existente.  
  
## <a name="example"></a>Exemplo  
 A expressão de consulta a seguir associa uma lista de clientes e uma lista de pedidos de clientes. O `Distinct` cláusula é incluída para retornar uma lista de nomes exclusivos de clientes e datas de pedido.  
  
 [!code-vb[20 VbSimpleQuerySamples](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)   
 [Cláusula FROM](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)   
 [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)

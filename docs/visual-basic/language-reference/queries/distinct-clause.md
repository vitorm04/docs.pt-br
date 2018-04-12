---
title: Cláusula Distinct (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6ed92d5d601c1ec329728346ac881c4fa2bad8aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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

---
title: Cláusula Take (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: 0dddb411af1b4ee269e091c07553a94589d90b2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604023"
---
# <a name="take-clause-visual-basic"></a>Cláusula Take (Visual Basic)
Retorna um número especificado de elementos contíguos do início de uma coleção.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Take count  
```  
  
## <a name="parts"></a>Partes  
 `count`  
 Necessário. Um valor ou uma expressão que é avaliada como o número de elementos da sequência para retornar.  
  
## <a name="remarks"></a>Comentários  
 O `Take` cláusula faz com que uma consulta incluir um número especificado de elementos contíguos do início de uma lista de resultados. O número de elementos para incluir é especificado pelo `count` parâmetro.  
  
 Você pode usar o `Take` cláusula com o `Skip` cláusula para retornar um intervalo de dados de qualquer segmento de uma consulta. Para fazer isso, passe o índice do primeiro elemento do intervalo para o `Skip` cláusula e o tamanho do intervalo para o `Take` cláusula. Nesse caso, o `Take` cláusula deve ser especificada após o `Skip` cláusula.  
  
 Quando você usa o `Take` cláusula em uma consulta, você também precisará garantir que os resultados são retornados em uma ordem que permitirá a `Take` cláusula para incluir os resultados desejados. Para obter mais informações sobre a ordenação de resultados da consulta, consulte [cláusula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Você pode usar o `TakeWhile` cláusula para especificar que somente determinados elementos serão retornado, dependendo de uma condição fornecida.  
  
## <a name="example"></a>Exemplo  
 O seguinte exemplo de código usa o `Take` cláusula junto com o `Skip` cláusula para retornar dados de uma consulta em páginas. A função GetCustomers usa o `Skip` cláusula para ignorar os clientes na lista até que o de índice inicial fornecido valor e usa o `Take` cláusula para retornar uma página de clientes a partir desse valor de índice.  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-clause_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)  
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Cláusula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Cláusula Take While](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [Cláusula Skip](../../../visual-basic/language-reference/queries/skip-clause.md)

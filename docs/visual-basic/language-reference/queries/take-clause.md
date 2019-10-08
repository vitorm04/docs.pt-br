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
ms.openlocfilehash: 32a4c7fd7f1e2f6fe640f3f53f15579f014759d5
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004722"
---
# <a name="take-clause-visual-basic"></a>Cláusula Take (Visual Basic)
Retorna um número especificado de elementos contíguos do início de uma coleção.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Take count  
```  
  
## <a name="parts"></a>Partes  
 `count`  
 Necessário. Um valor ou uma expressão que é avaliada como o número de elementos da sequência a ser retornado.  
  
## <a name="remarks"></a>Comentários  
 A cláusula `Take` faz com que uma consulta inclua um número especificado de elementos contíguos do início de uma lista de resultados. O número de elementos a serem incluídos é especificado pelo parâmetro `count`.  
  
 Você pode usar a cláusula `Take` com a cláusula `Skip` para retornar um intervalo de dados de qualquer segmento de uma consulta. Para fazer isso, passe o índice do primeiro elemento do intervalo para a cláusula `Skip` e o tamanho do intervalo para a cláusula `Take`. Nesse caso, a cláusula `Take` deve ser especificada após a cláusula `Skip`.  
  
 Quando você usa a cláusula `Take` em uma consulta, também pode ser necessário garantir que os resultados sejam retornados em uma ordem que permitirá que a cláusula `Take` inclua os resultados pretendidos. Para obter mais informações sobre como ordenar os resultados da consulta, consulte [cláusula order by](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Você pode usar a cláusula `TakeWhile` para especificar que apenas determinados elementos sejam retornados, dependendo de uma condição fornecida.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir usa a cláusula `Take` junto com a cláusula `Skip` para retornar dados de uma consulta em páginas. A função GetCustomers usa a cláusula `Skip` para ignorar os clientes na lista até o valor de índice inicial fornecido e usa a cláusula `Take` para retornar uma página de clientes que inicia com esse valor de índice.  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Consultas](../../../visual-basic/language-reference/queries/index.md)
- [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Cláusula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Cláusula Take While](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [Cláusula Skip](../../../visual-basic/language-reference/queries/skip-clause.md)

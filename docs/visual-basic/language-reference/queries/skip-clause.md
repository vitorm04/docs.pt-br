---
title: Cláusula Skip (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 508f3c094df4c834305bcb4a78223c1cee82b1c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="skip-clause-visual-basic"></a>Cláusula Skip (Visual Basic)
Ignora um número especificado de elementos em uma coleção e, em seguida, retorna os elementos restantes.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Skip count  
```  
  
## <a name="parts"></a>Partes  
 `count`  
 Necessário. Um valor ou uma expressão que é avaliada como o número de elementos da sequência de ignorar.  
  
## <a name="remarks"></a>Comentários  
 O `Skip` cláusula faz com que uma consulta ignorar os elementos no início de uma lista de resultados e retorna os elementos restantes. O número de elementos a serem ignorados é identificado pelo `count` parâmetro.  
  
 Você pode usar o `Skip` cláusula com o `Take` cláusula para retornar um intervalo de dados de qualquer segmento de uma consulta. Para fazer isso, passe o índice do primeiro elemento do intervalo para o `Skip` cláusula e o tamanho do intervalo para o `Take` cláusula.  
  
 Quando você usa o `Skip` cláusula em uma consulta, você também precisará garantir que os resultados são retornados em uma ordem que permitirá a `Skip` cláusula para ignorar os resultados desejados. Para obter mais informações sobre a ordenação de resultados da consulta, consulte [cláusula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Você pode usar o `SkipWhile` cláusula para especificar que somente determinados elementos são ignorados, dependendo de uma condição fornecida.  
  
## <a name="example"></a>Exemplo  
 O seguinte exemplo de código usa o `Skip` cláusula junto com o `Take` cláusula para retornar dados de uma consulta em páginas. O `GetCustomers` função usa o `Skip` cláusula para ignorar os clientes na lista até que o de índice inicial fornecido valor e usa o `Take` cláusula para retornar uma página de clientes a partir desse valor de índice.  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-clause_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)  
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Cláusula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Cláusula Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Cláusula Take](../../../visual-basic/language-reference/queries/take-clause.md)

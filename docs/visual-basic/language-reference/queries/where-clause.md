---
title: "Cláusula Where (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8c2572f513d00bc72e869cf28d382be799f7a303
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="where-clause-visual-basic"></a>Cláusula Where (Visual Basic)
Especifica a condição de filtragem para uma consulta.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Where condition  
```  
  
## <a name="parts"></a>Partes  
 `condition`  
 Necessário. Uma expressão que determina se os valores para o item atual na coleção são incluídos na coleção de saída. A expressão deve ser avaliada como um `Boolean` valor ou o equivalente de uma `Boolean` valor. Se a condição for avaliada como `True`, o elemento é incluído no resultado da consulta; caso contrário, o elemento é excluído do resultado da consulta.  
  
## <a name="remarks"></a>Comentários  
 O `Where` cláusula permite que você filtre dados da consulta selecionando apenas os elementos que atendam a certos critérios. Elementos cujos valores fazem com que o `Where` cláusula para avaliar a `True` são incluídos no resultado da consulta; outros elementos serão excluídos. A expressão que é usada em uma `Where` cláusula deve ser avaliada como um `Boolean` ou o equivalente de um `Boolean`, como um número inteiro que é avaliada como `False` quando seu valor é zero. Você pode combinar várias expressões em uma `Where` cláusula usando operadores lógicos, como `And`, `Or`, `AndAlso`, `OrElse`, `Is`, e `IsNot`.  
  
 Por padrão, expressões de consulta não são avaliadas até que sejam acessadas — por exemplo, quando eles são associados a dados ou repetidas através de um `For` loop. Como resultado, o `Where` cláusula não é avaliada até que a consulta seja acessada. Se você tiver valores externos a consulta que são usados no `Where` cláusula, certifique-se de que o valor apropriado é usado no `Where` cláusula no momento em que a consulta é executada. Para obter mais informações sobre a execução da consulta, consulte [gravar sua consulta LINQ primeiro](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
 Você pode chamar funções em um `Where` cláusula para executar um cálculo ou operação em um valor do elemento atual na coleção. Chamando uma função em um `Where` cláusula pode fazer com que a consulta a ser executada imediatamente quando ele é definido em vez de quando ele é acessado. Para obter mais informações sobre a execução da consulta, consulte [gravar sua consulta LINQ primeiro](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="example"></a>Exemplo  
 A consulta a seguir usa expressões um `From` cláusula para declarar uma variável de intervalo `cust` para cada `Customer` objeto o `customers` coleção. O `Where` cláusula usa a variável de intervalo para restringir a saída para os clientes da região especificada. O `For Each` loop exibe o nome da empresa para cada cliente no resultado da consulta.  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `And` e `Or` operadores lógicos no `Where` cláusula.  
  
 [!code-vb[VbSimpleQuerySamples#31](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)  
 [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Instrução For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)

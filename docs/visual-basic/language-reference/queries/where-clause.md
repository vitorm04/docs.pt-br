---
title: Cláusula Where (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: de7b4bf3e7dc1145b7e95197c7bd05c66acdabd6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43674473"
---
# <a name="where-clause-visual-basic"></a>Cláusula Where (Visual Basic)
Especifica a condição de filtragem para uma consulta.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Where condition  
```  
  
## <a name="parts"></a>Partes  
 `condition`  
 Necessário. Uma expressão que determina se os valores para o item atual na coleção são incluídos na coleção de saída. A expressão deve ser avaliada como um `Boolean` valor ou o equivalente a um `Boolean` valor. Se a condição for avaliada como `True`, o elemento é incluído no resultado da consulta; caso contrário, o elemento é excluído do resultado da consulta.  
  
## <a name="remarks"></a>Comentários  
 O `Where` cláusula permite que você filtre os dados da consulta, selecionando apenas os elementos que atendem a certos critérios. Elementos cujos valores fazem com que o `Where` cláusula a ser avaliada como `True` estão incluídos no resultado da consulta; outros elementos são excluídos. A expressão que é usada em uma `Where` cláusula deve ser avaliada como uma `Boolean` ou o equivalente de uma `Boolean`, como um inteiro que é avaliada como `False` quando seu valor é zero. Você pode combinar várias expressões em uma `Where` cláusula usando operadores lógicos, como `And`, `Or`, `AndAlso`, `OrElse`, `Is`, e `IsNot`.  
  
 Por padrão, expressões de consulta não são avaliadas até que sejam acessadas — por exemplo, quando eles são associados a dados ou repetidas através uma `For` loop. Como resultado, o `Where` cláusula não é avaliada até que a consulta seja acessada. Se você tiver valores externos a consulta que são usados na `Where` cláusula, certifique-se de que o valor apropriado é usado no `Where` cláusula no momento em que a consulta é executada. Para obter mais informações sobre a execução da consulta, consulte [escrever sua primeira consulta de LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
 Você pode chamar funções em um `Where` cláusula para executar um cálculo ou uma operação em um valor do elemento atual na coleção. Chamar uma função em um `Where` cláusula pode fazer com que a consulta a ser executada imediatamente quando ele é definido em vez de quando ele é acessado. Para obter mais informações sobre a execução da consulta, consulte [escrever sua primeira consulta de LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta de expressão usa uma `From` cláusula para declarar uma variável de intervalo `cust` para cada `Customer` objeto o `customers` coleção. O `Where` cláusula usa a variável de intervalo para restringir a saída para os clientes da região especificada. O `For Each` loop exibe o nome da empresa para cada cliente no resultado da consulta.  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `And` e `Or` operadores lógicos no `Where` cláusula.  
  
 [!code-vb[VbSimpleQuerySamples#31](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Consultas](../../../visual-basic/language-reference/queries/index.md)  
 [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Instrução For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)

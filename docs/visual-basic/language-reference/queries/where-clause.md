---
title: Cláusula Where
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: 60b7ebe96ce0c4580c36675b2e4aa5f9888732c3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349624"
---
# <a name="where-clause-visual-basic"></a>Cláusula Where (Visual Basic)
Especifica a condição de filtragem para uma consulta.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Where condition  
```  
  
## <a name="parts"></a>Partes  
 `condition`  
 Necessária. Uma expressão que determina se os valores para o item atual na coleção são incluídos na coleção de saída. A expressão deve ser avaliada como um valor `Boolean` ou o equivalente de um valor `Boolean`. Se a condição for avaliada como `True`, o elemento será incluído no resultado da consulta; caso contrário, o elemento será excluído do resultado da consulta.  
  
## <a name="remarks"></a>Comentários  
 A cláusula `Where` permite filtrar dados de consulta selecionando apenas os elementos que atendem a determinados critérios. Os elementos cujos valores fazem com que a cláusula de `Where` seja avaliada como `True` são incluídos no resultado da consulta; outros elementos são excluídos. A expressão usada em uma cláusula `Where` deve ser avaliada como um `Boolean` ou equivalente a um `Boolean`, como um inteiro que é avaliado como `False` quando seu valor é zero. Você pode combinar várias expressões em uma cláusula `Where` usando operadores lógicos, como `And`, `Or`, `AndAlso`, `OrElse`, `Is`e `IsNot`.  
  
 Por padrão, as expressões de consulta não são avaliadas até que sejam acessadas — por exemplo, quando elas são vinculadas a dados ou iteradas em um loop de `For`. Como resultado, a cláusula `Where` não é avaliada até que a consulta seja acessada. Se você tiver valores externos à consulta que são usados na cláusula `Where`, verifique se o valor apropriado é usado na cláusula `Where` no momento em que a consulta é executada. Para obter mais informações sobre a execução da consulta, consulte [escrevendo sua primeira consulta LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
 Você pode chamar funções dentro de uma cláusula `Where` para executar um cálculo ou uma operação em um valor do elemento atual na coleção. Chamar uma função em uma cláusula `Where` pode fazer com que a consulta seja executada imediatamente quando definida em vez de quando ela é acessada. Para obter mais informações sobre a execução da consulta, consulte [escrevendo sua primeira consulta LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="example"></a>Exemplo  
 A expressão de consulta a seguir usa uma cláusula `From` para declarar uma variável de intervalo `cust` para cada objeto `Customer` na coleção de `customers`. A cláusula `Where` usa a variável Range para restringir a saída aos clientes da região especificada. O loop de `For Each` exibe o nome da empresa para cada cliente no resultado da consulta.  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `And` e `Or` operadores lógicos na cláusula `Where`.  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a>Consulte também

- [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Consultas](../../../visual-basic/language-reference/queries/index.md)
- [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Instrução For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)

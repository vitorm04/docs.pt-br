---
title: "Cláusula Order By (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryOrderBy
- vb.QueryAscending
- vb.QueryDescending
dev_langs:
- VB
helpviewer_keywords:
- queries [Visual Basic], Order By
- Order By clause
- Order By statement
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
caps.latest.revision: 16
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
ms.openlocfilehash: 33da857b99a37ab904b5abf00968cdffa950ecd4
ms.lasthandoff: 03/13/2017

---
# <a name="order-by-clause-visual-basic"></a>Cláusula Order By (Visual Basic)
Especifica a ordem de classificação para um resultado de consulta.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a>Partes  
 `orderExp1`  
 Necessário. Um ou mais campos do resultado da consulta atual que identificam como ordenar os valores retornados. Os nomes de campo devem ser separados por vírgulas (,). Você pode identificar cada campo como classificado em ordem crescente ou decrescente usando o `Ascending` ou `Descending` palavras-chave. Se nenhum `Ascending` ou `Descending` palavra-chave for especificado, a ordem de classificação padrão é crescente. Os campos de ordem de classificação terá precedência da esquerda para a direita.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar o `Order By` cláusula para classificar os resultados de uma consulta. O `Order By` cláusula só pode classificar um resultado com base na variável de intervalo para o escopo atual. Por exemplo, o `Select` cláusula introduz um novo escopo em uma expressão de consulta com novas variáveis de iteração para esse escopo. Intervalo de variáveis definidas antes de uma `Select` cláusula em uma consulta não estão disponíveis após o `Select` cláusula. Portanto, se você quiser ordenar os resultados por um campo que não está disponível na `Select` cláusula, você deve colocar o `Order By` cláusula antes de `Select` cláusula. Um exemplo de quando você precisa fazer isso é quando você deseja classificar sua consulta pelos campos que não são retornadas como parte do resultado.  
  
 Ordem crescente e decrescente para um campo é determinado pela implementação do <xref:System.IComparable>interface para o tipo de dados do campo.</xref:System.IComparable> Se o tipo de dados não implementa a <xref:System.IComparable>interface, a ordem de classificação é ignorada.</xref:System.IComparable>  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta expressão utiliza um `From` cláusula para declarar uma variável de intervalo `book` para o `books` coleção. O `Order By` cláusula classifica o resultado da consulta por preço crescente ordem (o padrão). Livros com o mesmo preço são classificados por título em ordem crescente. O `Select` cláusula seleciona o `Title` e `Price` propriedades como os valores retornados pela consulta.  
  
 [!code-vb[VbSimpleQuerySamples&#24;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_1.vb)]  
  
## <a name="example"></a>Exemplo  
 A consulta a seguir usa expressões de `Order By` cláusula para classificar o resultado da consulta por preço em ordem decrescente. Livros com o mesmo preço são classificados por título em ordem crescente.  
  
 [!code-vb[25 VbSimpleQuerySamples](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_2.vb)]  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta expressão utiliza um `Select` cláusula para selecionar o título do livro, preço, data de publicação e autor. Ele preenche o `Title`, `Price`, `PublishDate`, e `Author` campos da variável de intervalo para o novo escopo. O `Order By` cláusula ordena a nova variável de intervalo pelo nome do autor, título do livro e preço. Cada coluna é classificada em ordem padrão (crescente).  
  
 [!code-vb[VbSimpleQuerySamples&#26;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_3.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)   
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)   
 [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)

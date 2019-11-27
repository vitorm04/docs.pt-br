---
title: Cláusula Order By
ms.date: 07/20/2015
f1_keywords:
- vb.QueryOrderBy
- vb.QueryAscending
- vb.QueryDescending
helpviewer_keywords:
- queries [Visual Basic], Order By
- Order By clause [Visual Basic]
- Order By statement [Visual Basic]
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
ms.openlocfilehash: a7104e3dd82ff2dde2911861ce98a7367faf3b25
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350426"
---
# <a name="order-by-clause-visual-basic"></a>Cláusula Order By (Visual Basic)
Especifica a ordem de classificação para um resultado de consulta.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a>Partes  
 `orderExp1`  
 Necessária. Um ou mais campos do resultado da consulta atual que identificam como ordenar os valores retornados. Os nomes de campo devem ser separados por vírgulas (,). Você pode identificar cada campo como classificado em ordem crescente ou decrescente usando as palavras-chave `Ascending` ou `Descending`. Se nenhuma palavra-chave `Ascending` ou `Descending` for especificada, a ordem de classificação padrão será ascendente. Os campos de ordem de classificação recebem precedência da esquerda para a direita.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar a cláusula `Order By` para classificar os resultados de uma consulta. A cláusula `Order By` só pode classificar um resultado com base na variável de intervalo para o escopo atual. Por exemplo, a cláusula `Select` introduz um novo escopo em uma expressão de consulta com novas variáveis de iteração para esse escopo. Variáveis de intervalo definidas antes de uma cláusula `Select` em uma consulta não estão disponíveis após a cláusula `Select`. Portanto, se você quiser ordenar os resultados por um campo que não está disponível na cláusula `Select`, deverá colocar a cláusula `Order By` antes da cláusula `Select`. Um exemplo de quando você precisa fazer isso é quando deseja classificar sua consulta por campos que não são retornados como parte do resultado.  
  
 A ordem crescente e decrescente de um campo é determinada pela implementação da interface <xref:System.IComparable> para o tipo de dados do campo. Se o tipo de dados não implementar a interface <xref:System.IComparable>, a ordem de classificação será ignorada.  
  
## <a name="example"></a>Exemplo  
 A expressão de consulta a seguir usa uma cláusula `From` para declarar uma variável de intervalo `book` para a coleção de `books`. A cláusula `Order By` classifica o resultado da consulta por preço em ordem crescente (o padrão). Os livros com o mesmo preço são classificados por título em ordem crescente. A cláusula `Select` seleciona as propriedades `Title` e `Price` como os valores retornados pela consulta.  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a>Exemplo  
 A expressão de consulta a seguir usa a cláusula `Order By` para classificar o resultado da consulta por preço em ordem decrescente. Os livros com o mesmo preço são classificados por título em ordem crescente.  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a>Exemplo  
 A expressão de consulta a seguir usa uma cláusula `Select` para selecionar o título do livro, o preço, a data de publicação e o autor. Em seguida, ele preenche os campos `Title`, `Price`, `PublishDate`e `Author` da variável de intervalo para o novo escopo. A cláusula `Order By` ordena a nova variável de intervalo pelo nome do autor, pelo título do livro e pelo preço. Cada coluna é classificada na ordem padrão (em ordem crescente).  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a>Consulte também

- [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Consultas](../../../visual-basic/language-reference/queries/index.md)
- [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)

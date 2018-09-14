---
title: Cláusula Order By (Visual Basic)
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
ms.openlocfilehash: d4abb5f0b75ae4069c1dbe695a5c810b1f7aa6e1
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45558006"
---
# <a name="order-by-clause-visual-basic"></a>Cláusula Order By (Visual Basic)
Especifica a ordem de classificação para um resultado da consulta.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a>Partes  
 `orderExp1`  
 Necessário. Um ou mais campos do resultado da consulta atual que identificam como ordenar os valores retornados. Os nomes de campo devem ser separados por vírgulas (,). Você pode identificar cada campo como classificados em ordem crescente ou decrescente, usando o `Ascending` ou `Descending` palavras-chave. Se nenhum `Ascending` ou `Descending` palavra-chave for especificada, a ordem de classificação padrão é crescente. Os campos de ordem de classificação terá precedência da esquerda para a direita.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar o `Order By` cláusula para classificar os resultados de uma consulta. O `Order By` cláusula só pode classificar um resultado com base na variável de intervalo para o escopo atual. Por exemplo, o `Select` cláusula introduz um novo escopo em uma expressão de consulta com novas variáveis de iteração para esse escopo. Intervalo de variáveis definidas antes de uma `Select` cláusula em uma consulta não estão disponíveis após o `Select` cláusula. Portanto, se você quiser ordenar os resultados por um campo que não está disponível na `Select` cláusula, você deve colocar o `Order By` cláusula antes do `Select` cláusula. Um exemplo de quando você teria de fazer isso é quando você deseja classificar por campos não são retornadas como parte do resultado da consulta.  
  
 Ordem crescente e decrescente para um campo é determinado pela implementação do <xref:System.IComparable> interface para o tipo de dados do campo. Se o tipo de dados não implementa o <xref:System.IComparable> interface, a ordem de classificação é ignorado.  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta de expressão usa uma `From` cláusula para declarar uma variável de intervalo `book` para o `books` coleção. O `Order By` cláusula classifica o resultado da consulta por preço em ordem (o padrão) crescente. Livros com o mesmo preço são classificados por título em ordem crescente. O `Select` cláusula seleciona o `Title` e `Price` propriedades como valores retornados pela consulta.  
  
 [!code-vb[VbSimpleQuerySamples#24](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_1.vb)]  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta de expressão usa o `Order By` cláusula para classificar o resultado da consulta por preço em ordem decrescente. Livros com o mesmo preço são classificados por título em ordem crescente.  
  
 [!code-vb[VbSimpleQuerySamples#25](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_2.vb)]  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta de expressão usa um `Select` cláusula para selecionar o título do livro, preço, data da publicação e autor. Em seguida, ele preenche os `Title`, `Price`, `PublishDate`, e `Author` campos da variável de intervalo para o novo escopo. O `Order By` cláusula ordena a nova variável de intervalo pelo nome do autor, título do livro e preço. Cada coluna é classificada na ordem padrão (crescente).  
  
 [!code-vb[VbSimpleQuerySamples#26](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_3.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Consultas](../../../visual-basic/language-reference/queries/index.md)  
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)

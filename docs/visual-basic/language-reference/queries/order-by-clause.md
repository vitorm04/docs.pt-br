---
title: "Cl&#225;usula Order By (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.QueryOrderBy"
  - "vb.QueryAscending"
  - "vb.QueryDescending"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "cláusula Order By"
  - "Instrução Order By"
  - "consultas [Visual Basic], Order By"
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Cl&#225;usula Order By (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica a ordem de classificação para um resultado de consulta.  
  
## Sintaxe  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## Partes  
 `orderExp1`  
 Obrigatório.  Um ou mais campos do resultado da consulta atual que identificam como pedir os valores retornados.  Os nomes dos campos devem ser separados por vírgulas \(,\).  Você pode identificar cada campo, como classificados em ordem crescente ou decrescente, usando o `Ascending` ou `Descending` as palavras\-chave.  Se nenhum `Ascending` ou `Descending` palavra\-chave for especificado, a ordem de classificação padrão é crescente.  Os campos de ordem de classificação são dadas a precedência da esquerda para a direita.  
  
## Comentários  
 Você pode usar o `Order By` cláusula para classificar os resultados de uma consulta.  O `Order By` cláusula só pode classificar um resultado baseado na variável de intervalo para o escopo atual.  Por exemplo, o `Select` cláusula introduz um novo escopo em uma expressão de consulta com novas variáveis de iteração para esse escopo.  O intervalo de variáveis definidas antes de um `Select` cláusula em uma consulta não estão disponíveis após a `Select` cláusula.  Portanto, se você deseja ordenar os resultados por um campo que não está disponível na `Select` cláusula, você deve colocar o `Order By` cláusula antes do `Select` cláusula.  Um exemplo de quando você teria que fazer isso é quando você deseja classificar a sua consulta pelos campos que não são retornados como parte do resultado.  
  
 Ordem crescente ou decrescente para um campo é determinado pela implementação da <xref:System.IComparable> interface para o tipo de dados do campo.  Se o tipo de dados não implementa o <xref:System.IComparable> interface, a ordem de classificação será ignorado.  
  
## Exemplo  
 A expressão de consulta a seguir usa uma cláusula `From` para declarar uma variável de intervalod `book` para a coleção `books`.  O `Order By` cláusula classifica o resultado da consulta pelo preço em \(o padrão\) da ordem crescente.  Livros com o mesmo preço são classificados por título em ordem crescente.  O `Select` cláusula seleciona o `Title` e `Price` propriedades como os valores retornados pela consulta.  
  
 [!code-vb[VbSimpleQuerySamples#24](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_1.vb)]  
  
## Exemplo  
 A seguinte consulta expressão usa a `Order By` cláusula para classificar o resultado da consulta pelo preço em ordem decrescente.  Livros com o mesmo preço são classificados por título em ordem crescente.  
  
 [!code-vb[VbSimpleQuerySamples#25](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_2.vb)]  
  
## Exemplo  
 A seguinte consulta expressão usa um `Select` cláusula para selecionar o título do livro, preço, data de publicação e autor.  Em seguida, preenche o `Title`, `Price`, `PublishDate`, e `Author` campos de que a variável de intervalo para o novo escopo.  O `Order By` cláusula ordena a nova variável de intervalo pelo nome do autor, título do livro e preço.  Cada coluna é classificada na ordem padrão \(crescente\).  
  
 [!code-vb[VbSimpleQuerySamples#26](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_3.vb)]  
  
## Consulte também  
 [Introdução a LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)   
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)   
 [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)
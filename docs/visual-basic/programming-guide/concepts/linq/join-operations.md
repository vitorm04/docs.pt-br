---
title: "Ingressar em opera&#231;&#245;es (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: 39ab4854-ac84-4738-9d0b-3cb79be84db4
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ingressar em opera&#231;&#245;es (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Um *junção* de duas fontes de dados é a associação de objetos em uma fonte de dados com objetos que compartilham um atributo comum em outra fonte de dados.  
  
 A junção é uma operação importante em consultas que cujas relações entre si não podem ser seguidas diretamente de fontes de dados de destino. Na programação orientada a objeto, isso pode significar uma correlação entre os objetos que não é modelado, como as versões anteriores a direção de uma relação unidirecional. Um exemplo de uma relação unidirecional é uma classe de cliente que tenha uma propriedade do tipo cidade, mas a classe cidade não tem uma propriedade que é uma coleção de objetos Customer. Se você tiver uma lista de objetos cidade e você deseja localizar todos os clientes em cada cidade, você pode usar uma operação de junção para encontrá\-los.  
  
 Os métodos de associação fornecidos no framework LINQ são <xref:System.Linq.Enumerable.Join%2A> e <xref:System.Linq.Enumerable.GroupJoin%2A>. Esses métodos executam junções equivalentes ou junções que correspondem a duas fontes de dados com base na igualdade de suas chaves. \(Para comparação, Transact\-SQL oferece suporte a operadores de junção diferente de 'equals', por exemplo o ' operador less than'.\) Em termos de banco de dados relacional, <xref:System.Linq.Enumerable.Join%2A> implementa uma junção interna, um tipo de junção em que apenas os objetos que têm uma correspondência no conjunto de dados são retornados. O <xref:System.Linq.Enumerable.GroupJoin%2A> método não tem equivalente em termos de banco de dados relacional, mas ele implementa um superconjunto de junções internas e junções externas esquerdas. Uma junção externa esquerda é uma associação que retorna cada elemento da primeira fonte de dados \(esquerda\), mesmo que ele não tenha elementos correlacionados na fonte de dados.  
  
 A ilustração a seguir mostra uma exibição conceitual de dois conjuntos e os elementos dentro desses conjuntos que estão incluídos em uma junção interna ou uma junção externa esquerda.  
  
 ![Dois círculos sobrepostos mostrando interna&#47;externa.](../../../../csharp/programming-guide/concepts/linq/media/joincircles.png "JoinCircles")  
  
## Métodos  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta do Visual Basic|Mais Informações|  
|--------------------|---------------|------------------------------------------------------|----------------------|  
|Join|Une duas sequências com base nas funções de seletor de chave e extrai pares de valores.|`From x In …, y In … Where x.a = y.a`<br /><br /> \- ou \-<br /><br /> `Join … [As …]In … On …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=fullName>|  
|GroupJoin|Une duas sequências com base em funções de seletor de chave e agrupa as correspondências resultantes para cada elemento.|`Group Join … In … On …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=fullName>|  
  
## Consulte também  
 <xref:System.Linq>   
 [Visão geral de operadores de consulta padrão \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Formulate Joins and Cross\-Product Queries](../Topic/Formulate%20Joins%20and%20Cross-Product%20Queries.md)   
 [Cláusula Join](../../../../visual-basic/language-reference/queries/join-clause.md)   
 [Como: unir conteúdo a partir de arquivos diferentes \(LINQ\) \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)   
 [Como: preencher coleções de objetos de várias fontes \(LINQ\) \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
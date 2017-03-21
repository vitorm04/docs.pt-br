---
title: "Operações (Visual Basic) JOIN | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 39ab4854-ac84-4738-9d0b-3cb79be84db4
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: dce1adb5b918674bc8ee8fc48c8ff5b3c3814a88
ms.lasthandoff: 03/13/2017

---
# <a name="join-operations-visual-basic"></a>Ingressar em operações (Visual Basic)
A *junção* de duas fontes de dados é a associação de objetos em uma fonte de dados com objetos que compartilham um atributo comum em outra fonte de dados.  
  
 A junção é uma operação importante em consultas que têm como destino fontes de dados cujas relações entre si não podem ser seguidas diretamente. Na programação orientada a objeto, isso pode significar uma correlação entre objetos que não são modelados, como a direção retroativa de uma relação unidirecional. Um exemplo de uma relação unidirecional é uma classe Cliente que tem uma propriedade do tipo Cidade, mas a classe Cidade ainda não tem uma propriedade que é uma coleção de objetos Cliente. Se você tem uma lista de objetos Cidade e você quer encontrar todos os clientes em cada cidade, você pode usar uma operação de junção para encontrá-los.  
  
 Os métodos de associação fornecidos no framework LINQ são <xref:System.Linq.Enumerable.Join%2A>e <xref:System.Linq.Enumerable.GroupJoin%2A>.</xref:System.Linq.Enumerable.GroupJoin%2A> </xref:System.Linq.Enumerable.Join%2A> Esses métodos executam junções equivalentes ou junções que correspondem a duas fontes de dados com base na igualdade de suas chaves. (Para comparação, o Transact-SQL oferece suporte a operadores de junção diferentes de 'equals', por exemplo, o 'less than'.) Em termos de banco de dados relacional, <xref:System.Linq.Enumerable.Join%2A>implementa uma junção interna, um tipo de junção em que apenas os objetos que têm uma correspondência no conjunto de dados são retornados.</xref:System.Linq.Enumerable.Join%2A> O <xref:System.Linq.Enumerable.GroupJoin%2A>método não tem equivalente em termos de banco de dados relacional, mas ele implementa um superconjunto de junções internas e junções externas esquerdas.</xref:System.Linq.Enumerable.GroupJoin%2A> Uma junção externa esquerda é uma associação que retorna cada elemento da primeira fonte de dados (esquerda), mesmo que ele não tenha elementos correlacionados na fonte de dados.  
  
 A ilustração a seguir mostra uma visão conceitual de dois conjuntos e os elementos dentro desses conjuntos que estão incluídos em uma junção interna ou externa à esquerda.  
  
 ![Dois círculos sobrepostos mostrando interna/externa. ] (../../../../csharp/programming-guide/concepts/linq/media/joincircles.png "JoinCircles")  
  
## <a name="methods"></a>Métodos  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta do Visual Basic|Mais informações|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Join|Une duas sequências com base nas funções de seletor de chave e extrai pares de valores.|`From x In …, y In … Where x.a = y.a`<br /><br /> -ou-<br /><br /> `Join … [As …]In … On …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Join%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=fullName></xref:System.Linq.Queryable.Join%2A?displayProperty=fullName>|  
|GroupJoin|Une duas sequências baseadas em funções de seletor de chave e agrupa as correspondências resultantes para cada elemento.|`Group Join … In … On …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=fullName></xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=fullName></xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=fullName>|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq></xref:System.Linq>   
 [Visão geral de operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Formular junções e consultas entre produtos](http://msdn.microsoft.com/library/d8072ede-0521-4670-9bec-1778ceeb875b)   
 [Cláusula JOIN](../../../../visual-basic/language-reference/queries/join-clause.md)   
 [Como: unir conteúdo a partir de arquivos diferentes (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)   
 [Como: preencher coleções de objetos de várias fontes (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)

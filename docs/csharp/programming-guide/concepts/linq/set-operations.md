---
title: "Opera&#231;&#245;es de conjunto (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Opera&#231;&#245;es de conjunto (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Operações de conjunto em LINQ, consulte operações de consulta que produzem um conjunto de resultados com base na presença ou ausência de elementos equivalentes dentro do mesmo ou separados coleções \(ou conjuntos\).  
  
 Os métodos de operador de consulta padrão que realizam operações de conjunto são listados na seção a seguir.  
  
## Métodos  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta c\#|Mais Informações|  
|--------------------|---------------|------------------------------------------|----------------------|  
|Distinct|Remove os valores de uma coleção duplicados.|Não aplicável.|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=fullName>|  
|Exceto|Retorna a diferença de conjunto, o que significa que os elementos de uma coleção que não aparecem em uma segunda coleção.|Não aplicável.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=fullName>|  
|Intersect|Retorna a interseção de conjunto, o que significa que os elementos que aparecem em cada uma das duas coleções.|Não aplicável.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=fullName>|  
|União|Retorna a união de conjunto, o que significa que os elementos exclusivos que aparecem em qualquer uma das duas coleções.|Não aplicável.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=fullName>|  
  
## Comparação de operações de conjunto  
  
### Distinct  
 A ilustração a seguir descreve o comportamento do <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName> método em uma seqüência de caracteres. A sequência retornada contém os elementos exclusivos da seqüência de entrada.  
  
 ![Gráfico mostrando o comportamento de Distinct&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinct")  
  
### Exceto  
 A ilustração a seguir descreve o comportamento de <xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName>. A sequência retornada contém apenas os elementos da primeira seqüência de entrada que não estão na segunda sequência de entrada.  
  
 ![Gráfico mostrando a ação de except &#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")  
  
### Intersect  
 A ilustração a seguir descreve o comportamento de <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName>. A sequência retornada contém os elementos que são comuns a ambas as seqüências de entrada.  
  
 ![Gráfico mostrando a interseção de duas seqüências.](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")  
  
### União  
 A ilustração a seguir mostra uma operação de união em duas seqüências de caracteres. A sequência retornada contém os elementos exclusivos de ambas as seqüências.  
  
 ![Gráfico mostrando a união de duas seqüências.](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")  
  
## Consulte também  
 <xref:System.Linq>   
 [Visão geral de operadores de consulta padrão \(c\#\)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Como: combinar e comparar coleções de cadeia de caracteres \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)   
 [Como: localizar a diferença definida entre as duas listas \(LINQ\) \(c\#\)](../Topic/How%20to:%20Find%20the%20Set%20Difference%20Between%20Two%20Lists%20\(LINQ\)%20\(C%23\).md)
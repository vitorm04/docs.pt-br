---
title: "Funcional. Programa&#231;&#227;o procedural (LINQ to XML) (c#) | Microsoft Docs"
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
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Funcional. Programa&#231;&#227;o procedural (LINQ to XML) (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Há vários tipos de aplicativos XML:  
  
-   Alguns aplicativos utilizam documentos XML de origem e geram novos documentos XML que estão em uma forma diferente os documentos de origem.  
  
-   Alguns aplicativos utilizam documentos XML de origem e produzem documentos de resultado em um formato totalmente diferente, como arquivos de texto HTML ou CSV.  
  
-   Alguns aplicativos utilizam documentos XML de origem e inserir registros em um banco de dados.  
  
-   Alguns aplicativos utilizam dados de outra fonte, como um banco de dados e criam documentos XML a partir dele.  
  
 Esses não são todos os tipos de aplicativos XML, mas eles são um conjunto representativo dos tipos de funcionalidade que um programador XML tem que implementar.  
  
 Com todos esses tipos de aplicativos, há duas abordagens contrastantes que um desenvolvedor pode utilizar:  
  
-   Construção funcional usando uma abordagem declarativa.  
  
-   Modificação de árvore XML na memória usando código procedural.  
  
 LINQ to XML suporta duas abordagens.  
  
 Ao usar a abordagem funcional, você escreve as transformações que utilizam os documentos de origem e geram documentos de resultado completamente novos com o formato desejado.  
  
 Ao modificar uma árvore XML no lugar, você escrever código que percorre e navega através de nós em uma árvore XML na memória, inserir, excluir e modificar nós conforme necessário.  
  
 Você pode usar o LINQ to XML com essa abordagem. Use as mesmas classes e, em alguns casos, os mesmos métodos. No entanto, a estrutura e as metas das duas abordagens são muito diferentes. Por exemplo, em situações diferentes, uma ou outra abordagem será geralmente têm um desempenho melhor e usará mais ou menos memória. Além disso, uma ou outra abordagem será mais fácil de escrever e produzirá um código mais sustentável.  
  
 Para ver as duas abordagens contrastadas, consulte [In\-Memory XML Tree Modification vs. Functional Construction \(LINQ to XML\) \(C\#\)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).  
  
 Para obter um tutorial sobre como escrever transformações funcionais, consulte [Pure Functional Transformations of XML \(C\#\)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).  
  
## Consulte também  
 [LINQ to XML visão geral da programação \(c\#\)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
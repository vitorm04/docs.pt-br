---
title: "Opera&#231;&#245;es de quantificador (c#) | Microsoft Docs"
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
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Opera&#231;&#245;es de quantificador (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Operações de quantificador retornam um <xref:System.Boolean> valor que indica se alguns ou todos os elementos em uma sequência satisfazem uma condição.  
  
 A ilustração a seguir mostra duas operações de quantificador diferentes em duas seqüências de fonte diferente. A primeira operação pergunta se um ou mais dos elementos são a caractere 'A', e o resultado é `true`. A segunda operação pergunta se todos os elementos são a caractere 'A', e o resultado é `true`.  
  
 ![Operações de quantificador LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ\_Quantifier")  
  
 Os métodos de operador de consulta padrão que executam operações de quantificador são listados na seção a seguir.  
  
## Métodos  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta c\#|Mais Informações|  
|--------------------|---------------|------------------------------------------|----------------------|  
|Todos os|Determina se todos os elementos em uma sequência satisfazem uma condição.|Não aplicável.|<xref:System.Linq.Enumerable.All%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=fullName>|  
|Qualquer|Determina se todos os elementos em uma sequência satisfazem uma condição.|Não aplicável.|<xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=fullName>|  
|Contém|Determina se uma seqüência contém um elemento especificado.|Não aplicável.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=fullName>|  
  
## Consulte também  
 <xref:System.Linq>   
 [Visão geral de operadores de consulta padrão \(c\#\)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Como especificar filtros predicados dinamicamente em tempo de execução](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)   
 [Como: consultar sentenças que contêm um conjunto especificado de palavras \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
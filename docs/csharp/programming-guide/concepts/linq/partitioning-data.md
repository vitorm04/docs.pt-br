---
title: "Particionamento de dados (c#) | Microsoft Docs"
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
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Particionamento de dados (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Particionamento em LINQ refere\-se a operação de dividir uma seqüência de entrada em duas seções, sem reorganizar os elementos e, em seguida, retornando uma das seções.  
  
 A ilustração a seguir mostra os resultados de três particionamentos operações diferentes em uma seqüência de caracteres. A primeira operação retorna os três primeiros elementos na sequência. A segunda operação ignora os três primeiros elementos e retorna os elementos restantes. A terceira operação ignora os primeiros dois elementos na sequência e retorna os três elementos.  
  
 ![Operações de particionamento LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ\_Partition")  
  
 Os métodos de operador de consulta padrão que seqüências de partição são listados na seção a seguir.  
  
## Operadores  
  
|Nome do operador|Descrição|Sintaxe de expressão de consulta c\#|Mais Informações|  
|----------------------|---------------|------------------------------------------|----------------------|  
|Skip|Ignora elementos até uma posição especificada em uma sequência.|Não aplicável.|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=fullName>|  
|SkipWhile|Ignora elementos com base em uma função de predicado até que um elemento não atendem à condição.|Não aplicável.|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=fullName>|  
|Take|Usa elementos até uma posição especificada em uma sequência.|Não aplicável.|<xref:System.Linq.Enumerable.Take%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=fullName>|  
|TakeWhile|Usa elementos com base em uma função de predicado até que um elemento não atendem à condição.|Não aplicável.|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=fullName>|  
  
## Consulte também  
 <xref:System.Linq>   
 [Visão geral de operadores de consulta padrão \(c\#\)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
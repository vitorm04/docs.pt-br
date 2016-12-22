---
title: "Opera&#231;&#245;es de quantificador (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Opera&#231;&#245;es de quantificador (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Operações de quantificador retornam um <xref:System.Boolean> valor que indica se alguns ou todos os elementos em uma sequência satisfazem uma condição.  
  
 A ilustração a seguir mostra duas operações de quantificador diferentes em duas seqüências de fonte diferente. A primeira operação pergunta se um ou mais dos elementos são a caractere 'A', e o resultado é `true`. A segunda operação pergunta se todos os elementos são a caractere 'A', e o resultado é `true`.  
  
 ![Operações de quantificador LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ\_Quantifier")  
  
 Os métodos de operador de consulta padrão que executam operações de quantificador são listados na seção a seguir.  
  
## Métodos  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta do Visual Basic|Mais Informações|  
|--------------------|---------------|------------------------------------------------------|----------------------|  
|Todos os|Determina se todos os elementos em uma sequência satisfazem uma condição.|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=fullName>|  
|Qualquer|Determina se todos os elementos em uma sequência satisfazem uma condição.|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=fullName>|  
|Contém|Determina se uma seqüência contém um elemento especificado.|Não aplicável.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=fullName>|  
  
## Exemplos de sintaxe de expressão de consulta  
 Esses exemplos usam o `Aggregate` cláusula no Visual Basic como parte da condição de filtragem em uma consulta LINQ.  
  
 O exemplo a seguir usa o `Aggregate` cláusula e o <xref:System.Linq.Enumerable.All%2A> método de extensão para retornar de uma coleção às pessoas cujos animais de estimação são todos os mais antigos do que uma determinada idade.  
  
 [!code-vb[CsLINQAnyAll#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_1.vb)]  
  
 O exemplo a seguir usa o `Aggregate` cláusula e o <xref:System.Linq.Enumerable.Any%2A> método de extensão para retornar de uma coleção, as pessoas que tenham pelo menos uma pet que for mais antigo que uma determinada idade.  
  
 [!code-vb[CsLINQAnyAll#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_2.vb)]  
  
## Consulte também  
 <xref:System.Linq>   
 [Visão geral de operadores de consulta padrão \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md)   
 [Como: consultar sentenças que contêm um conjunto especificado de palavras \(LINQ\) \(Visual Basic\)](../Topic/How%20to:%20Query%20for%20Sentences%20that%20Contain%20a%20Specified%20Set%20of%20Words%20\(LINQ\)%20\(Visual%20Basic\)1.md)
---
title: "Operações de quantificador (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
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
ms.openlocfilehash: 7f69aed2e0e6791ca7f17c3420ff75a1ba220187
ms.lasthandoff: 03/13/2017

---
# <a name="quantifier-operations-visual-basic"></a>Operações de quantificador (Visual Basic)
Operações de quantificador retornam um <xref:System.Boolean>valor que indica se alguns ou todos os elementos em uma sequência satisfazem uma condição.</xref:System.Boolean>  
  
 A ilustração a seguir mostra duas operações de quantificador diferentes em duas sequências de fonte diferente. A primeira operação pergunta se um ou mais dos elementos são a caractere 'A', e o resultado é `true`. A segunda operação pergunta se todos os elementos são a caractere 'A', e o resultado é `true`.  
  
 ![Operações de quantificador LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")  
  
 Os métodos de operador de consulta padrão que executam operações de quantificador são listados na seção a seguir.  
  
## <a name="methods"></a>Métodos  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta do Visual Basic|Mais informações|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Todos|Determina se todos os elementos em uma sequência satisfazem uma condição.|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=fullName></xref:System.Linq.Enumerable.All%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=fullName></xref:System.Linq.Queryable.All%2A?displayProperty=fullName>|  
|Qualquer|Determina se todos os elementos em uma sequência satisfazem uma condição.|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=fullName></xref:System.Linq.Queryable.Any%2A?displayProperty=fullName>|  
|Contém|Determina se uma sequência contém um elemento especificado.|Não aplicável.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Contains%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=fullName></xref:System.Linq.Queryable.Contains%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-examples"></a>Exemplos de sintaxe de expressão de consulta  
 Esses exemplos usam o `Aggregate` cláusula no Visual Basic como parte da condição de filtragem em uma consulta LINQ.  
  
 O exemplo a seguir usa o `Aggregate` cláusula e o <xref:System.Linq.Enumerable.All%2A>método de extensão para retornar de uma coleção às pessoas cujos animais de estimação são todos os mais antigos do que uma determinada idade.</xref:System.Linq.Enumerable.All%2A>  
  
 [!code-vb[CsLINQAnyAll n º&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_1.vb)]  
  
 O exemplo a seguir usa o `Aggregate` cláusula e o <xref:System.Linq.Enumerable.Any%2A>método de extensão para retornar de uma coleção, as pessoas que tenham pelo menos uma pet que for mais antigo que uma determinada idade.</xref:System.Linq.Enumerable.Any%2A>  
  
 [!code-vb[CsLINQAnyAll n º&2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq></xref:System.Linq>   
 [Visão geral de operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md)   
 [Como: consultar sentenças que contêm um conjunto especificado de palavras (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

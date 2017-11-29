---
title: "Operações de quantificador (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9bc48c69179b1f8876efaa465295e94a9a0e0fb6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="quantifier-operations-visual-basic"></a>Operações de quantificador (Visual Basic)
As operações de quantificador retornam um valor <xref:System.Boolean> que indica se alguns ou todos os elementos em uma sequência satisfazem uma condição.  
  
 A ilustração a seguir mostra duas operações de quantificador diferentes em duas sequências de origem diferentes. A primeira operação pergunta se um ou mais dos elementos são o caractere 'A' e o resultado é `true`. A segunda operação pergunta se todos os elementos são o caractere 'A' e o resultado é `true`.  
  
 ![Operações de quantificador LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")  
  
 Os métodos de operador de consulta padrão que realizam operações de quantificador estão listados na seção a seguir.  
  
## <a name="methods"></a>Métodos  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta do Visual Basic|Mais informações|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Todos|Determina se todos os elementos em uma sequência satisfazem uma condição.|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|Qualquer|Determina se todos os elementos em uma sequência satisfazem uma condição.|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|Contém|Determina se uma sequência contém um elemento especificado.|Não aplicável.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Exemplos de sintaxe de expressão de consulta  
 Esses exemplos usam o `Aggregate` cláusula no Visual Basic, como parte da condição de filtragem em uma consulta LINQ.  
  
 O exemplo a seguir usa o `Aggregate` cláusula e o <xref:System.Linq.Enumerable.All%2A> método de extensão para as pessoas cujos animais de estimação são todos os mais antigos do que uma determinada idade de retorno de uma coleção.  
  
 [!code-vb[CsLINQAnyAll#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_1.vb)]  
  
 O exemplo a seguir usa o `Aggregate` cláusula e o <xref:System.Linq.Enumerable.Any%2A> método de extensão para retornar de uma coleção, as pessoas que possuem pelo menos um pet que é mais de uma determinada idade.  
  
 [!code-vb[CsLINQAnyAll#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq>  
 [Visão geral de operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Como: consultar sentenças que contêm um conjunto especificado de palavras (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

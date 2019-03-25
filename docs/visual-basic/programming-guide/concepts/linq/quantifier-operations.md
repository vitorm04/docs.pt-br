---
title: Operações de quantificador (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: c358c3181ecbefeedcbe22e6f3c877d2924c66b3
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409504"
---
# <a name="quantifier-operations-visual-basic"></a>Operações de quantificador (Visual Basic)
As operações de quantificador retornam um valor <xref:System.Boolean> que indica se alguns ou todos os elementos em uma sequência satisfazem uma condição.  
  
 A ilustração a seguir mostra duas operações de quantificador diferentes em duas sequências de origem diferentes. A primeira operação pergunta se um ou mais dos elementos são o caractere 'A' e o resultado é `true`. A segunda operação pergunta se todos os elementos são o caractere 'A' e o resultado é `true`.  
  
 ![Operações de quantificador LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 Os métodos de operador de consulta padrão que realizam operações de quantificador estão listados na seção a seguir.  
  
## <a name="methods"></a>Métodos  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta do Visual Basic|Mais informações|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Todos|Determina se todos os elementos em uma sequência satisfazem uma condição.|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|Qualquer|Determina se todos os elementos em uma sequência satisfazem uma condição.|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|Contém|Determina se uma sequência contém um elemento especificado.|Não aplicável.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Exemplos de sintaxe de expressão de consulta  
 Esses exemplos usam o `Aggregate` cláusula no Visual Basic como parte da condição de filtragem em uma consulta LINQ.  
  
 O exemplo a seguir usa o `Aggregate` cláusula e o <xref:System.Linq.Enumerable.All%2A> método de extensão para retornar de uma coleção às pessoas cujos animais de estimação são todos os mais antigos do que uma determinada idade.  
  
 [!code-vb[CsLINQAnyAll#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#1)]  
  
 O próximo exemplo usa o `Aggregate` cláusula e o <xref:System.Linq.Enumerable.Any%2A> método de extensão para retornar de uma coleção, as pessoas que possuem pelo menos uma pet que é mais antigo que uma determinada idade.  
  
 [!code-vb[CsLINQAnyAll#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#2)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Linq>
- [Visão geral de operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Como: Consultar sentenças que contenham um conjunto especificado de palavras (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

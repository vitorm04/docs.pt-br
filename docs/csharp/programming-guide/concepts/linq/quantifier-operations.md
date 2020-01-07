---
title: Operações de quantificador (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 5c931e0971a2ae7970415905be8772a64a82ee39
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635477"
---
# <a name="quantifier-operations-c"></a>Operações de quantificador (C#)
As operações de quantificador retornam um valor <xref:System.Boolean> que indica se alguns ou todos os elementos em uma sequência satisfazem uma condição.  
  
 A ilustração a seguir mostra duas operações de quantificador diferentes em duas sequências de origem diferentes. A primeira operação pergunta se um ou mais dos elementos são o caractere 'A' e o resultado é `true`. A segunda operação pergunta se todos os elementos são o caractere 'A' e o resultado é `true`.  
  
 ![Operações de quantificador LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 Os métodos de operador de consulta padrão que realizam operações de quantificador estão listados na seção a seguir.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta C#|Mais Informações|  
|-----------------|-----------------|---------------------------------|----------------------|  
|{1&gt;Todos&lt;1}|Determina se todos os elementos em uma sequência satisfazem uma condição.|{1&gt;Não aplicável.&lt;1}|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|Qualquer|Determina se todos os elementos em uma sequência satisfazem uma condição.|{1&gt;Não aplicável.&lt;1}|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|Contém|Determina se uma sequência contém um elemento especificado.|{1&gt;Não aplicável.&lt;1}|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  

## <a name="query-expression-syntax-examples"></a>Exemplos de sintaxe de expressão de consulta  
  
### <a name="all"></a>{1&gt;Todos&lt;1}  
O exemplo a seguir usa o `All` para verificar se todas as cadeias de caracteres são de um comprimento específico.
  
[!code-csharp[All](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#All)]  
  
### <a name="any"></a>Qualquer  
O exemplo a seguir usa o `Any` para verificar se todas as cadeias de caracteres são iniciadas com ' o '.  
  
[!code-csharp[Any](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Any)]  
  
### <a name="contains"></a>Contém  
O exemplo a seguir usa o `Contains` para verificar se uma matriz tem um elemento específico.  
  
[!code-csharp[Contains](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Contains)]  
  
## <a name="see-also"></a>Veja também

- <xref:System.Linq>
- [Visão geral de operadores de consulta padrão (C#)](./standard-query-operators-overview.md)
- [Especificar filtros predicados dinamicamente em runtime](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [Como consultar frases que contenham um conjunto especificado de palavras (LINQ) (C#)](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

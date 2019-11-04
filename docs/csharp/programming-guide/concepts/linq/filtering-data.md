---
title: Filtrando dados (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: eb448c1c2ea6d9b3fcf0120043cafebc01cd3805
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418468"
---
# <a name="filtering-data-c"></a>Filtrando dados (C#)
A filtragem é a operação de restringir o conjunto de resultados de forma que ele contenha apenas os elementos correspondentes a uma condição especificada. Ela também é conhecida como seleção.  
  
 A ilustração a seguir mostra os resultados da filtragem de uma sequência de caracteres. O predicado para a operação de filtragem especifica que o caractere deve ser "A".  
  
 ![Diagrama que mostra uma operação de filtragem do LINQ](./media/filtering-data/linq-filter-operation.png)  
  
 Os métodos de operador de consulta padrão que realizam a seleção estão listados na seção a seguir.  
  
## <a name="methods"></a>Métodos  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta C#|Mais informações|  
|-----------------|-----------------|---------------------------------|----------------------|  
|OfType|Seleciona valores, dependendo da capacidade de serem convertidos em um tipo especificado.|Não aplicável.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|Where|Seleciona valores com base em uma função de predicado.|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Exemplo de sintaxe de expressão de consulta  
 O exemplo a seguir usa a cláusula `where` para filtrar em uma matriz as cadeias de caracteres com um tamanho específico.  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            where word.Length == 3  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
*/  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Linq>
- [Visão geral de operadores de consulta padrão (C#)](./standard-query-operators-overview.md)
- [Cláusula where](../../../language-reference/keywords/where-clause.md)
- [Como especificar filtros predicados dinamicamente em tempo de execução](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [Como consultar metadados de um assembly com reflexão (LINQ) (C#)](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [Como consultar arquivos com um atributo ou nome especificado (C#)](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [Como classificar ou filtrar dados de texto por qualquer palavra ou campo (LINQ) (C#)](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

---
title: Filtrando dados (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: 74399244990f8ff2deaa1d10576ea94a57c16bee
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346985"
---
# <a name="filtering-data-c"></a>Filtrando dados (C#)
A filtragem é a operação de restringir o conjunto de resultados de forma que ele contenha apenas os elementos correspondentes a uma condição especificada. Ela também é conhecida como seleção.  
  
 A ilustração a seguir mostra os resultados da filtragem de uma sequência de caracteres. O predicado para a operação de filtragem especifica que o caractere deve ser "A".  
  
 ![Diagrama que mostra uma operação de filtragem do LINQ](./media/filtering-data/linq-filter-operation.png)  
  
 Os métodos de operador de consulta padrão que realizam a seleção estão listados na seção a seguir.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta C#|Mais Informações|  
|-----------------|-----------------|---------------------------------|----------------------|  
|OfType|Seleciona valores, dependendo da capacidade de serem convertidos em um tipo especificado.|{1&gt;Não aplicável.&lt;1}|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|Onde|Seleciona valores com base em uma função de predicado.|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
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
  
## <a name="see-also"></a>Veja também

- <xref:System.Linq>
- [Visão geral de operadores de consulta padrão (C#)](./standard-query-operators-overview.md)
- [Cláusula where](../../../language-reference/keywords/where-clause.md)
- [Especificar filtros predicados dinamicamente em runtime](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [Como consultar metadados de um assembly com reflexão (LINQ) (C#)](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [Como consultar arquivos com um atributo ou nome especificado (C#)](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [Como classificar ou filtrar dados de texto por qualquer palavra ou campo (LINQ) (C#)](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

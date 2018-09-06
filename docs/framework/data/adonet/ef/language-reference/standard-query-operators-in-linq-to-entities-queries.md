---
title: Operadores de consulta padrão em consultas LINQ to Entities
ms.date: 08/21/2018
ms.assetid: 7fa55a9b-6219-473d-b1e5-2884a32dcdff
ms.openlocfilehash: 302fa281767fc95e9a9a2192382034b3a519cd92
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43884863"
---
# <a name="standard-query-operators-in-linq-to-entities-queries"></a>Operadores de consulta padrão em consultas LINQ to Entities
Em uma consulta, você especifica as informações que deseja recuperar da fonte de dados. Uma consulta também pode especificar como essas informações devem ser classificadas, agrupadas e moldadas antes de serem retornadas. A sintaxe de consulta LINQ fornece um conjunto de métodos de consulta padrão que você pode usar em uma consulta. A maioria desses métodos opera em sequências; Nesse contexto, uma sequência é um objeto cujo tipo implementa a <xref:System.Collections.Generic.IEnumerable%601> interface ou o <xref:System.Linq.IQueryable%601> interface. A funcionalidade de consulta de operadores de consulta padrão inclui filtragem, projeção, agregação, classificação, agrupamento, paginação e muito mais. Alguns dos operadores de consulta padrão mais usados possuem sintaxe de palavra-chave dedicada para que possam ser chamados por meio da sintaxe da expressão de consulta. Uma expressão de consulta é uma maneira diferente e mais legível de expressar uma consulta do que o equivalente baseado em método. As cláusulas de expressão de consulta são convertidas em chamadas para os métodos de consulta em tempo de compilação. Para obter uma lista de operadores de consulta padrão que têm cláusulas de expressão de consulta equivalente, consulte [visão geral de operadores de consulta padrão](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).  
  
 Nem todos os operadores de consulta padrão têm suporte em consultas [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]. Para obter mais informações, consulte [com suporte e os métodos LINQ (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md). Este tópico fornece informações sobre os operadores de consulta padrão que são específicas para [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]. Para obter mais informações sobre problemas conhecidos [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] consultas, consulte [problemas conhecidos e considerações no LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md).  
  
## <a name="projection-and-filtering-methods"></a>Métodos de projeção e filtragem  
 *Projeção* refere-se a transformação de elementos de um conjunto de resultados em um formulário desejado. Por exemplo, você pode projetar um subconjunto das propriedades de que precisa de cada objeto do conjunto de resultados, projetar uma propriedade e efetuar um cálculo matemático nela ou projetar o objeto inteiro do conjunto de resultados. Os métodos de projeção são `Select` e `SelectMany`.  
  
 *Filtragem* refere-se para a operação de restringir o conjunto de resultados para conter apenas os elementos que correspondem a uma condição especificada. O método de filtragem é `Where`.  
  
 A maioria das sobrecargas dos métodos de projeção e de filtragem tem suporte em [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], exceto aquelas que aceitam um argumento posicional.  
  
## <a name="join-methods"></a>Métodos de junção  
 A junção é uma operação importante em consultas que usam fontes de dados de destino que não têm nenhuma relação navegável entre si. Uma junção de duas fontes de dados é a associação de objetos em uma fonte de dados com objetos em outra fonte de dados que compartilham um atributo ou uma propriedade comum. Os métodos de junção são `Join` e `GroupJoin`.  
  
 A maioria das sobrecargas dos métodos de junção tem suporte, exceto aquelas que usam <xref:System.Collections.Generic.IEqualityComparer%601>. Isso ocorre porque o comparador não pode ser convertido na fonte de dados.  
  
## <a name="set-methods"></a>Definir métodos  
 As operações de definição em LINQ são operações de consulta que baseiam seus conjuntos de resultados na presença ou na ausência de elementos equivalentes na mesma ou em outra coleção (ou em um conjunto). Os métodos de definição são `All`, `Any`, `Concat`, `Contains`, `DefaultIfEmpty`, `Distinct`, `EqualAll`, `Except`, `Intersect` e `Union`.  
  
 A maioria das sobrecargas dos métodos de definição tem suporte em [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], embora existam algumas diferenças de comportamento em relação a LINQ to Objects. No entanto, definir métodos que usam um <xref:System.Collections.Generic.IEqualityComparer%601> não têm suporte porque o comparer não pode ser convertido para a fonte de dados.  
  
## <a name="ordering-methods"></a>Métodos de ordenação  
 Ordenação ou Classificação é a operação de ordenar os elementos de um conjunto de resultados com base em um ou mais atributos. Ao especificar mais de um critério de classificação, você pode romper os vínculos em um grupo.  
  
 Há suporte para a maioria dos métodos de ordenação, exceto para aqueles que usam <xref:System.Collections.Generic.IComparer%601>. Isso ocorre porque o comparador não pode ser convertido na fonte de dados. Os métodos de ordenação são `OrderBy`, `OrderByDescending`, `ThenBy`, `ThenByDescending` e `Reverse`.  
  
 Como a consulta é executada na fonte de dados, o comportamento de ordenação pode diferir das consultas executadas em CLR. Isso ocorre porque as opções de ordenação, por exemplo, a ordenação de casos, a ordenação de kanji e a ordenação de valores nulos, podem ser definidas na fonte de dados. Dependendo da fonte de dados, essas opções de ordenação podem produzir diferentes resultados em relação a CLR.  
  
 Se você especificar o mesmo seletor de chave em mais de uma operação de ordenação, uma ordenação duplicada será produzida. Isso não é válido e uma exceção será gerada.  
  
## <a name="grouping-methods"></a>Métodos de agrupamento  
 O agrupamento é a colocação de dados em grupos de modo que os elementos em cada grupo compartilhem um atributo comum. O método de agrupamento é `GroupBy`.  
  
 Há suporte para a maioria dos métodos de agrupamento, exceto para aqueles que usam <xref:System.Collections.Generic.IEqualityComparer%601>. Isso ocorre porque o comparador não pode ser convertido na fonte de dados.  
  
 Os métodos de agrupamento são mapeados para a fonte de dados usando uma subconsulta distinta para o seletor de chave. A subconsulta de comparação de seletor de chave é executada usando a semântica da fonte de dados, incluindo os problemas relacionados à comparação de valores `null`.  
  
## <a name="aggregate-methods"></a>Métodos de agregação  
 Uma operação de agregação computa um único valor de uma coleção de valores. Por exemplo, calcular a temperatura média diária a partir dos valores de temperatura diária de um mês é uma operação de agregação. Os métodos de agregação são `Aggregate`, `Average`, `Count`, `LongCount`, `Max`, `Min` e `Sum`.  
  
 Há suporte para a maioria das sobrecargas dos métodos de agregação. No que se refere ao comportamento de valores nulos, os métodos de agregação usam a semântica de fonte de dados. Quando valores nulos estão envolvidos, o comportamento dos métodos de agregação pode ser diferente, dependendo da fonte de dados back-end em uso. O comportamento do método de agregação que usa a semântica da fonte de dados também pode ser diferente daquele que é esperado dos métodos CLR. Por exemplo, o comportamento padrão do método `Sum` no SQL Server é ignorar todos os valores nulos, em vez de gerar uma exceção.  
  
 Todas as exceções resultantes de agregação, como um estouro da função `Sum`, são geradas como exceções da fonte de dados ou como exceções de Entity Framework durante a materialização dos resultados da consulta.  
  
 Para esses métodos que envolvem um cálculo em uma sequência, como `Sum` ou `Average`, o cálculo real é efetuado no servidor. Como resultado, podem ocorrer conversões de tipo e perda de precisão no servidor, e os resultados podem diferir daquele que é esperado usando a semântica CLR.  
  
 O comportamento padrão dos métodos de agregação para valores nulos/não nulos é mostrado na seguinte tabela:  
  
|Método|Nenhum dado|Todos os valores nulos|Alguns valores nulos|Nenhum valor nulo|  
|------------|-------------|---------------------|----------------------|--------------------|  
|`Average`|Retorna um valor nulo.|Retorna um valor nulo.|Retorna a média dos valores não nulos em uma sequência.|Computa a média de uma sequência de valores numéricos.|  
|`Count`|Retorna 0|Retorna o número de valores nulos na sequência.|Retorna o número de valores nulos e não nulos na sequência.|Retorna o número de elementos na sequência.|  
|`Max`|Retorna um valor nulo.|Retorna um valor nulo.|Retorna o valor não nulo máximo em uma sequência.|Retorna o valor máximo em uma sequência.|  
|`Min`|Retorna um valor nulo.|Retorna um valor nulo.|Retorna o valor não nulo mínimo em uma sequência.|Retorna o valor mínimo em uma sequência.|  
|`Sum`|Retorna um valor nulo.|Retorna um valor nulo.|Retorna a soma do valor não nulo em uma sequência.|Computa a soma de uma sequência de valores numéricos.|  
  
## <a name="type-methods"></a>Métodos de tipo  
 Há suporte para os dois métodos LINQ que tratam da conversão e do teste de tipos no contexto do [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Isso significa que os únicos tipos com suporte são aqueles que mapeiam para o tipo [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] apropriado. Para obter uma lista desses tipos, consulte [tipos de modelo conceituais (CSDL)](https://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4). Os métodos de tipo são `Convert` e `OfType`.  
  
 Há suporte para `OfType` em tipos de entidade. Há suporte para `Convert` em tipos primitivos de modelo conceitual.  Também há suporte para os métodos C# `is` e `as`.  
  
## <a name="paging-methods"></a>Métodos de paginação  
 Operações de paginação retornam um único elemento ou em vários elementos de uma sequência. Os métodos de paginação com suporte são `First`, `FirstOrDefault`, `Single`, `SingleOrDefault`, `Skip`, e `Take`.  
  
 Um número de métodos de paginação não têm suporte, devido à impossibilidade de mapear funções para a fonte de dados ou à falta de ordenação implícita de conjuntos na fonte de dados. Os métodos que retornam um valor padrão são restritos a tipos primitivos de modelo conceitual e a tipos de referência com valores nulos como padrão. Os métodos de paginação executados em uma sequência vazia retornam nulo.  
  
## <a name="see-also"></a>Consulte também  
 [Métodos LINQ com e sem suporte (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md)  
 [Visão Geral de Operadores de Consulta Padrão](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)

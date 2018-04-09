---
title: Como comparar cadeias de caracteres – Guia do C#
description: Saiba como comparar e ordenar valores de cadeia de caracteres, com ou sem ordem específica de cultura ou de diferenciação entre maiúsculas e minúsculas
ms.date: 03/20/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- strings [C#], comparison
- comparing strings [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3edc1ffdcb4d084f8f76ff27144402fbf98fcbdb
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-compare-strings-in-c"></a>Como comparar cadeias de caracteres no C# #

Você compara cadeias de caracteres para responder uma dessas duas perguntas: "Essas duas cadeias de caracteres são iguais?" ou "Em que ordem essas cadeias de caracteres devem ser colocadas ao classificá-las?"

Essas duas perguntas são complicadas devido a fatores que afetam as comparações de cadeia de caracteres: 
- Você pode escolher uma comparação ordinal ou linguística.
- Você pode escolher se o uso de maiúsculas faz diferença.
- Você pode escolher comparações específicas de cultura.
- As comparações linguísticas são dependentes de plataforma e cultura.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Ao comparar cadeias de caracteres, você pode definir uma ordem entre elas. As comparações são usadas para classificar uma sequência de cadeias de caracteres. Com a sequência em uma ordem conhecida, fica mais fácil de pesquisar, tanto para softwares quanto para os usuários. Outras comparações podem verificar se as cadeias de caracteres são iguais. Essas verificações são semelhantes a igualdade, mas algumas diferenças, como diferenças entre maiúsculas e minúsculas, podem ser ignoradas.

## <a name="default-ordinal-comparisons"></a>Comparações ordinárias padrão

As operações mais comuns, <xref:System.String.CompareTo%2A?displayProperty=nameWithType> e <xref:System.String.Equals%2A?displayProperty=nameWithType> ou <xref:System.String.op_Equality%2A?displayProperty=nameWithType>, usam uma comparação ordinal, uma comparação que diferencia maiúsculas de minúsculas e a cultura atual. Os resultados são mostrados no exemplo a seguir.

[!code-csharp-interactive[Comparing strings using an ordinal comparison](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#1)]

As comparações ordinais não consideram regras linguísticas ao comparar cadeias de caracteres. Elas vão comparar cada caractere das cadeias de caracteres. As comparações que diferenciam letras maiúsculas e minúsculas usam a capitalização em suas comparações. O ponto mais importante sobre esses métodos de comparação padrão é que, como eles usam a cultura atual, os resultados dependem das configurações de idioma e localidade do computador em que são executadas. Essas comparações são inadequadas para comparações em que a ordem deve ser consistente entre computadores ou localidades.

## <a name="case-insensitive-ordinal-comparisons"></a>Comparações ordinais que não diferenciam maiúsculas de minúsculas

O método <xref:System.String.Equals%2A?displayProperty=nameWithType> permite que você especifique um valor <xref:System.StringComparison> de <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> para especificar uma comparação que não diferencia maiúsculas de minúsculas. Também há um método <xref:System.String.Compare%2A> estático que inclui um argumento booliano para especificar comparações que não diferenciam maiúsculas de minúsculas. Eles são mostrados no código a seguir:

[!code-csharp-interactive[Comparing strings ignoring case](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#2)]

## <a name="linguistic-comparisons"></a>Comparações linguísticas

As cadeias de caracteres também podem ser ordenadas usando regras linguísticas para a cultura atual.
Às vezes, isso é conhecido como "ordem de classificação de palavra". Quando você executa uma comparação linguística, alguns caracteres Unicode não alfanuméricos podem ter pesos especiais atribuídos. Por exemplo, o hífen "-" pode ter um peso muito pequeno atribuído, de modo que "co-op" e "coop" apareçam próximos um do outro na ordem de classificação. Além disso, alguns caracteres Unicode podem ser equivalentes a uma sequência de caracteres alfanuméricos. O exemplo a seguir usa a frase "They dance in the street." em alemão com o "ss" e 'ß'. Linguisticamente (no Windows), "ss" é igual ao eszett alemão: caractere 'ß' nas culturas "en-US" e "de-DE". 

[!code-csharp-interactive[Comparing strings using linguistic rules](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#3)]

Este exemplo demonstra a natureza dependente de sistema operacional das comparações linguísticas. O host da janela interativa é um host Linux. As comparações de linguísticas e ordinais produzem os mesmos resultados. Se você executar este mesmo exemplo em um host do Windows, a saída será a seguinte:

```console
<coop> is less than <co-op> using invariant culture
<coop> is greater than <co-op> using ordinal comparison
<coop> is less than <cop> using invariant culture
<coop> is less than <cop> using ordinal comparison
<co-op> is less than <cop> using invariant culture
<co-op> is less than <cop> using ordinal comparison
```

No Windows, a ordem de classificação de "cop", "coop" e "co-op" muda quando você muda de uma comparação linguística para uma comparação ordinal. As duas frases em alemão também são comparadas de forma diferente ao usar os tipos diferentes de comparação.

## <a name="comparisons-using-specific-cultures"></a>Comparações usando culturas específicas

Este exemplo armazena <xref:System.Globalization.CultureInfo> para a cultura atual.
A cultura original pode ser definida e recuperada no objeto de thread atual. As comparações são executadas usando o valor <xref:System.StringComparison.CurrentCulture> para garantir uma comparação específica da cultura.

A cultura usada afeta as comparações linguísticas. O exemplo a seguir mostra os resultados da comparação das duas frases em alemão usando a cultura "en-US" e a cultura "de-DE":

[!code-csharp-interactive[Comparing strings across cultures](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#4)]

As comparações que diferenciam cultura normalmente são usadas para comparar e classificar cadeias de caracteres inseridas por usuários com outras cadeias de caracteres inseridas por usuários. Os caracteres e as convenções de classificação dessas cadeias de caracteres podem variar de acordo com a localidade do computador do usuário. Até mesmo cadeias de caracteres que contêm caracteres idênticos podem ser classificadas de formas diferentes dependendo da cultura do thread atual. Além disso, experimente este código de exemplo localmente em um computador Windows, e você verá os seguintes resultados:

```console
<coop> is less than <co-op> using en-US culture
<coop> is greater than <co-op> using ordinal comparison
<coop> is less than <cop> using en-US culture
<coop> is less than <cop> using ordinal comparison
<co-op> is less than <cop> using en-US culture
<co-op> is less than <cop> using ordinal comparison
```

As comparações linguísticas dependem da cultura atual e são dependentes do SO. Você deve considerar isso ao trabalhar com comparações de cadeia de caracteres.

## <a name="linguistic-sorting-and-searching-strings-in-arrays"></a>Classificação linguística e cadeias de caracteres de pesquisa em matrizes

Os exemplos a seguir mostram como classificar e pesquisar cadeias de caracteres em uma matriz usando uma comparação linguística que depende da cultura atual. Use os métodos <xref:System.Array> estáticos que aceitam um parâmetro <xref:System.StringComparer?displayProperty=nameWithType>.

Este exemplo mostra como classificar uma matriz de cadeias de caracteres usando a cultura atual: 

[!code-csharp-interactive[Sorting an array of strings](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#5)]

Depois que a matriz é classificada, você pode procurar as entradas usando uma pesquisa binária. Uma pesquisa binária é iniciada no meio da coleção para determinar qual metade da coleção contém a cadeia de caracteres procurada. Cada comparação subsequente subdivide a parte restante da coleção na metade.  A matriz é classificada usando <xref:System.StringComparer.CurrentCulture?displayProperty=nameWithType>. A função local `ShowWhere` exibe informações sobre o local em que a cadeia de caracteres foi encontrada. Se a cadeia de caracteres não for encontrada, o valor retornado indicará o local em que estaria se fosse encontrada.

[!code-csharp-interactive[Searching in a sorted array](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#6)]

## <a name="ordinal-sorting-and-searching-in-collections"></a>Classificação ordinal e pesquisa em coleções

O código a seguir usa a classe de coleção <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> para armazenar cadeias de caracteres. As cadeias de caracteres são classificadas usando o método <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType>. Esse método precisa de um delegado que compara e ordena as duas cadeias de caracteres. O método <xref:System.String.CompareTo%2A?displayProperty=nameWithType> fornece essa função de comparação. Execute o exemplo e observe a ordem. Essa operação de classificação usa uma classificação ordinal que diferencia maiúsculas e minúsculas. Você usaria os métodos <xref:System.String.Compare%2A?displayProperty=nameWithType> estáticos para especificar regras de comparação diferentes.

[!code-csharp-interactive[Sorting a list of strings](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#7)]

Uma vez classificada, a lista de cadeias de caracteres pode ser pesquisada usando uma pesquisa binária. O exemplo a seguir mostra como pesquisar a lista classificada usando a mesma função de comparação. A função local `ShowWhere` mostra o local em que o texto procurado está ou deveria estar:

[!code-csharp-interactive[csProgGuideStrings#11](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#8)]

Use sempre o mesmo tipo de comparação para classificação e pesquisa. O uso de tipos diferentes de comparação para classificação e pesquisa produz resultados inesperados. 

Classes de coleção como <xref:System.Collections.Hashtable?displayProperty=nameWithType>, <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> e <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> têm construtores que usam um parâmetro <xref:System.StringComparer?displayProperty=nameWithType> quando o tipo dos elementos ou chaves é `string`. Em geral, você deve usar esses construtores sempre que possível e especificar <xref:System.StringComparer.Ordinal?displayProperty=nameWithType> ou <xref:System.StringComparer.OrdinalIgnoreCase?displayProperty=nameWithType>.

## <a name="reference-equality-and-string-interning"></a>Igualdade de referência e centralização de cadeia de caracteres

Nenhum dos exemplos usou <xref:System.Object.ReferenceEquals%2A>. Este método determina se duas cadeias de caracteres são o mesmo objeto. Isso pode levar a resultados inconsistentes em comparações de cadeia de caracteres. O exemplo a seguir demonstra o recurso de *centralização da cadeia de caracteres* do C#. Quando um programa declara duas ou mais variáveis de cadeia de caracteres idênticas, o compilador armazena todas no mesmo local. Chamando o método <xref:System.Object.ReferenceEquals%2A>, você pode ver que as duas cadeias de caracteres na verdade se referem ao mesmo objeto na memória. Use o método <xref:System.String.Copy%2A?displayProperty=nameWithType> para evitar a centralização. Depois que a cópia for feita, as duas cadeias de caracteres terão locais de armazenamento diferentes, mesmo que tenham o mesmo valor. Execute o exemplo a seguir para mostrar que as cadeias de caracteres `a` e `b` são *centralizadas*, ou seja, que elas compartilham o mesmo armazenamento. As cadeias de caracteres `a` e `c` não são.

[!code-csharp-interactive[Demonstrating string interning](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#9)]

> [!NOTE]
> Quando você testa cadeias de caracteres quanto a igualdade, é necessário usar os métodos que especificam explicitamente o tipo de comparação que você pretende executar. O código fica muito mais legível e fácil de manter. Use as sobrecargas dos métodos das classes <xref:System.String?displayProperty=nameWithType> e <xref:System.Array?displayProperty=nameWithType> que aceitam um parâmetro de enumeração <xref:System.StringComparison>. Você especifica o tipo de comparação a ser executado. Evite usar os operadores `==` e `!=` ao testar a igualdade. Os métodos de instância <xref:System.String.CompareTo%2A?displayProperty=nameWithType> sempre executam uma comparação ordinal que diferencia maiúsculas de minúsculas. Basicamente, eles são adequados para colocar cadeias de caracteres em ordem alfabética.

## <a name="see-also"></a>Consulte também
 <xref:System.Globalization.CultureInfo?displayProperty=nameWithType>  
 <xref:System.StringComparer?displayProperty=nameWithType>  
 [Cadeias de Caracteres](../programming-guide/strings/index.md)  
 [Comparação de cadeias de caracteres](../../standard/base-types/comparing.md)  
 [Globalizando e localizando aplicativos](/visualstudio/ide/globalizing-and-localizing-applications)
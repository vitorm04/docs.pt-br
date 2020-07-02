---
title: Escolhendo entre tipos anônimos e de tupla
description: Saiba quando é apropriado escolher entre tipos anônimos e tipo de tupla.
ms.date: 06/29/2020
ms.technology: dotnet-standard
ms.openlocfilehash: bc17695830a42a6eed9d60c0e097ee9d02a7957e
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803762"
---
# <a name="choosing-between-anonymous-and-tuple-types"></a>Escolhendo entre tipos anônimos e de tupla

Escolher o tipo apropriado envolve considerar sua usabilidade, desempenho e compensações em comparação com outros tipos. Os tipos anônimos estão disponíveis desde o C# 3,0, enquanto os <xref:System.Tuple%602?displayProperty=nameWithType> tipos genéricos foram introduzidos com .NET Framework 4,0. Desde então, novas opções foram introduzidas com suporte de nível de idioma, como <xref:System.ValueTuple%602?displayProperty=nameWithType> -que como o nome sugere, forneça um tipo de valor com a flexibilidade de tipos anônimos. Neste artigo, você aprenderá quando for apropriado escolher um tipo no outro.

## <a name="usability-and-functionality"></a>Usabilidade e funcionalidade

Os tipos anônimos foram introduzidos em C# 3,0 com expressões LINQ (consulta integrada à linguagem). Com o LINQ, os desenvolvedores geralmente projetam resultados de consultas em tipos anônimos que contêm algumas propriedades Select dos objetos com os quais estão trabalhando. Considere o exemplo a seguir, que instancia uma matriz de <xref:System.DateTime> objetos e itera através deles projetando em um tipo anônimo com duas propriedades.

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var anonymous in
             dates.Select(
                 date => new { Formatted = $"{date:MMM dd, yyyy hh:mm zzz}", date.Ticks }))
{
    Console.WriteLine($"Ticks: {anonymous.Ticks}, formatted: {anonymous.Formatted}");
}
```

Os tipos anônimos são instanciados usando o [`new`](../../csharp/language-reference/operators/new-operator.md) operador, e os nomes e tipos de propriedade são inferidos da declaração. Se dois ou mais inicializadores de objeto anônimo no mesmo assembly especificarem uma sequência de propriedades que estão na mesma ordem e que têm os mesmos nomes e tipos, o compilador tratará os objetos como instâncias do mesmo tipo. Eles compartilham o mesmo tipo de informação gerado pelo compilador.

O trecho C# anterior projeta um tipo anônimo com duas propriedades, assim como a seguinte classe C# gerada pelo compilador:

```csharp
internal sealed class f__AnonymousType0
{
    public string Formatted { get; }
    public long Ticks { get; }

    public f__AnonymousType0(string formatted, long ticks)
    {
        Formatted = formatted;
        Ticks = ticks;
    }
}
```

Para obter mais informações, consulte [tipos anônimos](../../csharp/programming-guide/classes-and-structs/anonymous-types.md). A mesma funcionalidade existe com tuplas ao projetar em consultas LINQ, você pode selecionar propriedades em tuplas. Essas tuplas fluem pela consulta, assim como os tipos anônimos. Agora, considere o exemplo a seguir usando o `System.Tuple<string, long>` .

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var tuple in
            dates.Select(
                date => new Tuple<string, long>($"{date:MMM dd, yyyy hh:mm zzz}", date.Ticks)))
{
    Console.WriteLine($"Ticks: {tuple.Item2}, formatted: {tuple.Item1}");
}
```

Com o <xref:System.Tuple%602?displayProperty=nameWithType> , a instância expõe as propriedades de item numeradas, como `Item1` e `Item2` . Esses nomes de propriedade podem dificultar a compreensão da intenção dos valores de propriedade, uma vez que o nome da propriedade fornece apenas o ordinal. Além disso, os `System.Tuple` tipos são `class` tipos de referência. <xref:System.ValueTuple%602?displayProperty=nameWithType>No entanto, é um `struct` tipo de valor. O trecho de código C# a seguir usa o `ValueTuple<string, long>` para projetar no. Ao fazer isso, ele atribui usando uma sintaxe literal.

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var (formatted, ticks) in
            dates.Select(
                date => (Formatted: $"{date:MMM dd, yyyy at hh:mm zzz}", date.Ticks)))
{
    Console.WriteLine($"Ticks: {ticks}, formatted: {formatted}");
}
```

O C# fornece suporte a idiomas de tuplas com o <xref:System.ValueTuple> tipo e a semântica para:

- [Atribuição de tupla](../../csharp/tuples.md#assignment-and-tuples)
- [Desconstrução de tupla](../../csharp/deconstruct.md) (não limitada a tuplas)
- [Verificações de igualdade de tupla](../../csharp/tuples.md#equality-and-tuples)
- [Inicializadores de projeção de tupla](../../csharp/tuples.md#tuple-projection-initializers)

No entanto, os exemplos anteriores são funcionalmente equivalentes; Há pequenas diferenças na usabilidade e nas implementações subjacentes.

## <a name="tradeoffs"></a>Compensações

Você talvez queira sempre usar os <xref:System.ValueTuple> <xref:System.Tuple> tipos anônimos e próprios, mas há compensações que você deve considerar. Os <xref:System.ValueTuple> tipos são mutáveis, enquanto <xref:System.Tuple> são somente leitura. Tipos anônimos podem ser usados em árvores de expressão, enquanto as tuplas não podem. A tabela a seguir é uma visão geral de algumas das principais diferenças.

### <a name="key-differences"></a>Principais diferenças

| Name                     | Modificador de acesso | Type     | Nome da propriedade personalizada | Suporte à desconstrução | Suporte à árvore de expressões |
|--------------------------|-----------------|----------|----------------------|------------------------|-------------------------|
| Tipos anônimos          | `internal`      | `class`  | ✔️                   | ❌                     | ✔️                     |
| <xref:System.Tuple>      | `public`        | `class`  | ❌                   | ❌                     | ✔️                     |
| <xref:System.ValueTuple> | `public`        | `struct` | ✔️                   | ✔️                     | ❌                     |

### <a name="serialization"></a>Serialização

Uma consideração importante ao escolher um tipo, é se ele precisará ser serializado ou não. A serialização é o processo de conversão do estado de um objeto em um formulário que possa ser persistido ou transportado. Para obter mais informações, consulte [serialização](../../csharp/programming-guide/concepts/serialization/index.md). Quando a serialização é importante, a criação de uma `class` ou `struct` é preferida sobre tipos anônimos ou tipos de tupla.

## <a name="performance"></a>Desempenho

O desempenho entre esses tipos depende do cenário. O grande impacto envolve a compensação entre as alocações e a cópia. Na maioria dos cenários, o impacto é pequeno. Quando os principais impactos podem surgir, as medidas devem ser tomadas para informar a decisão.

## <a name="conclusion"></a>Conclusão

Como um desenvolvedor escolhendo entre tuplas e tipos anônimos, há vários fatores a serem considerados. Em termos gerais, se você não estiver trabalhando com [árvores de expressão](../../csharp/expression-trees.md)e estiver familiarizado com a sintaxe de tupla, escolha <xref:System.ValueTuple> como elas fornecem um tipo de valor com a flexibilidade para nomear Propriedades. Se você estiver trabalhando com árvores de expressão e preferir nomear Propriedades, escolha tipos anônimos. Caso contrário, use <xref:System.Tuple>.

## <a name="see-also"></a>Consulte também

- [Tipos anônimos](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [Árvores de expressão](../../csharp/expression-trees.md)
- [Diretrizes de design de estrutura](index.md)
- [Tipos de tupla](../../csharp/tuples.md)
- [Diretrizes de design de tipo](type.md)

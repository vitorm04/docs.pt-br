---
ms.openlocfilehash: f131933f3cf7890939854c46f115e8deb8da1cc2
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888158"
---
### <a name="stringinfo-and-textelementenumerator-are-now-uax29-compliant"></a>StringInfo e TextElementEnumerator agora estão compatíveis com uax29

Antes desta <xref:System.Globalization.StringInfo?displayProperty=fullName> mudança, <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> e não manuseou corretamente todos os clusters de grafeme. Alguns grafemes foram divididos em seus componentes constituintes em vez de serem mantidos juntos. Agora, <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> e processe clusters de grafeme de acordo com a versão mais recente do Padrão Unicode.

Além disso, <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> o método, que inverte os caracteres em uma seqüência no Visual Basic, agora também segue o padrão Unicode para clusters de grafeme.

#### <a name="change-description"></a>Descrição da alteração

Um [grapheme](https://www.unicode.org/glossary/#grapheme) gráfico ou [um cluster de grafeme estendido](https://www.unicode.org/glossary/#extended_grapheme_cluster) é um único caractere percebido pelo usuário que pode ser composto de vários pontos de código Unicode. Por exemplo, a seqüência contendo o:::no-loc text="กำ":::caractere tailandês "kam" () consiste nos seguintes dois caracteres:

- :::no-loc text="ก":::(= \u0e01') PERSONAGEM TAILANDÊS KO KAI
- :::no-loc text=" ำ":::(= \u0e33') PERSONAGEM TAILANDESA SARA AM

Quando exibido ao usuário, o sistema operacional combina os dois caracteres para formar o caractere :::no-loc text="กำ":::de exibição único (ou grafeme) "kam" ou . Emoji também pode consistir de vários caracteres que são combinados para exibição de forma semelhante.

> [!TIP]
> A documentação .NET às vezes usa o termo "elemento texto" quando se refere a um grafeme.

As <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> classes e as classes inspecionam as cordas e retornam informações sobre os grafemes que contêm. No .NET Framework (todas as versões) e no .NET Core 3.x e anteriormente, essas duas classes usam lógica personalizada que lida com algumas classes combinadas, mas não está totalmente em conformidade com o [Padrão Unicode](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries). Por exemplo, <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> as classes e as classes dividem incorretamente o único caractere tailandês "kam" de volta em seus componentes constituintes em vez de mantê-los juntos. Essas classes também dividiram incorretamente o caractere emoji "🤷🏽 ♀️" em quatro clusters (pessoa encolhendo os ombros, modificador de tom de pele, modificador de gênero e um combinador invisível) em vez de mantê-los juntos como um único cluster de grafeme.

A partir de .NET 5, as <xref:System.Globalization.StringInfo> classes e as <xref:System.Globalization.TextElementEnumerator> classes implementam o padrão Unicode conforme definido pelo Anexo [ \#Padrão Unicode 29, rev. 35, seg. 3](https://www.unicode.org/reports/tr29/tr29-35.html). Em particular, eles agora retornam [clusters de grafeme estendidos](https://www.unicode.org/glossary/#extended_grapheme_cluster) para todas as classes combinadas.

Considere o seguinte código C#:

```cs
using System.Globalization;

static void Main(string[] args)
{
    PrintGraphemes("กำ");
    PrintGraphemes("🤷🏽‍♀️");
}

static void PrintGraphemes(string str)
{
    Console.WriteLine($"Printing graphemes of \"{str}\"...");
    int i = 0;

    TextElementEnumerator enumerator = StringInfo.GetTextElementEnumerator(str);
    while (enumerator.MoveNext())
    {
        Console.WriteLine($"Grapheme {++i}: \"{enumerator.Current}\"");
    }

    Console.WriteLine($"({i} grapheme(s) total.)");
    Console.WriteLine();
}
```

Nas versões .NET Framework e .NET Core 3.x e anteriores, os grafemes são divididos e a saída do console é a seguinte:

```txt
Printing graphemes of "กำ"...
Grapheme 1: "ก"
Grapheme 2: "ำ"
(2 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷"
Grapheme 2: "🏽"
Grapheme 3: "‍"
Grapheme 4: "♀️"
(4 grapheme(s) total.)
```

Nas versões .NET 5 e posteriores, os grafemes são mantidos juntos, e a saída do console é a seguinte:

```txt
Printing graphemes of "กำ"...
Grapheme 1: "กำ"
(1 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷🏽‍♀️"
(1 grapheme(s) total.)
```

Além disso, a partir de <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> .NET 5, o método, que inverte os caracteres em uma seqüência no Visual Basic, agora também segue o padrão Unicode para clusters de grafeme.

Essas alterações fazem parte de um conjunto mais amplo de melhorias Unicode e UTF-8 no .NET, incluindo uma API de enumeração <xref:System.Text.Rune?displayProperty=fullName> de cluster de grafeme estendida para complementar as APIs de enumeração de valor escalar unicode que foram introduzidas com o tipo no .NET Core 3.0.

#### <a name="version-introduced"></a>Versão introduzida

.NET 5.0 Visualização 1

### <a name="recommended-action"></a>Ação recomendada

Você não precisa realizar nenhuma ação. Seus aplicativos se comportarão automaticamente de forma mais compatível com os padrões em uma variedade de cenários relacionados à globalização.

### <a name="category"></a>Categoria

Globalização

### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Globalization.StringInfo?displayProperty=fullName>
- <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName>
- <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>

<!--

- `T:System.Globalization.StringInfo`
- `T:System.Globalization.TextElementEnumerator`
- `Overload:Microsoft.VisualBasic.Strings.StrReverse`

-->

---
ms.openlocfilehash: f131933f3cf7890939854c46f115e8deb8da1cc2
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888158"
---
### <a name="stringinfo-and-textelementenumerator-are-now-uax29-compliant"></a><span data-ttu-id="bc8ae-101">StringInfo e TextElementEnumerator agora estão compatíveis com uax29</span><span class="sxs-lookup"><span data-stu-id="bc8ae-101">StringInfo and TextElementEnumerator are now UAX29-compliant</span></span>

<span data-ttu-id="bc8ae-102">Antes desta <xref:System.Globalization.StringInfo?displayProperty=fullName> mudança, <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> e não manuseou corretamente todos os clusters de grafeme.</span><span class="sxs-lookup"><span data-stu-id="bc8ae-102">Prior to this change, <xref:System.Globalization.StringInfo?displayProperty=fullName> and <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> didn't properly handle all grapheme clusters.</span></span> <span data-ttu-id="bc8ae-103">Alguns grafemes foram divididos em seus componentes constituintes em vez de serem mantidos juntos.</span><span class="sxs-lookup"><span data-stu-id="bc8ae-103">Some graphemes were split into their constituent components instead of being kept together.</span></span> <span data-ttu-id="bc8ae-104">Agora, <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> e processe clusters de grafeme de acordo com a versão mais recente do Padrão Unicode.</span><span class="sxs-lookup"><span data-stu-id="bc8ae-104">Now, <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> process grapheme clusters according to the latest version of the Unicode Standard.</span></span>

<span data-ttu-id="bc8ae-105">Além disso, <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> o método, que inverte os caracteres em uma seqüência no Visual Basic, agora também segue o padrão Unicode para clusters de grafeme.</span><span class="sxs-lookup"><span data-stu-id="bc8ae-105">In addition, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

#### <a name="change-description"></a><span data-ttu-id="bc8ae-106">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="bc8ae-106">Change description</span></span>

<span data-ttu-id="bc8ae-107">Um [grapheme](https://www.unicode.org/glossary/#grapheme) gráfico ou [um cluster de grafeme estendido](https://www.unicode.org/glossary/#extended_grapheme_cluster) é um único caractere percebido pelo usuário que pode ser composto de vários pontos de código Unicode.</span><span class="sxs-lookup"><span data-stu-id="bc8ae-107">A [grapheme](https://www.unicode.org/glossary/#grapheme) or [extended grapheme cluster](https://www.unicode.org/glossary/#extended_grapheme_cluster) is a single user-perceived character that may be made up of multiple Unicode code points.</span></span> <span data-ttu-id="bc8ae-108">Por exemplo, a seqüência contendo o:::no-loc text="กำ":::caractere tailandês "kam" () consiste nos seguintes dois caracteres:</span><span class="sxs-lookup"><span data-stu-id="bc8ae-108">For example, the string containing the Thai character "kam" (:::no-loc text="กำ":::) consists of the following two characters:</span></span>

- <span data-ttu-id="bc8ae-109">:::no-loc text="ก":::(= \u0e01') PERSONAGEM TAILANDÊS KO KAI</span><span class="sxs-lookup"><span data-stu-id="bc8ae-109">:::no-loc text="ก"::: (= '\u0e01') THAI CHARACTER KO KAI</span></span>
- <span data-ttu-id="bc8ae-110">:::no-loc text=" ำ":::(= \u0e33') PERSONAGEM TAILANDESA SARA AM</span><span class="sxs-lookup"><span data-stu-id="bc8ae-110">:::no-loc text=" ำ"::: (= '\u0e33') THAI CHARACTER SARA AM</span></span>

<span data-ttu-id="bc8ae-111">Quando exibido ao usuário, o sistema operacional combina os dois caracteres para formar o caractere :::no-loc text="กำ":::de exibição único (ou grafeme) "kam" ou .</span><span class="sxs-lookup"><span data-stu-id="bc8ae-111">When displayed to the user, the operating system combines the two characters to form the single display character (or grapheme) "kam" or :::no-loc text="กำ":::.</span></span> <span data-ttu-id="bc8ae-112">Emoji também pode consistir de vários caracteres que são combinados para exibição de forma semelhante.</span><span class="sxs-lookup"><span data-stu-id="bc8ae-112">Emoji can also consist of multiple characters that are combined for display in a similar way.</span></span>

> [!TIP]
> <span data-ttu-id="bc8ae-113">A documentação .NET às vezes usa o termo "elemento texto" quando se refere a um grafeme.</span><span class="sxs-lookup"><span data-stu-id="bc8ae-113">The .NET documentation sometimes uses the term "text element" when referring to a grapheme.</span></span>

<span data-ttu-id="bc8ae-114">As <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> classes e as classes inspecionam as cordas e retornam informações sobre os grafemes que contêm.</span><span class="sxs-lookup"><span data-stu-id="bc8ae-114">The <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes inspect strings and return information about the graphemes they contain.</span></span> <span data-ttu-id="bc8ae-115">No .NET Framework (todas as versões) e no .NET Core 3.x e anteriormente, essas duas classes usam lógica personalizada que lida com algumas classes combinadas, mas não está totalmente em conformidade com o [Padrão Unicode](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries).</span><span class="sxs-lookup"><span data-stu-id="bc8ae-115">In .NET Framework (all versions) and .NET Core 3.x and earlier, these two classes use custom logic that handles some combining classes but doesn't fully comply with the [Unicode Standard](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries).</span></span> <span data-ttu-id="bc8ae-116">Por exemplo, <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> as classes e as classes dividem incorretamente o único caractere tailandês "kam" de volta em seus componentes constituintes em vez de mantê-los juntos.</span><span class="sxs-lookup"><span data-stu-id="bc8ae-116">For example, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes incorrectly split the single Thai character "kam" back into its constituent components instead of keeping them together.</span></span> <span data-ttu-id="bc8ae-117">Essas classes também dividiram incorretamente o caractere emoji "🤷🏽 ♀️" em quatro clusters (pessoa encolhendo os ombros, modificador de tom de pele, modificador de gênero e um combinador invisível) em vez de mantê-los juntos como um único cluster de grafeme.</span><span class="sxs-lookup"><span data-stu-id="bc8ae-117">These classes also incorrectly split the emoji character "🤷🏽‍♀️" into four clusters (person shrugging, skin tone modifier, gender modifier, and an invisible combiner) instead of keeping them together as a single grapheme cluster.</span></span>

<span data-ttu-id="bc8ae-118">A partir de .NET 5, as <xref:System.Globalization.StringInfo> classes e as <xref:System.Globalization.TextElementEnumerator> classes implementam o padrão Unicode conforme definido pelo Anexo [ \#Padrão Unicode 29, rev. 35, seg. 3](https://www.unicode.org/reports/tr29/tr29-35.html).</span><span class="sxs-lookup"><span data-stu-id="bc8ae-118">Starting with .NET 5, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes implement the Unicode standard as defined by [Unicode Standard Annex \#29, rev. 35, sec. 3](https://www.unicode.org/reports/tr29/tr29-35.html).</span></span> <span data-ttu-id="bc8ae-119">Em particular, eles agora retornam [clusters de grafeme estendidos](https://www.unicode.org/glossary/#extended_grapheme_cluster) para todas as classes combinadas.</span><span class="sxs-lookup"><span data-stu-id="bc8ae-119">In particular, they now return [extended grapheme clusters](https://www.unicode.org/glossary/#extended_grapheme_cluster) for all combining classes.</span></span>

<span data-ttu-id="bc8ae-120">Considere o seguinte código C#:</span><span class="sxs-lookup"><span data-stu-id="bc8ae-120">Consider the following C# code:</span></span>

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

<span data-ttu-id="bc8ae-121">Nas versões .NET Framework e .NET Core 3.x e anteriores, os grafemes são divididos e a saída do console é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="bc8ae-121">In .NET Framework and .NET Core 3.x and earlier versions, the graphemes are split up, and the console output is as follows:</span></span>

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

<span data-ttu-id="bc8ae-122">Nas versões .NET 5 e posteriores, os grafemes são mantidos juntos, e a saída do console é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="bc8ae-122">In .NET 5 and later versions, the graphemes are kept together, and the console output is as follows:</span></span>

```txt
Printing graphemes of "กำ"...
Grapheme 1: "กำ"
(1 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷🏽‍♀️"
(1 grapheme(s) total.)
```

<span data-ttu-id="bc8ae-123">Além disso, a partir de <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> .NET 5, o método, que inverte os caracteres em uma seqüência no Visual Basic, agora também segue o padrão Unicode para clusters de grafeme.</span><span class="sxs-lookup"><span data-stu-id="bc8ae-123">In addition, starting in .NET 5, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

<span data-ttu-id="bc8ae-124">Essas alterações fazem parte de um conjunto mais amplo de melhorias Unicode e UTF-8 no .NET, incluindo uma API de enumeração <xref:System.Text.Rune?displayProperty=fullName> de cluster de grafeme estendida para complementar as APIs de enumeração de valor escalar unicode que foram introduzidas com o tipo no .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="bc8ae-124">These changes are part of a wider set of Unicode and UTF-8 improvements in .NET, including an extended grapheme cluster enumeration API to complement the Unicode scalar-value enumeration APIs that were introduced with the <xref:System.Text.Rune?displayProperty=fullName> type in .NET Core 3.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bc8ae-125">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="bc8ae-125">Version introduced</span></span>

<span data-ttu-id="bc8ae-126">.NET 5.0 Visualização 1</span><span class="sxs-lookup"><span data-stu-id="bc8ae-126">.NET 5.0 Preview 1</span></span>

### <a name="recommended-action"></a><span data-ttu-id="bc8ae-127">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="bc8ae-127">Recommended action</span></span>

<span data-ttu-id="bc8ae-128">Você não precisa realizar nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="bc8ae-128">You don't need to take any action.</span></span> <span data-ttu-id="bc8ae-129">Seus aplicativos se comportarão automaticamente de forma mais compatível com os padrões em uma variedade de cenários relacionados à globalização.</span><span class="sxs-lookup"><span data-stu-id="bc8ae-129">Your apps will automatically behave in a more standards-compliant manner in a variety of globalization-related scenarios.</span></span>

### <a name="category"></a><span data-ttu-id="bc8ae-130">Categoria</span><span class="sxs-lookup"><span data-stu-id="bc8ae-130">Category</span></span>

<span data-ttu-id="bc8ae-131">Globalização</span><span class="sxs-lookup"><span data-stu-id="bc8ae-131">Globalization</span></span>

### <a name="affected-apis"></a><span data-ttu-id="bc8ae-132">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="bc8ae-132">Affected APIs</span></span>

- <xref:System.Globalization.StringInfo?displayProperty=fullName>
- <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName>
- <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>

<!--

- `T:System.Globalization.StringInfo`
- `T:System.Globalization.TextElementEnumerator`
- `Overload:Microsoft.VisualBasic.Strings.StrReverse`

-->

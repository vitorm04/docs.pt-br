---
ms.openlocfilehash: 70b71fc55f76514dd17e5b9ba0e76151a966eebb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539431"
---
### <a name="stringinfo-and-textelementenumerator-are-now-uax29-compliant"></a><span data-ttu-id="91c01-101">StringInfo e TextElementEnumerator agora são compatíveis com UAX29</span><span class="sxs-lookup"><span data-stu-id="91c01-101">StringInfo and TextElementEnumerator are now UAX29-compliant</span></span>

<span data-ttu-id="91c01-102">Antes dessa alteração, <xref:System.Globalization.StringInfo?displayProperty=fullName> e <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> não tratamos adequadamente de todos os clusters do grafemas.</span><span class="sxs-lookup"><span data-stu-id="91c01-102">Prior to this change, <xref:System.Globalization.StringInfo?displayProperty=fullName> and <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> didn't properly handle all grapheme clusters.</span></span> <span data-ttu-id="91c01-103">Algumas graphemes foram divididas em seus componentes constituintes em vez de serem mantidas juntas.</span><span class="sxs-lookup"><span data-stu-id="91c01-103">Some graphemes were split into their constituent components instead of being kept together.</span></span> <span data-ttu-id="91c01-104">Agora, <xref:System.Globalization.StringInfo> e <xref:System.Globalization.TextElementEnumerator> processe os clusters grafemas de acordo com a versão mais recente do padrão Unicode.</span><span class="sxs-lookup"><span data-stu-id="91c01-104">Now, <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> process grapheme clusters according to the latest version of the Unicode Standard.</span></span>

<span data-ttu-id="91c01-105">Além disso, o <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> método, que reverte os caracteres em uma cadeia de caracteres em Visual Basic, agora também segue o padrão Unicode para clusters grafemas.</span><span class="sxs-lookup"><span data-stu-id="91c01-105">In addition, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

#### <a name="change-description"></a><span data-ttu-id="91c01-106">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="91c01-106">Change description</span></span>

<span data-ttu-id="91c01-107">Um cluster [grafemas](https://www.unicode.org/glossary/#grapheme) ou [grafemas estendido](https://www.unicode.org/glossary/#extended_grapheme_cluster) é um único caractere percebido pelo usuário que pode ser composto por vários pontos de código Unicode.</span><span class="sxs-lookup"><span data-stu-id="91c01-107">A [grapheme](https://www.unicode.org/glossary/#grapheme) or [extended grapheme cluster](https://www.unicode.org/glossary/#extended_grapheme_cluster) is a single user-perceived character that may be made up of multiple Unicode code points.</span></span> <span data-ttu-id="91c01-108">Por exemplo, a cadeia de caracteres que contém o caractere Tai "Kam" ( :::no-loc text="กำ"::: ) consiste nos dois caracteres a seguir:</span><span class="sxs-lookup"><span data-stu-id="91c01-108">For example, the string containing the Thai character "kam" (:::no-loc text="กำ":::) consists of the following two characters:</span></span>

- <span data-ttu-id="91c01-109">:::no-loc text="ก"::: (= ' \u0e01 ') CARACTERE TAI KO KAI</span><span class="sxs-lookup"><span data-stu-id="91c01-109">:::no-loc text="ก"::: (= '\u0e01') THAI CHARACTER KO KAI</span></span>
- <span data-ttu-id="91c01-110">:::no-loc text=" ำ"::: (= ' \u0e33 ') CARACTERE TAI SARA AM</span><span class="sxs-lookup"><span data-stu-id="91c01-110">:::no-loc text=" ำ"::: (= '\u0e33') THAI CHARACTER SARA AM</span></span>

<span data-ttu-id="91c01-111">Quando exibido para o usuário, o sistema operacional combina os dois caracteres para formar o único caractere de exibição (ou grafemas) "Kam" ou :::no-loc text="กำ"::: .</span><span class="sxs-lookup"><span data-stu-id="91c01-111">When displayed to the user, the operating system combines the two characters to form the single display character (or grapheme) "kam" or :::no-loc text="กำ":::.</span></span> <span data-ttu-id="91c01-112">O emoji também pode consistir em vários caracteres que são combinados para exibição de forma semelhante.</span><span class="sxs-lookup"><span data-stu-id="91c01-112">Emoji can also consist of multiple characters that are combined for display in a similar way.</span></span>

> [!TIP]
> <span data-ttu-id="91c01-113">A documentação do .NET às vezes usa o termo "elemento de texto" ao fazer referência a um grafemas.</span><span class="sxs-lookup"><span data-stu-id="91c01-113">The .NET documentation sometimes uses the term "text element" when referring to a grapheme.</span></span>

<span data-ttu-id="91c01-114">As <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> classes e inspecionam cadeias de caracteres e retornam informações sobre as graphemes que elas contêm.</span><span class="sxs-lookup"><span data-stu-id="91c01-114">The <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes inspect strings and return information about the graphemes they contain.</span></span> <span data-ttu-id="91c01-115">No .NET Framework (todas as versões) e no .NET Core 3. x e versões anteriores, essas duas classes usam lógica personalizada que lida com algumas classes combinadoras, mas que não está totalmente em conformidade com o [padrão Unicode](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries).</span><span class="sxs-lookup"><span data-stu-id="91c01-115">In .NET Framework (all versions) and .NET Core 3.x and earlier, these two classes use custom logic that handles some combining classes but doesn't fully comply with the [Unicode Standard](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries).</span></span> <span data-ttu-id="91c01-116">Por exemplo, as <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> classes e dividem incorretamente o caractere Tai único "Kam" de volta em seus componentes constituintes em vez de mantê-los juntos.</span><span class="sxs-lookup"><span data-stu-id="91c01-116">For example, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes incorrectly split the single Thai character "kam" back into its constituent components instead of keeping them together.</span></span> <span data-ttu-id="91c01-117">Essas classes também dividem incorretamente o caractere de Emoji "🤷🏽 ♀️" em quatro clusters (pessoa shrugging, modificador de Tom de pele, modificador de sexo e um combinador invisível) em vez de mantê-los juntos como um único cluster grafemas.</span><span class="sxs-lookup"><span data-stu-id="91c01-117">These classes also incorrectly split the emoji character "🤷🏽‍♀️" into four clusters (person shrugging, skin tone modifier, gender modifier, and an invisible combiner) instead of keeping them together as a single grapheme cluster.</span></span>

<span data-ttu-id="91c01-118">A partir do .NET 5, <xref:System.Globalization.StringInfo> as <xref:System.Globalization.TextElementEnumerator> classes e implementam o padrão Unicode conforme definido pelo [anexo 29 do padrão Unicode \# , Rev. 35, seg. 3](https://www.unicode.org/reports/tr29/tr29-35.html).</span><span class="sxs-lookup"><span data-stu-id="91c01-118">Starting with .NET 5, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes implement the Unicode standard as defined by [Unicode Standard Annex \#29, rev. 35, sec. 3](https://www.unicode.org/reports/tr29/tr29-35.html).</span></span> <span data-ttu-id="91c01-119">Em particular, eles agora retornam [clusters grafemas estendidos](https://www.unicode.org/glossary/#extended_grapheme_cluster) para todas as classes combinadas.</span><span class="sxs-lookup"><span data-stu-id="91c01-119">In particular, they now return [extended grapheme clusters](https://www.unicode.org/glossary/#extended_grapheme_cluster) for all combining classes.</span></span>

<span data-ttu-id="91c01-120">Considere o seguinte código C#:</span><span class="sxs-lookup"><span data-stu-id="91c01-120">Consider the following C# code:</span></span>

```csharp
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

<span data-ttu-id="91c01-121">No .NET Framework e no .NET Core 3. x e versões anteriores, os graphemes são divididos e a saída do console é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="91c01-121">In .NET Framework and .NET Core 3.x and earlier versions, the graphemes are split up, and the console output is as follows:</span></span>

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

<span data-ttu-id="91c01-122">No .NET 5 e versões posteriores, os graphemes são mantidos juntos e a saída do console é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="91c01-122">In .NET 5 and later versions, the graphemes are kept together, and the console output is as follows:</span></span>

```txt
Printing graphemes of "กำ"...
Grapheme 1: "กำ"
(1 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷🏽‍♀️"
(1 grapheme(s) total.)
```

<span data-ttu-id="91c01-123">Além disso, a partir do .NET 5, o <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> método, que reverte os caracteres em uma cadeia de caracteres em Visual Basic, agora também segue o padrão Unicode para clusters grafemas.</span><span class="sxs-lookup"><span data-stu-id="91c01-123">In addition, starting in .NET 5, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

<span data-ttu-id="91c01-124">Essas alterações fazem parte de um conjunto mais amplo de aprimoramentos de Unicode e UTF-8 no .NET, incluindo uma API de enumeração de cluster grafemas estendida para complementar as APIs de enumeração de valor escalar Unicode que foram introduzidas com o <xref:System.Text.Rune?displayProperty=fullName> tipo no .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="91c01-124">These changes are part of a wider set of Unicode and UTF-8 improvements in .NET, including an extended grapheme cluster enumeration API to complement the Unicode scalar-value enumeration APIs that were introduced with the <xref:System.Text.Rune?displayProperty=fullName> type in .NET Core 3.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="91c01-125">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="91c01-125">Version introduced</span></span>

<span data-ttu-id="91c01-126">.NET 5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="91c01-126">.NET 5.0 Preview 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="91c01-127">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="91c01-127">Recommended action</span></span>

<span data-ttu-id="91c01-128">Você não precisa realizar nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="91c01-128">You don't need to take any action.</span></span> <span data-ttu-id="91c01-129">Seus aplicativos se comportarão automaticamente em uma maneira mais compatível com padrões em uma variedade de cenários relacionados à globalização.</span><span class="sxs-lookup"><span data-stu-id="91c01-129">Your apps will automatically behave in a more standards-compliant manner in a variety of globalization-related scenarios.</span></span>

#### <a name="category"></a><span data-ttu-id="91c01-130">Categoria</span><span class="sxs-lookup"><span data-stu-id="91c01-130">Category</span></span>

<span data-ttu-id="91c01-131">Globalização</span><span class="sxs-lookup"><span data-stu-id="91c01-131">Globalization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="91c01-132">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="91c01-132">Affected APIs</span></span>

- <xref:System.Globalization.StringInfo?displayProperty=fullName>
- <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName>
- <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Globalization.StringInfo`
- `T:System.Globalization.TextElementEnumerator`
- `Overload:Microsoft.VisualBasic.Strings.StrReverse`

-->

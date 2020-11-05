---
ms.openlocfilehash: 02b5dc181abe384c1a5f47c042e475f67a0afe1c
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400794"
---
### <a name="globalization-apis-use-icu-libraries-on-windows"></a><span data-ttu-id="b2dbd-101">APIs de globalização usam bibliotecas ICU no Windows</span><span class="sxs-lookup"><span data-stu-id="b2dbd-101">Globalization APIs use ICU libraries on Windows</span></span>

<span data-ttu-id="b2dbd-102">O .NET 5,0 e versões posteriores usam bibliotecas [internacionais para](http://site.icu-project.org/home) a funcionalidade de globalização na execução no Windows 10 pode ser 2019 atualização ou posterior.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-102">.NET 5.0 and later versions use [International Components for Unicode (ICU)](http://site.icu-project.org/home) libraries for globalization functionality when running on Windows 10 May 2019 Update or later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b2dbd-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="b2dbd-103">Change description</span></span>

<span data-ttu-id="b2dbd-104">No .NET Core 1,0-3,1 e .NET Framework 4 e versões posteriores, as bibliotecas do .NET usam APIs [NLS (suporte a idioma nacional)](/windows/win32/intl/national-language-support) para a funcionalidade de globalização no Windows.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-104">In .NET Core 1.0 - 3.1 and .NET Framework 4 and later, .NET libraries use [National Language Support (NLS)](/windows/win32/intl/national-language-support) APIs for globalization functionality on Windows.</span></span> <span data-ttu-id="b2dbd-105">Por exemplo, as funções NLS foram usadas para comparar cadeias de caracteres, obter informações de cultura e executar maiúsculas e minúsculas na cultura apropriada.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-105">For example, NLS functions were used to compare strings, get culture information, and perform string casing in the appropriate culture.</span></span>

<span data-ttu-id="b2dbd-106">A partir do .NET 5,0, se um aplicativo estiver em execução no Windows 10 pode ser 2019 Update ou posterior, as bibliotecas do .NET usarão APIs de globalização [ICU](http://site.icu-project.org/home) , por padrão.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-106">Starting in .NET 5.0, if an app is running on Windows 10 May 2019 Update or later, .NET libraries use [ICU](http://site.icu-project.org/home) globalization APIs, by default.</span></span>

> [!NOTE]
> <span data-ttu-id="b2dbd-107">O Windows 10 pode 2019 atualização e versões posteriores são fornecidas com a biblioteca nativa do ICU.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-107">Windows 10 May 2019 Update and later versions ship with the ICU native library.</span></span> <span data-ttu-id="b2dbd-108">Se o tempo de execução do .NET não puder carregar o ICU, ele usará o NLS.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-108">If the .NET runtime can't load ICU, it uses NLS instead.</span></span>

#### <a name="behavioral-differences"></a><span data-ttu-id="b2dbd-109">Diferenças de comportamento</span><span class="sxs-lookup"><span data-stu-id="b2dbd-109">Behavioral differences</span></span>

<span data-ttu-id="b2dbd-110">Você poderá ver as alterações em seu aplicativo mesmo se não perceber que está usando instalações de globalização.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-110">You might see changes in your app even if you don't realize you're using globalization facilities.</span></span> <span data-ttu-id="b2dbd-111">Esta seção lista algumas das alterações comportamentais que você pode ver, mas também há outras.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-111">This section lists a couple of the behavioral changes you might see, but there are others too.</span></span>

##### <a name="stringindexof"></a><span data-ttu-id="b2dbd-112">String.IndexOf</span><span class="sxs-lookup"><span data-stu-id="b2dbd-112">String.IndexOf</span></span>

<span data-ttu-id="b2dbd-113">Considere o código a seguir que chama <xref:System.String.IndexOf(System.String)?displayProperty=nameWithType> para localizar o índice do caractere de nova linha em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-113">Consider the following code that calls <xref:System.String.IndexOf(System.String)?displayProperty=nameWithType> to find the index of the newline character in a string.</span></span>

```csharp
string s = "Hello\r\nworld!";
int idx = s.IndexOf("\n");
Console.WriteLine(idx);
```

- <span data-ttu-id="b2dbd-114">Nas versões anteriores do .NET no Windows, o trecho é impresso `6` .</span><span class="sxs-lookup"><span data-stu-id="b2dbd-114">In previous versions of .NET on Windows, the snippet prints `6`.</span></span>
- <span data-ttu-id="b2dbd-115">No .NET 5,0 e versões posteriores no Windows 19H1 e versões posteriores, o trecho de código é impresso `-1` .</span><span class="sxs-lookup"><span data-stu-id="b2dbd-115">In .NET 5.0 and later versions on Windows 19H1 and later versions, the snippet prints `-1`.</span></span>

<span data-ttu-id="b2dbd-116">Para corrigir esse código realizando uma pesquisa ordinal em vez de uma pesquisa sensível à cultura, chame a <xref:System.String.IndexOf(System.String,System.StringComparison)> sobrecarga e passe <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> como um argumento.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-116">To fix this code by conducting an ordinal search instead of a culture-sensitive search, call the <xref:System.String.IndexOf(System.String,System.StringComparison)> overload and pass in <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> as an argument.</span></span>

<span data-ttu-id="b2dbd-117">Você pode executar as regras [de análise de código CA1307: especificar StringComparison para clareza](../../../../docs/fundamentals/code-analysis/quality-rules/ca1307.md) e [CA1309: Use o ordinal StringComparison](../../../../docs/fundamentals/code-analysis/quality-rules/ca1309.md) para encontrar esses sites de chamada em seu código.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-117">You can run code analysis rules [CA1307: Specify StringComparison for clarity](../../../../docs/fundamentals/code-analysis/quality-rules/ca1307.md) and [CA1309: Use ordinal StringComparison](../../../../docs/fundamentals/code-analysis/quality-rules/ca1309.md) to find these call sites in your code.</span></span>

<span data-ttu-id="b2dbd-118">Para obter mais informações, consulte [comportamento de alterações ao comparar cadeias de caracteres no .NET 5 +](../../../../docs/standard/base-types/string-comparison-net-5-plus.md).</span><span class="sxs-lookup"><span data-stu-id="b2dbd-118">For more information, see [Behavior changes when comparing strings on .NET 5+](../../../../docs/standard/base-types/string-comparison-net-5-plus.md).</span></span>

##### <a name="currency-symbol"></a><span data-ttu-id="b2dbd-119">Símbolo de moeda</span><span class="sxs-lookup"><span data-stu-id="b2dbd-119">Currency symbol</span></span>

<span data-ttu-id="b2dbd-120">Considere o código a seguir que formata uma cadeia de caracteres usando o especificador de formato de moeda `C` .</span><span class="sxs-lookup"><span data-stu-id="b2dbd-120">Consider the following code that formats a string using the currency format specifier `C`.</span></span> <span data-ttu-id="b2dbd-121">A cultura do thread atual é definida como uma cultura que inclui apenas o idioma e não o país.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-121">The current thread's culture is set to a culture that includes only the language and not the country.</span></span>

```csharp
System.Threading.Thread.CurrentThread.CurrentCulture = new System.Globalization.CultureInfo("de");
string text = string.Format("{0:C}", 100);
```

- <span data-ttu-id="b2dbd-122">Nas versões anteriores do .NET no Windows, o valor do texto é `"100,00 €"` .</span><span class="sxs-lookup"><span data-stu-id="b2dbd-122">In previous versions of .NET on Windows, the value of text is `"100,00 €"`.</span></span>
- <span data-ttu-id="b2dbd-123">No .NET 5,0 e versões posteriores no Windows 19H1 e versões posteriores, o valor de Text é `"100,00 ¤"` , que usa o símbolo de moeda internacional em vez do euro.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-123">In .NET 5.0 and later versions on Windows 19H1 and later versions, the value of text is `"100,00 ¤"`, which uses the international currency symbol instead of the euro.</span></span> <span data-ttu-id="b2dbd-124">No ICU, o design é que uma moeda é uma propriedade de um país ou região, não um idioma.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-124">In ICU, the design is that a currency is a property of a country or region, not a language.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b2dbd-125">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="b2dbd-125">Reason for change</span></span>

<span data-ttu-id="b2dbd-126">Essa alteração foi introduzida para unificar. Comportamento de globalização da rede em todos os sistemas operacionais com suporte.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-126">This change was introduced to unify .NET's globalization behavior across all supported operating systems.</span></span> <span data-ttu-id="b2dbd-127">Ele também fornece a capacidade de os aplicativos agruparem suas próprias bibliotecas de globalização em vez de depender das bibliotecas internas do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-127">It also provides the ability for applications to bundle their own globalization libraries rather than depend on the operating system's built-in libraries.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b2dbd-128">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="b2dbd-128">Version introduced</span></span>

<span data-ttu-id="b2dbd-129">.NET 5,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="b2dbd-129">.NET 5.0 Preview 4</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b2dbd-130">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="b2dbd-130">Recommended action</span></span>

<span data-ttu-id="b2dbd-131">Nenhuma ação é necessária na parte do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-131">No action is required on the part of the developer.</span></span> <span data-ttu-id="b2dbd-132">No entanto, se você quiser continuar usando as APIs de globalização NLS, poderá definir uma [opção de tempo de execução](../../../../docs/core/run-time-config/globalization.md#nls) para reverter para esse comportamento.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-132">However, if you wish to continue using NLS globalization APIs, you can set a [run-time switch](../../../../docs/core/run-time-config/globalization.md#nls) to revert to that behavior.</span></span> <span data-ttu-id="b2dbd-133">Para obter mais informações sobre as opções disponíveis, consulte o artigo [globalização .net e ICU](../../../../docs/standard/globalization-localization/globalization-icu.md) .</span><span class="sxs-lookup"><span data-stu-id="b2dbd-133">For more information about the available switches, see the [.NET globalization and ICU](../../../../docs/standard/globalization-localization/globalization-icu.md) article.</span></span>

#### <a name="category"></a><span data-ttu-id="b2dbd-134">Categoria</span><span class="sxs-lookup"><span data-stu-id="b2dbd-134">Category</span></span>

- <span data-ttu-id="b2dbd-135">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="b2dbd-135">Core .NET libraries</span></span>
- <span data-ttu-id="b2dbd-136">Globalização</span><span class="sxs-lookup"><span data-stu-id="b2dbd-136">Globalization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b2dbd-137">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="b2dbd-137">Affected APIs</span></span>

- <xref:System.Span%601?displayProperty=fullName>
- <xref:System.String?displayProperty=fullName>
- <span data-ttu-id="b2dbd-138">Maioria dos tipos no <xref:System.Globalization?displayProperty=fullName> namespace</span><span class="sxs-lookup"><span data-stu-id="b2dbd-138">Most types in the <xref:System.Globalization?displayProperty=fullName> namespace</span></span>
- <span data-ttu-id="b2dbd-139"><xref:System.Array.Sort%2A?displayProperty=fullName> (ao classificar uma matriz de cadeias de caracteres)</span><span class="sxs-lookup"><span data-stu-id="b2dbd-139"><xref:System.Array.Sort%2A?displayProperty=fullName> (when sorting an array of strings)</span></span>
- <span data-ttu-id="b2dbd-140"><xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (quando os elementos da lista são cadeias de caracteres)</span><span class="sxs-lookup"><span data-stu-id="b2dbd-140"><xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (when the list elements are strings)</span></span>
- <span data-ttu-id="b2dbd-141"><xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (quando as chaves são cadeias de caracteres)</span><span class="sxs-lookup"><span data-stu-id="b2dbd-141"><xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (when the keys are strings)</span></span>
- <span data-ttu-id="b2dbd-142"><xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (quando as chaves são cadeias de caracteres)</span><span class="sxs-lookup"><span data-stu-id="b2dbd-142"><xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (when the keys are strings)</span></span>
- <span data-ttu-id="b2dbd-143"><xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (quando o conjunto contém cadeias de caracteres)</span><span class="sxs-lookup"><span data-stu-id="b2dbd-143"><xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (when the set contains strings)</span></span>

<!--

#### Affected APIs

- ``T:System.Span`1``
- `T:System.String`
- `N:System.Globalization`
- `Overload:System.Array.Sort`
- ``M:System.Collections.Generic.List`1.Sort``
- ``T:System.Collections.Generic.SortedDictionary`2``
- ``T:System.Collections.Generic.SortedList`2``
- ``T:System.Collections.Generic.SortedSet`1``

-->

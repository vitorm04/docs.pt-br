---
ms.openlocfilehash: 6643f64010332cf14d466cbba28a1c3cca671ac3
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117187"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a><span data-ttu-id="50a1b-101">O .NET Core 3,0 segue as práticas recomendadas de Unicode ao substituir sequências de bytes UTF-8 malformadas</span><span class="sxs-lookup"><span data-stu-id="50a1b-101">.NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>

<span data-ttu-id="50a1b-102">Quando a <xref:System.Text.UTF8Encoding> classe encontra uma sequência de bytes UTF-8 mal formada durante uma operação de transcodificação byte a caractere, ela substituirá essa sequência por um caractere ' ' (caractere de substituição U + FFFD) na cadeia de caracteres de saída.</span><span class="sxs-lookup"><span data-stu-id="50a1b-102">When the <xref:System.Text.UTF8Encoding> class encounters an ill-formed UTF-8 byte sequence during a byte-to-character transcoding operation, it will replace that sequence with a '�' (U+FFFD REPLACEMENT CHARACTER) character in the output string.</span></span> <span data-ttu-id="50a1b-103">O .NET Core 3,0 é diferente das versões anteriores do .NET Core e do .NET Framework seguindo a prática recomendada de Unicode para executar essa substituição durante a operação de transcodificação.</span><span class="sxs-lookup"><span data-stu-id="50a1b-103">.NET Core 3.0 differs from previous versions of .NET Core and the .NET Framework by following the Unicode best practice for performing this replacement during the transcoding operation.</span></span>

<span data-ttu-id="50a1b-104">Isso faz parte de um esforço maior para melhorar a manipulação de UTF-8 em todo o .net, <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> incluindo <xref:System.Text.Rune?displayProperty=nameWithType> os novos e os tipos.</span><span class="sxs-lookup"><span data-stu-id="50a1b-104">This is part of a larger effort to improve UTF-8 handling throughout .NET, including by the new <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> and <xref:System.Text.Rune?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="50a1b-105">O <xref:System.Text.UTF8Encoding> tipo recebeu uma melhor mecânica de tratamento de erros para que produza a saída consistente com os tipos introduzidos recentemente.</span><span class="sxs-lookup"><span data-stu-id="50a1b-105">The <xref:System.Text.UTF8Encoding> type was given improved error handling mechanics so that it produces output consistent with the newly introduced types.</span></span>

#### <a name="details"></a><span data-ttu-id="50a1b-106">Detalhes</span><span class="sxs-lookup"><span data-stu-id="50a1b-106">Details</span></span>

<span data-ttu-id="50a1b-107">A partir do .NET Core 3,0, ao transcodificar bytes em caracteres, <xref:System.Text.UTF8Encoding> a classe executa a substituição de caracteres com base nas práticas recomendadas do Unicode.</span><span class="sxs-lookup"><span data-stu-id="50a1b-107">Starting with .NET Core 3.0, when transcoding bytes to characters, the <xref:System.Text.UTF8Encoding> class performs character substitution based on Unicode best practices.</span></span> <span data-ttu-id="50a1b-108">O mecanismo de substituição usado é descrito pelo [padrão Unicode, versão 12,0, seg. 3,9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) no título intitulado _U + FFFD substituição de subpartes do máximo_.</span><span class="sxs-lookup"><span data-stu-id="50a1b-108">The substitution mechanism used is described by [The Unicode Standard, Version 12.0, Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) in the heading titled _U+FFFD Substitution of Maximal Subparts_.</span></span>

<span data-ttu-id="50a1b-109">Esse comportamento se aplica _somente_ quando a sequência de bytes de entrada contém dados UTF-8 mal formados.</span><span class="sxs-lookup"><span data-stu-id="50a1b-109">This behavior _only_ applies when the input byte sequence contains ill-formed UTF-8 data.</span></span> <span data-ttu-id="50a1b-110">Além disso, se <xref:System.Text.UTF8Encoding> a instância tiver sido construída `throwOnInvalidBytes: true` com (consulte a [documentação do construtor do<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>UTF8Encoding] `UTF8Encoding` (, a instância continuará a gerar uma entrada inválida em vez de executar U + FFFD irá.</span><span class="sxs-lookup"><span data-stu-id="50a1b-110">Additionally, if the <xref:System.Text.UTF8Encoding> instance has been constructed with `throwOnInvalidBytes: true` (see the [UTF8Encoding constructor documentation](<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>, the `UTF8Encoding` instance will continue to throw on invalid input rather than perform U+FFFD replacement.</span></span>

<span data-ttu-id="50a1b-111">O seguinte ilustra o impacto dessa alteração com uma entrada de 3 bytes inválida:</span><span class="sxs-lookup"><span data-stu-id="50a1b-111">The following illustrates the impact of this change with an invalid 3-byte input:</span></span>

|<span data-ttu-id="50a1b-112">Entrada de 3 bytes formada incorretamente</span><span class="sxs-lookup"><span data-stu-id="50a1b-112">Ill-formed 3-byte input</span></span>|<span data-ttu-id="50a1b-113">Saída antes do .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="50a1b-113">Output before .NET Core 3.0</span></span>|<span data-ttu-id="50a1b-114">Saída a partir do .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="50a1b-114">Output starting with .NET Core 3.0</span></span>|
|---|---|---|
| `[ ED A0 90 ]` | <span data-ttu-id="50a1b-115">`[ FFFD FFFD ]`(saída de 2 caracteres)</span><span class="sxs-lookup"><span data-stu-id="50a1b-115">`[ FFFD FFFD ]` (2-character output)</span></span>| <span data-ttu-id="50a1b-116">`[ FFFD FFFD FFFD ]`(saída de 3 caracteres)</span><span class="sxs-lookup"><span data-stu-id="50a1b-116">`[ FFFD FFFD FFFD ]` (3-character output)</span></span>|

<span data-ttu-id="50a1b-117">Essa saída de 3 caracteres é a saída preferida, de acordo com a _tabela 3-9_ do PDF padrão Unicode vinculado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="50a1b-117">This 3-char output is the preferred output, according to _Table 3-9_ of the previously linked Unicode Standard PDF.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="50a1b-118">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="50a1b-118">Version introduced</span></span>

<span data-ttu-id="50a1b-119">3.0</span><span class="sxs-lookup"><span data-stu-id="50a1b-119">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="50a1b-120">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="50a1b-120">Recommended action</span></span>

<span data-ttu-id="50a1b-121">Nenhuma ação é necessária na parte do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="50a1b-121">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="50a1b-122">Categoria</span><span class="sxs-lookup"><span data-stu-id="50a1b-122">Category</span></span>

<span data-ttu-id="50a1b-123">CoreFx</span><span class="sxs-lookup"><span data-stu-id="50a1b-123">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="50a1b-124">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="50a1b-124">Affected APIs</span></span>

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->


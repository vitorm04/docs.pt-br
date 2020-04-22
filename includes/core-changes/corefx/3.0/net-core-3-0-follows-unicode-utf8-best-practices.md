---
ms.openlocfilehash: 843c78bb4e4f88d9ac58308a91ab8278364c9580
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021599"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a><span data-ttu-id="0e878-101">O Núcleo 3.0 do .NET segue as práticas recomendadas da Unicode ao substituir sequências de bytes UTF-8 mal formadas</span><span class="sxs-lookup"><span data-stu-id="0e878-101">.NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>

<span data-ttu-id="0e878-102">Quando <xref:System.Text.UTF8Encoding> a classe encontra uma seqüência de bytes UTF-8 mal formada durante uma operação de transcodificação byte-to-character, ela substituirá essa seqüência por um ' (U+FFFD REPLACEMENT CHARACTER) na seqüência de saída.</span><span class="sxs-lookup"><span data-stu-id="0e878-102">When the <xref:System.Text.UTF8Encoding> class encounters an ill-formed UTF-8 byte sequence during a byte-to-character transcoding operation, it will replace that sequence with a '�' (U+FFFD REPLACEMENT CHARACTER) character in the output string.</span></span> <span data-ttu-id="0e878-103">O .NET Core 3.0 difere das versões anteriores do .NET Core e do .NET Framework, seguindo as práticas recomendadas do Unicode para realizar essa substituição durante a operação de transcodificação.</span><span class="sxs-lookup"><span data-stu-id="0e878-103">.NET Core 3.0 differs from previous versions of .NET Core and the .NET Framework by following the Unicode best practice for performing this replacement during the transcoding operation.</span></span>

<span data-ttu-id="0e878-104">Isso faz parte de um esforço maior para melhorar o manuseio do <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> <xref:System.Text.Rune?displayProperty=nameWithType> UTF-8 em todo o .NET, inclusive pelos novos e tipos.</span><span class="sxs-lookup"><span data-stu-id="0e878-104">This is part of a larger effort to improve UTF-8 handling throughout .NET, including by the new <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> and <xref:System.Text.Rune?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="0e878-105">O <xref:System.Text.UTF8Encoding> tipo recebeu mecânica de manuseio de erros melhorada para que produza saída consistente com os tipos recém-introduzidos.</span><span class="sxs-lookup"><span data-stu-id="0e878-105">The <xref:System.Text.UTF8Encoding> type was given improved error handling mechanics so that it produces output consistent with the newly introduced types.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0e878-106">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="0e878-106">Change description</span></span>

<span data-ttu-id="0e878-107">Começando com o .NET Core 3.0, ao transcodificar bytes para caracteres, a classe executa a <xref:System.Text.UTF8Encoding> substituição de caracteres com base nas práticas recomendadas do Unicode.</span><span class="sxs-lookup"><span data-stu-id="0e878-107">Starting with .NET Core 3.0, when transcoding bytes to characters, the <xref:System.Text.UTF8Encoding> class performs character substitution based on Unicode best practices.</span></span> <span data-ttu-id="0e878-108">O mecanismo de substituição utilizado é descrito pelo [Unicode Standard, Versão 12.0, Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) no título intitulado _U+FFFD Replacement of Maximal Subparts_.</span><span class="sxs-lookup"><span data-stu-id="0e878-108">The substitution mechanism used is described by [The Unicode Standard, Version 12.0, Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) in the heading titled _U+FFFD Substitution of Maximal Subparts_.</span></span>

<span data-ttu-id="0e878-109">Esse comportamento _só_ se aplica quando a seqüência de bytes de entrada contém dados UTF-8 mal formados.</span><span class="sxs-lookup"><span data-stu-id="0e878-109">This behavior _only_ applies when the input byte sequence contains ill-formed UTF-8 data.</span></span> <span data-ttu-id="0e878-110">Além disso, <xref:System.Text.UTF8Encoding> se a instância `throwOnInvalidBytes: true` tiver sido construída com (consulte a documentação do construtor UTF8Encoding](<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>, a `UTF8Encoding` instância continuará a jogar em entrada inválida em vez de executar a substituição U+FFFD.</span><span class="sxs-lookup"><span data-stu-id="0e878-110">Additionally, if the <xref:System.Text.UTF8Encoding> instance has been constructed with `throwOnInvalidBytes: true` (see the [UTF8Encoding constructor documentation](<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>, the `UTF8Encoding` instance will continue to throw on invalid input rather than perform U+FFFD replacement.</span></span>

<span data-ttu-id="0e878-111">O seguinte ilustra o impacto desta mudança com uma entrada inválida de 3 bytes:</span><span class="sxs-lookup"><span data-stu-id="0e878-111">The following illustrates the impact of this change with an invalid 3-byte input:</span></span>

|<span data-ttu-id="0e878-112">Entrada mal formada de 3 bytes</span><span class="sxs-lookup"><span data-stu-id="0e878-112">Ill-formed 3-byte input</span></span>|<span data-ttu-id="0e878-113">Saída antes do .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0e878-113">Output before .NET Core 3.0</span></span>|<span data-ttu-id="0e878-114">Saída começando com .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0e878-114">Output starting with .NET Core 3.0</span></span>|
|---|---|---|
| `[ ED A0 90 ]` | <span data-ttu-id="0e878-115">`[ FFFD FFFD ]`(Saída de 2 caracteres)</span><span class="sxs-lookup"><span data-stu-id="0e878-115">`[ FFFD FFFD ]` (2-character output)</span></span>| <span data-ttu-id="0e878-116">`[ FFFD FFFD FFFD ]`(Saída de 3 caracteres)</span><span class="sxs-lookup"><span data-stu-id="0e878-116">`[ FFFD FFFD FFFD ]` (3-character output)</span></span>|

<span data-ttu-id="0e878-117">Esta saída de 3 char é a saída preferida, de acordo com a _Tabela 3-9_ do PDF Padrão Unicode anteriormente vinculado.</span><span class="sxs-lookup"><span data-stu-id="0e878-117">This 3-char output is the preferred output, according to _Table 3-9_ of the previously linked Unicode Standard PDF.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0e878-118">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="0e878-118">Version introduced</span></span>

<span data-ttu-id="0e878-119">3.0</span><span class="sxs-lookup"><span data-stu-id="0e878-119">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0e878-120">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="0e878-120">Recommended action</span></span>

<span data-ttu-id="0e878-121">Nenhuma ação é necessária por parte do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="0e878-121">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="0e878-122">Categoria</span><span class="sxs-lookup"><span data-stu-id="0e878-122">Category</span></span>

<span data-ttu-id="0e878-123">Bibliotecas Core .NET</span><span class="sxs-lookup"><span data-stu-id="0e878-123">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0e878-124">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="0e878-124">Affected APIs</span></span>

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->

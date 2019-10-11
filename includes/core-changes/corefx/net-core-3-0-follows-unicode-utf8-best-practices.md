---
ms.openlocfilehash: db1d09c8c9e606b5327a42977a74a74703282d84
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237280"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a><span data-ttu-id="fc53a-101">O .NET Core 3,0 segue as práticas recomendadas de Unicode ao substituir sequências de bytes UTF-8 malformadas</span><span class="sxs-lookup"><span data-stu-id="fc53a-101">.NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>

<span data-ttu-id="fc53a-102">Quando a classe <xref:System.Text.UTF8Encoding> encontra uma sequência de bytes UTF-8 mal formada durante uma operação de transcodificação byte a caractere, ela substituirá essa sequência por um caractere ' ' (caractere de substituição U + FFFD) na cadeia de caracteres de saída.</span><span class="sxs-lookup"><span data-stu-id="fc53a-102">When the <xref:System.Text.UTF8Encoding> class encounters an ill-formed UTF-8 byte sequence during a byte-to-character transcoding operation, it will replace that sequence with a '�' (U+FFFD REPLACEMENT CHARACTER) character in the output string.</span></span> <span data-ttu-id="fc53a-103">O .NET Core 3,0 é diferente das versões anteriores do .NET Core e do .NET Framework seguindo a prática recomendada de Unicode para executar essa substituição durante a operação de transcodificação.</span><span class="sxs-lookup"><span data-stu-id="fc53a-103">.NET Core 3.0 differs from previous versions of .NET Core and the .NET Framework by following the Unicode best practice for performing this replacement during the transcoding operation.</span></span>

<span data-ttu-id="fc53a-104">Isso faz parte de um esforço maior para melhorar a manipulação de UTF-8 em todo o .NET, incluindo os novos tipos <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> e <xref:System.Text.Rune?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fc53a-104">This is part of a larger effort to improve UTF-8 handling throughout .NET, including by the new <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> and <xref:System.Text.Rune?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="fc53a-105">O tipo <xref:System.Text.UTF8Encoding> recebeu um mecanismo de tratamento de erros aprimorado para que ele produza uma saída consistente com os tipos introduzidos recentemente.</span><span class="sxs-lookup"><span data-stu-id="fc53a-105">The <xref:System.Text.UTF8Encoding> type was given improved error handling mechanics so that it produces output consistent with the newly introduced types.</span></span>

#### <a name="change-description"></a><span data-ttu-id="fc53a-106">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="fc53a-106">Change description</span></span>

<span data-ttu-id="fc53a-107">A partir do .NET Core 3,0, ao transcodificar bytes em caracteres, a classe <xref:System.Text.UTF8Encoding> executa a substituição de caracteres com base nas práticas recomendadas Unicode.</span><span class="sxs-lookup"><span data-stu-id="fc53a-107">Starting with .NET Core 3.0, when transcoding bytes to characters, the <xref:System.Text.UTF8Encoding> class performs character substitution based on Unicode best practices.</span></span> <span data-ttu-id="fc53a-108">O mecanismo de substituição usado é descrito pelo [padrão Unicode, versão 12,0, seg. 3,9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) no título intitulado _U + FFFD substituição de subpartes do máximo_.</span><span class="sxs-lookup"><span data-stu-id="fc53a-108">The substitution mechanism used is described by [The Unicode Standard, Version 12.0, Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) in the heading titled _U+FFFD Substitution of Maximal Subparts_.</span></span>

<span data-ttu-id="fc53a-109">Esse comportamento se aplica _somente_ quando a sequência de bytes de entrada contém dados UTF-8 mal formados.</span><span class="sxs-lookup"><span data-stu-id="fc53a-109">This behavior _only_ applies when the input byte sequence contains ill-formed UTF-8 data.</span></span> <span data-ttu-id="fc53a-110">Além disso, se a instância <xref:System.Text.UTF8Encoding> tiver sido construída com `throwOnInvalidBytes: true` (consulte a [documentação do construtor do UTF8Encoding] (<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>, a instância `UTF8Encoding` continuará a gerar uma entrada inválida em vez de executar a substituição U + FFFD.</span><span class="sxs-lookup"><span data-stu-id="fc53a-110">Additionally, if the <xref:System.Text.UTF8Encoding> instance has been constructed with `throwOnInvalidBytes: true` (see the [UTF8Encoding constructor documentation](<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>, the `UTF8Encoding` instance will continue to throw on invalid input rather than perform U+FFFD replacement.</span></span>

<span data-ttu-id="fc53a-111">O seguinte ilustra o impacto dessa alteração com uma entrada de 3 bytes inválida:</span><span class="sxs-lookup"><span data-stu-id="fc53a-111">The following illustrates the impact of this change with an invalid 3-byte input:</span></span>

|<span data-ttu-id="fc53a-112">Entrada de 3 bytes formada incorretamente</span><span class="sxs-lookup"><span data-stu-id="fc53a-112">Ill-formed 3-byte input</span></span>|<span data-ttu-id="fc53a-113">Saída antes do .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="fc53a-113">Output before .NET Core 3.0</span></span>|<span data-ttu-id="fc53a-114">Saída a partir do .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="fc53a-114">Output starting with .NET Core 3.0</span></span>|
|---|---|---|
| `[ ED A0 90 ]` | <span data-ttu-id="fc53a-115">`[ FFFD FFFD ]` (saída de 2 caracteres)</span><span class="sxs-lookup"><span data-stu-id="fc53a-115">`[ FFFD FFFD ]` (2-character output)</span></span>| <span data-ttu-id="fc53a-116">`[ FFFD FFFD FFFD ]` (saída de 3 caracteres)</span><span class="sxs-lookup"><span data-stu-id="fc53a-116">`[ FFFD FFFD FFFD ]` (3-character output)</span></span>|

<span data-ttu-id="fc53a-117">Essa saída de 3 caracteres é a saída preferida, de acordo com a _tabela 3-9_ do PDF padrão Unicode vinculado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="fc53a-117">This 3-char output is the preferred output, according to _Table 3-9_ of the previously linked Unicode Standard PDF.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fc53a-118">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="fc53a-118">Version introduced</span></span>

<span data-ttu-id="fc53a-119">3.0</span><span class="sxs-lookup"><span data-stu-id="fc53a-119">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fc53a-120">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="fc53a-120">Recommended action</span></span>

<span data-ttu-id="fc53a-121">Nenhuma ação é necessária na parte do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="fc53a-121">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="fc53a-122">Categoria</span><span class="sxs-lookup"><span data-stu-id="fc53a-122">Category</span></span>

<span data-ttu-id="fc53a-123">CoreFx</span><span class="sxs-lookup"><span data-stu-id="fc53a-123">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fc53a-124">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="fc53a-124">Affected APIs</span></span>

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->

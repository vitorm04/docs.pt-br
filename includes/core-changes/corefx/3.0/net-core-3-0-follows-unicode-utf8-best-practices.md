---
ms.openlocfilehash: becae23cd810623bbb33c693b707c2d4735aeece
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158457"
---
### <a name="replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines"></a><span data-ttu-id="652e5-101">A substituição de sequências de bytes UTF-8 mal formados segue as diretrizes de Unicode</span><span class="sxs-lookup"><span data-stu-id="652e5-101">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>

<span data-ttu-id="652e5-102">Quando a <xref:System.Text.UTF8Encoding> classe encontra uma sequência de bytes UTF-8 mal formada durante uma operação de transcodificação de byte para caractere, ela substitui essa sequência por um caractere ' ' (caractere de substituição U + FFFD) na cadeia de caracteres de saída.</span><span class="sxs-lookup"><span data-stu-id="652e5-102">When the <xref:System.Text.UTF8Encoding> class encounters an ill-formed UTF-8 byte sequence during a byte-to-character transcoding operation, it replaces that sequence with a '�' (U+FFFD REPLACEMENT CHARACTER) character in the output string.</span></span> <span data-ttu-id="652e5-103">O .NET Core 3,0 é diferente das versões anteriores do .NET Core e do .NET Framework seguindo a prática recomendada de Unicode para executar essa substituição durante a operação de transcodificação.</span><span class="sxs-lookup"><span data-stu-id="652e5-103">.NET Core 3.0 differs from previous versions of .NET Core and the .NET Framework by following the Unicode best practice for performing this replacement during the transcoding operation.</span></span>

<span data-ttu-id="652e5-104">Isso faz parte de um esforço maior para melhorar a manipulação de UTF-8 em todo o .NET, <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> incluindo <xref:System.Text.Rune?displayProperty=nameWithType> os novos e os tipos.</span><span class="sxs-lookup"><span data-stu-id="652e5-104">This is part of a larger effort to improve UTF-8 handling throughout .NET, including by the new <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> and <xref:System.Text.Rune?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="652e5-105">O <xref:System.Text.UTF8Encoding> tipo recebeu uma melhor mecânica de tratamento de erros para que produza a saída consistente com os tipos introduzidos recentemente.</span><span class="sxs-lookup"><span data-stu-id="652e5-105">The <xref:System.Text.UTF8Encoding> type was given improved error handling mechanics so that it produces output consistent with the newly introduced types.</span></span>

#### <a name="change-description"></a><span data-ttu-id="652e5-106">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="652e5-106">Change description</span></span>

<span data-ttu-id="652e5-107">A partir do .NET Core 3,0, ao transcodificar bytes em caracteres, <xref:System.Text.UTF8Encoding> a classe executa a substituição de caracteres com base nas práticas recomendadas do Unicode.</span><span class="sxs-lookup"><span data-stu-id="652e5-107">Starting with .NET Core 3.0, when transcoding bytes to characters, the <xref:System.Text.UTF8Encoding> class performs character substitution based on Unicode best practices.</span></span> <span data-ttu-id="652e5-108">O mecanismo de substituição usado é descrito pelo [padrão Unicode, versão 12,0, seg. 3,9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) no título intitulado _U + FFFD substituição de subpartes do máximo_.</span><span class="sxs-lookup"><span data-stu-id="652e5-108">The substitution mechanism used is described by [The Unicode Standard, Version 12.0, Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) in the heading titled _U+FFFD Substitution of Maximal Subparts_.</span></span>

<span data-ttu-id="652e5-109">Esse comportamento se aplica _somente_ quando a sequência de bytes de entrada contém dados UTF-8 mal formados.</span><span class="sxs-lookup"><span data-stu-id="652e5-109">This behavior _only_ applies when the input byte sequence contains ill-formed UTF-8 data.</span></span> <span data-ttu-id="652e5-110">Além disso, se <xref:System.Text.UTF8Encoding> a instância tiver sido construída `throwOnInvalidBytes: true`com, `UTF8Encoding` a instância continuará a gerar uma entrada inválida em vez de executar a substituição U + FFFD.</span><span class="sxs-lookup"><span data-stu-id="652e5-110">Additionally, if the <xref:System.Text.UTF8Encoding> instance has been constructed with `throwOnInvalidBytes: true`, the `UTF8Encoding` instance will continue to throw on invalid input rather than perform U+FFFD replacement.</span></span> <span data-ttu-id="652e5-111">Para obter mais informações sobre `UTF8Encoding` o construtor, <xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>consulte.</span><span class="sxs-lookup"><span data-stu-id="652e5-111">For more information about the `UTF8Encoding` constructor, see <xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>.</span></span>

<span data-ttu-id="652e5-112">A tabela a seguir ilustra o impacto dessa alteração com uma entrada de 3 bytes inválida:</span><span class="sxs-lookup"><span data-stu-id="652e5-112">The following table illustrates the impact of this change with an invalid 3-byte input:</span></span>

| <span data-ttu-id="652e5-113">Entrada de 3 bytes formada incorretamente</span><span class="sxs-lookup"><span data-stu-id="652e5-113">Ill-formed 3-byte input</span></span> | <span data-ttu-id="652e5-114">Saída antes do .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="652e5-114">Output before .NET Core 3.0</span></span>          | <span data-ttu-id="652e5-115">Saída a partir do .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="652e5-115">Output starting with .NET Core 3.0</span></span>        |
|-------------------------|--------------------------------------|-------------------------------------------|
| `[ ED A0 90 ]`          | <span data-ttu-id="652e5-116">`[ FFFD FFFD ]`(saída de 2 caracteres)</span><span class="sxs-lookup"><span data-stu-id="652e5-116">`[ FFFD FFFD ]` (2-character output)</span></span> | <span data-ttu-id="652e5-117">`[ FFFD FFFD FFFD ]`(saída de 3 caracteres)</span><span class="sxs-lookup"><span data-stu-id="652e5-117">`[ FFFD FFFD FFFD ]` (3-character output)</span></span> |

<span data-ttu-id="652e5-118">A saída de 3 caracteres é a saída preferida, de acordo com a _tabela 3-9_ do PDF padrão Unicode vinculado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="652e5-118">The 3-char output is the preferred output, according to _Table 3-9_ of the previously linked Unicode Standard PDF.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="652e5-119">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="652e5-119">Version introduced</span></span>

<span data-ttu-id="652e5-120">3.0</span><span class="sxs-lookup"><span data-stu-id="652e5-120">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="652e5-121">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="652e5-121">Recommended action</span></span>

<span data-ttu-id="652e5-122">Nenhuma ação é necessária na parte do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="652e5-122">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="652e5-123">Categoria</span><span class="sxs-lookup"><span data-stu-id="652e5-123">Category</span></span>

<span data-ttu-id="652e5-124">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="652e5-124">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="652e5-125">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="652e5-125">Affected APIs</span></span>

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->

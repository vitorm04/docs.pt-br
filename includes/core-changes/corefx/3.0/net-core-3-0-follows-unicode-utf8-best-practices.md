---
ms.openlocfilehash: 298cb441bf9fe7daddb30c85f9d7366dc972628c
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721248"
---
### <a name="replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines"></a><span data-ttu-id="83927-101">A substituição de sequências de bytes UTF-8 mal formados segue as diretrizes de Unicode</span><span class="sxs-lookup"><span data-stu-id="83927-101">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>

<span data-ttu-id="83927-102">Quando a <xref:System.Text.UTF8Encoding> classe encontra uma sequência de bytes UTF-8 mal formada durante uma operação de transcodificação de byte para caractere, ela substitui essa sequência por um caractere ' ' (caractere de substituição U + FFFD) na cadeia de caracteres de saída.</span><span class="sxs-lookup"><span data-stu-id="83927-102">When the <xref:System.Text.UTF8Encoding> class encounters an ill-formed UTF-8 byte sequence during a byte-to-character transcoding operation, it replaces that sequence with a '�' (U+FFFD REPLACEMENT CHARACTER) character in the output string.</span></span> <span data-ttu-id="83927-103">O .NET Core 3,0 é diferente das versões anteriores do .NET Core e do .NET Framework seguindo a prática recomendada de Unicode para executar essa substituição durante a operação de transcodificação.</span><span class="sxs-lookup"><span data-stu-id="83927-103">.NET Core 3.0 differs from previous versions of .NET Core and the .NET Framework by following the Unicode best practice for performing this replacement during the transcoding operation.</span></span>

<span data-ttu-id="83927-104">Isso faz parte de um esforço maior para melhorar a manipulação de UTF-8 em todo o .NET, incluindo os novos <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> e os <xref:System.Text.Rune?displayProperty=nameWithType> tipos.</span><span class="sxs-lookup"><span data-stu-id="83927-104">This is part of a larger effort to improve UTF-8 handling throughout .NET, including by the new <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> and <xref:System.Text.Rune?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="83927-105">O <xref:System.Text.UTF8Encoding> tipo recebeu uma melhor mecânica de tratamento de erros para que produza a saída consistente com os tipos introduzidos recentemente.</span><span class="sxs-lookup"><span data-stu-id="83927-105">The <xref:System.Text.UTF8Encoding> type was given improved error handling mechanics so that it produces output consistent with the newly introduced types.</span></span>

#### <a name="change-description"></a><span data-ttu-id="83927-106">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="83927-106">Change description</span></span>

<span data-ttu-id="83927-107">A partir do .NET Core 3,0, ao transcodificar bytes em caracteres, a <xref:System.Text.UTF8Encoding> classe executa a substituição de caracteres com base nas práticas recomendadas do Unicode.</span><span class="sxs-lookup"><span data-stu-id="83927-107">Starting with .NET Core 3.0, when transcoding bytes to characters, the <xref:System.Text.UTF8Encoding> class performs character substitution based on Unicode best practices.</span></span> <span data-ttu-id="83927-108">O mecanismo de substituição usado é descrito pelo [padrão Unicode, versão 12,0, seg. 3,9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) no título intitulado _U + FFFD substituição de subpartes do máximo_.</span><span class="sxs-lookup"><span data-stu-id="83927-108">The substitution mechanism used is described by [The Unicode Standard, Version 12.0, Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) in the heading titled _U+FFFD Substitution of Maximal Subparts_.</span></span>

<span data-ttu-id="83927-109">Esse comportamento se aplica _somente_ quando a sequência de bytes de entrada contém dados UTF-8 mal formados.</span><span class="sxs-lookup"><span data-stu-id="83927-109">This behavior _only_ applies when the input byte sequence contains ill-formed UTF-8 data.</span></span> <span data-ttu-id="83927-110">Além disso, se a <xref:System.Text.UTF8Encoding> instância tiver sido construída com `throwOnInvalidBytes: true` , a `UTF8Encoding` instância continuará a gerar uma entrada inválida em vez de executar a substituição U + FFFD.</span><span class="sxs-lookup"><span data-stu-id="83927-110">Additionally, if the <xref:System.Text.UTF8Encoding> instance has been constructed with `throwOnInvalidBytes: true`, the `UTF8Encoding` instance will continue to throw on invalid input rather than perform U+FFFD replacement.</span></span> <span data-ttu-id="83927-111">Para obter mais informações sobre o `UTF8Encoding` Construtor, consulte <xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)> .</span><span class="sxs-lookup"><span data-stu-id="83927-111">For more information about the `UTF8Encoding` constructor, see <xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>.</span></span>

<span data-ttu-id="83927-112">A tabela a seguir ilustra o impacto dessa alteração com uma entrada de 3 bytes inválida:</span><span class="sxs-lookup"><span data-stu-id="83927-112">The following table illustrates the impact of this change with an invalid 3-byte input:</span></span>

| <span data-ttu-id="83927-113">Entrada de 3 bytes formada incorretamente</span><span class="sxs-lookup"><span data-stu-id="83927-113">Ill-formed 3-byte input</span></span> | <span data-ttu-id="83927-114">Saída antes do .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="83927-114">Output before .NET Core 3.0</span></span>          | <span data-ttu-id="83927-115">Saída a partir do .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="83927-115">Output starting with .NET Core 3.0</span></span>        |
|-------------------------|--------------------------------------|-------------------------------------------|
| `[ ED A0 90 ]`          | <span data-ttu-id="83927-116">`[ FFFD FFFD ]`(saída de 2 caracteres)</span><span class="sxs-lookup"><span data-stu-id="83927-116">`[ FFFD FFFD ]` (2-character output)</span></span> | <span data-ttu-id="83927-117">`[ FFFD FFFD FFFD ]`(saída de 3 caracteres)</span><span class="sxs-lookup"><span data-stu-id="83927-117">`[ FFFD FFFD FFFD ]` (3-character output)</span></span> |

<span data-ttu-id="83927-118">A saída de 3 caracteres é a saída preferida, de acordo com a _tabela 3-9_ do PDF padrão Unicode vinculado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="83927-118">The 3-char output is the preferred output, according to _Table 3-9_ of the previously linked Unicode Standard PDF.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="83927-119">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="83927-119">Version introduced</span></span>

<span data-ttu-id="83927-120">3.0</span><span class="sxs-lookup"><span data-stu-id="83927-120">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="83927-121">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="83927-121">Recommended action</span></span>

<span data-ttu-id="83927-122">Nenhuma ação é necessária na parte do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="83927-122">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="83927-123">Categoria</span><span class="sxs-lookup"><span data-stu-id="83927-123">Category</span></span>

<span data-ttu-id="83927-124">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="83927-124">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="83927-125">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="83927-125">Affected APIs</span></span>

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->

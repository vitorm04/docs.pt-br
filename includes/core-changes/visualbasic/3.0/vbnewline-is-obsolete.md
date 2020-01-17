---
ms.openlocfilehash: 95a4c807f5c1077cf52f54b196e904ebc98c32f8
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116368"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="b98aa-101">Microsoft. VisualBasic. Constants. vbNewLine é obsoleto</span><span class="sxs-lookup"><span data-stu-id="b98aa-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="b98aa-102">A constante <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> é marcada como [\[obsoleta\]](xref:System.ObsoleteAttribute) a partir do .net Core 3,0 Preview 8.</span><span class="sxs-lookup"><span data-stu-id="b98aa-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked as [\[Obsolete\]](xref:System.ObsoleteAttribute) starting with .NET Core 3.0 Preview 8.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b98aa-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="b98aa-103">Version introduced</span></span>

<span data-ttu-id="b98aa-104">3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="b98aa-104">3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="b98aa-105">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="b98aa-105">Change description</span></span>

<span data-ttu-id="b98aa-106">A partir do .NET Core 3,0 Preview 8, o atributo [obsoleto](xref:System.ObsoleteAttribute) foi aplicado à constante <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="b98aa-106">Starting with .NET Core 3.0 Preview 8, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant.</span></span> <span data-ttu-id="b98aa-107">O uso da constante produz um aviso do compilador.</span><span class="sxs-lookup"><span data-stu-id="b98aa-107">Use of the constant produces a compiler warning.</span></span> <span data-ttu-id="b98aa-108">Em .NET Framework e versões anteriores do .NET Core, ele não foi marcado como obsoleto.</span><span class="sxs-lookup"><span data-stu-id="b98aa-108">In .NET Framework and previous releases of .NET Core, it was not marked as obsolete.</span></span>

<span data-ttu-id="b98aa-109">Essa alteração foi feita para dar suporte a Visual Basic como uma linguagem para o desenvolvimento de várias plataformas.</span><span class="sxs-lookup"><span data-stu-id="b98aa-109">This change was made to support Visual Basic as a language for multi-platform development.</span></span> <span data-ttu-id="b98aa-110">A constante <xref:Microsoft.VisualBasic.Constants.vbNewLine> é equivalente a `\r\n`, a seqüência de caracteres de nova linha no Windows.</span><span class="sxs-lookup"><span data-stu-id="b98aa-110">The <xref:Microsoft.VisualBasic.Constants.vbNewLine> constant is equivalent to `\r\n`, the newline character sequence on Windows.</span></span> <span data-ttu-id="b98aa-111">Em sistemas baseados em UNIX, o caractere de nova linha é `\n`.</span><span class="sxs-lookup"><span data-stu-id="b98aa-111">On Unix-based systems, the newline character is `\n`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b98aa-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="b98aa-112">Recommended action</span></span>

<span data-ttu-id="b98aa-113">A mensagem de atributo [obsoleto](xref:System.ObsoleteAttribute) para o <xref:Microsoft.VisualBasic.Constants.vbNewLine> inclui a seguinte recomendação:</span><span class="sxs-lookup"><span data-stu-id="b98aa-113">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for <xref:Microsoft.VisualBasic.Constants.vbNewLine> includes the following recommendation:</span></span>

<span data-ttu-id="b98aa-114">Para um retorno de carro e alimentação de linha, use <xref:Microsoft.VisualBasic.Constants.vbCrLf>.</span><span class="sxs-lookup"><span data-stu-id="b98aa-114">For a carriage return and line feed, use <xref:Microsoft.VisualBasic.Constants.vbCrLf>.</span></span> <span data-ttu-id="b98aa-115">Para a nova linha da plataforma atual, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b98aa-115">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="b98aa-116">Categoria</span><span class="sxs-lookup"><span data-stu-id="b98aa-116">Category</span></span>

<span data-ttu-id="b98aa-117">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b98aa-117">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b98aa-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="b98aa-118">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->

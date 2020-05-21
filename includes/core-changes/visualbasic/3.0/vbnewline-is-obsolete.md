---
ms.openlocfilehash: 535a73c6b748166a1e4a4661a6bab0671c653278
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721522"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="93131-101">Microsoft. VisualBasic. Constants. vbNewLine é obsoleto</span><span class="sxs-lookup"><span data-stu-id="93131-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="93131-102">A <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constante é marcada como [ \[ obsoleta \] ](xref:System.ObsoleteAttribute) a partir do .NET Core 3,0 Preview 8.</span><span class="sxs-lookup"><span data-stu-id="93131-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked as [\[Obsolete\]](xref:System.ObsoleteAttribute) starting with .NET Core 3.0 Preview 8.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="93131-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="93131-103">Version introduced</span></span>

<span data-ttu-id="93131-104">3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="93131-104">3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="93131-105">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="93131-105">Change description</span></span>

<span data-ttu-id="93131-106">A partir do .NET Core 3,0 Preview 8, o atributo [obsoleto](xref:System.ObsoleteAttribute) foi aplicado à <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constante.</span><span class="sxs-lookup"><span data-stu-id="93131-106">Starting with .NET Core 3.0 Preview 8, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant.</span></span> <span data-ttu-id="93131-107">O uso da constante produz um aviso do compilador.</span><span class="sxs-lookup"><span data-stu-id="93131-107">Use of the constant produces a compiler warning.</span></span> <span data-ttu-id="93131-108">Em .NET Framework e versões anteriores do .NET Core, ele não foi marcado como obsoleto.</span><span class="sxs-lookup"><span data-stu-id="93131-108">In .NET Framework and previous releases of .NET Core, it was not marked as obsolete.</span></span>

<span data-ttu-id="93131-109">Essa alteração foi feita para dar suporte a Visual Basic como uma linguagem para o desenvolvimento de várias plataformas.</span><span class="sxs-lookup"><span data-stu-id="93131-109">This change was made to support Visual Basic as a language for multi-platform development.</span></span> <span data-ttu-id="93131-110">A <xref:Microsoft.VisualBasic.Constants.vbNewLine> constante é equivalente a `\r\n` , a seqüência de caracteres de nova linha no Windows.</span><span class="sxs-lookup"><span data-stu-id="93131-110">The <xref:Microsoft.VisualBasic.Constants.vbNewLine> constant is equivalent to `\r\n`, the newline character sequence on Windows.</span></span> <span data-ttu-id="93131-111">Em sistemas baseados em UNIX, o caractere de nova linha é `\n` .</span><span class="sxs-lookup"><span data-stu-id="93131-111">On Unix-based systems, the newline character is `\n`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="93131-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="93131-112">Recommended action</span></span>

<span data-ttu-id="93131-113">A mensagem de atributo [obsoleto](xref:System.ObsoleteAttribute) para <xref:Microsoft.VisualBasic.Constants.vbNewLine> o inclui a seguinte recomendação:</span><span class="sxs-lookup"><span data-stu-id="93131-113">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for <xref:Microsoft.VisualBasic.Constants.vbNewLine> includes the following recommendation:</span></span>

<span data-ttu-id="93131-114">Para um retorno de carro e alimentação de linha, use <xref:Microsoft.VisualBasic.Constants.vbCrLf> .</span><span class="sxs-lookup"><span data-stu-id="93131-114">For a carriage return and line feed, use <xref:Microsoft.VisualBasic.Constants.vbCrLf>.</span></span> <span data-ttu-id="93131-115">Para a nova linha da plataforma atual, use <xref:System.Environment.NewLine?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="93131-115">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="93131-116">Categoria</span><span class="sxs-lookup"><span data-stu-id="93131-116">Category</span></span>

<span data-ttu-id="93131-117">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="93131-117">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="93131-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="93131-118">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

#### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->

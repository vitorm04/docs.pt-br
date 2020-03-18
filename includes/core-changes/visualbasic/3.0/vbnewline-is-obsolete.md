---
ms.openlocfilehash: 95a4c807f5c1077cf52f54b196e904ebc98c32f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116368"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="d7c1f-101">Microsoft.VisualBasic.Constants.vbNewLine é obsoleto</span><span class="sxs-lookup"><span data-stu-id="d7c1f-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="d7c1f-102">A <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constante é marcada como [ \[Obsoleta\] ](xref:System.ObsoleteAttribute) começando com .NET Core 3.0 Preview 8.</span><span class="sxs-lookup"><span data-stu-id="d7c1f-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked as [\[Obsolete\]](xref:System.ObsoleteAttribute) starting with .NET Core 3.0 Preview 8.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d7c1f-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="d7c1f-103">Version introduced</span></span>

<span data-ttu-id="d7c1f-104">3.0 Visualização 8</span><span class="sxs-lookup"><span data-stu-id="d7c1f-104">3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="d7c1f-105">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="d7c1f-105">Change description</span></span>

<span data-ttu-id="d7c1f-106">Começando com .NET Core 3.0 [Obsolete](xref:System.ObsoleteAttribute) Preview 8, o <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> atributo Obsolete foi aplicado à constante.</span><span class="sxs-lookup"><span data-stu-id="d7c1f-106">Starting with .NET Core 3.0 Preview 8, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant.</span></span> <span data-ttu-id="d7c1f-107">O uso da constante produz um aviso compilador.</span><span class="sxs-lookup"><span data-stu-id="d7c1f-107">Use of the constant produces a compiler warning.</span></span> <span data-ttu-id="d7c1f-108">No .NET Framework e nas versões anteriores do .NET Core, ele não foi marcado como obsoleto.</span><span class="sxs-lookup"><span data-stu-id="d7c1f-108">In .NET Framework and previous releases of .NET Core, it was not marked as obsolete.</span></span>

<span data-ttu-id="d7c1f-109">Essa mudança foi feita para apoiar o Visual Basic como uma linguagem para o desenvolvimento de várias plataformas.</span><span class="sxs-lookup"><span data-stu-id="d7c1f-109">This change was made to support Visual Basic as a language for multi-platform development.</span></span> <span data-ttu-id="d7c1f-110">A <xref:Microsoft.VisualBasic.Constants.vbNewLine> constante é `\r\n`equivalente à seqüência de caracteres newline no Windows.</span><span class="sxs-lookup"><span data-stu-id="d7c1f-110">The <xref:Microsoft.VisualBasic.Constants.vbNewLine> constant is equivalent to `\r\n`, the newline character sequence on Windows.</span></span> <span data-ttu-id="d7c1f-111">Nos sistemas baseados em Unix, `\n`o caractere newline é .</span><span class="sxs-lookup"><span data-stu-id="d7c1f-111">On Unix-based systems, the newline character is `\n`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d7c1f-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="d7c1f-112">Recommended action</span></span>

<span data-ttu-id="d7c1f-113">A mensagem <xref:Microsoft.VisualBasic.Constants.vbNewLine> de atributo [Obsoleto](xref:System.ObsoleteAttribute) para inclui a seguinte recomendação:</span><span class="sxs-lookup"><span data-stu-id="d7c1f-113">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for <xref:Microsoft.VisualBasic.Constants.vbNewLine> includes the following recommendation:</span></span>

<span data-ttu-id="d7c1f-114">Para um retorno de carruagem <xref:Microsoft.VisualBasic.Constants.vbCrLf>e alimentação de linha, use .</span><span class="sxs-lookup"><span data-stu-id="d7c1f-114">For a carriage return and line feed, use <xref:Microsoft.VisualBasic.Constants.vbCrLf>.</span></span> <span data-ttu-id="d7c1f-115">Para a nova linha da <xref:System.Environment.NewLine?displayProperty=nameWithType>plataforma atual, use .</span><span class="sxs-lookup"><span data-stu-id="d7c1f-115">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="d7c1f-116">Categoria</span><span class="sxs-lookup"><span data-stu-id="d7c1f-116">Category</span></span>

<span data-ttu-id="d7c1f-117">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d7c1f-117">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d7c1f-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="d7c1f-118">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->

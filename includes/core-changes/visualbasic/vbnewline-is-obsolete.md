---
ms.openlocfilehash: 86cdb845c436f424bbcc70e0736568031143b204
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522653"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="73a71-101">Microsoft. VisualBasic. Constants. vbNewLine é obsoleto</span><span class="sxs-lookup"><span data-stu-id="73a71-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="73a71-102">A constante <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> é marcada como [obsoleta](xref:System.ObsoleteAttribute) a partir do .net Core 3,0 Preview 8.</span><span class="sxs-lookup"><span data-stu-id="73a71-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked [Obsolete](xref:System.ObsoleteAttribute) starting with .NET Core 3.0 Preview 8.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="73a71-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="73a71-103">Version introduced</span></span>

<span data-ttu-id="73a71-104">3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="73a71-104">3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="73a71-105">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="73a71-105">Change description</span></span>

<span data-ttu-id="73a71-106">A partir do .NET Core 3,0 Preview 8, o atributo [obsoleto](xref:System.ObsoleteAttribute) foi aplicado à constante <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="73a71-106">Starting with .NET Core 3.0 Preview 8, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant.</span></span> <span data-ttu-id="73a71-107">O uso da constante produz um aviso do compilador.</span><span class="sxs-lookup"><span data-stu-id="73a71-107">Use of the constant produces a compiler warning.</span></span> <span data-ttu-id="73a71-108">Nas versões anteriores do .NET Core e .NET Framework, ela não estava marcada como obsoleta.</span><span class="sxs-lookup"><span data-stu-id="73a71-108">In previous releases of both .NET Core and .NET Framework, it was not marked as obsolete.</span></span>

<span data-ttu-id="73a71-109">Essa alteração foi feita para dar suporte a Visual Basic como uma linguagem para o desenvolvimento de várias plataformas.</span><span class="sxs-lookup"><span data-stu-id="73a71-109">This change was made to support Visual Basic as a language for multi-platform development.</span></span> <span data-ttu-id="73a71-110">A constante `vbNewLine` é equivalente a `\r\n`, a seqüência de caracteres de nova linha no Windows.</span><span class="sxs-lookup"><span data-stu-id="73a71-110">The `vbNewLine` constant is equivalent to `\r\n`, the newline character sequence on Windows.</span></span> <span data-ttu-id="73a71-111">Em sistemas baseados em UNIX, o caractere de nova linha é `\n`.</span><span class="sxs-lookup"><span data-stu-id="73a71-111">On Unix-based systems, the newline character is `\n`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="73a71-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="73a71-112">Recommended action</span></span>

<span data-ttu-id="73a71-113">A mensagem de atributo [obsoleto](xref:System.ObsoleteAttribute) para o `vbNewLine` inclui a seguinte recomendação:</span><span class="sxs-lookup"><span data-stu-id="73a71-113">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for `vbNewLine` includes the following recommendation:</span></span>

> <span data-ttu-id="73a71-114">Para um retorno de carro e alimentação de linha, use [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf).</span><span class="sxs-lookup"><span data-stu-id="73a71-114">For a carriage return and line feed, use [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf).</span></span> <span data-ttu-id="73a71-115">Para a nova linha da plataforma atual, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="73a71-115">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="73a71-116">Categoria</span><span class="sxs-lookup"><span data-stu-id="73a71-116">Category</span></span>

<span data-ttu-id="73a71-117">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="73a71-117">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="73a71-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="73a71-118">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->

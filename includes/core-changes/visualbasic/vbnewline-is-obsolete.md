---
ms.openlocfilehash: f7c13688236f3d66f3225ecf5d93b4c3284e2e71
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002896"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="03db3-101">Microsoft. VisualBasic. Constants. vbNewLine é obsoleto</span><span class="sxs-lookup"><span data-stu-id="03db3-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="03db3-102">A constante <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> é marcada como [obsoleta](xref:System.ObsoleteAttribute) a partir do .net Core 3,0 Preview 8.</span><span class="sxs-lookup"><span data-stu-id="03db3-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked [Obsolete](xref:System.ObsoleteAttribute) starting with .NET Core 3.0 Preview 8.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="03db3-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="03db3-103">Version introduced</span></span>

<span data-ttu-id="03db3-104">3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="03db3-104">3.0 Preview 8</span></span>

#### <a name="details"></a><span data-ttu-id="03db3-105">Detalhes</span><span class="sxs-lookup"><span data-stu-id="03db3-105">Details</span></span>

<span data-ttu-id="03db3-106">A partir do .NET Core 3,0 Preview 8, o atributo [obsoleto](xref:System.ObsoleteAttribute) foi aplicado à constante <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="03db3-106">Starting with .NET Core 3.0 Preview 8, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant.</span></span> <span data-ttu-id="03db3-107">O uso da constante produz um aviso do compilador.</span><span class="sxs-lookup"><span data-stu-id="03db3-107">Use of the constant produces a compiler warning.</span></span> <span data-ttu-id="03db3-108">Nas versões anteriores do .NET Core e .NET Framework, ela não estava marcada como obsoleta.</span><span class="sxs-lookup"><span data-stu-id="03db3-108">In previous releases of both .NET Core and .NET Framework, it was not marked as obsolete.</span></span>

<span data-ttu-id="03db3-109">Essa alteração foi feita para dar suporte a Visual Basic como uma linguagem para o desenvolvimento de várias plataformas.</span><span class="sxs-lookup"><span data-stu-id="03db3-109">This change was made to support Visual Basic as a language for multi-platform development.</span></span> <span data-ttu-id="03db3-110">A constante `vbNewLine` é equivalente a `\r\n`, a seqüência de caracteres de nova linha no Windows.</span><span class="sxs-lookup"><span data-stu-id="03db3-110">The `vbNewLine` constant is equivalent to `\r\n`, the newline character sequence on Windows.</span></span> <span data-ttu-id="03db3-111">Em sistemas baseados em UNIX, o caractere de nova linha é `\n`.</span><span class="sxs-lookup"><span data-stu-id="03db3-111">On Unix-based systems, the newline character is `\n`.</span></span>
 
#### <a name="recommended-action"></a><span data-ttu-id="03db3-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="03db3-112">Recommended action</span></span>

<span data-ttu-id="03db3-113">A mensagem de atributo [obsoleto](xref:System.ObsoleteAttribute) para `vbNewLine` inclui a seguinte recomendação:</span><span class="sxs-lookup"><span data-stu-id="03db3-113">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for `vbNewLine` includes the following recommendation:</span></span>

> <span data-ttu-id="03db3-114">Para um retorno de carro e alimentação de linha, use [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf).</span><span class="sxs-lookup"><span data-stu-id="03db3-114">For a carriage return and line feed, use [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf).</span></span> <span data-ttu-id="03db3-115">Para a nova linha da plataforma atual, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="03db3-115">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="03db3-116">Categoria</span><span class="sxs-lookup"><span data-stu-id="03db3-116">Category</span></span>

<span data-ttu-id="03db3-117">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="03db3-117">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="03db3-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="03db3-118">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-- >


---
ms.openlocfilehash: 072ed716910e2e1f1f98dbddc56d5bd097b75acc
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555898"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="b9e18-101">Microsoft. VisualBasic. Constants. vbNewLine é obsoleto</span><span class="sxs-lookup"><span data-stu-id="b9e18-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="b9e18-102">A <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constante é marcada como [ \[ obsoleta \] ](xref:System.ObsoleteAttribute) a partir do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="b9e18-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked as [\[Obsolete\]](xref:System.ObsoleteAttribute) starting with .NET Core 3.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b9e18-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="b9e18-103">Version introduced</span></span>

<span data-ttu-id="b9e18-104">3.0</span><span class="sxs-lookup"><span data-stu-id="b9e18-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="b9e18-105">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="b9e18-105">Change description</span></span>

<span data-ttu-id="b9e18-106">A partir do .NET Core 3,0, o atributo [obsoleto](xref:System.ObsoleteAttribute) foi aplicado à <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constante.</span><span class="sxs-lookup"><span data-stu-id="b9e18-106">Starting with .NET Core 3.0, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant.</span></span> <span data-ttu-id="b9e18-107">O uso da constante produz um aviso do compilador.</span><span class="sxs-lookup"><span data-stu-id="b9e18-107">Use of the constant produces a compiler warning.</span></span> <span data-ttu-id="b9e18-108">Em .NET Framework e versões anteriores do .NET Core, ele não foi marcado como obsoleto.</span><span class="sxs-lookup"><span data-stu-id="b9e18-108">In .NET Framework and previous releases of .NET Core, it was not marked as obsolete.</span></span>

<span data-ttu-id="b9e18-109">Essa alteração foi feita para dar suporte a Visual Basic como uma linguagem para o desenvolvimento de várias plataformas.</span><span class="sxs-lookup"><span data-stu-id="b9e18-109">This change was made to support Visual Basic as a language for multi-platform development.</span></span> <span data-ttu-id="b9e18-110">A <xref:Microsoft.VisualBasic.Constants.vbNewLine> constante é equivalente a `\r\n` , a seqüência de caracteres de nova linha no Windows.</span><span class="sxs-lookup"><span data-stu-id="b9e18-110">The <xref:Microsoft.VisualBasic.Constants.vbNewLine> constant is equivalent to `\r\n`, the newline character sequence on Windows.</span></span> <span data-ttu-id="b9e18-111">Em sistemas baseados em UNIX, o caractere de nova linha é `\n` .</span><span class="sxs-lookup"><span data-stu-id="b9e18-111">On Unix-based systems, the newline character is `\n`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b9e18-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="b9e18-112">Recommended action</span></span>

<span data-ttu-id="b9e18-113">A mensagem de atributo [obsoleto](xref:System.ObsoleteAttribute) para <xref:Microsoft.VisualBasic.Constants.vbNewLine> o inclui a seguinte recomendação:</span><span class="sxs-lookup"><span data-stu-id="b9e18-113">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for <xref:Microsoft.VisualBasic.Constants.vbNewLine> includes the following recommendation:</span></span>

<span data-ttu-id="b9e18-114">Para um retorno de carro e alimentação de linha, use <xref:Microsoft.VisualBasic.Constants.vbCrLf> .</span><span class="sxs-lookup"><span data-stu-id="b9e18-114">For a carriage return and line feed, use <xref:Microsoft.VisualBasic.Constants.vbCrLf>.</span></span> <span data-ttu-id="b9e18-115">Para a nova linha da plataforma atual, use <xref:System.Environment.NewLine?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b9e18-115">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="b9e18-116">Categoria</span><span class="sxs-lookup"><span data-stu-id="b9e18-116">Category</span></span>

<span data-ttu-id="b9e18-117">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b9e18-117">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b9e18-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="b9e18-118">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

#### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->

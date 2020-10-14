---
ms.openlocfilehash: 80d13609f1b02ae0ac875b2028e745670bb8f503
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050554"
---
### <a name="frameworkdescriptions-value-is-net-instead-of-net-core"></a><span data-ttu-id="15f66-101">O valor de FrameworkDescription é .NET, em vez de .NET Core</span><span class="sxs-lookup"><span data-stu-id="15f66-101">FrameworkDescription's value is .NET instead of .NET Core</span></span>

<span data-ttu-id="15f66-102"><xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> agora retorna ".NET" em vez de ".NET Core".</span><span class="sxs-lookup"><span data-stu-id="15f66-102"><xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> now returns ".NET" instead of ".NET Core".</span></span>

#### <a name="change-description"></a><span data-ttu-id="15f66-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="15f66-103">Change description</span></span>

<span data-ttu-id="15f66-104">Nas versões anteriores do .NET, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> retorna ".NET Core" como parte da cadeia de caracteres de descrição, por exemplo, `.NET Core 3.1.1` .</span><span class="sxs-lookup"><span data-stu-id="15f66-104">In previous .NET versions, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> returns ".NET Core" as part of the description string, for example, `.NET Core 3.1.1`.</span></span>

<span data-ttu-id="15f66-105">A partir do .NET 5,0, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> retorna ".net" como parte da cadeia de caracteres de descrição, por exemplo, `.NET 5.0.0` .</span><span class="sxs-lookup"><span data-stu-id="15f66-105">Starting in .NET 5.0, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> returns ".NET" as part of the description string, for example, `.NET 5.0.0`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="15f66-106">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="15f66-106">Reason for change</span></span>

<span data-ttu-id="15f66-107">Com o .NET 5, `netcoreapp` é substituído pelo `net` como o moniker de estrutura de destino curto.</span><span class="sxs-lookup"><span data-stu-id="15f66-107">With .NET 5, `netcoreapp` is replaced by `net` as the short target-framework moniker.</span></span> <span data-ttu-id="15f66-108">Para consistência, a descrição da estrutura também foi atualizada.</span><span class="sxs-lookup"><span data-stu-id="15f66-108">For consistency, the framework's description has also been updated.</span></span> <span data-ttu-id="15f66-109">A alteração é superficial, pois a `FrameworkName` não é codificada em nenhum outro lugar do que na <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="15f66-109">The change is cosmetic, as the `FrameworkName` isn't encoded anywhere else than in the <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> property.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="15f66-110">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="15f66-110">Version introduced</span></span>

<span data-ttu-id="15f66-111">5.0</span><span class="sxs-lookup"><span data-stu-id="15f66-111">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="15f66-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="15f66-112">Recommended action</span></span>

<span data-ttu-id="15f66-113">Atualize qualquer código que pesquise ".NET Core" na cadeia de caracteres retornada por <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription> .</span><span class="sxs-lookup"><span data-stu-id="15f66-113">Update any code that searches for ".NET Core" in the string returned by <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription>.</span></span>

#### <a name="category"></a><span data-ttu-id="15f66-114">Categoria</span><span class="sxs-lookup"><span data-stu-id="15f66-114">Category</span></span>

<span data-ttu-id="15f66-115">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="15f66-115">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="15f66-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="15f66-116">Affected APIs</span></span>

- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->

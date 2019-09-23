---
ms.openlocfilehash: bb163d5a6eb3d926a44a83ea79572c3a497bbe8d
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181735"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a><span data-ttu-id="56678-101">Os tipos no namespace Microsoft. VisualBasic. Devices não estão disponíveis</span><span class="sxs-lookup"><span data-stu-id="56678-101">Types in Microsoft.VisualBasic.Devices namespace not available</span></span>

<span data-ttu-id="56678-102">Os tipos no <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace não estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="56678-102">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="56678-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="56678-103">Version introduced</span></span>

<span data-ttu-id="56678-104">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="56678-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="details"></a><span data-ttu-id="56678-105">Detalhes</span><span class="sxs-lookup"><span data-stu-id="56678-105">Details</span></span>

<span data-ttu-id="56678-106">Os tipos no <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace estavam disponíveis em algumas versões de visualização do .NET Core 3,0,.</span><span class="sxs-lookup"><span data-stu-id="56678-106">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases,.</span></span> <span data-ttu-id="56678-107">Eles não estão mais disponíveis a partir do .NET Core 3,0 Preview 9.</span><span class="sxs-lookup"><span data-stu-id="56678-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="56678-108">Os tipos foram removidos para evitar dependências de assembly desnecessárias ou alterações significativas nas versões subsequentes.</span><span class="sxs-lookup"><span data-stu-id="56678-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>
 
#### <a name="recommended-action"></a><span data-ttu-id="56678-109">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="56678-109">Recommended action</span></span>

<span data-ttu-id="56678-110">Se o seu código depende do uso de <xref:Microsoft.VisualBasic.Devices> tipos e de seus membros, você poderá usar um tipo ou membro correspondente na biblioteca de classes do .net.</span><span class="sxs-lookup"><span data-stu-id="56678-110">If your code depends on the use of <xref:Microsoft.VisualBasic.Devices> types and their members, you may be able to use a corresponding type or member in the .NET class library.</span></span> <span data-ttu-id="56678-111">Por exemplo, a funcionalidade equivalente à <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> classe é fornecida <xref:System.DateTime?displayProperty=nameWithType> pelos tipos e <xref:System.Environment?displayProperty=nameWithType> e a funcionalidade equivalente à <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> classe é fornecida por tipos no <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="56678-111">For example, equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> class is provided by the <xref:System.DateTime?displayProperty=nameWithType> and <xref:System.Environment?displayProperty=nameWithType> types, and equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> class is provided by types in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span>

#### <a name="category"></a><span data-ttu-id="56678-112">Categoria</span><span class="sxs-lookup"><span data-stu-id="56678-112">Category</span></span>

<span data-ttu-id="56678-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="56678-113">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="56678-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="56678-114">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-- >


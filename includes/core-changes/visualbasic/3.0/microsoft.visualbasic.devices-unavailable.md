---
ms.openlocfilehash: a35de09b9a7bb9686433205359c3cc55954c29c3
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721786"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a><span data-ttu-id="b725a-101">Os tipos no namespace Microsoft. VisualBasic. Devices não estão disponíveis</span><span class="sxs-lookup"><span data-stu-id="b725a-101">Types in Microsoft.VisualBasic.Devices namespace not available</span></span>

<span data-ttu-id="b725a-102">Os tipos no <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace não estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="b725a-102">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b725a-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="b725a-103">Version introduced</span></span>

<span data-ttu-id="b725a-104">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="b725a-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="b725a-105">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="b725a-105">Change description</span></span>

<span data-ttu-id="b725a-106">Os tipos no <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace estavam disponíveis em algumas versões de visualização do .NET Core 3,0,.</span><span class="sxs-lookup"><span data-stu-id="b725a-106">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases,.</span></span> <span data-ttu-id="b725a-107">Eles não estão mais disponíveis a partir do .NET Core 3,0 Preview 9.</span><span class="sxs-lookup"><span data-stu-id="b725a-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="b725a-108">Os tipos foram removidos para evitar dependências de assembly desnecessárias ou alterações significativas nas versões subsequentes.</span><span class="sxs-lookup"><span data-stu-id="b725a-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b725a-109">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="b725a-109">Recommended action</span></span>

<span data-ttu-id="b725a-110">Se o seu código depende do uso de <xref:Microsoft.VisualBasic.Devices> tipos e de seus membros, você poderá usar um tipo ou membro correspondente na biblioteca de classes do .net.</span><span class="sxs-lookup"><span data-stu-id="b725a-110">If your code depends on the use of <xref:Microsoft.VisualBasic.Devices> types and their members, you may be able to use a corresponding type or member in the .NET class library.</span></span> <span data-ttu-id="b725a-111">Por exemplo, a funcionalidade equivalente à <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> classe é fornecida pelos <xref:System.DateTime?displayProperty=nameWithType> tipos e e a <xref:System.Environment?displayProperty=nameWithType> funcionalidade equivalente à <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> classe é fornecida por tipos no <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="b725a-111">For example, equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> class is provided by the <xref:System.DateTime?displayProperty=nameWithType> and <xref:System.Environment?displayProperty=nameWithType> types, and equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> class is provided by types in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span>

#### <a name="category"></a><span data-ttu-id="b725a-112">Categoria</span><span class="sxs-lookup"><span data-stu-id="b725a-112">Category</span></span>

<span data-ttu-id="b725a-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b725a-113">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b725a-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="b725a-114">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

#### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-->

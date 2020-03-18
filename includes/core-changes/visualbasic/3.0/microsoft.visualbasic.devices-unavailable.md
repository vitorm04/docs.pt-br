---
ms.openlocfilehash: 7f528510e4158dad71280a7b1f269a231b8c60f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116364"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a><span data-ttu-id="10b3e-101">Tipos em Microsoft.VisualBasic.Espaço de nome dos dispositivos não disponíveis</span><span class="sxs-lookup"><span data-stu-id="10b3e-101">Types in Microsoft.VisualBasic.Devices namespace not available</span></span>

<span data-ttu-id="10b3e-102">Os tipos <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> no namespace não estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="10b3e-102">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="10b3e-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="10b3e-103">Version introduced</span></span>

<span data-ttu-id="10b3e-104">.NET Core 3.0 Visualização 8</span><span class="sxs-lookup"><span data-stu-id="10b3e-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="10b3e-105">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="10b3e-105">Change description</span></span>

<span data-ttu-id="10b3e-106">Os tipos <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> no namespace estavam disponíveis em algumas versões do .NET Core 3.0 Preview,.</span><span class="sxs-lookup"><span data-stu-id="10b3e-106">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases,.</span></span> <span data-ttu-id="10b3e-107">Eles não estão mais disponíveis a partir do .NET Core 3.0 Preview 9.</span><span class="sxs-lookup"><span data-stu-id="10b3e-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="10b3e-108">Os tipos foram removidos para evitar dependências de montagem desnecessárias ou alterações de quebra em versões subseqüentes.</span><span class="sxs-lookup"><span data-stu-id="10b3e-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="10b3e-109">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="10b3e-109">Recommended action</span></span>

<span data-ttu-id="10b3e-110">Se o seu código depender <xref:Microsoft.VisualBasic.Devices> do uso de tipos e seus membros, você poderá usar um tipo ou membro correspondente na biblioteca de classes .NET.</span><span class="sxs-lookup"><span data-stu-id="10b3e-110">If your code depends on the use of <xref:Microsoft.VisualBasic.Devices> types and their members, you may be able to use a corresponding type or member in the .NET class library.</span></span> <span data-ttu-id="10b3e-111">Por <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> exemplo, a funcionalidade equivalente à classe <xref:System.DateTime?displayProperty=nameWithType> <xref:System.Environment?displayProperty=nameWithType> é fornecida pelos e <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> tipos, e a funcionalidade <xref:System.IO.Ports?displayProperty=nameWithType> equivalente à classe é fornecida por tipos no namespace.</span><span class="sxs-lookup"><span data-stu-id="10b3e-111">For example, equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> class is provided by the <xref:System.DateTime?displayProperty=nameWithType> and <xref:System.Environment?displayProperty=nameWithType> types, and equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> class is provided by types in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span>

#### <a name="category"></a><span data-ttu-id="10b3e-112">Categoria</span><span class="sxs-lookup"><span data-stu-id="10b3e-112">Category</span></span>

<span data-ttu-id="10b3e-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="10b3e-113">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="10b3e-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="10b3e-114">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-->

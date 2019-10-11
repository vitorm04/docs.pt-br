---
ms.openlocfilehash: dae4afa92b8833f326b4eacd00b36bb3e1199cc1
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237276"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a><span data-ttu-id="14988-101">Os tipos no namespace Microsoft. VisualBasic. Devices não estão disponíveis</span><span class="sxs-lookup"><span data-stu-id="14988-101">Types in Microsoft.VisualBasic.Devices namespace not available</span></span>

<span data-ttu-id="14988-102">Os tipos no namespace <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> não estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="14988-102">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="14988-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="14988-103">Version introduced</span></span>

<span data-ttu-id="14988-104">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="14988-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="14988-105">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="14988-105">Change description</span></span>

<span data-ttu-id="14988-106">Os tipos no namespace <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> estavam disponíveis em algumas versões de visualização do .NET Core 3,0,.</span><span class="sxs-lookup"><span data-stu-id="14988-106">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases,.</span></span> <span data-ttu-id="14988-107">Eles não estão mais disponíveis a partir do .NET Core 3,0 Preview 9.</span><span class="sxs-lookup"><span data-stu-id="14988-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="14988-108">Os tipos foram removidos para evitar dependências de assembly desnecessárias ou alterações significativas nas versões subsequentes.</span><span class="sxs-lookup"><span data-stu-id="14988-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>
 
#### <a name="recommended-action"></a><span data-ttu-id="14988-109">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="14988-109">Recommended action</span></span>

<span data-ttu-id="14988-110">Se seu código depende do uso de tipos <xref:Microsoft.VisualBasic.Devices> e seus membros, você poderá usar um tipo ou membro correspondente na biblioteca de classes do .NET.</span><span class="sxs-lookup"><span data-stu-id="14988-110">If your code depends on the use of <xref:Microsoft.VisualBasic.Devices> types and their members, you may be able to use a corresponding type or member in the .NET class library.</span></span> <span data-ttu-id="14988-111">Por exemplo, a funcionalidade equivalente à classe <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> é fornecida pelos tipos <xref:System.DateTime?displayProperty=nameWithType> e <xref:System.Environment?displayProperty=nameWithType>, e a funcionalidade equivalente à classe <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> é fornecida por tipos no namespace <xref:System.IO.Ports?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="14988-111">For example, equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> class is provided by the <xref:System.DateTime?displayProperty=nameWithType> and <xref:System.Environment?displayProperty=nameWithType> types, and equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> class is provided by types in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span>

#### <a name="category"></a><span data-ttu-id="14988-112">Categoria</span><span class="sxs-lookup"><span data-stu-id="14988-112">Category</span></span>

<span data-ttu-id="14988-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="14988-113">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="14988-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="14988-114">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-- >


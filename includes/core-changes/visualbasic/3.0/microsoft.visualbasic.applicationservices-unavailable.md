---
ms.openlocfilehash: 09027863ff2f0009a14578db35db870c27369726
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720947"
---
### <a name="types-in-microsoftvisualbasicapplicationservices-namespace-not-available"></a><span data-ttu-id="32730-101">Os tipos no namespace Microsoft. VisualBasic. ApplicationServices não estão disponíveis</span><span class="sxs-lookup"><span data-stu-id="32730-101">Types in Microsoft.VisualBasic.ApplicationServices namespace not available</span></span>

<span data-ttu-id="32730-102">Os tipos no <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> namespace não estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="32730-102">The types in the <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="32730-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="32730-103">Version introduced</span></span>

<span data-ttu-id="32730-104">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="32730-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="32730-105">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="32730-105">Change description</span></span>

<span data-ttu-id="32730-106">Os tipos no <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> namespace estavam disponíveis em algumas versões de visualização do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="32730-106">The types in the <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases.</span></span> <span data-ttu-id="32730-107">Eles não estão mais disponíveis a partir do .NET Core 3,0 Preview 9.</span><span class="sxs-lookup"><span data-stu-id="32730-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="32730-108">Os tipos foram removidos para evitar dependências de assembly desnecessárias ou alterações significativas nas versões subsequentes.</span><span class="sxs-lookup"><span data-stu-id="32730-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="32730-109">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="32730-109">Recommended action</span></span>

<span data-ttu-id="32730-110">Se o seu código depende do uso de <xref:Microsoft.VisualBasic.ApplicationServices> tipos e de seus membros, você poderá usar um tipo ou membro correspondente na biblioteca de classes do .net.</span><span class="sxs-lookup"><span data-stu-id="32730-110">If your code depends on the use of <xref:Microsoft.VisualBasic.ApplicationServices> types and their members, you may be able to use a corresponding type or member in the .NET class library.</span></span> <span data-ttu-id="32730-111">Por exemplo, alguns <xref:System.Environment?displayProperty=nameWithType> <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> Membros e fornecem funcionalidade equivalente às propriedades da <xref:Microsoft.VisualBasic.ApplicationServices.User?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="32730-111">For example, some <xref:System.Environment?displayProperty=nameWithType> and <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> members provide equivalent functionality to the properties of the <xref:Microsoft.VisualBasic.ApplicationServices.User?displayProperty=nameWithType> class.</span></span>

#### <a name="category"></a><span data-ttu-id="32730-112">Categoria</span><span class="sxs-lookup"><span data-stu-id="32730-112">Category</span></span>

<span data-ttu-id="32730-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="32730-113">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="32730-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="32730-114">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName>

<!--

#### Affected APIs

- `N:Microsoft.VisualBasic.ApplicationServices`

-->

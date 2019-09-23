---
ms.openlocfilehash: ba543414d4f84362c9b9b876395815e837efbd3f
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181748"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a><span data-ttu-id="6ff88-101">Tipos no namespace Microsoft. VisualBasic. MyServices não estão disponíveis</span><span class="sxs-lookup"><span data-stu-id="6ff88-101">Types in Microsoft.VisualBasic.MyServices namespace not available</span></span>

<span data-ttu-id="6ff88-102">Os tipos no <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace não estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="6ff88-102">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6ff88-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="6ff88-103">Version introduced</span></span>

<span data-ttu-id="6ff88-104">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="6ff88-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="details"></a><span data-ttu-id="6ff88-105">Detalhes</span><span class="sxs-lookup"><span data-stu-id="6ff88-105">Details</span></span>

<span data-ttu-id="6ff88-106">Os tipos no <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace estavam disponíveis em algumas versões de visualização do .NET Core 3,0,.</span><span class="sxs-lookup"><span data-stu-id="6ff88-106">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases,.</span></span> <span data-ttu-id="6ff88-107">Eles não estão mais disponíveis a partir do .NET Core 3,0 Preview 9.</span><span class="sxs-lookup"><span data-stu-id="6ff88-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="6ff88-108">Os tipos foram removidos para evitar dependências de assembly desnecessárias ou alterações significativas nas versões subsequentes.</span><span class="sxs-lookup"><span data-stu-id="6ff88-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>
 
#### <a name="recommended-action"></a><span data-ttu-id="6ff88-109">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="6ff88-109">Recommended action</span></span>

<span data-ttu-id="6ff88-110">Se seu código depende do uso de tipos **Microsoft. VisualBasic. MyServices** e seus membros, há tipos e membros correspondentes na biblioteca de classes do .net.</span><span class="sxs-lookup"><span data-stu-id="6ff88-110">If your code depends on the use of **Microsoft.VisualBasic.MyServices** types and their members, there are corresponding types and members in the .NET class library.</span></span> <span data-ttu-id="6ff88-111">Veja a seguir um mapeamento dos tipos **Microsoft. VisualBasic. MyServices** para seus tipos de biblioteca de classes do .net equivalentes:</span><span class="sxs-lookup"><span data-stu-id="6ff88-111">The following is a mapping of  **Microsoft.VisualBasic.MyServices** types to their equivalent .NET class library types:</span></span>

|<span data-ttu-id="6ff88-112">Tipo Microsoft. VisualBasic. MyServices</span><span class="sxs-lookup"><span data-stu-id="6ff88-112">Microsoft.VisualBasic.MyServices type</span></span>|<span data-ttu-id="6ff88-113">Tipo de biblioteca de classes .NET</span><span class="sxs-lookup"><span data-stu-id="6ff88-113">.NET class library type</span></span>|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<span data-ttu-id="6ff88-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType>para aplicativos do WPF <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> , para aplicativos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6ff88-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType> for WPF applications, <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> for Windows Forms applications</span></span>| 
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|<span data-ttu-id="6ff88-115">Tipos no <xref:System.IO> namespace</span><span class="sxs-lookup"><span data-stu-id="6ff88-115">Types in the <xref:System.IO> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|<span data-ttu-id="6ff88-116">Tipos relacionados ao registro no <xref:Microsoft.Win32> namespace</span><span class="sxs-lookup"><span data-stu-id="6ff88-116">Registry-related types in the <xref:Microsoft.Win32> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a><span data-ttu-id="6ff88-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="6ff88-117">Category</span></span>

<span data-ttu-id="6ff88-118">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6ff88-118">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6ff88-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="6ff88-119">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-- >


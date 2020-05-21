---
ms.openlocfilehash: acb8ed44b7d18b257731e32339f087c8fe5fdd4a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721567"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a><span data-ttu-id="fbb2d-101">Tipos no namespace Microsoft. VisualBasic. MyServices não estão disponíveis</span><span class="sxs-lookup"><span data-stu-id="fbb2d-101">Types in Microsoft.VisualBasic.MyServices namespace not available</span></span>

<span data-ttu-id="fbb2d-102">Os tipos no <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace não estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="fbb2d-102">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fbb2d-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="fbb2d-103">Version introduced</span></span>

<span data-ttu-id="fbb2d-104">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="fbb2d-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="fbb2d-105">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="fbb2d-105">Change description</span></span>

<span data-ttu-id="fbb2d-106">Os tipos no <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace estavam disponíveis em algumas versões de visualização do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="fbb2d-106">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases.</span></span> <span data-ttu-id="fbb2d-107">Eles não estão mais disponíveis a partir do .NET Core 3,0 Preview 9.</span><span class="sxs-lookup"><span data-stu-id="fbb2d-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="fbb2d-108">Os tipos foram removidos para evitar dependências de assembly desnecessárias ou alterações significativas nas versões subsequentes.</span><span class="sxs-lookup"><span data-stu-id="fbb2d-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fbb2d-109">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="fbb2d-109">Recommended action</span></span>

<span data-ttu-id="fbb2d-110">Se seu código depende do uso de tipos **Microsoft. VisualBasic. MyServices** e seus membros, há tipos e membros correspondentes na biblioteca de classes do .net.</span><span class="sxs-lookup"><span data-stu-id="fbb2d-110">If your code depends on the use of **Microsoft.VisualBasic.MyServices** types and their members, there are corresponding types and members in the .NET class library.</span></span> <span data-ttu-id="fbb2d-111">Veja a seguir um mapeamento dos tipos **Microsoft. VisualBasic. MyServices** para seus tipos de biblioteca de classes do .net equivalentes:</span><span class="sxs-lookup"><span data-stu-id="fbb2d-111">The following is a mapping of  **Microsoft.VisualBasic.MyServices** types to their equivalent .NET class library types:</span></span>

|<span data-ttu-id="fbb2d-112">Tipo Microsoft. VisualBasic. MyServices</span><span class="sxs-lookup"><span data-stu-id="fbb2d-112">Microsoft.VisualBasic.MyServices type</span></span>|<span data-ttu-id="fbb2d-113">Tipo de biblioteca de classes .NET</span><span class="sxs-lookup"><span data-stu-id="fbb2d-113">.NET class library type</span></span>|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<span data-ttu-id="fbb2d-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType>para aplicativos do WPF, <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> para aplicativos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fbb2d-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType> for WPF applications, <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> for Windows Forms applications</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|<span data-ttu-id="fbb2d-115">Tipos no <xref:System.IO> namespace</span><span class="sxs-lookup"><span data-stu-id="fbb2d-115">Types in the <xref:System.IO> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|<span data-ttu-id="fbb2d-116">Tipos relacionados ao registro no <xref:Microsoft.Win32> namespace</span><span class="sxs-lookup"><span data-stu-id="fbb2d-116">Registry-related types in the <xref:Microsoft.Win32> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a><span data-ttu-id="fbb2d-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="fbb2d-117">Category</span></span>

<span data-ttu-id="fbb2d-118">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fbb2d-118">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fbb2d-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="fbb2d-119">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

#### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-->

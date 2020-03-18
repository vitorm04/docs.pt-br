---
ms.openlocfilehash: d207a937917da78f6b902ad8ca4f02fa9a46c2e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116326"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a><span data-ttu-id="d59b1-101">Tipos em Microsoft.VisualBasic.MyServices namespace não disponíveis</span><span class="sxs-lookup"><span data-stu-id="d59b1-101">Types in Microsoft.VisualBasic.MyServices namespace not available</span></span>

<span data-ttu-id="d59b1-102">Os tipos <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> no namespace não estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d59b1-102">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d59b1-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="d59b1-103">Version introduced</span></span>

<span data-ttu-id="d59b1-104">.NET Core 3.0 Visualização 8</span><span class="sxs-lookup"><span data-stu-id="d59b1-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="d59b1-105">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="d59b1-105">Change description</span></span>

<span data-ttu-id="d59b1-106">Os tipos <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> no namespace estavam disponíveis em algumas versões do .NET Core 3.0 Preview.</span><span class="sxs-lookup"><span data-stu-id="d59b1-106">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases.</span></span> <span data-ttu-id="d59b1-107">Eles não estão mais disponíveis a partir do .NET Core 3.0 Preview 9.</span><span class="sxs-lookup"><span data-stu-id="d59b1-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="d59b1-108">Os tipos foram removidos para evitar dependências de montagem desnecessárias ou alterações de quebra em versões subseqüentes.</span><span class="sxs-lookup"><span data-stu-id="d59b1-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d59b1-109">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="d59b1-109">Recommended action</span></span>

<span data-ttu-id="d59b1-110">Se o seu código depender do uso dos tipos **Microsoft.VisualBasic.MyServices** e seus membros, há tipos e membros correspondentes na biblioteca de classes .NET.</span><span class="sxs-lookup"><span data-stu-id="d59b1-110">If your code depends on the use of **Microsoft.VisualBasic.MyServices** types and their members, there are corresponding types and members in the .NET class library.</span></span> <span data-ttu-id="d59b1-111">A seguir está um mapeamento dos tipos **Microsoft.VisualBasic.MyServices** para seus tipos de biblioteca de classe .NET equivalentes:</span><span class="sxs-lookup"><span data-stu-id="d59b1-111">The following is a mapping of  **Microsoft.VisualBasic.MyServices** types to their equivalent .NET class library types:</span></span>

|<span data-ttu-id="d59b1-112">Microsoft.VisualBasic.MyServices tipo</span><span class="sxs-lookup"><span data-stu-id="d59b1-112">Microsoft.VisualBasic.MyServices type</span></span>|<span data-ttu-id="d59b1-113">Tipo de biblioteca de classe .NET</span><span class="sxs-lookup"><span data-stu-id="d59b1-113">.NET class library type</span></span>|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<span data-ttu-id="d59b1-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType>para aplicativos WPF, <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> para aplicativos do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d59b1-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType> for WPF applications, <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> for Windows Forms applications</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|<span data-ttu-id="d59b1-115">Tipos no <xref:System.IO> namespace</span><span class="sxs-lookup"><span data-stu-id="d59b1-115">Types in the <xref:System.IO> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|<span data-ttu-id="d59b1-116">Tipos relacionados ao <xref:Microsoft.Win32> registro no namespace</span><span class="sxs-lookup"><span data-stu-id="d59b1-116">Registry-related types in the <xref:Microsoft.Win32> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a><span data-ttu-id="d59b1-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="d59b1-117">Category</span></span>

<span data-ttu-id="d59b1-118">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d59b1-118">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d59b1-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="d59b1-119">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-->

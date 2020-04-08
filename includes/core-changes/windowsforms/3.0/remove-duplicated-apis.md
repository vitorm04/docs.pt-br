---
ms.openlocfilehash: 0be59258df10aa13920551f011d68bc8efe20b93
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888094"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a><span data-ttu-id="a874b-101">APIs duplicadas removidas dos formulários do Windows</span><span class="sxs-lookup"><span data-stu-id="a874b-101">Duplicated APIs removed from Windows Forms</span></span>

<span data-ttu-id="a874b-102">Uma série de APIs acidentalmente <xref:System.Windows.Forms?displayProperty=fullName> duplicadas no namespace a partir do .NET Core 3.0 Preview 4 foram removidas no .NET Core 3.0 RC1.</span><span class="sxs-lookup"><span data-stu-id="a874b-102">A number of APIs accidentally duplicated in the <xref:System.Windows.Forms?displayProperty=fullName> namespace starting in .NET Core 3.0 Preview 4 have been removed in .NET Core 3.0 RC1.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a874b-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="a874b-103">Change description</span></span>

<span data-ttu-id="a874b-104">.NET Core 3.0 Preview 4 inadvertidamente duplicava <xref:System.Windows.Forms?displayProperty=fullName> uma série de tipos <xref:System.ComponentModel.Design?displayProperty=fullName> no namespace que já existiam no namespace.</span><span class="sxs-lookup"><span data-stu-id="a874b-104">.NET Core 3.0 Preview 4 inadvertently duplicated a number of types in the <xref:System.Windows.Forms?displayProperty=fullName> namespace that already existed in the <xref:System.ComponentModel.Design?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="a874b-105">A partir do .NET Core 3.0 RC1, esses tipos duplicados não estão mais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="a874b-105">Starting with .NET Core 3.0 RC1, these duplicated types are no longer available.</span></span> <span data-ttu-id="a874b-106">A tabela a seguir mostra listas do tipo original e seu tipo duplicado:</span><span class="sxs-lookup"><span data-stu-id="a874b-106">The following table shows lists the original type and its duplicated type:</span></span>

> [!div class="mx-tdCol2BreakAll"]
> |<span data-ttu-id="a874b-107">Tipo original</span><span class="sxs-lookup"><span data-stu-id="a874b-107">Original type</span></span>|<span data-ttu-id="a874b-108">Tipo duplicado</span><span class="sxs-lookup"><span data-stu-id="a874b-108">Duplicated type</span></span>|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a><span data-ttu-id="a874b-109">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="a874b-109">Version introduced</span></span>

<span data-ttu-id="a874b-110">3.0 RC1</span><span class="sxs-lookup"><span data-stu-id="a874b-110">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a874b-111">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="a874b-111">Recommended action</span></span>

<span data-ttu-id="a874b-112">Atualize o código para fazer referência ao tipo original, conforme mostrado na coluna **de tipo Original** da tabela.</span><span class="sxs-lookup"><span data-stu-id="a874b-112">Update the code to reference the original type, as shown in the **Original type** column of the table.</span></span>

#### <a name="category"></a><span data-ttu-id="a874b-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="a874b-113">Category</span></span>

<span data-ttu-id="a874b-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a874b-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a874b-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="a874b-115">Affected APIs</span></span>

- <span data-ttu-id="a874b-116">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a874b-116">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis.

-->

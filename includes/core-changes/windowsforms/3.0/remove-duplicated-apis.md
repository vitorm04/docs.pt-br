---
ms.openlocfilehash: e609b8006846cd202a6a7eeec2529cf1fbb09e7c
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937098"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a><span data-ttu-id="9a299-101">APIs duplicadas removidas do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9a299-101">Duplicated APIs removed from Windows Forms</span></span>

<span data-ttu-id="9a299-102">Várias APIs duplicadas acidentalmente no namespace <xref:System.Windows.Forms?displayProperty=fullName> a partir do .NET Core 3,0 Preview 4 foram removidas no .NET Core 3,0 RC1.</span><span class="sxs-lookup"><span data-stu-id="9a299-102">A number of APIs accidentally duplicated in the <xref:System.Windows.Forms?displayProperty=fullName> namespace starting in .NET Core 3.0 Preview 4 have been removed in .NET Core 3.0 RC1.</span></span>

#### <a name="change-description"></a><span data-ttu-id="9a299-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="9a299-103">Change description</span></span>

<span data-ttu-id="9a299-104">O .NET Core 3,0 Preview 4 duplicava inadvertidamente um número de tipos no namespace de <xref:System.Windows.Forms?displayProperty=fullName> que já existiam no namespace <xref:System.ComponentModel.Design?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="9a299-104">.NET Core 3.0 Preview 4 inadvertently duplicated a number of types in the <xref:System.Windows.Forms?displayProperty=fullName> namespace that already existed in the <xref:System.ComponentModel.Design?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="9a299-105">A partir do .NET Core 3,0 RC1, esses tipos duplicados não estão mais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="9a299-105">Starting with .NET Core 3.0 RC1, these duplicated types are no longer available.</span></span> <span data-ttu-id="9a299-106">A tabela a seguir mostra como lista o tipo original e seu tipo duplicado:</span><span class="sxs-lookup"><span data-stu-id="9a299-106">The following table shows lists the original type and its duplicated type:</span></span>

> [!div class="mx-tdCol2BreakAll"]
> |<span data-ttu-id="9a299-107">Tipo original</span><span class="sxs-lookup"><span data-stu-id="9a299-107">Original type</span></span>|<span data-ttu-id="9a299-108">Tipo duplicado</span><span class="sxs-lookup"><span data-stu-id="9a299-108">Duplicated type</span></span>|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a><span data-ttu-id="9a299-109">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="9a299-109">Version introduced</span></span>

<span data-ttu-id="9a299-110">RC1 3,0</span><span class="sxs-lookup"><span data-stu-id="9a299-110">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9a299-111">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="9a299-111">Recommended action</span></span>

<span data-ttu-id="9a299-112">Atualize o código para referenciar o tipo original, conforme mostrado na coluna **tipo original** da tabela.</span><span class="sxs-lookup"><span data-stu-id="9a299-112">Update the code to reference the original type, as shown in the **Original type** column of the table.</span></span>

#### <a name="category"></a><span data-ttu-id="9a299-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="9a299-113">Category</span></span>

<span data-ttu-id="9a299-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9a299-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9a299-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="9a299-115">Affected APIs</span></span>

- <span data-ttu-id="9a299-116">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="9a299-116">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis.

-->

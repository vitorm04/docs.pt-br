---
ms.openlocfilehash: 4fbec1028b6d75b90d4638814c877c263c8c8936
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181993"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a><span data-ttu-id="01d84-101">TypeDescriptionProviderAttribute movido para outro assembly</span><span class="sxs-lookup"><span data-stu-id="01d84-101">TypeDescriptionProviderAttribute moved to another assembly</span></span>

<span data-ttu-id="01d84-102">A <xref:System.ComponentModel.TypeDescriptionProviderAttribute> classe foi movida.</span><span class="sxs-lookup"><span data-stu-id="01d84-102">The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="01d84-103">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="01d84-103">Change description</span></span>

<span data-ttu-id="01d84-104">No .NET Core 2,2 e versões anteriores, a <xref:System.ComponentModel.TypeDescriptionProviderAttribute> classe é encontrada no assembly *System. ComponentModel. TypeConverter* .</span><span class="sxs-lookup"><span data-stu-id="01d84-104">In .NET Core 2.2 and earlier versions, The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="01d84-105">A partir do .NET Core 3,0, ele é encontrado no assembly *System. ObjectModel* .</span><span class="sxs-lookup"><span data-stu-id="01d84-105">Starting with .NET Core 3.0, it is found in the *System.ObjectModel* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="01d84-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="01d84-106">Version introduced</span></span>

<span data-ttu-id="01d84-107">3.0</span><span class="sxs-lookup"><span data-stu-id="01d84-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="01d84-108">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="01d84-108">Recommended action</span></span>

<span data-ttu-id="01d84-109">Essa alteração afeta apenas os aplicativos que usam a reflexão para <xref:System.ComponentModel.TypeDescriptionProviderAttribute> carregar o tipo chamando um método <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> como ou uma sobrecarga de <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> que assume que o tipo está em um assembly específico.</span><span class="sxs-lookup"><span data-stu-id="01d84-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.TypeDescriptionProviderAttribute> type by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="01d84-110">Se esse for o caso, o assembly referenciado na chamada do método deverá ser atualizado para refletir o novo local do assembly do tipo.</span><span class="sxs-lookup"><span data-stu-id="01d84-110">If that is the case, the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="01d84-111">Categoria</span><span class="sxs-lookup"><span data-stu-id="01d84-111">Category</span></span>

<span data-ttu-id="01d84-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="01d84-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="01d84-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="01d84-113">Affected APIs</span></span>

- <span data-ttu-id="01d84-114">Nenhum</span><span class="sxs-lookup"><span data-stu-id="01d84-114">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
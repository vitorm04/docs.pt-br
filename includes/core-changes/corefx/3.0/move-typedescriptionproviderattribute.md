---
ms.openlocfilehash: 57ca2ad839aab8d61da1a929660920efe1190334
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147530"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a><span data-ttu-id="ef2a6-101">TypeDescriptionProviderAttribute movido para outro conjunto</span><span class="sxs-lookup"><span data-stu-id="ef2a6-101">TypeDescriptionProviderAttribute moved to another assembly</span></span>

<span data-ttu-id="ef2a6-102">A <xref:System.ComponentModel.TypeDescriptionProviderAttribute> classe foi movida.</span><span class="sxs-lookup"><span data-stu-id="ef2a6-102">The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ef2a6-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="ef2a6-103">Change description</span></span>

<span data-ttu-id="ef2a6-104">Nas versões .NET Core 2.2 e anteriores, a <xref:System.ComponentModel.TypeDescriptionProviderAttribute> classe é encontrada no conjunto *System.ComponentModel.TypeConverter.*</span><span class="sxs-lookup"><span data-stu-id="ef2a6-104">In .NET Core 2.2 and earlier versions, The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="ef2a6-105">A partir do .NET Core 3.0, ele é encontrado no conjunto *System.ObjectModel.*</span><span class="sxs-lookup"><span data-stu-id="ef2a6-105">Starting with .NET Core 3.0, it is found in the *System.ObjectModel* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ef2a6-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="ef2a6-106">Version introduced</span></span>

<span data-ttu-id="ef2a6-107">3.0</span><span class="sxs-lookup"><span data-stu-id="ef2a6-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ef2a6-108">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="ef2a6-108">Recommended action</span></span>

<span data-ttu-id="ef2a6-109">Essa alteração afeta apenas aplicativos que usam <xref:System.ComponentModel.TypeDescriptionProviderAttribute> reflexão para carregar <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> o tipo <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> chamando um método como ou uma sobrecarga que assume que o tipo está em um conjunto específico.</span><span class="sxs-lookup"><span data-stu-id="ef2a6-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.TypeDescriptionProviderAttribute> type by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="ef2a6-110">Se esse for o caso, a montagem referenciada na chamada do método deve ser atualizada para refletir o novo local de montagem do tipo.</span><span class="sxs-lookup"><span data-stu-id="ef2a6-110">If that is the case, the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="ef2a6-111">Categoria</span><span class="sxs-lookup"><span data-stu-id="ef2a6-111">Category</span></span>

<span data-ttu-id="ef2a6-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ef2a6-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ef2a6-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ef2a6-113">Affected APIs</span></span>

<span data-ttu-id="ef2a6-114">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ef2a6-114">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->

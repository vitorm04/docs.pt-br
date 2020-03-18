---
ms.openlocfilehash: 19359422f79f8240676b0057c7391f6b06f961ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147543"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a><span data-ttu-id="ef5f7-101">InvalidAsynchronousStateException mudou-se para outro conjunto</span><span class="sxs-lookup"><span data-stu-id="ef5f7-101">InvalidAsynchronousStateException moved to another assembly</span></span>

<span data-ttu-id="ef5f7-102">A <xref:System.ComponentModel.InvalidAsynchronousStateException> classe foi movida.</span><span class="sxs-lookup"><span data-stu-id="ef5f7-102">The <xref:System.ComponentModel.InvalidAsynchronousStateException> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ef5f7-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="ef5f7-103">Change description</span></span>

<span data-ttu-id="ef5f7-104">Nas versões .NET Core 2.2 e anteriores, a <xref:System.ComponentModel.InvalidAsynchronousStateException> classe é encontrada no conjunto *System.ComponentModel.TypeConverter.*</span><span class="sxs-lookup"><span data-stu-id="ef5f7-104">In .NET Core 2.2 and earlier versions, the <xref:System.ComponentModel.InvalidAsynchronousStateException> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="ef5f7-105">A partir do .NET Core 3.0, ele é encontrado no conjunto *System.ComponentModel.Primitives.*</span><span class="sxs-lookup"><span data-stu-id="ef5f7-105">Starting with .NET Core 3.0, it is found in the *System.ComponentModel.Primitives* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ef5f7-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="ef5f7-106">Version introduced</span></span>

<span data-ttu-id="ef5f7-107">3.0</span><span class="sxs-lookup"><span data-stu-id="ef5f7-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ef5f7-108">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="ef5f7-108">Recommended action</span></span>

<span data-ttu-id="ef5f7-109">Essa alteração afeta apenas aplicativos que usam <xref:System.ComponentModel.InvalidAsynchronousStateException> reflexão para <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> carregar o <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> chamado de um método como ou uma sobrecarga que pressupõe que o tipo esteja em um conjunto específico.</span><span class="sxs-lookup"><span data-stu-id="ef5f7-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.InvalidAsynchronousStateException> by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="ef5f7-110">Se esse for o caso, a montagem da montagem referenciada na chamada do método deve ser atualizada para refletir o novo local de montagem do tipo.</span><span class="sxs-lookup"><span data-stu-id="ef5f7-110">If that is the case, the assembly the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="ef5f7-111">Categoria</span><span class="sxs-lookup"><span data-stu-id="ef5f7-111">Category</span></span>

<span data-ttu-id="ef5f7-112">CoreFx</span><span class="sxs-lookup"><span data-stu-id="ef5f7-112">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ef5f7-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ef5f7-113">Affected APIs</span></span>

<span data-ttu-id="ef5f7-114">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ef5f7-114">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->

---
ms.openlocfilehash: ace0a4a60ad4d3f3a13cf4bdb2431e61d04ad8e7
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021619"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a><span data-ttu-id="1c3ed-101">InvalidAsynchronousStateException mudou-se para outro conjunto</span><span class="sxs-lookup"><span data-stu-id="1c3ed-101">InvalidAsynchronousStateException moved to another assembly</span></span>

<span data-ttu-id="1c3ed-102">A <xref:System.ComponentModel.InvalidAsynchronousStateException> classe foi movida.</span><span class="sxs-lookup"><span data-stu-id="1c3ed-102">The <xref:System.ComponentModel.InvalidAsynchronousStateException> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1c3ed-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="1c3ed-103">Change description</span></span>

<span data-ttu-id="1c3ed-104">Nas versões .NET Core 2.2 e anteriores, a <xref:System.ComponentModel.InvalidAsynchronousStateException> classe é encontrada no conjunto *System.ComponentModel.TypeConverter.*</span><span class="sxs-lookup"><span data-stu-id="1c3ed-104">In .NET Core 2.2 and earlier versions, the <xref:System.ComponentModel.InvalidAsynchronousStateException> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="1c3ed-105">A partir do .NET Core 3.0, ele é encontrado no conjunto *System.ComponentModel.Primitives.*</span><span class="sxs-lookup"><span data-stu-id="1c3ed-105">Starting with .NET Core 3.0, it is found in the *System.ComponentModel.Primitives* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1c3ed-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="1c3ed-106">Version introduced</span></span>

<span data-ttu-id="1c3ed-107">3.0</span><span class="sxs-lookup"><span data-stu-id="1c3ed-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1c3ed-108">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="1c3ed-108">Recommended action</span></span>

<span data-ttu-id="1c3ed-109">Essa alteração afeta apenas aplicativos que usam <xref:System.ComponentModel.InvalidAsynchronousStateException> reflexão para <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> carregar o <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> chamado de um método como ou uma sobrecarga que pressupõe que o tipo esteja em um conjunto específico.</span><span class="sxs-lookup"><span data-stu-id="1c3ed-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.InvalidAsynchronousStateException> by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="1c3ed-110">Se esse for o caso, a montagem da montagem referenciada na chamada do método deve ser atualizada para refletir o novo local de montagem do tipo.</span><span class="sxs-lookup"><span data-stu-id="1c3ed-110">If that is the case, the assembly the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="1c3ed-111">Categoria</span><span class="sxs-lookup"><span data-stu-id="1c3ed-111">Category</span></span>

<span data-ttu-id="1c3ed-112">Bibliotecas Core .NET</span><span class="sxs-lookup"><span data-stu-id="1c3ed-112">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1c3ed-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="1c3ed-113">Affected APIs</span></span>

<span data-ttu-id="1c3ed-114">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="1c3ed-114">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->

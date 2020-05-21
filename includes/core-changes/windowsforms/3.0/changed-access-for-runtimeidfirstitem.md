---
ms.openlocfilehash: 1ea2d70a7cfe04cc4c4b9b58ea6bb6fa0226b245
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721461"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a><span data-ttu-id="94246-101">Alteração de acesso para AccessibleObject. RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="94246-101">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>

<span data-ttu-id="94246-102">A partir do .NET Core 3,0 RC1, a acessibilidade do `AccessibleObject.RuntimeIDFirstItem` foi alterada de `protected` para `internal` .</span><span class="sxs-lookup"><span data-stu-id="94246-102">Starting in .NET Core 3.0 RC1, the accessibility of `AccessibleObject.RuntimeIDFirstItem` has changed from `protected` to `internal`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="94246-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="94246-103">Change description</span></span>

<span data-ttu-id="94246-104">A partir do .NET Core 3,0 Preview 4, o `AccessibleObject.RuntimeIDFirstItem` campo era `protected` .</span><span class="sxs-lookup"><span data-stu-id="94246-104">Starting with .NET Core 3.0 Preview 4, the `AccessibleObject.RuntimeIDFirstItem` field was `protected`.</span></span> <span data-ttu-id="94246-105">A partir do .NET Core 3,0 RC1, ele mudou de `protected` para `internal` para alinhar com a acessibilidade do campo no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="94246-105">Starting with .NET Core 3.0 RC1, it has changed from `protected` to `internal` to align with the accessibility of the field in the .NET Framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="94246-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="94246-106">Version introduced</span></span>

<span data-ttu-id="94246-107">RC1 3,0</span><span class="sxs-lookup"><span data-stu-id="94246-107">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="94246-108">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="94246-108">Recommended action</span></span>

<span data-ttu-id="94246-109">A alteração poderá afetar você se você tiver desenvolvido um aplicativo .NET Core com um tipo que deriva de <xref:System.Windows.Forms.AccessibleObject> e acessa o `RuntimeIDFirstItem` campo.</span><span class="sxs-lookup"><span data-stu-id="94246-109">The change can affect you if you've developed a .NET Core app with a type that derives from <xref:System.Windows.Forms.AccessibleObject> and accesses the `RuntimeIDFirstItem` field.</span></span> <span data-ttu-id="94246-110">Se esse for o caso, você poderá definir uma constante local da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="94246-110">If this is the case, you can define a local constant as follows:</span></span>

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a><span data-ttu-id="94246-111">Categoria</span><span class="sxs-lookup"><span data-stu-id="94246-111">Category</span></span>

<span data-ttu-id="94246-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="94246-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="94246-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="94246-113">Affected APIs</span></span>

- <span data-ttu-id="94246-114">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="94246-114">Not detectable via API analysis.</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis.

-->

---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74644043"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a><span data-ttu-id="a1c8a-101">Mudança de acesso para AccessibleObject.RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="a1c8a-101">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>

<span data-ttu-id="a1c8a-102">A partir do .NET Core 3.0 `AccessibleObject.RuntimeIDFirstItem` RC1, `protected` `internal`a acessibilidade mudou de para .</span><span class="sxs-lookup"><span data-stu-id="a1c8a-102">Starting in .NET Core 3.0 RC1, the accessibility of `AccessibleObject.RuntimeIDFirstItem` has changed from `protected` to `internal`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a1c8a-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="a1c8a-103">Change description</span></span>

<span data-ttu-id="a1c8a-104">Começando com .NET Core 3.0 `AccessibleObject.RuntimeIDFirstItem` Preview `protected`4, o campo foi .</span><span class="sxs-lookup"><span data-stu-id="a1c8a-104">Starting with .NET Core 3.0 Preview 4, the `AccessibleObject.RuntimeIDFirstItem` field was `protected`.</span></span> <span data-ttu-id="a1c8a-105">Começando com o .NET Core 3.0 `protected` RC1, ele mudou de para `internal` alinhar-se com a acessibilidade do campo no Quadro .NET.</span><span class="sxs-lookup"><span data-stu-id="a1c8a-105">Starting with .NET Core 3.0 RC1, it has changed from `protected` to `internal` to align with the accessibility of the field in the .NET Framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a1c8a-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="a1c8a-106">Version introduced</span></span>

<span data-ttu-id="a1c8a-107">3.0 RC1</span><span class="sxs-lookup"><span data-stu-id="a1c8a-107">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a1c8a-108">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="a1c8a-108">Recommended action</span></span>

<span data-ttu-id="a1c8a-109">A alteração pode afetá-lo se você desenvolveu um aplicativo <xref:System.Windows.Forms.AccessibleObject> .NET `RuntimeIDFirstItem` Core com um tipo que deriva e acessa o campo.</span><span class="sxs-lookup"><span data-stu-id="a1c8a-109">The change can affect you if you've developed a .NET Core app with a type that derives from <xref:System.Windows.Forms.AccessibleObject> and accesses the `RuntimeIDFirstItem` field.</span></span> <span data-ttu-id="a1c8a-110">Se este for o caso, você pode definir uma constante local da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="a1c8a-110">If this is the case, you can define a local constant as follows:</span></span>

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a><span data-ttu-id="a1c8a-111">Categoria</span><span class="sxs-lookup"><span data-stu-id="a1c8a-111">Category</span></span>

<span data-ttu-id="a1c8a-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a1c8a-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a1c8a-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="a1c8a-113">Affected APIs</span></span>

- <span data-ttu-id="a1c8a-114">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="a1c8a-114">Not detectable via API analysis.</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->

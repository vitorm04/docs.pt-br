---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644043"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a><span data-ttu-id="2419e-101">Alteração de acesso para AccessibleObject. RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="2419e-101">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>

<span data-ttu-id="2419e-102">A partir do .NET Core 3,0 RC1, a acessibilidade do `AccessibleObject.RuntimeIDFirstItem` foi alterada de `protected` para `internal`.</span><span class="sxs-lookup"><span data-stu-id="2419e-102">Starting in .NET Core 3.0 RC1, the accessibility of `AccessibleObject.RuntimeIDFirstItem` has changed from `protected` to `internal`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2419e-103">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="2419e-103">Change description</span></span>

<span data-ttu-id="2419e-104">A partir do .NET Core 3,0 Preview 4, o campo `AccessibleObject.RuntimeIDFirstItem` foi `protected`.</span><span class="sxs-lookup"><span data-stu-id="2419e-104">Starting with .NET Core 3.0 Preview 4, the `AccessibleObject.RuntimeIDFirstItem` field was `protected`.</span></span> <span data-ttu-id="2419e-105">A partir do .NET Core 3,0 RC1, ele mudou de `protected` para `internal` para se alinhar com a acessibilidade do campo no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2419e-105">Starting with .NET Core 3.0 RC1, it has changed from `protected` to `internal` to align with the accessibility of the field in the .NET Framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2419e-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="2419e-106">Version introduced</span></span>

<span data-ttu-id="2419e-107">RC1 3,0</span><span class="sxs-lookup"><span data-stu-id="2419e-107">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2419e-108">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="2419e-108">Recommended action</span></span>

<span data-ttu-id="2419e-109">A alteração poderá afetar você se você tiver desenvolvido um aplicativo .NET Core com um tipo derivado de <xref:System.Windows.Forms.AccessibleObject> e acessar o campo `RuntimeIDFirstItem`.</span><span class="sxs-lookup"><span data-stu-id="2419e-109">The change can affect you if you've developed a .NET Core app with a type that derives from <xref:System.Windows.Forms.AccessibleObject> and accesses the `RuntimeIDFirstItem` field.</span></span> <span data-ttu-id="2419e-110">Se esse for o caso, você poderá definir uma constante local da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="2419e-110">If this is the case, you can define a local constant as follows:</span></span>

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a><span data-ttu-id="2419e-111">Categoria</span><span class="sxs-lookup"><span data-stu-id="2419e-111">Category</span></span>

<span data-ttu-id="2419e-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2419e-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2419e-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="2419e-113">Affected APIs</span></span>

- <span data-ttu-id="2419e-114">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="2419e-114">Not detectable via API analysis.</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->

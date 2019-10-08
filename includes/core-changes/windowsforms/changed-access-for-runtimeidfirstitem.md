---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003005"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a><span data-ttu-id="ec676-101">Alteração de acesso para AccessibleObject. RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="ec676-101">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>

<span data-ttu-id="ec676-102">A partir do .NET Core 3,0 RC1, a acessibilidade de `AccessibleObject.RuntimeIDFirstItem` foi alterada de `protected` para `internal`.</span><span class="sxs-lookup"><span data-stu-id="ec676-102">Starting in .NET Core 3.0 RC1, the accessibility of `AccessibleObject.RuntimeIDFirstItem` has changed from `protected` to `internal`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ec676-103">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="ec676-103">Change description</span></span>

<span data-ttu-id="ec676-104">A partir do .NET Core 3,0 Preview 4, o campo `AccessibleObject.RuntimeIDFirstItem` foi `protected`.</span><span class="sxs-lookup"><span data-stu-id="ec676-104">Starting with .NET Core 3.0 Preview 4, the `AccessibleObject.RuntimeIDFirstItem` field was `protected`.</span></span> <span data-ttu-id="ec676-105">A partir do .NET Core 3,0 RC1, ele mudou de `protected` para `internal` para se alinhar com a acessibilidade do campo no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ec676-105">Starting with .NET Core 3.0 RC1, it has changed from `protected` to `internal` to align with the accessibility of the field in the .NET Framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ec676-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="ec676-106">Version introduced</span></span>

<span data-ttu-id="ec676-107">RC1 3,0</span><span class="sxs-lookup"><span data-stu-id="ec676-107">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ec676-108">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="ec676-108">Recommended action</span></span>

<span data-ttu-id="ec676-109">A alteração poderá afetar você se você tiver desenvolvido um aplicativo .NET Core com um tipo derivado de <xref:System.Windows.Forms.AccessibleObject> e acessar o campo `RuntimeIDFirstItem`.</span><span class="sxs-lookup"><span data-stu-id="ec676-109">The change can affect you if you've developed a .NET Core app with a type that derives from <xref:System.Windows.Forms.AccessibleObject> and accesses the `RuntimeIDFirstItem` field.</span></span> <span data-ttu-id="ec676-110">Se esse for o caso, você poderá definir uma constante local da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ec676-110">If this is the case, you can define a local constant as follows:</span></span>

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a><span data-ttu-id="ec676-111">Categoria</span><span class="sxs-lookup"><span data-stu-id="ec676-111">Category</span></span>

<span data-ttu-id="ec676-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ec676-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ec676-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ec676-113">Affected APIs</span></span>

- <span data-ttu-id="ec676-114">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="ec676-114">Not detectable via API analysis.</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->

---
ms.openlocfilehash: 843007ac6467584fbe6350b6ea19ef67609d73e2
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643945"
---
### <a name="controldefaultfont-changed-to-segoe-ui-9pt"></a><span data-ttu-id="aa1f5-101">`Control.DefaultFont` alterado para `Segoe UI 9pt`</span><span class="sxs-lookup"><span data-stu-id="aa1f5-101">`Control.DefaultFont` changed to `Segoe UI 9pt`</span></span>

#### <a name="change-description"></a><span data-ttu-id="aa1f5-102">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="aa1f5-102">Change description</span></span>

<span data-ttu-id="aa1f5-103">No .NET Framework, a propriedade <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> foi definida como `Microsoft Sans Serif 8pt`.</span><span class="sxs-lookup"><span data-stu-id="aa1f5-103">In the .NET Framework, the <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> property was set to `Microsoft Sans Serif 8pt`.</span></span> <span data-ttu-id="aa1f5-104">A figura a seguir mostra uma janela que usa a fonte padrão.</span><span class="sxs-lookup"><span data-stu-id="aa1f5-104">The following figure shows a window that uses the default font.</span></span>

![fonte de controle padrão no .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

<span data-ttu-id="aa1f5-106">No .NET Core a partir do .NET Core 3,0, ele é definido como `Segoe UI 9pt` (a mesma fonte que <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="aa1f5-106">In .NET Core starting with .NET Core 3.0, it is set to `Segoe UI 9pt` (the same font as <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>).</span></span> <span data-ttu-id="aa1f5-107">Como resultado dessa alteração, formulários e controles serão dimensionados cerca de 27% a mais para considerar o tamanho maior da nova fonte padrão.</span><span class="sxs-lookup"><span data-stu-id="aa1f5-107">As a result of this change, forms and controls will be sized about 27% larger to account for the larger size of the new default font.</span></span> <span data-ttu-id="aa1f5-108">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="aa1f5-108">For example:</span></span>

![fonte de controle padrão-no .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

<span data-ttu-id="aa1f5-110">Essa alteração foi feita para se alinhar com as [diretrizes de UX do Windows](https://docs.microsoft.com/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span><span class="sxs-lookup"><span data-stu-id="aa1f5-110">This change was made to align with [Windows UX guidelines](https://docs.microsoft.com/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="aa1f5-111">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="aa1f5-111">Version introduced</span></span>

<span data-ttu-id="aa1f5-112">3.0</span><span class="sxs-lookup"><span data-stu-id="aa1f5-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="aa1f5-113">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="aa1f5-113">Recommended action</span></span>

<span data-ttu-id="aa1f5-114">Devido à alteração no tamanho de formulários e controles, certifique-se de que seu aplicativo seja renderizado corretamente.</span><span class="sxs-lookup"><span data-stu-id="aa1f5-114">Because of the change in the size of forms and controls, ensure that your application renders correctly.</span></span>

<span data-ttu-id="aa1f5-115">Para manter a fonte original, defina a fonte padrão do formulário como `Microsoft Sans Serif 8pt`.</span><span class="sxs-lookup"><span data-stu-id="aa1f5-115">To retain the original font, set your form's default font to `Microsoft Sans Serif 8pt`.</span></span> <span data-ttu-id="aa1f5-116">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="aa1f5-116">For example:</span></span>

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a><span data-ttu-id="aa1f5-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="aa1f5-117">Category</span></span>

- <span data-ttu-id="aa1f5-118">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aa1f5-118">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="aa1f5-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="aa1f5-119">Affected APIs</span></span>

<span data-ttu-id="aa1f5-120">Nenhuma.</span><span class="sxs-lookup"><span data-stu-id="aa1f5-120">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->

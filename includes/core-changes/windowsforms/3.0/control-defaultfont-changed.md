---
ms.openlocfilehash: 0b2d3c1383246d4259c6d906ecf9dab927f4bdb1
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721012"
---
### <a name="default-control-font-changed-to-segoe-ui-9-pt"></a><span data-ttu-id="33a99-101">Fonte de controle padrão alterada para Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="33a99-101">Default control font changed to Segoe UI 9 pt</span></span>

#### <a name="change-description"></a><span data-ttu-id="33a99-102">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="33a99-102">Change description</span></span>

<span data-ttu-id="33a99-103">Em .NET Framework, a <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> propriedade foi definida como `Microsoft Sans Serif 8 pt` .</span><span class="sxs-lookup"><span data-stu-id="33a99-103">In .NET Framework, the <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> property was set to `Microsoft Sans Serif 8 pt`.</span></span> <span data-ttu-id="33a99-104">A imagem a seguir mostra uma janela que usa a fonte padrão.</span><span class="sxs-lookup"><span data-stu-id="33a99-104">The following image shows a window that uses the default font.</span></span>

![Fonte de controle padrão no .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

<span data-ttu-id="33a99-106">A partir do .NET Core 3,0, a fonte padrão é definida como `Segoe UI 9 pt` (a mesma fonte como <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType> ).</span><span class="sxs-lookup"><span data-stu-id="33a99-106">Starting in .NET Core 3.0, the default font is set to `Segoe UI 9 pt` (the same font as <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>).</span></span> <span data-ttu-id="33a99-107">Como resultado dessa alteração, formulários e controles são dimensionados de 27% a mais para considerar o tamanho maior da nova fonte padrão.</span><span class="sxs-lookup"><span data-stu-id="33a99-107">As a result of this change, forms and controls are sized about 27% larger to account for the larger size of the new default font.</span></span> <span data-ttu-id="33a99-108">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="33a99-108">For example:</span></span>

![Fonte de controle padrão no .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

<span data-ttu-id="33a99-110">Essa alteração foi feita para se alinhar com as [diretrizes de experiência do usuário do Windows (UX)](/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span><span class="sxs-lookup"><span data-stu-id="33a99-110">This change was made to align with [Windows user experience (UX) guidelines](/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="33a99-111">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="33a99-111">Version introduced</span></span>

<span data-ttu-id="33a99-112">3.0</span><span class="sxs-lookup"><span data-stu-id="33a99-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="33a99-113">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="33a99-113">Recommended action</span></span>

<span data-ttu-id="33a99-114">Devido à alteração no tamanho de formulários e controles, certifique-se de que seu aplicativo seja renderizado corretamente.</span><span class="sxs-lookup"><span data-stu-id="33a99-114">Because of the change in the size of forms and controls, ensure that your application renders correctly.</span></span>

<span data-ttu-id="33a99-115">Para manter a fonte original, defina a fonte padrão do formulário como `Microsoft Sans Serif 8 pt` .</span><span class="sxs-lookup"><span data-stu-id="33a99-115">To retain the original font, set your form's default font to `Microsoft Sans Serif 8 pt`.</span></span> <span data-ttu-id="33a99-116">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="33a99-116">For example:</span></span>

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a><span data-ttu-id="33a99-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="33a99-117">Category</span></span>

- <span data-ttu-id="33a99-118">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="33a99-118">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="33a99-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="33a99-119">Affected APIs</span></span>

<span data-ttu-id="33a99-120">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="33a99-120">None.</span></span>

<!--

#### Affected APIs

- Not detectable via API analysis

-->

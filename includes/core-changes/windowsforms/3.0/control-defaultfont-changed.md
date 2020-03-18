---
ms.openlocfilehash: b0c4e9617677cf95e3a059b57f3d50ddfb072f4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937110"
---
### <a name="default-control-font-changed-to-segoe-ui-9-pt"></a><span data-ttu-id="c4b78-101">Fonte de controle padrão alterada para Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="c4b78-101">Default control font changed to Segoe UI 9 pt</span></span>

#### <a name="change-description"></a><span data-ttu-id="c4b78-102">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="c4b78-102">Change description</span></span>

<span data-ttu-id="c4b78-103">No Framework .NET, a <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> `Microsoft Sans Serif 8 pt`propriedade foi definida como .</span><span class="sxs-lookup"><span data-stu-id="c4b78-103">In .NET Framework, the <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> property was set to `Microsoft Sans Serif 8 pt`.</span></span> <span data-ttu-id="c4b78-104">A imagem a seguir mostra uma janela que usa a fonte padrão.</span><span class="sxs-lookup"><span data-stu-id="c4b78-104">The following image shows a window that uses the default font.</span></span>

![Fonte de controle padrão em .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

<span data-ttu-id="c4b78-106">A partir do .NET Core 3.0, `Segoe UI 9 pt` a fonte <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>padrão é definida como (a mesma fonte de ).</span><span class="sxs-lookup"><span data-stu-id="c4b78-106">Starting in .NET Core 3.0, the default font is set to `Segoe UI 9 pt` (the same font as <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>).</span></span> <span data-ttu-id="c4b78-107">Como resultado dessa mudança, os formulários e controles são dimensionados cerca de 27% maiores para explicar o tamanho maior da nova fonte padrão.</span><span class="sxs-lookup"><span data-stu-id="c4b78-107">As a result of this change, forms and controls are sized about 27% larger to account for the larger size of the new default font.</span></span> <span data-ttu-id="c4b78-108">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="c4b78-108">For example:</span></span>

![Fonte de controle padrão em .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

<span data-ttu-id="c4b78-110">Essa alteração foi feita para se alinhar com [as diretrizes de experiência do usuário do Windows (UX).](/windows/win32/uxguide/vis-fonts#fonts-and-colors)</span><span class="sxs-lookup"><span data-stu-id="c4b78-110">This change was made to align with [Windows user experience (UX) guidelines](/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c4b78-111">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="c4b78-111">Version introduced</span></span>

<span data-ttu-id="c4b78-112">3.0</span><span class="sxs-lookup"><span data-stu-id="c4b78-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c4b78-113">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="c4b78-113">Recommended action</span></span>

<span data-ttu-id="c4b78-114">Devido à mudança no tamanho dos formulários e controles, certifique-se de que sua aplicação seja renderizada corretamente.</span><span class="sxs-lookup"><span data-stu-id="c4b78-114">Because of the change in the size of forms and controls, ensure that your application renders correctly.</span></span>

<span data-ttu-id="c4b78-115">Para reter a fonte original, defina `Microsoft Sans Serif 8 pt`a fonte padrão do formulário como .</span><span class="sxs-lookup"><span data-stu-id="c4b78-115">To retain the original font, set your form's default font to `Microsoft Sans Serif 8 pt`.</span></span> <span data-ttu-id="c4b78-116">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="c4b78-116">For example:</span></span>

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a><span data-ttu-id="c4b78-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="c4b78-117">Category</span></span>

- <span data-ttu-id="c4b78-118">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c4b78-118">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c4b78-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="c4b78-119">Affected APIs</span></span>

<span data-ttu-id="c4b78-120">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c4b78-120">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->

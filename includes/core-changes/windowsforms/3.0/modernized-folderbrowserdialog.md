---
ms.openlocfilehash: 24141f4b95cda2ae382a923da034e75c329b8555
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643959"
---
### <a name="modernization-of-the-folderbrowserdialog"></a><span data-ttu-id="29cb6-101">Modernização do FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="29cb6-101">Modernization of the FolderBrowserDialog</span></span>

<span data-ttu-id="29cb6-102">O controle de <xref:System.Windows.Forms.FolderBrowserDialog> foi alterado em Windows Forms aplicativos para .NET Core.</span><span class="sxs-lookup"><span data-stu-id="29cb6-102">The <xref:System.Windows.Forms.FolderBrowserDialog> control has changed in Windows Forms applications for .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="29cb6-103">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="29cb6-103">Change description</span></span>

<span data-ttu-id="29cb6-104">Na .NET Framework, o Windows Forms usa a caixa de diálogo a seguir para o controle de <xref:System.Windows.Forms.FolderBrowserDialog>:</span><span class="sxs-lookup"><span data-stu-id="29cb6-104">In the .NET Framework, Windows forms uses the following dialog for the <xref:System.Windows.Forms.FolderBrowserDialog> control:</span></span>

![O FolderBrowserDialogControl no .NET Framework](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

<span data-ttu-id="29cb6-106">No .NET Core 3,0, Windows Forms usuários um controle baseado em COM mais recente que foi introduzido no Windows Vista:</span><span class="sxs-lookup"><span data-stu-id="29cb6-106">In .NET Core 3.0, Windows Forms users a newer COM-based control that was introduced in Windows Vista:</span></span>

![O FolderBrowserDialogControl no .NET Core](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a><span data-ttu-id="29cb6-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="29cb6-108">Version introduced</span></span>

<span data-ttu-id="29cb6-109">3.0</span><span class="sxs-lookup"><span data-stu-id="29cb6-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="29cb6-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="29cb6-110">Recommended action</span></span>

<span data-ttu-id="29cb6-111">A caixa de diálogo será atualizada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="29cb6-111">The dialog will be upgraded automatically.</span></span>

<span data-ttu-id="29cb6-112">Se você quiser manter a caixa de diálogo original, defina a propriedade <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> como `false` antes de mostrar a caixa de diálogo, conforme ilustrado pelo seguinte fragmento de código:</span><span class="sxs-lookup"><span data-stu-id="29cb6-112">If you desire to retain the original dialog, set the <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> property to `false` before showing the dialog, as illustrated by the following code fragment:</span></span>

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a><span data-ttu-id="29cb6-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="29cb6-113">Category</span></span>

<span data-ttu-id="29cb6-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="29cb6-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="29cb6-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="29cb6-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

### Affected APIs

- `System.Windows.Forms.FolderBrowserDialog`

-->

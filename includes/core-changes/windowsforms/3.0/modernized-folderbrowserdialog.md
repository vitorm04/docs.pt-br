---
ms.openlocfilehash: 24141f4b95cda2ae382a923da034e75c329b8555
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74643959"
---
### <a name="modernization-of-the-folderbrowserdialog"></a><span data-ttu-id="853de-101">Modernização do FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="853de-101">Modernization of the FolderBrowserDialog</span></span>

<span data-ttu-id="853de-102">O <xref:System.Windows.Forms.FolderBrowserDialog> controle foi alterado nos aplicativos do Windows Forms para .NET Core.</span><span class="sxs-lookup"><span data-stu-id="853de-102">The <xref:System.Windows.Forms.FolderBrowserDialog> control has changed in Windows Forms applications for .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="853de-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="853de-103">Change description</span></span>

<span data-ttu-id="853de-104">No .NET Framework, os formulários do <xref:System.Windows.Forms.FolderBrowserDialog> Windows usam a seguinte caixa de diálogo para o controle:</span><span class="sxs-lookup"><span data-stu-id="853de-104">In the .NET Framework, Windows forms uses the following dialog for the <xref:System.Windows.Forms.FolderBrowserDialog> control:</span></span>

![O FolderBrowserControl no Framework .NET](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

<span data-ttu-id="853de-106">No .NET Core 3.0, o Windows Forms faz com que os usuários de um novo controle baseado em COM tenha sido introduzido no Windows Vista:</span><span class="sxs-lookup"><span data-stu-id="853de-106">In .NET Core 3.0, Windows Forms users a newer COM-based control that was introduced in Windows Vista:</span></span>

![O FolderBrowserControl no Núcleo .NET](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a><span data-ttu-id="853de-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="853de-108">Version introduced</span></span>

<span data-ttu-id="853de-109">3.0</span><span class="sxs-lookup"><span data-stu-id="853de-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="853de-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="853de-110">Recommended action</span></span>

<span data-ttu-id="853de-111">A caixa de diálogo será atualizada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="853de-111">The dialog will be upgraded automatically.</span></span>

<span data-ttu-id="853de-112">Se desejar manter a caixa de <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> diálogo `false` original, defina a propriedade antes de mostrar a caixa de diálogo, conforme ilustrado pelo seguinte fragmento de código:</span><span class="sxs-lookup"><span data-stu-id="853de-112">If you desire to retain the original dialog, set the <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> property to `false` before showing the dialog, as illustrated by the following code fragment:</span></span>

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a><span data-ttu-id="853de-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="853de-113">Category</span></span>

<span data-ttu-id="853de-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="853de-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="853de-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="853de-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

### Affected APIs

- `System.Windows.Forms.FolderBrowserDialog`

-->

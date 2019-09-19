---
ms.openlocfilehash: a7cf6210e288d3521f1df248927f0e7cfaf45cab
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119320"
---
### <a name="modernization-of-the-folderbrowserdialog"></a>Modernização do FolderBrowserDialog

O <xref:System.Windows.Forms.FolderBrowserDialog> controle foi alterado em aplicativos Windows Forms para .NET Core.

#### <a name="change-description"></a>Alterar descrição

Na .NET Framework, o Windows Forms usa a caixa de diálogo a <xref:System.Windows.Forms.FolderBrowserDialog> seguir para o controle:

![O FolderBrowserDialogControl no .NET Framework](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

No .NET Core 3,0, Windows Forms usuários um controle baseado em COM mais recente que foi introduzido no Windows Vista:

![O FolderBrowserDialogControl no .NET Core](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

A caixa de diálogo será atualizada automaticamente.

Se você quiser manter a caixa de diálogo original, defina <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> a propriedade `false` como antes de mostrar a caixa de diálogo, conforme ilustrado pelo fragmento de código a seguir:

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!-- 

### Affected APIs

- `System.Windows.Forms.FolderBrowserDialog`

-->
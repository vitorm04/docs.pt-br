---
ms.openlocfilehash: 24141f4b95cda2ae382a923da034e75c329b8555
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74643959"
---
### <a name="modernization-of-the-folderbrowserdialog"></a>Modernização do FolderBrowserDialog

O <xref:System.Windows.Forms.FolderBrowserDialog> controle foi alterado nos aplicativos do Windows Forms para .NET Core.

#### <a name="change-description"></a>Descrição da alteração

No .NET Framework, os formulários do <xref:System.Windows.Forms.FolderBrowserDialog> Windows usam a seguinte caixa de diálogo para o controle:

![O FolderBrowserControl no Framework .NET](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

No .NET Core 3.0, o Windows Forms faz com que os usuários de um novo controle baseado em COM tenha sido introduzido no Windows Vista:

![O FolderBrowserControl no Núcleo .NET](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

A caixa de diálogo será atualizada automaticamente.

Se desejar manter a caixa de <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> diálogo `false` original, defina a propriedade antes de mostrar a caixa de diálogo, conforme ilustrado pelo seguinte fragmento de código:

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

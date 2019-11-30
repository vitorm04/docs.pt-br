---
ms.openlocfilehash: 843007ac6467584fbe6350b6ea19ef67609d73e2
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643945"
---
### <a name="controldefaultfont-changed-to-segoe-ui-9pt"></a>`Control.DefaultFont` alterado para `Segoe UI 9pt`

#### <a name="change-description"></a>Alterar descrição

No .NET Framework, a propriedade <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> foi definida como `Microsoft Sans Serif 8pt`. A figura a seguir mostra uma janela que usa a fonte padrão.

![fonte de controle padrão no .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

No .NET Core a partir do .NET Core 3,0, ele é definido como `Segoe UI 9pt` (a mesma fonte que <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>). Como resultado dessa alteração, formulários e controles serão dimensionados cerca de 27% a mais para considerar o tamanho maior da nova fonte padrão. Por exemplo:

![fonte de controle padrão-no .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

Essa alteração foi feita para se alinhar com as [diretrizes de UX do Windows](https://docs.microsoft.com/windows/win32/uxguide/vis-fonts#fonts-and-colors).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

Devido à alteração no tamanho de formulários e controles, certifique-se de que seu aplicativo seja renderizado corretamente.

Para manter a fonte original, defina a fonte padrão do formulário como `Microsoft Sans Serif 8pt`. Por exemplo:

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a>Categoria

- Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

Nenhuma.

<!--

### Affected APIs

- Not detectable via API analysis

-->

---
ms.openlocfilehash: 0b2d3c1383246d4259c6d906ecf9dab927f4bdb1
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721012"
---
### <a name="default-control-font-changed-to-segoe-ui-9-pt"></a>Fonte de controle padrão alterada para Segoe UI 9 pt

#### <a name="change-description"></a>Descrição da alteração

Em .NET Framework, a <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> propriedade foi definida como `Microsoft Sans Serif 8 pt` . A imagem a seguir mostra uma janela que usa a fonte padrão.

![Fonte de controle padrão no .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

A partir do .NET Core 3,0, a fonte padrão é definida como `Segoe UI 9 pt` (a mesma fonte como <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType> ). Como resultado dessa alteração, formulários e controles são dimensionados de 27% a mais para considerar o tamanho maior da nova fonte padrão. Por exemplo:

![Fonte de controle padrão no .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

Essa alteração foi feita para se alinhar com as [diretrizes de experiência do usuário do Windows (UX)](/windows/win32/uxguide/vis-fonts#fonts-and-colors).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

Devido à alteração no tamanho de formulários e controles, certifique-se de que seu aplicativo seja renderizado corretamente.

Para manter a fonte original, defina a fonte padrão do formulário como `Microsoft Sans Serif 8 pt` . Por exemplo:

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

Nenhum.

<!--

#### Affected APIs

- Not detectable via API analysis

-->

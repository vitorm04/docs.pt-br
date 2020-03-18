---
ms.openlocfilehash: b0c4e9617677cf95e3a059b57f3d50ddfb072f4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937110"
---
### <a name="default-control-font-changed-to-segoe-ui-9-pt"></a>Fonte de controle padrão alterada para Segoe UI 9 pt

#### <a name="change-description"></a>Descrição da alteração

No Framework .NET, a <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> `Microsoft Sans Serif 8 pt`propriedade foi definida como . A imagem a seguir mostra uma janela que usa a fonte padrão.

![Fonte de controle padrão em .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

A partir do .NET Core 3.0, `Segoe UI 9 pt` a fonte <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>padrão é definida como (a mesma fonte de ). Como resultado dessa mudança, os formulários e controles são dimensionados cerca de 27% maiores para explicar o tamanho maior da nova fonte padrão. Por exemplo: 

![Fonte de controle padrão em .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

Essa alteração foi feita para se alinhar com [as diretrizes de experiência do usuário do Windows (UX).](/windows/win32/uxguide/vis-fonts#fonts-and-colors)

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

Devido à mudança no tamanho dos formulários e controles, certifique-se de que sua aplicação seja renderizada corretamente.

Para reter a fonte original, defina `Microsoft Sans Serif 8 pt`a fonte padrão do formulário como . Por exemplo: 

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

### Affected APIs

- Not detectable via API analysis

-->

---
ms.openlocfilehash: 9631e64bb403a3fe7b1b91e8ac592b57ce8068d9
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75936991"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a>Não há suporte para a opção de compatibilidade DoNotSupportSelectAllShortcutInMultilineTextBox

O `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` opção de compatibilidade, que foi introduzido no .NET Framework 4.6.1, não tem suporte no Windows Forms no .NET Core 3,0.

#### <a name="change-description"></a>Descrição das alterações

Começando com .NET Framework 4.6.1, selecionando o <kbd>Ctrl</kbd> + <kbd>uma</kbd> tecla de atalho em um controle de <xref:System.Windows.Forms.TextBox> selecionou todo o texto. No .NET Framework 4,6 e versões anteriores, a seleção do <kbd>Ctrl</kbd> + <kbd>uma</kbd> tecla de atalho falhou ao selecionar todo o texto se as propriedades [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) e <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> fossem ambas definidas como `true`. A opção de compatibilidade `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` foi introduzida em .NET Framework 4.6.1 para manter o comportamento original. Para obter mais informações, consulte <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.

No .NET Core, não há suporte para a opção `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`.

#### <a name="version-introduced"></a>Versão introduzida

3,0 Preview 9

#### <a name="recommended-action"></a>Ação recomendada

Remova a opção. Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

- {1&gt;Nenhum&lt;1}

<!-- 

### Affected APIs

- Not detectable via API analysis

-->

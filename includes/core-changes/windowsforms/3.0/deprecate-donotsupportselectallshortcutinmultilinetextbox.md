---
ms.openlocfilehash: 9631e64bb403a3fe7b1b91e8ac592b57ce8068d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75936991"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a>DoNotSupportSelect$ShortcutInMultilineTextBox não é suportado

O `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch de compatibilidade, que foi introduzido no .NET Framework 4.6.1, não é suportado no Windows Forms no .NET Core 3.0.

#### <a name="change-description"></a>Descrição da alteração

Começando com o Quadro .NET 4.6.1, selecionando <xref:System.Windows.Forms.TextBox> a tecla De atalho <kbd>Ctrl</kbd> + <kbd>A</kbd> em um controle selecionou todo o texto. Nas versões .NET Framework 4.6 e anteriores, a seleção da tecla <kbd>Ctrl</kbd> + <kbd>A</kbd> não conseguiu selecionar todo o texto se a caixa [de texto.atalhoshabilitados](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) e <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> as propriedades foram definidas como `true`. O `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch de compatibilidade foi introduzido no .NET Framework 4.6.1 para manter o comportamento original. Para obter mais informações, consulte <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.

No .NET Core, o `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch não é suportado.

#### <a name="version-introduced"></a>Versão introduzida

3.0 Visualização 9

#### <a name="recommended-action"></a>Ação recomendada

Remova o interruptor. O switch não é suportado e nenhuma funcionalidade alternativa está disponível.

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

- Nenhum

<!-- 

### Affected APIs

- Not detectable via API analysis

-->

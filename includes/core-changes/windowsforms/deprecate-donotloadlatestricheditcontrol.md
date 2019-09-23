---
ms.openlocfilehash: 265fc5bea97bf85bcb9cc8111f915e14297d9957
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181864"
---
### <a name="switchsystemwindowsformsdonotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>Não há suporte para a opção de compatibilidade switch. System. Windows. Forms. DoNotLoadLatestRichEditControl

A `Switch.System.Windows.Forms.UseLegacyImages` opção de compatibilidade, que foi introduzida no .NET Framework 4.7.1, não tem suporte no Windows Forms no .NET Core 3,0.

#### <a name="change-description"></a>Alterar descrição

No .NET Framework 4.6.2 e versões anteriores, o <xref:System.Windows.Forms.RichTextBox> controle criaria uma instância do controle RichEdit do Win32 v 3.0 e para aplicativos direcionados .NET Framework 4.7.1, o controle criaria uma instância do <xref:System.Windows.Forms.RichTextBox> RichEdit v 4.1 (no  *MsftEdit. dll*). A `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` opção de compatibilidade foi introduzida para permitir aplicativos direcionados .NET Framework 4.7.1 e versões posteriores para recusar o novo controle RichEdit v 4.1 e usar o antigo controle RichEdit v3.

No .NET Core, não `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` há suporte para a opção. Há suporte apenas para novas <xref:System.Windows.Forms.RichTextBox> versões do controle.

#### <a name="version-introduced"></a>Versão introduzida

3,0 Preview 9

#### <a name="recommended-action"></a>Ação recomendada

Remova a opção. Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->

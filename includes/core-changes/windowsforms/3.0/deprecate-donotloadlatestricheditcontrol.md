---
ms.openlocfilehash: 3f0e8fb4d0d727b40cff5de7cfdc7529bf32dac4
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937010"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>Não há suporte para a opção de compatibilidade DoNotLoadLatestRichEditControl

O `Switch.System.Windows.Forms.UseLegacyImages` opção de compatibilidade, que foi introduzido no .NET Framework 4.7.1, não tem suporte no Windows Forms no .NET Core 3,0.

#### <a name="change-description"></a>Descrição das alterações

No .NET Framework 4.6.2 e versões anteriores, o controle de <xref:System.Windows.Forms.RichTextBox> instanciaria o controle RichEdit do Win32 v 3.0 e, para aplicativos direcionados .NET Framework 4.7.1, o controle de <xref:System.Windows.Forms.RichTextBox> instanciaria o RichEdit v 4.1 (em *MsftEdit. dll*). A opção de compatibilidade `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` foi introduzida para permitir aplicativos direcionados .NET Framework 4.7.1 e versões posteriores para recusar o novo controle RichEdit v 4.1 e usar o antigo controle RichEdit v3.

No .NET Core, não há suporte para a opção `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl`. Há suporte apenas para novas versões do controle de <xref:System.Windows.Forms.RichTextBox>.

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

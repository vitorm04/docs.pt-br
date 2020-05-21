---
ms.openlocfilehash: cb8c0532bb2bcfbcd619cd382f3d236b431c3480
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720989"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>Não há suporte para a opção de compatibilidade DoNotLoadLatestRichEditControl

A `Switch.System.Windows.Forms.UseLegacyImages` opção de compatibilidade, que foi introduzida no .NET Framework 4.7.1, não tem suporte no Windows Forms no .NET Core 3,0.

#### <a name="change-description"></a>Descrição da alteração

No .NET Framework 4.6.2 e versões anteriores, o <xref:System.Windows.Forms.RichTextBox> controle criaria uma instância do controle RichEdit do Win32 v 3.0 e, para aplicativos direcionados .NET Framework 4.7.1, o <xref:System.Windows.Forms.RichTextBox> controle criaria uma instância de RichEdit v 4.1 (em *MsftEdit. dll*). A `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` opção de compatibilidade foi introduzida para permitir aplicativos direcionados .NET Framework 4.7.1 e versões posteriores para recusar o novo controle RichEdit v 4.1 e usar o antigo controle RichEdit v3.

No .NET Core, `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` não há suporte para a opção. Há suporte apenas para novas versões do <xref:System.Windows.Forms.RichTextBox> controle.

#### <a name="version-introduced"></a>Versão introduzida

3,0 Preview 9

#### <a name="recommended-action"></a>Ação recomendada

Remova a opção. Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

#### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->

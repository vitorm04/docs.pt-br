---
ms.openlocfilehash: 3f0e8fb4d0d727b40cff5de7cfdc7529bf32dac4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937010"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>DoNotLoadLastRichEditO switch de compatibilidade não suportado

O `Switch.System.Windows.Forms.UseLegacyImages` switch de compatibilidade, que foi introduzido no .NET Framework 4.7.1, não é suportado no Windows Forms no .NET Core 3.0.

#### <a name="change-description"></a>Descrição da alteração

No Quadro .NET 4.6.2 e <xref:System.Windows.Forms.RichTextBox> nas versões anteriores, o controle instanciaria o controle Win32 RichEdit v3.0, e para aplicativos que visam o .NET Framework 4.7.1, o <xref:System.Windows.Forms.RichTextBox> controle instanciaria RichEdit v4.1 (in *msftedit.dll*). O `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` switch de compatibilidade foi introduzido para permitir que aplicativos que visam as versões .NET Framework 4.7.1 e posteriores optem pelo novo controle RichEdit v4.1 e usem o antigo controle RichEdit v3.

No .NET Core, o `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` switch não é suportado. Apenas novas versões do <xref:System.Windows.Forms.RichTextBox> controle são suportadas.

#### <a name="version-introduced"></a>Versão introduzida

3.0 Visualização 9

#### <a name="recommended-action"></a>Ação recomendada

Remova o interruptor. O switch não é suportado e nenhuma funcionalidade alternativa está disponível.

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->

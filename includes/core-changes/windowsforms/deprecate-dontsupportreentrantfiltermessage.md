---
ms.openlocfilehash: cb72e1b92172b8989ce99b47181c13561a7ccd76
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181751"
---
### <a name="switchsystemwindowsformsdontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a>Não há suporte para a opção de compatibilidade switch. System. Windows. Forms. DontSupportReentrantFilterMessage

A `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` opção de compatibilidade, que foi introduzida no .NET Framework 4.6.1, não tem suporte no Windows Forms no .NET Core 3,0.

#### <a name="change-description"></a>Alterar descrição

Começando com o .NET Framework 4.6.1, a `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` opção de compatibilidade resolve <xref:System.IndexOutOfRangeException> as possíveis exceções <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> quando a mensagem é chamada com <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> uma implementação personalizada. Para obter mais informações, confira [Mitigação: Implementações](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)personalizadas de IMessageFilter. PreFilterMessage.

No .NET Core, não `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` há suporte para a opção.

#### <a name="version-introduced"></a>Versão introduzida

3,0 Preview 9

#### <a name="recommended-action"></a>Ação recomendada

Remova a opção. Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->

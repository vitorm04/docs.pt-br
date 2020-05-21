---
ms.openlocfilehash: 55c13aa70a03bcc548ce1d096cca8f40de6cda84
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721144"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a>Não há suporte para a opção de compatibilidade DontSupportReentrantFilterMessage

A `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` opção de compatibilidade, que foi introduzida no .NET Framework 4.6.1, não tem suporte no Windows Forms no .NET Core 3,0.

#### <a name="change-description"></a>Descrição da alteração

Começando com o .NET Framework 4.6.1, a `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` opção de compatibilidade resolve as possíveis <xref:System.IndexOutOfRangeException> exceções quando a <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> mensagem é chamada com uma <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementação personalizada. Para saber mais, confira [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md) (Mitigação: implementações personalizadas de IMessageFilter.PreFilterMessage).

No .NET Core, `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` não há suporte para a opção.

#### <a name="version-introduced"></a>Versão introduzida

3,0 Preview 9

#### <a name="recommended-action"></a>Ação recomendada

Remova a opção. Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->

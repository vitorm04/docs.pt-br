---
ms.openlocfilehash: 3272dc562981269b868df4ca9d3a5806918aba5f
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937000"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a>Não há suporte para a opção de compatibilidade DontSupportReentrantFilterMessage

O `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` opção de compatibilidade, que foi introduzido no .NET Framework 4.6.1, não tem suporte no Windows Forms no .NET Core 3,0.

#### <a name="change-description"></a>Descrição das alterações

A partir do .NET Framework 4.6.1, a opção de compatibilidade de `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` resolve possíveis exceções de <xref:System.IndexOutOfRangeException> quando a mensagem de <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> é chamada com uma implementação de <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> personalizada. Para saber mais, confira [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md) (Mitigação: implementações personalizadas de IMessageFilter.PreFilterMessage).

No .NET Core, não há suporte para a opção `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`.

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

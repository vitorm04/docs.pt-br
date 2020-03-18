---
ms.openlocfilehash: 3272dc562981269b868df4ca9d3a5806918aba5f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937000"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a>Interruptor de compatibilidade DontSupportReentrantFilterMessage não suportado

O `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` switch de compatibilidade, que foi introduzido no .NET Framework 4.6.1, não é suportado no Windows Forms no .NET Core 3.0.

#### <a name="change-description"></a>Descrição da alteração

Começando pelo .NET Framework `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` 4.6.1, o <xref:System.IndexOutOfRangeException> switch de <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> compatibilidade resolve possíveis <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> exceções quando a mensagem é chamada com uma implementação personalizada. Para saber mais, confira [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md) (Mitigação: implementações personalizadas de IMessageFilter.PreFilterMessage).

No .NET Core, o `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` switch não é suportado.

#### <a name="version-introduced"></a>Versão introduzida

3.0 Visualização 9

#### <a name="recommended-action"></a>Ação recomendada

Remova o interruptor. O switch não é suportado e nenhuma funcionalidade alternativa está disponível.

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->

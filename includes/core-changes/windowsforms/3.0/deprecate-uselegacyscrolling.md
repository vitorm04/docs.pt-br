---
ms.openlocfilehash: dd850e83540ffed4dc95b00f807f49b0dd3725e9
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720960"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a>Não há suporte para a opção de compatibilidade DomainUpDown. UseLegacyScrolling

A `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` opção de compatibilidade, que foi introduzida no .NET Framework 4.7.1, não tem suporte no Windows Forms no .NET Core 3,0.

#### <a name="change-description"></a>Descrição da alteração

Começando com o .NET Framework 4.7.1, a `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` opção de compatibilidade permitia que os desenvolvedores desautorizassem as <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> ações e independentes <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> . A opção restaurou o comportamento herdado, no qual <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> será ignorada se o texto do contexto estiver presente e o desenvolvedor for solicitado a usar a <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> ação no controle antes da <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> ação. Para obter mais informações, consulte [ \< AppContextSwitchOverrides> Element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

No .NET Core, `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` não há suporte para a opção.

#### <a name="version-introduced"></a>Versão introduzida

3,0 Preview 9

#### <a name="recommended-action"></a>Ação recomendada

Remova a opção. Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->

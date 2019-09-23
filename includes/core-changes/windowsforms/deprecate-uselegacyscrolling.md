---
ms.openlocfilehash: 459e7e1f0b5543f069682dadf60668e94b472377
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181740"
---
### <a name="switchsystemwindowsformsdomainupdownuselegacyscrolling-compatibility-switch-not-supported"></a>Não há suporte para a opção de compatibilidade switch. System. Windows. Forms. DomainUpDown. UseLegacyScrolling

A `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` opção de compatibilidade, que foi introduzida no .NET Framework 4.7.1, não tem suporte no Windows Forms no .NET Core 3,0.

#### <a name="change-description"></a>Alterar descrição

Começando com o .NET Framework 4.7.1, a `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` opção de compatibilidade permitia que os desenvolvedores desautorizassem <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> as ações e independentes <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> . A opção restaurou o comportamento herdado, no <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> qual será ignorada se o texto do contexto estiver presente e o desenvolvedor for <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> solicitado a usar a ação no <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> controle antes da ação. Para obter mais informações, consulte [ \<AppContextSwitchOverrides > Element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

No .NET Core, não `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` há suporte para a opção.

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

### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->

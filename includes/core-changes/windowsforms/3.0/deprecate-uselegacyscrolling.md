---
ms.openlocfilehash: 80fc75d0736e2ae17699073a025e79b52b340613
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937024"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a>DomínioUpDown.UseLegacyO switch de compatibilidade não é suportado

O `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` switch de compatibilidade, que foi introduzido no .NET Framework 4.7.1, não é suportado no Windows Forms no .NET Core 3.0.

#### <a name="change-description"></a>Descrição da alteração

Começando com o .NET Framework 4.7.1, o `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` switch de compatibilidade <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> permitiu que os desenvolvedores optassem por desativar ações e independentes. O switch restaurou o comportamento <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> legado, no qual o texto de contexto <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> é ignorado, e <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> o desenvolvedor é obrigado a usar a ação no controle antes da ação. Para obter mais informações, consulte [ \<AppContextSwitchOverrides> elemento](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

No .NET Core, o `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` switch não é suportado.

#### <a name="version-introduced"></a>Versão introduzida

3.0 Visualização 9

#### <a name="recommended-action"></a>Ação recomendada

Remova o interruptor. O switch não é suportado e nenhuma funcionalidade alternativa está disponível.

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

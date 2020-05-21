---
ms.openlocfilehash: 3ada05a13ec7acde1d8374ed733d0d51cdfb408c
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721177"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a>Não há suporte para a opção de compatibilidade UseLegacyContextMenuStripSourceControlValue

A `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` opção de compatibilidade, que foi introduzida no .NET Framework 4.7.2, não tem suporte no Windows Forms no .NET Core 3,0.

#### <a name="change-description"></a>Descrição da alteração

Começando com o .NET Framework 4.7.2, a `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` opção de compatibilidade permite que o desenvolvedor cancele o novo comportamento da <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> propriedade, que agora retorna uma referência ao controle do código-fonte. O comportamento anterior da propriedade era retornar `null` . Para obter mais informações, consulte [ \< AppContextSwitchOverrides> Element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

No .NET Core, `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` não há suporte para a opção.

#### <a name="version-introduced"></a>Versão introduzida

3,0 Preview 9

#### <a name="recommended-action"></a>Ação recomendada

Remova a opção. Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->

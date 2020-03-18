---
ms.openlocfilehash: 5aca2b8b3ca6572194692888eae3c5614245b481
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75936994"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a>UseLegacyContextMenuStripStripOswitch de compatibilidade Do value não suportado

O `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch de compatibilidade, que foi introduzido no .NET Framework 4.7.2, não é suportado no Windows Forms no .NET Core 3.0.

#### <a name="change-description"></a>Descrição da alteração

Começando pelo .NET Framework 4.7.2, o `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch de compatibilidade permite que <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> o desenvolvedor opte por sair do novo comportamento da propriedade, que agora retorna uma referência ao controle de origem. O comportamento anterior da propriedade `null`era retornar. Para obter mais informações, consulte [ \<AppContextSwitchOverrides> elemento](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

No .NET Core, o `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch não é suportado.

#### <a name="version-introduced"></a>Versão introduzida

3.0 Visualização 9

#### <a name="recommended-action"></a>Ação recomendada

Remova o interruptor. O switch não é suportado e nenhuma funcionalidade alternativa está disponível.

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->

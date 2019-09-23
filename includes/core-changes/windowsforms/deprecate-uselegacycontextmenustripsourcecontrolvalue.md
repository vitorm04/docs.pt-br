---
ms.openlocfilehash: 5c1dc42a451d2c6a82e2c2429115db023c610334
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181802"
---
### <a name="switchsystemwindowsformsuselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a>Não há suporte para a opção de compatibilidade switch. System. Windows. Forms. UseLegacyContextMenuStripSourceControlValue

A `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` opção de compatibilidade, que foi introduzida no .NET Framework 4.7.2, não tem suporte no Windows Forms no .NET Core 3,0.

#### <a name="change-description"></a>Alterar descrição

Começando com o .NET Framework 4.7.2, a `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` opção de compatibilidade permite que o desenvolvedor cancele o novo comportamento <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> da propriedade, que agora retorna uma referência ao controle do código-fonte. O comportamento anterior da propriedade era retornar `null`. Para obter mais informações, consulte [ \<AppContextSwitchOverrides > Element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

No .NET Core, não `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` há suporte para a opção.

#### <a name="version-introduced"></a>Versão introduzida

3,0 Preview 9

#### <a name="recommended-action"></a>Ação recomendada

Remova a opção. Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->

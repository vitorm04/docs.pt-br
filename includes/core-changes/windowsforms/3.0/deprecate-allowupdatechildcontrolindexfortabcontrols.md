---
ms.openlocfilehash: 7e76c32ddeb50eaf1ee93d7cf3cac7469187cc41
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937060"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a>Não há suporte para a opção de compatibilidade AllowUpdateChildControlIndexForTabControls

A opção de compatibilidade `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` tem suporte no Windows Forms no .NET Framework 4,6 e em versões posteriores, mas não tem suporte no Windows Forms a partir do .NET Core 3,0.

#### <a name="change-description"></a>Descrição das alterações

No .NET Framework 4,6 e versões posteriores, a seleção de uma guia reordena sua coleção de controle. A opção de compatibilidade `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` permite que um aplicativo ignore essa reordenação quando esse comportamento é indesejável.

No .NET Core, não há suporte para a opção `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`.

#### <a name="version-introduced"></a>Versão introduzida

3,0 Preview 9

#### <a name="recommended-action"></a>Ação recomendada

Remova a opção. Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

- {1&gt;Nenhum&lt;1}

<!-- 

### Affected APIs

- Not detectable via API analysis

-->

---
ms.openlocfilehash: 1d01de4b978309e05a6036953f2a6909628a2480
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2019
ms.locfileid: "71181835"
---
### <a name="switchsystemwindowsformsallowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a>Não há suporte para a opção de compatibilidade switch. System. Windows. Forms. AllowUpdateChildControlIndexForTabControls

A `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` opção de compatibilidade tem suporte no Windows Forms no .NET Framework 4,6 e em versões posteriores, mas não tem suporte no Windows Forms a partir do .NET Core 3,0.

#### <a name="change-description"></a>Alterar descrição

No .NET Framework 4,6 e versões posteriores, a seleção de uma guia reordena sua coleção de controle. A `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` opção de compatibilidade permite que um aplicativo ignore essa reordenação quando esse comportamento é indesejável.

No .NET Core, não `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` há suporte para a opção.

#### <a name="version-introduced"></a>Versão introduzida

3,0 Preview 9

#### <a name="recommended-action"></a>Ação recomendada

Remova a opção. Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

- Nenhum

<!-- 

### Affected APIs

- Not detectable via API analysis

-->

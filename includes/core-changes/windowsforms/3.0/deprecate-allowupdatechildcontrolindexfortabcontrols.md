---
ms.openlocfilehash: e1c55eab0b968daab7322350e201b49149e63215
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721436"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a>Não há suporte para a opção de compatibilidade AllowUpdateChildControlIndexForTabControls

A `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` opção de compatibilidade tem suporte no Windows Forms no .NET Framework 4,6 e em versões posteriores, mas não tem suporte no Windows Forms a partir do .NET Core 3,0.

#### <a name="change-description"></a>Descrição da alteração

No .NET Framework 4,6 e versões posteriores, a seleção de uma guia reordena sua coleção de controle. A `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` opção de compatibilidade permite que um aplicativo ignore essa reordenação quando esse comportamento é indesejável.

No .NET Core, `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` não há suporte para a opção.

#### <a name="version-introduced"></a>Versão introduzida

3,0 Preview 9

#### <a name="recommended-action"></a>Ação recomendada

Remova a opção. Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

- Nenhum

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->

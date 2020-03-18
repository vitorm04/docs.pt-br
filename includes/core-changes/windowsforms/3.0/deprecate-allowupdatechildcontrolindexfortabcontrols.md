---
ms.openlocfilehash: 7e76c32ddeb50eaf1ee93d7cf3cac7469187cc41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937060"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a>AllowUpdateChildControlIndexForTabControls switch de compatibilidade não suportado

O `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch de compatibilidade é suportado no Windows Forms em versões .NET Framework 4.6 e posteriores, mas não é suportado no Windows Forms a partir do .NET Core 3.0.

#### <a name="change-description"></a>Descrição da alteração

Nas versões .NET Framework 4.6 e posteriores, selecionando uma guia reordena sua coleção de controles. O `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch de compatibilidade permite que um aplicativo pule esse reordenamento quando esse comportamento é indesejável.

No .NET Core, o `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch não é suportado.

#### <a name="version-introduced"></a>Versão introduzida

3.0 Visualização 9

#### <a name="recommended-action"></a>Ação recomendada

Remova o interruptor. O switch não é suportado e nenhuma funcionalidade alternativa está disponível.

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

- Nenhum

<!-- 

### Affected APIs

- Not detectable via API analysis

-->

---
ms.openlocfilehash: 75baa4f23eae838defafd3ce9b3907a187982a18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937062"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a>Ativaro switch de compatibilidade DoVisualStyleValidation não suportado

O `Switch.System.Windows.Forms.EnableVisualStyleValidation` switch de compatibilidade não é suportado no Windows Forms no .NET Core 3.0.

#### <a name="change-description"></a>Descrição da alteração

No .NET Framework, o `Switch.System.Windows.Forms.EnableVisualStyleValidation` switch de compatibilidade permitiu que um aplicativo optasse por não validar os estilos visuais fornecidos de forma numérica.

No .NET Core, o `Switch.System.Windows.Forms.EnableVisualStyleValidation` switch não é suportado.

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

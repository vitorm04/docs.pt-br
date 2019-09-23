---
ms.openlocfilehash: e6bb1d53cbe1883b8faef75bd22942bd4f65a5e6
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2019
ms.locfileid: "71181709"
---
### <a name="switchsystemwindowsformsenablevisualstylevalidation-compatibility-switch-not-supported"></a>Não há suporte para a opção de compatibilidade switch. System. Windows. Forms. EnableVisualStyleValidation

Não `Switch.System.Windows.Forms.EnableVisualStyleValidation` há suporte para a opção de compatibilidade em Windows Forms no .NET Core 3,0.

#### <a name="change-description"></a>Alterar descrição

No .NET Framework, a `Switch.System.Windows.Forms.EnableVisualStyleValidation` opção de compatibilidade permitia que um aplicativo recusasse a validação de estilos visuais fornecidos em um formato numérico. 

No .NET Core, não `Switch.System.Windows.Forms.EnableVisualStyleValidation` há suporte para a opção.

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

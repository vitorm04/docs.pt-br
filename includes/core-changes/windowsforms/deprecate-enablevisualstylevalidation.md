---
ms.openlocfilehash: 84b6bfc32f5a73597b227098e5aee1e3450cf85b
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198328"
---
### <a name="switchsystemwindowsformsenablevisualstylevalidation-compatibility-switch-not-supported"></a>Não há suporte para a opção de compatibilidade switch. System. Windows. Forms. EnableVisualStyleValidation

Não há suporte para a opção de compatibilidade `Switch.System.Windows.Forms.EnableVisualStyleValidation` no Windows Forms no .NET Core 3,0.

#### <a name="change-description"></a>Alterar descrição

No .NET Framework, a opção de compatibilidade de `Switch.System.Windows.Forms.EnableVisualStyleValidation` permitiu que um aplicativo recusasse a validação de estilos visuais fornecidos em um formato numérico.

No .NET Core, não há suporte para a opção `Switch.System.Windows.Forms.EnableVisualStyleValidation`.

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

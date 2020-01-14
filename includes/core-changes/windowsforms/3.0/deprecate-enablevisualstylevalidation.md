---
ms.openlocfilehash: 75baa4f23eae838defafd3ce9b3907a187982a18
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937062"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a>Não há suporte para a opção de compatibilidade EnableVisualStyleValidation

Não há suporte para a opção de compatibilidade `Switch.System.Windows.Forms.EnableVisualStyleValidation` no Windows Forms no .NET Core 3,0.

#### <a name="change-description"></a>Descrição das alterações

No .NET Framework, a opção de compatibilidade de `Switch.System.Windows.Forms.EnableVisualStyleValidation` permitiu que um aplicativo recusasse a validação de estilos visuais fornecidos em um formato numérico.

No .NET Core, não há suporte para a opção `Switch.System.Windows.Forms.EnableVisualStyleValidation`.

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

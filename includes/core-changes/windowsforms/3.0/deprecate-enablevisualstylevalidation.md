---
ms.openlocfilehash: 97e38685777c7c418c0ccd91f4c433501ecf3aaa
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721064"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a>Não há suporte para a opção de compatibilidade EnableVisualStyleValidation

`Switch.System.Windows.Forms.EnableVisualStyleValidation`Não há suporte para a opção de compatibilidade em Windows Forms no .NET Core 3,0.

#### <a name="change-description"></a>Descrição da alteração

No .NET Framework, a `Switch.System.Windows.Forms.EnableVisualStyleValidation` opção de compatibilidade permitia que um aplicativo recusasse a validação de estilos visuais fornecidos em um formato numérico.

No .NET Core, `Switch.System.Windows.Forms.EnableVisualStyleValidation` não há suporte para a opção.

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

---
ms.openlocfilehash: 1ea2d70a7cfe04cc4c4b9b58ea6bb6fa0226b245
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721461"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a>Alteração de acesso para AccessibleObject. RuntimeIDFirstItem

A partir do .NET Core 3,0 RC1, a acessibilidade do `AccessibleObject.RuntimeIDFirstItem` foi alterada de `protected` para `internal` .

#### <a name="change-description"></a>Descrição da alteração

A partir do .NET Core 3,0 Preview 4, o `AccessibleObject.RuntimeIDFirstItem` campo era `protected` . A partir do .NET Core 3,0 RC1, ele mudou de `protected` para `internal` para alinhar com a acessibilidade do campo no .NET Framework.

#### <a name="version-introduced"></a>Versão introduzida

RC1 3,0

#### <a name="recommended-action"></a>Ação recomendada

A alteração poderá afetar você se você tiver desenvolvido um aplicativo .NET Core com um tipo que deriva de <xref:System.Windows.Forms.AccessibleObject> e acessa o `RuntimeIDFirstItem` campo. Se esse for o caso, você poderá definir uma constante local da seguinte maneira:

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

- Não detectável via análise de API.

<!-- 

#### Affected APIs

- Not detectable via API analysis.

-->

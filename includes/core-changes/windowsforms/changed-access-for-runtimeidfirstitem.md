---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003005"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a>Alteração de acesso para AccessibleObject. RuntimeIDFirstItem

A partir do .NET Core 3,0 RC1, a acessibilidade de `AccessibleObject.RuntimeIDFirstItem` foi alterada de `protected` para `internal`.

#### <a name="change-description"></a>Alterar descrição

A partir do .NET Core 3,0 Preview 4, o campo `AccessibleObject.RuntimeIDFirstItem` foi `protected`. A partir do .NET Core 3,0 RC1, ele mudou de `protected` para `internal` para se alinhar com a acessibilidade do campo no .NET Framework.

#### <a name="version-introduced"></a>Versão introduzida

RC1 3,0

#### <a name="recommended-action"></a>Ação recomendada

A alteração poderá afetar você se você tiver desenvolvido um aplicativo .NET Core com um tipo derivado de <xref:System.Windows.Forms.AccessibleObject> e acessar o campo `RuntimeIDFirstItem`. Se esse for o caso, você poderá definir uma constante local da seguinte maneira:

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

- Não detectável via análise de API.

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->

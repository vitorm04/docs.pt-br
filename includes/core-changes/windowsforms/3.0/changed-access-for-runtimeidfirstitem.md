---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74644043"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a>Mudança de acesso para AccessibleObject.RuntimeIDFirstItem

A partir do .NET Core 3.0 `AccessibleObject.RuntimeIDFirstItem` RC1, `protected` `internal`a acessibilidade mudou de para .

#### <a name="change-description"></a>Descrição da alteração

Começando com .NET Core 3.0 `AccessibleObject.RuntimeIDFirstItem` Preview `protected`4, o campo foi . Começando com o .NET Core 3.0 `protected` RC1, ele mudou de para `internal` alinhar-se com a acessibilidade do campo no Quadro .NET.

#### <a name="version-introduced"></a>Versão introduzida

3.0 RC1

#### <a name="recommended-action"></a>Ação recomendada

A alteração pode afetá-lo se você desenvolveu um aplicativo <xref:System.Windows.Forms.AccessibleObject> .NET `RuntimeIDFirstItem` Core com um tipo que deriva e acessa o campo. Se este for o caso, você pode definir uma constante local da seguinte forma:

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

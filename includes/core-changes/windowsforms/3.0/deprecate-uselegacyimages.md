---
ms.openlocfilehash: 3eab49acd3eaa5b6d5802af5f4e6f0fe2699ee97
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937063"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a>Não há suporte para a opção de compatibilidade UseLegacyImages

O `Switch.System.Windows.Forms.UseLegacyImages` opção de compatibilidade, que foi introduzido no .NET Framework 4,8, não tem suporte no Windows Forms no .NET Core 3,0.

#### <a name="change-description"></a>Descrição das alterações

A partir do .NET Framework 4,8, a opção de compatibilidade de `Switch.System.Windows.Forms.UseLegacyImages` resolveu possíveis problemas de dimensionamento de imagem em cenários de ClickOnce em ambientes de DPI alto. Quando definido como `true`, a opção permite que o usuário restaure o dimensionamento da imagem herdada em monitores de DPI alta, cuja escala é definida como maior que 100%. Para obter mais informações, consulte as [notas de versão do .NET Framework 4,8](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) no github.

No .NET Core, não há suporte para a opção `Switch.System.Windows.Forms.UseLegacyImages`.

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

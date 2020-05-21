---
ms.openlocfilehash: c980b0c0be9f4d6a529baa0743dec9ac16ca0d7f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721639"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a>Não há suporte para a opção de compatibilidade UseLegacyImages

A `Switch.System.Windows.Forms.UseLegacyImages` opção de compatibilidade, que foi introduzida no .NET Framework 4,8, não tem suporte no Windows Forms no .NET Core 3,0.

#### <a name="change-description"></a>Descrição da alteração

A partir do .NET Framework 4,8, a `Switch.System.Windows.Forms.UseLegacyImages` opção de compatibilidade resolveu possíveis problemas de dimensionamento de imagem em cenários de ClickOnce em ambientes de DPI alto. Quando definido como `true` , a opção permite que o usuário restaure o dimensionamento de imagem herdado em monitores de DPI alto cuja escala seja definida como maior que 100%. Para obter mais informações, consulte as [notas de versão do .NET Framework 4,8](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) no github.

No .NET Core, `Switch.System.Windows.Forms.UseLegacyImages` não há suporte para a opção.

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

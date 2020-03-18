---
ms.openlocfilehash: 3eab49acd3eaa5b6d5802af5f4e6f0fe2699ee97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937063"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a>O switch de compatibilidade UseLegacyImages não é suportado

O `Switch.System.Windows.Forms.UseLegacyImages` switch de compatibilidade, que foi introduzido no .NET Framework 4.8, não é suportado no Windows Forms no .NET Core 3.0.

#### <a name="change-description"></a>Descrição da alteração

Começando com o .NET Framework `Switch.System.Windows.Forms.UseLegacyImages` 4.8, o switch de compatibilidade abordou possíveis problemas de dimensionamento de imagem em cenários clickOnce em ambientes de DPI elevados. Quando definido `true`para , o switch permite que o usuário restaure o dimensionamento de imagem legado em displays de DPI elevadocuja escala está definida como superior a 100%. Para obter mais informações, consulte [.NET Framework 4.8 Release Notes](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) on GitHub.

No .NET Core, o `Switch.System.Windows.Forms.UseLegacyImages` switch não é suportado.

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

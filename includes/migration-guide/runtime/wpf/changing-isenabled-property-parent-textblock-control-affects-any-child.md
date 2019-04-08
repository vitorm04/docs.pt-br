---
ms.openlocfilehash: 38dd0b33202b8e8f1708ebec689333bd5367c93f
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760610"
---
### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a>Alterar a propriedade IsEnabled do pai de um controle TextBlock afeta os controles filho

|   |   |
|---|---|
|Detalhes|A partir do .NET Framework 4.6.2, alterar a propriedade <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> do pai de um controle <xref:System.Windows.Controls.TextBlock?displayProperty=name> afetará os controles filho (como hiperlinks e botões) do controle <xref:System.Windows.Controls.TextBlock?displayProperty=name>. No .NET Framework 4.6.1 e versões anteriores, os controles dentro de <xref:System.Windows.Controls.TextBlock?displayProperty=name> nem sempre refletiam o estado da propriedade <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> do pai <xref:System.Windows.Controls.TextBlock?displayProperty=name>.|
|Sugestão|nenhuma. Essa alteração está em conformidade com o comportamento esperado para controles dentro de um controle <xref:System.Windows.Controls.TextBlock?displayProperty=name>.|
|Escopo|Secundário|
|Versão|4.6.2|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType></li></ul>|


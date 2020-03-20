---
ms.openlocfilehash: 735278848cb7399e414a128afc650a0a1f882337
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857514"
---
### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a>Alterar a propriedade IsEnabled do pai de um controle TextBlock afeta os controles filho

|   |   |
|---|---|
|Detalhes|A partir do .NET Framework 4.6.2, alterar a propriedade <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> do pai de um controle <xref:System.Windows.Controls.TextBlock?displayProperty=name> afetará os controles filho (como hiperlinks e botões) do controle <xref:System.Windows.Controls.TextBlock?displayProperty=name>. No .NET Framework 4.6.1 e versões anteriores, os controles dentro de <xref:System.Windows.Controls.TextBlock?displayProperty=name> nem sempre refletiam o estado da propriedade <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> do pai <xref:System.Windows.Controls.TextBlock?displayProperty=name>.|
|Sugestão|Nenhum. Essa alteração está em conformidade com o comportamento esperado para controles dentro de um controle <xref:System.Windows.Controls.TextBlock?displayProperty=name>.|
|Escopo|Secundária|
|Versão|4.6.2|
|Type|Runtime|
|APIs afetadas|<ul><li><xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType></li></ul>|

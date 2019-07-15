---
ms.openlocfilehash: 0825233c0dae131fa9d00565348fac6fdf0be063
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857476"
---
### <a name="horizontal-scrolling-and-virtualization"></a>Rolagem horizontal e virtualização

|   |   |
|---|---|
|Detalhes|Essa alteração se aplica a um <xref:System.Windows.Controls.ItemsControl?displayProperty=name> que faz sua própria virtualização na direção ortogonal para a direção de rolagem principal (o principal exemplo é <xref:System.Windows.Controls.DataGrid?displayProperty=name> com EnableColumnVirtualization=&quot;True&quot;).  O resultado de certas operações de rolagem horizontal foi alterado para produzir resultados mais intuitivos e análogos aos resultados de operações verticais comparáveis.<p/>As operações específicas incluem &quot;Rolar Aqui&quot; e &quot;Borda Direita&quot; para usar os nomes dos menus obtidos clicando com o botão direito do mouse em uma barra de rolagem horizontal.  Ambas calculam um deslocamento candidato e chamam <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)>.<p/>Depois de rolar para o novo deslocamento, a definição de &quot;aqui&quot; ou de &quot;borda direita&quot; poderá mudar, pois um conteúdo com a virtualização removida recentemente alterou o valor de <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name>.<p/>Antes do .NET Framework 4.6.2, a operação de rolagem simplesmente usa o deslocamento candidato, embora ele talvez não seja mais &quot;aqui&quot; ou na &quot;borda direita&quot;.  Isso resulta em efeitos como o &quot;salto&quot; de rolagem, melhor ilustrado pelo exemplo. Suponha que um <xref:System.Windows.Controls.DataGrid?displayProperty=name> tenha ExtentWidth = 1000 e Width = 200.  Uma rolagem para &quot;Borda Direita&quot; usa o deslocamento de candidato 1000-200 = 800.  Durante a rolagem até esse deslocamento, a virtualização de novas colunas é eliminada. Vamos supor que elas sejam muito largas, então o <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name> muda para 2000.  A rolagem termina com HorizontalOffset=800 e o elevador &quot;retorna&quot; para perto do meio da barra de rolagem, precisamente em 800/2000 = 40%.<p/>A alteração é para recalcular um novo deslocamento candidato quando essa situação ocorre e tentar novamente. (A rolagem vertical já funciona assim.) <p/>A alteração proporciona uma experiência mais previsível e intuitiva para o usuário final, mas também pode afetar qualquer aplicativo que dependa do valor exato de <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=name> após uma rolagem horizontal, seja ela invocada pelo usuário final ou por uma chamada explícita para <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)>.|
|Sugestão|Um aplicativo que usa um valor previsto para <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=name> deve ser alterado para obter o valor real (e o valor de <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name>) após qualquer rolagem horizontal que poderia alterar <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name> devido à eliminação da virtualização.|
|Escopo|Secundário|
|Versão|4.6.2|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Windows.Controls.Primitives.IScrollInfo?displayProperty=nameWithType></li></ul>|


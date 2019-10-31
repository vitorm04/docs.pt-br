---
ms.openlocfilehash: 2f94ec58e6fdb56cfc5147e74b6ffd6bb657228d
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857482"
---
### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a>Items.Clear não remove duplicatas de SelectedItems

|   |   |
|---|---|
|Detalhes|Suponha que um Seletor (com seleção múltipla habilitada) tenha duplicatas em sua coleção <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> – o mesmo item é exibido mais de uma vez.  A remoção desses itens da fonte de dados (por exemplo, chamando Items.Clear) falha ao removê-los de <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name>; somente a primeira instância é removida. Além disso, o uso subsequente de <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> (por exemplo, SelectedItems.Clear()) pode encontrar problemas, como <xref:System.ArgumentException?displayProperty=name>, pois <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> contém itens que não estão mais na fonte de dados.|
|Sugestão|Atualize se possível para o .NET Framework 4.6.2.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType></li></ul>|


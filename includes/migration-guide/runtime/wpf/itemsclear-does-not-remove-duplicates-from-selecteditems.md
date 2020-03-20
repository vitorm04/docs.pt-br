---
ms.openlocfilehash: 1545c807e3bef675e63e14d01ab82c1131600f39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857482"
---
### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a>Items.Clear não remove duplicatas de SelectedItems

|   |   |
|---|---|
|Detalhes|Suponha que um Seletor (com seleção múltipla habilitada) tenha duplicatas em sua coleção <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> – o mesmo item é exibido mais de uma vez.  A remoção desses itens da fonte de dados (por exemplo, chamando Items.Clear) falha ao removê-los de <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name>; somente a primeira instância é removida. Além disso, o uso subsequente de <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> (por exemplo, SelectedItems.Clear()) pode encontrar problemas, como <xref:System.ArgumentException?displayProperty=name>, pois <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> contém itens que não estão mais na fonte de dados.|
|Sugestão|Atualize se possível para o .NET Framework 4.6.2.|
|Escopo|Secundária|
|Versão|4.5|
|Type|Runtime|
|APIs afetadas|<ul><li><xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType></li></ul>|

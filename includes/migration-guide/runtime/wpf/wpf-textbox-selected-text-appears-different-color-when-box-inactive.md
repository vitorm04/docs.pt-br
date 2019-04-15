---
ms.openlocfilehash: 74ce1bbc9a887aee3a33eaf05084e8c2000967c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235111"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a>O texto selecionado TextBox do WPF aparece em cor diferente quando a caixa de texto está inativa

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.5, quando um controle de caixa de texto do WPF estiver inativo (não tem o foco), o texto selecionado dentro da caixa terá uma cor diferente de quando o controle estiver ativo.|
|Sugestão|O comportamento anterior (.NET Framework 4.0) poderá ser restaurado definindo a propriedade <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> como <code>false</code>.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|

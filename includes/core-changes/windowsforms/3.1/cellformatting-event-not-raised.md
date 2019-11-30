---
ms.openlocfilehash: add3ff8faed2e7fab245e5b6f1b9158b7bdd06f5
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567359"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a>Evento CellFormatting não gerado se ToolTip for mostrado

Uma <xref:System.Windows.Forms.DataGridView> agora mostra as dicas de ferramenta de texto e erro de uma célula quando ele é focalizado por um mouse e quando selecionado por meio do teclado. Se uma dica de ferramenta for mostrada, o evento <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> não será gerado.

#### <a name="change-description"></a>Alterar descrição

Antes do .NET Core 3,1, um <xref:System.Windows.Forms.DataGridView> que tinha a propriedade <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> definida como `true` mostrou uma dica de ferramenta para o texto de uma célula e erros quando a célula foi focalizada por um mouse. Dicas de ferramentas não são mostradas quando uma célula foi selecionada por meio do teclado (por exemplo, usando a tecla Tab, teclas de atalho ou navegação de seta). Se o usuário editou uma célula e, em seguida, enquanto o <xref:System.Windows.Forms.DataGridView> ainda estava no modo de edição, focalizado em uma célula que não tinha a propriedade <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> definida, um evento <xref:System.Windows.Forms.DataGridView.CellFormatting> foi gerado para formatar o texto da célula para exibição na célula.

Para atender aos padrões de acessibilidade, a partir do .NET Core 3,1, um <xref:System.Windows.Forms.DataGridView> que tem a propriedade <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> definida como `true` mostra dicas de ferramenta para o texto de uma célula e erros não apenas quando a célula é focalizada, mas também quando ela é selecionada por meio do teclado. Como consequência dessa alteração, o evento <xref:System.Windows.Forms.DataGridView.CellFormatting> *não* é gerado quando as células que não têm o conjunto de propriedades <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> são focalizadas enquanto o <xref:System.Windows.Forms.DataGridView> está no modo de edição. O evento não é gerado porque o conteúdo da célula focalizada é mostrado como uma dica de ferramenta em vez de ser exibido na célula.

#### <a name="version-introduced"></a>Versão introduzida

3,1

#### <a name="recommended-action"></a>Ação recomendada

Refatore qualquer código que dependa do evento <xref:System.Windows.Forms.DataGridView.CellFormatting> enquanto o <xref:System.Windows.Forms.DataGridView> estiver no modo de edição.

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

Não detectável via análise de API.

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->

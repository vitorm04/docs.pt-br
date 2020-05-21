---
ms.openlocfilehash: 4a34a64eba72ea24c1d830566565ce4fbee8e5b7
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721375"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a>Evento CellFormatting não gerado se ToolTip for mostrado

<xref:System.Windows.Forms.DataGridView>Agora mostra as dicas de ferramenta de texto e erro de uma célula quando ele é focalizado por um mouse e quando selecionado por meio do teclado. Se uma dica de ferramenta for mostrada, o <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> evento não será gerado.

#### <a name="change-description"></a>Descrição da alteração

Antes do .NET Core 3,1, um <xref:System.Windows.Forms.DataGridView> que tinha a <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> propriedade definida para `true` mostrar uma dica de ferramenta para o texto de uma célula e erros quando a célula foi focalizada por um mouse. Dicas de ferramentas não são mostradas quando uma célula foi selecionada por meio do teclado (por exemplo, usando a tecla Tab, teclas de atalho ou navegação de seta). Se o usuário editou uma célula e, em seguida, enquanto o <xref:System.Windows.Forms.DataGridView> ainda estava no modo de edição, focalizado em uma célula que não tinha a <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> propriedade definida, um <xref:System.Windows.Forms.DataGridView.CellFormatting> evento foi gerado para formatar o texto da célula para exibição na célula.

Para atender aos padrões de acessibilidade, a partir do .NET Core 3,1, um <xref:System.Windows.Forms.DataGridView> que tem a <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> propriedade definida para `true` Mostrar as dicas de ferramenta para o texto de uma célula e erros não apenas quando a célula é focalizada, mas também quando ela é selecionada por meio do teclado. Como consequência dessa alteração, o <xref:System.Windows.Forms.DataGridView.CellFormatting> evento *não* é gerado quando células que não têm o conjunto de <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> Propriedades são focalizadas enquanto o <xref:System.Windows.Forms.DataGridView> estiver no modo de edição. O evento não é gerado porque o conteúdo da célula focalizada é mostrado como uma dica de ferramenta em vez de ser exibido na célula.

#### <a name="version-introduced"></a>Versão introduzida

3.1

#### <a name="recommended-action"></a>Ação recomendada

Refatore qualquer código que dependa do <xref:System.Windows.Forms.DataGridView.CellFormatting> evento enquanto o <xref:System.Windows.Forms.DataGridView> estiver no modo de edição.

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!-- 

#### Affected APIs

Not detectable via API analysis.

-->

---
ms.openlocfilehash: b736ab743a628fdcbc53c5ee51551e5dad986885
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888095"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a>Evento de formatação de células não levantada se a dica de ferramenta for mostrada

Um <xref:System.Windows.Forms.DataGridView> agora mostra as dicas de texto e erro de uma célula quando pairado por um mouse e quando selecionado através do teclado. Se uma dica de <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> ferramenta for mostrada, o evento não será levantado.

#### <a name="change-description"></a>Descrição da alteração

Antes do .NET Core 3.1, um <xref:System.Windows.Forms.DataGridView> que tinha a <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> propriedade definida para `true` mostrar uma dica de ferramenta para o texto de uma célula e erros quando a célula era pairada por um mouse. As dicas de ferramentas não foram mostradas quando uma célula foi selecionada através do teclado (por exemplo, usando a tecla Tab, teclas de atalho ou navegação de seta). Se o usuário editou uma célula <xref:System.Windows.Forms.DataGridView> e, em seguida, enquanto o ainda estava <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> no modo <xref:System.Windows.Forms.DataGridView.CellFormatting> de edição, pairava sobre uma célula que não tinha o conjunto de propriedades, um evento foi levantado para formatar o texto da célula para exibição na célula.

Para atender aos padrões de acessibilidade, a <xref:System.Windows.Forms.DataGridView> partir do <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> .NET `true` Core 3.1, um que tem a propriedade definida para mostrar dicas de ferramentas para o texto de uma célula e erros não apenas quando a célula é pairada, mas também quando é selecionada através do teclado. Como conseqüência dessa <xref:System.Windows.Forms.DataGridView.CellFormatting> mudança, o evento *não* é levantado quando <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> as células que <xref:System.Windows.Forms.DataGridView> não têm o conjunto de propriedades são pairadas enquanto o está no modo de edição. O evento não é levantado porque o conteúdo da célula pairada é mostrado como uma dica de ferramenta em vez de ser exibido na célula.

#### <a name="version-introduced"></a>Versão introduzida

3.1

#### <a name="recommended-action"></a>Ação recomendada

Refatorar qualquer código que <xref:System.Windows.Forms.DataGridView.CellFormatting> dependa <xref:System.Windows.Forms.DataGridView> do evento enquanto estiver no modo de edição.

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!-- 

### Affected APIs

Not detectable via API analysis.

-->

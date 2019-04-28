---
title: Teclado padrão e comportamento do mouse no controle DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid [WPF], keyboard behavior
- DataGrid [WPF], mouse behavior
- keyboard behavior [WPF], DataGrid
- mouse behavior [WPF], DataGrid
ms.assetid: 563b8854-ca39-4d97-8235-17eaa0f93c8d
ms.openlocfilehash: 6be464ce85bd3ba91dd6e6cc810ec7d04edc0c3d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61911840"
---
# <a name="default-keyboard-and-mouse-behavior-in-the-datagrid-control"></a>Teclado padrão e comportamento do mouse no controle DataGrid
Este tópico descreve como os usuários podem interagir com o <xref:System.Windows.Controls.DataGrid> controle usando o teclado e mouse.  
  
 As interações típicas com o <xref:System.Windows.Controls.DataGrid> incluem navegação, seleção e edição. Comportamento de seleção é afetado pela <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> e <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> propriedades. Os valores padrão que fazem com que o comportamento descrito neste tópico são <xref:System.Windows.Controls.DataGridSelectionMode.Extended?displayProperty=nameWithType> e <xref:System.Windows.Controls.DataGridSelectionUnit.FullRow?displayProperty=nameWithType>. Alterar esses valores pode causar um comportamento diferente daquele descrito. Quando uma célula está no modo de edição, o controle de edição pode substituir o comportamento de teclado padrão da <xref:System.Windows.Controls.DataGrid>.  
  
## <a name="default-keyboard-behavior"></a>Comportamento do teclado padrão  
 A tabela a seguir lista o comportamento de teclado padrão para o <xref:System.Windows.Controls.DataGrid>.  
  
|Tecla ou combinação de teclas|Descrição|  
|----------------------------|-----------------|  
|SETA PARA BAIXO|Move o foco para a célula diretamente abaixo da célula atual. Se o foco estiver na última linha, pressionar SETA PARA BAIXO não fará nada.|  
|SETA PARA CIMA|Move o foco para a célula diretamente acima da célula atual. Se o foco estiver na última linha, pressionar SETA PARA CIMA não fará nada.|  
|SETA PARA A ESQUERDA|Move o foco para a célula anterior na linha. Se o foco estiver na primeira célula na linha, pressionar SETA PARA A ESQUERDA não fará nada.|  
|SETA PARA A DIREITA|Move o foco para a próxima célula na linha. Se o foco estiver na última célula na linha, pressionar SETA PARA A DIREITA não fará nada.|  
|HOME|Move o foco para a primeira célula na linha atual.|  
|END|Move o foco até a última célula na linha atual.|  
|PAGE DOWN|Se as linhas não estiverem agrupadas, rola o controle para baixo pelo número de linhas que são totalmente exibidas. Move o foco para a última linha totalmente exibida sem alterar as colunas.<br /><br /> Se as linhas estiverem agrupadas, move o foco para a última linha no <xref:System.Windows.Controls.DataGrid> sem alterar as colunas.|  
|PAGE UP|Se as linhas não estiverem agrupadas, rola o controle para cima pelo número de linhas que são totalmente exibidas. Move o foco para a primeira linha exibida sem alterar as colunas.<br /><br /> Se as linhas estiverem agrupadas, move o foco para a primeira linha no <xref:System.Windows.Controls.DataGrid> sem alterar as colunas.|  
|TAB|Move o foco para a próxima célula na linha atual. Se o foco estiver na última célula da linha, moverá o foco para a primeira célula da linha seguinte. Se o foco estiver na última célula no controle, moverá o foco para o próximo controle na ordem de tabulação do contêiner pai.<br /><br /> Se a célula atual estiver em modo de edição e pressionar TAB fizer com que o foco se mova para fora da linha atual, as alterações que foram feitas na linha serão confirmadas antes de o foco ser alterado.|  
|SHIFT+TAB|Move o foco para a célula anterior na linha atual. Se o foco já estiver na primeira célula da linha, moverá o foco para a última célula da linha anterior. Se o foco estiver na primeira célula no controle, moverá o foco para o controle anterior na ordem de tabulação do contêiner pai.<br /><br /> Se a célula atual estiver em modo de edição e pressionar TAB fizer com que o foco se mova para fora da linha atual, as alterações que foram feitas na linha serão confirmadas antes de o foco ser alterado.|  
|CTRL + SETA PARA BAIXO|Move o foco para a última célula na coluna atual.|  
|CTRL+SETA PARA CIMA|Move o foco para a primeira célula na coluna atual.|  
|CTRL + SETA PARA A DIREITA|Move o foco até a última célula na linha atual.|  
|CTRL + SETA PARA A ESQUERDA|Move o foco para a primeira célula na linha atual.|  
|CTRL+HOME|Move o foco para a primeira célula no controle.|  
|CTRL+END|Move o foco para a última célula no controle.|  
|CTRL+PAGE DOWN|Mesmo que PAGE DOWN.|  
|CTRL+PAGE UP|Mesmo que PAGE UP.|  
|F2|Se o <xref:System.Windows.Controls.DataGrid.IsReadOnly%2A?displayProperty=nameWithType> é de propriedade `false` e o <xref:System.Windows.Controls.DataGridColumn.IsReadOnly%2A?displayProperty=nameWithType> é de propriedade `false` para a coluna atual, colocará a célula atual no modo de edição de célula.|  
|ENTER|Confirma as alterações feitas na célula e na linha atuais e move o foco para a célula diretamente abaixo da célula atual. Se o foco estiver na última linha, confirmará as alterações sem mover o foco.|  
|ESC|Se o controle estiver no modo de edição, cancelará a edição e reverterá quaisquer alterações feitas no controle. Se a fonte de dados subjacentes implementa <xref:System.ComponentModel.IEditableObject>, pressionar ESC uma segunda vez cancelará o modo de edição para a linha inteira.|  
|BACKSPACE|Exclui o caractere antes do cursor ao editar uma célula.|  
|DELETE|Exclui o caractere antes após o cursor ao editar uma célula.|  
|CTRL+ENTER|Confirma as alterações na célula atual sem mover o foco.|  
|CTRL+A|Se <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> é definido como <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, seleciona todas as linhas as <xref:System.Windows.Controls.DataGrid>.|  
  
## <a name="selection-keys"></a>Teclas de seleção  
 Se o <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> estiver definida como <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, não altera o comportamento de navegação, mas navegar com o teclado mantendo a tecla SHIFT pressionada (incluindo CTRL + SHIFT) modificará uma seleção de várias linhas. Antes de iniciar a navegação, o controle marca a linha atual como uma linha de âncora. Quando você navega mantendo a tecla SHIFT pressionada, a seleção inclui todas as linhas entre a linha de âncora e a linha atual.  
  
 As seguintes chaves de seleção modificam a seleção de várias linhas.  
  
- SHIFT + SETA ABAIXO  
  
- CTRL+SETA PARA CIMA  
  
- SHIFT + PAGE DOWN  
  
- SHIFT+PAGE UP  
  
- CTRL + SHIFT + SETA PARA BAIXO  
  
- CTRL + SHIFT + SETA PARA CIMA  
  
- CTRL+SHIFT+HOME  
  
- CTRL+SHIFT+END  
  
## <a name="default-mouse-behavior"></a>Comportamento padrão do mouse  
 A tabela a seguir lista o comportamento de mouse padrão para o <xref:System.Windows.Controls.DataGrid>.  
  
|Ação do mouse|Descrição|  
|------------------|-----------------|  
|Clicar em uma linha não selecionada|Torna a linha clicada a linha atual e a célula clicada a célula atual.|  
|Clicar na célula atual|Coloca a célula atual no modo de edição.|  
|Arrastar uma célula de cabeçalho de coluna|Se o <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A?displayProperty=nameWithType> é de propriedade `true` e o <xref:System.Windows.Controls.DataGridColumn.CanUserReorder%2A?displayProperty=nameWithType> é de propriedade `true` para a coluna atual, move a coluna para que ele pode ser descartado em uma nova posição.|  
|Arrastar um separador de cabeçalho de coluna|Se o <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> é de propriedade `true` e o <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> é de propriedade `true` para a coluna atual, redimensionará a coluna.|  
|Clicar duas vezes em um separador de cabeçalho de coluna|Se o <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> é de propriedade `true` e o <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> é de propriedade `true` para a coluna atual, redimensionará automaticamente a coluna usando o <xref:System.Windows.Controls.DataGridLength.Auto%2A> o modo de dimensionamento.|  
|Clicar em uma célula de cabeçalho de coluna|Se o <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A?displayProperty=nameWithType> é de propriedade `true` e o <xref:System.Windows.Controls.DataGridColumn.CanUserSort%2A?displayProperty=nameWithType> é de propriedade `true` para a coluna atual, classificará a coluna.<br /><br /> Clicar no cabeçalho de uma coluna que já está classificada reverterá a direção de classificação da coluna.<br /><br /> Pressionar a tecla SHIFT ao clicar em vários cabeçalhos de coluna classificará por várias colunas na ordem clicada.|  
|CTRL + clique em uma linha|Se <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> é definido como <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, modificará uma seleção de várias linhas não contíguas.<br /><br /> Se a linha já estiver selecionada, desmarcará a linha.|  
|SHIFT + clique em uma linha|Se <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> é definido como <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, modificará uma seleção de várias linhas contíguas.|  
|Clicar em um cabeçalho de grupo de linha|Expande ou recolhe o grupo.|  
|Clique no botão Selecionar tudo no canto superior esquerdo das <xref:System.Windows.Controls.DataGrid>|Se <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> é definido como <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, seleciona todas as linhas as <xref:System.Windows.Controls.DataGrid>.|  
  
## <a name="mouse-selection"></a>Seleção com o mouse  
 Se o <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> estiver definida como <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, clicando em uma linha ao pressionar a tecla CTRL ou SHIFT modificará uma seleção de várias linhas.  
  
 Ao clicar em uma linha mantendo a tecla CTRL pressionada, a linha mudará seu estado de seleção enquanto todas as outras linhas manterão o estado de seleção atual. Faça isso para selecionar linhas não adjacentes.  
  
 Ao clicar em uma linha ao pressionar a tecla SHIFT, a seleção incluirá todas as linhas entre a linha atual e uma linha de âncora localizada na posição da linha atual antes do clique. Os cliques subsequentes, mantendo a tecla SHIFT pressionada, alteram a linha atual, mas não a linha de âncora. Faça isso para selecionar várias linhas adjacentes.  
  
 As teclas CTRL + SHIFT podem ser combinadas para selecionar intervalos não adjacentes de linhas adjacentes. Para fazer isso, selecione o primeiro intervalo usando SHIFT + clique conforme descrito anteriormente. Depois que o primeiro intervalo de linhas for selecionado, use CTRL + clique para selecionar a primeira linha no próximo intervalo e clique na última linha no próximo intervalo ao pressionar CTRL + SHIFT.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.DataGrid>
- <xref:System.Windows.Controls.DataGrid.SelectionMode%2A>

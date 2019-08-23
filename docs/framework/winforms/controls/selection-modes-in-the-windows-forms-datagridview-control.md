---
title: Modos de seleção no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
ms.assetid: a3ebfd3d-0525-479d-9d96-d9e017289b36
ms.openlocfilehash: dfe26e4749e6bff2d0ccdff47c6ea0b301880772
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960465"
---
# <a name="selection-modes-in-the-windows-forms-datagridview-control"></a>Modos de seleção no controle DataGridView dos Windows Forms
Às vezes, você deseja que seu aplicativo execute ações com base nas seleções do <xref:System.Windows.Forms.DataGridView> usuário dentro de um controle. Dependendo das ações, você talvez queira restringir os tipos de seleção possíveis. Por exemplo, suponha que seu aplicativo possa imprimir um relatório para o registro selecionado no momento. Nesse caso, talvez você queira configurar o <xref:System.Windows.Forms.DataGridView> controle para que clicar em qualquer lugar dentro de uma linha sempre selecione a linha inteira e, portanto, somente uma linha de cada vez pode ser selecionada.  
  
 Você pode especificar as seleções permitidas definindo a <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> Propriedade como um dos valores de enumeração a seguir. <xref:System.Windows.Forms.DataGridViewSelectionMode>  
  
|Valor de DataGridViewSelectionMode|Descrição|  
|-------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>|Clicar em uma célula a seleciona. Cabeçalhos de linha e coluna não podem ser usados para seleção.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>|Clicar em uma célula a seleciona. Clicar em um cabeçalho de coluna seleciona a coluna inteira. Cabeçalhos de coluna não podem ser usados para classificação.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>|Clicar em um cabeçalho de coluna ou célula seleciona a coluna inteira. Cabeçalhos de coluna não podem ser usados para classificação.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>|Clicar em um cabeçalho de linha ou célula seleciona toda a linha.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>|Modo de seleção padrão. Clicar em uma célula a seleciona. Clicar em um cabeçalho de linha seleciona toda a linha.|  
  
> [!NOTE]
> Alterar o modo de seleção em tempo de execução automaticamente limpa a seleção atual.  
  
 Por padrão, os usuários podem selecionar várias linhas, colunas ou células arrastando com o mouse, pressionando CTRL ou SHIFT ao selecionar para estender ou modificar uma seleção ou clicando na célula de cabeçalho do canto superior esquerdo para selecionar todas as células no controle. Para evitar esse comportamento, defina a <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> Propriedade como `false`.  
  
 Os <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> modos <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> e permitem que os usuários excluam linhas selecionando-os e pressionando a tecla Delete. Os usuários podem excluir linhas somente quando a célula atual não está no modo de edição <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> , a propriedade é `true`definida como e a fonte de dados subjacente dá suporte à exclusão de linha controlada pelo usuário. Observe que essas configurações não impedem a exclusão programática de linha.  
  
## <a name="programmatic-selection"></a>Seleção programática  
 O modo de seleção atual restringe o comportamento de seleção programática, bem como a seleção do usuário. Você pode alterar a seleção atual programaticamente definindo `Selected` a propriedade de quaisquer células, linhas ou colunas presentes <xref:System.Windows.Forms.DataGridView> no controle. Você também pode selecionar todas as células no controle por meio <xref:System.Windows.Forms.DataGridView.SelectAll%2A> do método, dependendo do modo de seleção. Para limpar a seleção, use o <xref:System.Windows.Forms.DataGridView.ClearSelection%2A> método.  
  
 Se a <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> propriedade for definida como `true`, você poderá adicionar <xref:System.Windows.Forms.DataGridView> elementos ou removê-los da seleção alterando a `Selected` Propriedade do elemento. Caso contrário, configurar a propriedade `Selected` como `true` para um elemento remove automaticamente os outros elementos da seleção.  
  
 Observe que a alteração do valor da <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> propriedade não altera a seleção atual.  
  
 Você pode recuperar uma coleção das células, linhas ou colunas <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>atualmente selecionadas por meio das propriedades, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>e <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> do <xref:System.Windows.Forms.DataGridView> controle. O acesso a essas propriedades é ineficiente quando todas as células no controle estão selecionadas. Para evitar uma penalidade de desempenho nesse caso, use o <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> método primeiro. Além disso, acessar essas coleções para determinar o número de células, linhas ou colunas selecionadas pode ser ineficiente. Em vez disso, você deve <xref:System.Windows.Forms.DataGridView.GetCellCount%2A>usar <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A>o método <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A> ,, ou, passando <xref:System.Windows.Forms.DataGridViewElementStates.Selected> o valor.  
  
> [!TIP]
>  O código de exemplo que demonstra o uso programático de células selecionadas pode ser <xref:System.Windows.Forms.DataGridView> encontrado na visão geral da classe.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridViewSelectionMode>
- [Seleção e uso da Área de Transferência com o controle DataGridView do Windows Forms](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
- [Como: Definir o modo de seleção do controle Windows Forms DataGridView](how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)

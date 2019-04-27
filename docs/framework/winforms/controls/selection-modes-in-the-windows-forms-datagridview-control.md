---
title: Modos de seleção no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
ms.assetid: a3ebfd3d-0525-479d-9d96-d9e017289b36
ms.openlocfilehash: 79e13e65938252015e43b59a962d40f20963a5df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902662"
---
# <a name="selection-modes-in-the-windows-forms-datagridview-control"></a>Modos de seleção no controle DataGridView dos Windows Forms
Às vezes você deseja que seu aplicativo para executar ações com base nas seleções do usuário dentro de um <xref:System.Windows.Forms.DataGridView> controle. Dependendo das ações, você talvez queira restringir os tipos de seleção possíveis. Por exemplo, suponha que seu aplicativo possa imprimir um relatório para o registro selecionado no momento. Nesse caso, você talvez queira configurar o <xref:System.Windows.Forms.DataGridView> controle, de modo que clicar em qualquer lugar dentro de uma linha sempre seleciona a linha inteira, e então que apenas uma linha por vez pode ser selecionada.  
  
 Você pode especificar as seleções permitidas Configurando a <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> propriedade para um dos seguintes <xref:System.Windows.Forms.DataGridViewSelectionMode> valores de enumeração.  
  
|Valor de DataGridViewSelectionMode|Descrição|  
|-------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>|Clicar em uma célula a seleciona. Cabeçalhos de linha e coluna não podem ser usados para seleção.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>|Clicar em uma célula a seleciona. Clicar em um cabeçalho de coluna seleciona a coluna inteira. Cabeçalhos de coluna não podem ser usados para classificação.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>|Clicar em um cabeçalho de coluna ou célula seleciona a coluna inteira. Cabeçalhos de coluna não podem ser usados para classificação.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>|Clicar em um cabeçalho de linha ou célula seleciona toda a linha.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>|Modo de seleção padrão. Clicar em uma célula a seleciona. Clicar em um cabeçalho de linha seleciona toda a linha.|  
  
> [!NOTE]
>  Alterar o modo de seleção em tempo de execução automaticamente limpa a seleção atual.  
  
 Por padrão, os usuários podem selecionar várias linhas, colunas ou células arrastando com o mouse, pressionando CTRL ou SHIFT ao selecionar para estender ou modificar uma seleção ou clicando na célula de cabeçalho do canto superior esquerdo para selecionar todas as células no controle. Para evitar esse comportamento, defina as <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> propriedade para `false`.  
  
 O <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> e <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> os modos permitem que os usuários excluam linhas selecionando-os e pressionando a tecla DELETE. Os usuários podem excluir linhas apenas quando a célula atual não está no modo de edição, o <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> estiver definida como `true`, e a fonte de dados subjacente dá suporte à exclusão de linha controlada pelo usuário. Observe que essas configurações não impedem a exclusão programática de linha.  
  
## <a name="programmatic-selection"></a>Seleção programática  
 O modo de seleção atual restringe o comportamento de seleção programática, bem como a seleção do usuário. Você pode alterar a seleção atual programaticamente, definindo a `Selected` propriedade de qualquer células, linhas ou colunas presentes no <xref:System.Windows.Forms.DataGridView> controle. Você também pode selecionar todas as células no controle por meio de <xref:System.Windows.Forms.DataGridView.SelectAll%2A> método, dependendo do modo de seleção. Para limpar a seleção, use o <xref:System.Windows.Forms.DataGridView.ClearSelection%2A> método.  
  
 Se o <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> estiver definida como `true`, você pode adicionar <xref:System.Windows.Forms.DataGridView> elementos a ou removê-los da seleção alterando o `Selected` propriedade do elemento. Caso contrário, configurar a propriedade `Selected` como `true` para um elemento remove automaticamente os outros elementos da seleção.  
  
 Observe que o valor de alterar o <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> propriedade não altera a seleção atual.  
  
 Você pode recuperar uma coleção das células selecionadas no momento, linhas ou colunas por meio de <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, e <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> propriedades do <xref:System.Windows.Forms.DataGridView> controle. O acesso a essas propriedades é ineficiente quando todas as células no controle estão selecionadas. Para evitar uma penalidade de desempenho nesse caso, use o <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> método primeiro. Além disso, acessar essas coleções para determinar o número de células, linhas ou colunas selecionadas pode ser ineficiente. Em vez disso, você deve usar o <xref:System.Windows.Forms.DataGridView.GetCellCount%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A>, ou <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A> método, passando o <xref:System.Windows.Forms.DataGridViewElementStates.Selected> valor.  
  
> [!TIP]
>  Código de exemplo que demonstra o uso programático das células selecionadas pode ser encontrado na <xref:System.Windows.Forms.DataGridView> visão geral da classe.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridViewSelectionMode>
- [Seleção e uso da Área de Transferência com o controle DataGridView do Windows Forms](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
- [Como: Definir o modo de seleção do controle DataGridView dos Windows Forms](how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)

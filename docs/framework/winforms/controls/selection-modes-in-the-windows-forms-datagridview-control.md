---
title: Modos de seleção no controle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
ms.assetid: a3ebfd3d-0525-479d-9d96-d9e017289b36
ms.openlocfilehash: e20bf6307d77bf189b698e847c6b855c249dc3c1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743032"
---
# <a name="selection-modes-in-the-windows-forms-datagridview-control"></a>Modos de seleção no controle DataGridView dos Windows Forms

Às vezes, você deseja que seu aplicativo execute ações com base nas seleções do usuário dentro de um controle de <xref:System.Windows.Forms.DataGridView>. Dependendo das ações, você talvez queira restringir os tipos de seleção possíveis. Por exemplo, suponha que seu aplicativo possa imprimir um relatório para o registro selecionado no momento. Nesse caso, talvez você queira configurar o controle de <xref:System.Windows.Forms.DataGridView> para que clicar em qualquer lugar dentro de uma linha sempre selecione a linha inteira e, portanto, somente uma linha de cada vez pode ser selecionada.

Você pode especificar as seleções permitidas definindo a propriedade <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> como um dos valores de enumeração a seguir <xref:System.Windows.Forms.DataGridViewSelectionMode>.

|Valor de DataGridViewSelectionMode|Descrição|
|-------------------------------------|-----------------|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>|Clicar em uma célula a seleciona. Cabeçalhos de linha e coluna não podem ser usados para seleção.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>|Clicar em uma célula a seleciona. Clicar em um cabeçalho de coluna seleciona a coluna inteira. Cabeçalhos de coluna não podem ser usados para classificação.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>|Clicar em um cabeçalho de coluna ou célula seleciona a coluna inteira. Cabeçalhos de coluna não podem ser usados para classificação.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>|Clicar em um cabeçalho de linha ou célula seleciona toda a linha.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>|Modo de seleção padrão. Clicar em uma célula a seleciona. Clicar em um cabeçalho de linha seleciona toda a linha.|

> [!NOTE]
> Alterar o modo de seleção em tempo de execução automaticamente limpa a seleção atual.

Por padrão, os usuários podem selecionar várias linhas, colunas ou células arrastando com o mouse, pressionando CTRL ou SHIFT ao selecionar para estender ou modificar uma seleção ou clicando na célula de cabeçalho do canto superior esquerdo para selecionar todas as células no controle. Para evitar esse comportamento, defina a propriedade <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> como `false`.

Os modos <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> e <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> permitem que os usuários excluam linhas selecionando-os e pressionando a tecla DELETE. Os usuários podem excluir linhas somente quando a célula atual não está no modo de edição, a propriedade <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> é definida como `true`e a fonte de dados subjacente dá suporte à exclusão de linha controlada pelo usuário. Observe que essas configurações não impedem a exclusão programática de linha.

## <a name="programmatic-selection"></a>Seleção programática

O modo de seleção atual restringe o comportamento de seleção programática, bem como a seleção do usuário. Você pode alterar a seleção atual programaticamente definindo a propriedade `Selected` de quaisquer células, linhas ou colunas presentes no controle de <xref:System.Windows.Forms.DataGridView>. Você também pode selecionar todas as células no controle por meio do método <xref:System.Windows.Forms.DataGridView.SelectAll%2A>, dependendo do modo de seleção. Para limpar a seleção, use o método <xref:System.Windows.Forms.DataGridView.ClearSelection%2A>.

Se a propriedade <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> for definida como `true`, você poderá adicionar elementos <xref:System.Windows.Forms.DataGridView> ou removê-los da seleção alterando a propriedade `Selected` do elemento. Caso contrário, configurar a propriedade `Selected` como `true` para um elemento remove automaticamente os outros elementos da seleção.

Observe que a alteração do valor da propriedade <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> não altera a seleção atual.

Você pode recuperar uma coleção das células, linhas ou colunas atualmente selecionadas por meio das propriedades <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>e <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> do controle <xref:System.Windows.Forms.DataGridView>. O acesso a essas propriedades é ineficiente quando todas as células no controle estão selecionadas. Para evitar uma penalidade de desempenho nesse caso, use o método <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> primeiro. Além disso, acessar essas coleções para determinar o número de células, linhas ou colunas selecionadas pode ser ineficiente. Em vez disso, você deve usar o método <xref:System.Windows.Forms.DataGridView.GetCellCount%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A>ou <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A>, passando o valor de <xref:System.Windows.Forms.DataGridViewElementStates.Selected>.

> [!TIP]
> O código de exemplo que demonstra o uso programático de células selecionadas pode ser encontrado na visão geral da classe <xref:System.Windows.Forms.DataGridView>.

## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridViewSelectionMode>
- [Seleção e uso da Área de Transferência com o controle DataGridView dos Windows Forms](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
- [Como definir o modo de seleção do controle DataGridView dos Windows Forms](how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)

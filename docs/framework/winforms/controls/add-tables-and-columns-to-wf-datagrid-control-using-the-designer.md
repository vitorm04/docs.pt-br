---
title: Adicionar tabelas e colunas ao controle DataGrid usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 4a6d1b34-b696-476b-bf8a-57c6230aa9e1
ms.openlocfilehash: fed7465fbe665b1945161653616e3a21640e0b2a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746256"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control-using-the-designer"></a>Como adicionar tabelas e colunas ao controle DataGrid dos Windows Forms usando o designer

> [!NOTE]
> O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado. Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Você pode exibir dados no Windows Forms <xref:System.Windows.Forms.DataGrid> controle em tabelas e colunas criando <xref:System.Windows.Forms.DataGridTableStyle> objetos e adicionando-os ao objeto <xref:System.Windows.Forms.GridTableStylesCollection>, que é acessado por meio da propriedade <xref:System.Windows.Forms.DataGrid> do controle <xref:System.Windows.Forms.DataGrid.TableStyles%2A>. Cada estilo de tabela exibe o conteúdo de qualquer tabela de dados especificada na propriedade <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> da <xref:System.Windows.Forms.DataGridTableStyle>. Por padrão, um estilo de tabela sem estilos de coluna especificados exibirá todas as colunas dentro dessa tabela de dados. Você pode restringir quais colunas da tabela aparecem adicionando <xref:System.Windows.Forms.DataGridColumnStyle> objetos ao <xref:System.Windows.Forms.GridColumnStylesCollection>, que é acessado por meio da propriedade <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> de cada <xref:System.Windows.Forms.DataGridTableStyle>.

Os procedimentos a seguir exigem um projeto de **aplicativo do Windows** com um formulário que contenha um controle de <xref:System.Windows.Forms.DataGrid>. Para obter informações sobre como configurar esse projeto, consulte [como: criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como adicionar controles a Windows Forms](how-to-add-controls-to-windows-forms.md). Por padrão, no Visual Studio 2005, o controle <xref:System.Windows.Forms.DataGrid> não está na **caixa de ferramentas**. Para obter informações sobre como adicioná-lo, consulte [Como Adicionar Itens à Caixa de Ferramentas](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).

### <a name="to-add-a-table-to-the-datagrid-control-in-the-designer"></a>Para adicionar uma tabela ao controle DataGrid no designer

1. Para exibir os dados na tabela, primeiro você deve associar o controle de <xref:System.Windows.Forms.DataGrid> a um DataSet. Para obter mais informações, consulte [Como associar o controle DataGrid dos Windows Forms a uma fonte de dados usando o designer](bind-wf-datagrid-control-to-a-data-source-using-the-designer.md).

2. Selecione a propriedade <xref:System.Windows.Forms.DataGrid.TableStyles%2A> do controle de <xref:System.Windows.Forms.DataGrid> na janela Propriedades e, em seguida, clique no botão de reticências (![botão de reticências (...) na janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) ao lado da propriedade para exibir o **DataGridTableStyle Collection Editor**.

3. No editor de coleção, clique em **Adicionar** para inserir um estilo de tabela.

4. Clique em **OK** para fechar o editor de coleção e, em seguida, abra-o novamente clicando no botão de reticências ao lado da propriedade <xref:System.Windows.Forms.DataGrid.TableStyles%2A>.

     Quando você reabrir o editor de coleção, todas as tabelas de dados vinculadas ao controle aparecerão na lista suspensa da propriedade <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> do estilo de tabela.

5. Na caixa **Membros** do editor de coleção, clique no estilo de tabela.

6. Na caixa **Propriedades** do editor de coleção, selecione o valor <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> para a tabela que você deseja exibir.

### <a name="to-add-a-column-to-the-datagrid-control-in-the-designer"></a>Para adicionar uma coluna ao controle DataGrid no designer

1. Na caixa **Membros** do **Editor de Coleção DataGridTableStyle**, selecione o estilo de tabela adequado. Na caixa **Propriedades** do editor de coleção, selecione a coleção de <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> e, em seguida, clique no botão de reticências (![botão de reticências (...) na janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) ao lado da propriedade para exibir o **Editor de coleção DataGridColumnStyle**.

2. No editor de coleção, clique em **Adicionar** para inserir um estilo de coluna ou clique na seta para baixo ao lado de **Adicionar** para especificar um tipo de coluna.

     Na caixa suspensa, você pode selecionar o tipo de <xref:System.Windows.Forms.DataGridTextBoxColumn> ou de <xref:System.Windows.Forms.DataGridBoolColumn>.

3. Clique em OK para fechar o **Editor de coleção DataGridColumnStyle**e, em seguida, reabra-o clicando no botão de reticências ao lado da propriedade <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>.

     Quando você reabrir o editor de coleção, todas as colunas de dados na tabela de dados associados aparecerão na lista suspensa da propriedade <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> do estilo de coluna.

4. Na caixa **Membros** do editor de coleção, clique no estilo de coluna.

5. Na caixa **Propriedades** do editor de coleção, selecione o valor <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> para a coluna que você deseja exibir.

## <a name="see-also"></a>Consulte também

- [Controle DataGrid](datagrid-control-windows-forms.md)
- [Como excluir ou ocultar colunas no controle DataGrid dos Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)

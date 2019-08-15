---
title: 'Como: Adicionar tabelas e colunas do controle DataGrid do Windows Forms usando o Designer'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 4a6d1b34-b696-476b-bf8a-57c6230aa9e1
ms.openlocfilehash: d11c4f7e4cdfb597477bb99f38612ed648849f20
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040046"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control-using-the-designer"></a>Como: Adicionar tabelas e colunas do controle DataGrid do Windows Forms usando o Designer

> [!NOTE]
> O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado. Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Você pode exibir dados no controle de <xref:System.Windows.Forms.DataGrid> Windows Forms em tabelas e colunas criando <xref:System.Windows.Forms.DataGridTableStyle> objetos <xref:System.Windows.Forms.GridTableStylesCollection> e adicionando-os ao objeto, que é acessado por <xref:System.Windows.Forms.DataGrid> meio da <xref:System.Windows.Forms.DataGrid.TableStyles%2A> Propriedade do controle. Cada estilo de tabela exibe o conteúdo de qualquer tabela de dados especificada na <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> propriedade <xref:System.Windows.Forms.DataGridTableStyle>do. Por padrão, um estilo de tabela sem estilos de coluna especificados exibirá todas as colunas dentro dessa tabela de dados. Você pode restringir quais colunas da tabela aparecem <xref:System.Windows.Forms.DataGridColumnStyle> adicionando objetos <xref:System.Windows.Forms.GridColumnStylesCollection>ao, que é acessado por meio da <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> propriedade de cada <xref:System.Windows.Forms.DataGridTableStyle>uma.

Os procedimentos a seguir exigem um projeto de **aplicativo do Windows** com um formulário <xref:System.Windows.Forms.DataGrid> que contém um controle. Para obter informações sobre como configurar esse projeto, consulte [como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms [e como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md). Por padrão, no Visual Studio 2005, <xref:System.Windows.Forms.DataGrid> o controle não está na **caixa de ferramentas**. Para obter informações sobre como adicioná- [lo, consulte Como: Adicionar itens à caixa de](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))ferramentas.

### <a name="to-add-a-table-to-the-datagrid-control-in-the-designer"></a>Para adicionar uma tabela ao controle DataGrid no designer

1. Para exibir dados na tabela, primeiro você deve associar o <xref:System.Windows.Forms.DataGrid> controle a um conjunto de dado. Para obter mais informações, confira [Como: Associe o controle DataGrid Windows Forms a uma fonte de dados usando o](bind-wf-datagrid-control-to-a-data-source-using-the-designer.md)designer.

2. Selecione a <xref:System.Windows.Forms.DataGrid> Propriedade do <xref:System.Windows.Forms.DataGrid.TableStyles%2A> controle na janela Propriedades e, em seguida, clique no botão de![reticências (o botão de reticências (...) na janela Propriedades](./media/visual-studio-ellipsis-button.png)do Visual Studio.) ao lado da propriedade para exibir o **Editor de coleção DataGridTableStyle**.

3. No editor de coleção, clique em **Adicionar** para inserir um estilo de tabela.

4. Clique em **OK** para fechar o editor de coleção e, em seguida, abra-o novamente clicando no botão <xref:System.Windows.Forms.DataGrid.TableStyles%2A> de reticências ao lado da propriedade.

     Quando você reabrir o editor de coleção, todas as tabelas de dados vinculadas ao controle aparecerão na lista suspensa para a <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> Propriedade do estilo de tabela.

5. Na caixa **Membros** do editor de coleção, clique no estilo de tabela.

6. Na caixa **Propriedades** do editor de coleção, selecione o <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> valor da tabela que você deseja exibir.

### <a name="to-add-a-column-to-the-datagrid-control-in-the-designer"></a>Para adicionar uma coluna ao controle DataGrid no designer

1. Na caixa **Membros** do **Editor de Coleção DataGridTableStyle**, selecione o estilo de tabela adequado. Na caixa **Propriedades** do editor de coleção, selecione a <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> coleção e, em seguida, clique no botão de reticências (![o botão de reticências (...) na janela Propriedades](./media/visual-studio-ellipsis-button.png)do Visual Studio.) ao lado da propriedade como Exiba o **Editor de coleção DataGridColumnStyle**.

2. No editor de coleção, clique em **Adicionar** para inserir um estilo de coluna ou clique na seta para baixo ao lado de **Adicionar** para especificar um tipo de coluna.

     Na caixa suspensa, você pode selecionar o <xref:System.Windows.Forms.DataGridTextBoxColumn> tipo ou. <xref:System.Windows.Forms.DataGridBoolColumn>

3. Clique em OK para fechar o **Editor de coleção DataGridColumnStyle**e, em seguida, abra-o novamente clicando no botão <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> de reticências ao lado da propriedade.

     Quando você reabrir o editor de coleção, todas as colunas de dados na tabela de dados associados aparecerão na lista suspensa para a <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> Propriedade do estilo de coluna.

4. Na caixa **Membros** do editor de coleção, clique no estilo de coluna.

5. Na caixa **Propriedades** do editor de coleção, selecione o <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> valor da coluna que você deseja exibir.

## <a name="see-also"></a>Consulte também

- [Controle DataGrid](datagrid-control-windows-forms.md)
- [Como: Excluir ou ocultar colunas no controle DataGrid de Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)

---
title: Como adicionar tabelas e colunas ao controle DataGrid dos Windows Forms usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 4a6d1b34-b696-476b-bf8a-57c6230aa9e1
ms.openlocfilehash: 4b29a3040415cce8fad27abf9bf46aa3d3e14b4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control-using-the-designer"></a>Como adicionar tabelas e colunas ao controle DataGrid dos Windows Forms usando o designer
> [!NOTE]
>  O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado. Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Você pode exibir dados em Windows Forms <xref:System.Windows.Forms.DataGrid> controle em tabelas e colunas criando <xref:System.Windows.Forms.DataGridTableStyle> objetos e adicioná-los para o <xref:System.Windows.Forms.GridTableStylesCollection> objeto, que é acessado por meio de <xref:System.Windows.Forms.DataGrid> do controle <xref:System.Windows.Forms.DataGrid.TableStyles%2A> propriedade. Cada estilo de tabela exibe o conteúdo de qualquer tabela de dados é especificada no <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> propriedade o <xref:System.Windows.Forms.DataGridTableStyle>. Por padrão, um estilo de tabela sem estilos de coluna especificados exibirá todas as colunas dentro dessa tabela de dados. Você pode restringir quais colunas da tabela aparecem adicionando <xref:System.Windows.Forms.DataGridColumnStyle> objetos para o <xref:System.Windows.Forms.GridColumnStylesCollection>, que é acessado por meio de <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> propriedade de cada <xref:System.Windows.Forms.DataGridTableStyle>.  
  
 Os procedimentos a seguir exigem uma **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.DataGrid> controle. Para obter informações sobre como configurar um projeto desse tipo, consulte [Como criar um projeto de aplicativo do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) e [Como adicionar controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md). Por padrão em [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], o <xref:System.Windows.Forms.DataGrid> controle não está no **caixa de ferramentas**. Para obter informações sobre como adicioná-lo, consulte [Como Adicionar Itens à Caixa de Ferramentas](http://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-a-table-to-the-datagrid-control-in-the-designer"></a>Para adicionar uma tabela ao controle DataGrid no designer  
  
1.  Para exibir os dados na tabela, você deve primeiro associar o <xref:System.Windows.Forms.DataGrid> controle a um conjunto de dados. Para obter mais informações, consulte [Como associar o controle DataGrid dos Windows Forms a uma fonte de dados usando o designer](../../../../docs/framework/winforms/controls/bind-wf-datagrid-control-to-a-data-source-using-the-designer.md).  
  
2.  Selecione o <xref:System.Windows.Forms.DataGrid> do controle <xref:System.Windows.Forms.DataGrid.TableStyles%2A> propriedade na janela Propriedades e, em seguida, clique no botão de reticências (![de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) ao lado de a propriedade para exibir o **DataGridTableStyle Collection Editor**.  
  
3.  No editor de coleção, clique em **Adicionar** para inserir um estilo de tabela.  
  
4.  Clique em **Okey** para fechar o editor de coleção e, em seguida, reabra-o clicando no botão de reticências ao lado de <xref:System.Windows.Forms.DataGrid.TableStyles%2A> propriedade.  
  
     Quando você reabrir o editor de coleção, nenhuma tabela de dados associada ao controle aparecerá na lista suspensa para o <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> propriedade de estilo de tabela.  
  
5.  Na caixa **Membros** do editor de coleção, clique no estilo de tabela.  
  
6.  No **propriedades** caixa do editor de coleção, selecione o <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> valor para a tabela que você deseja exibir.  
  
### <a name="to-add-a-column-to-the-datagrid-control-in-the-designer"></a>Para adicionar uma coluna ao controle DataGrid no designer  
  
1.  Na caixa **Membros** do **Editor de Coleção DataGridTableStyle**, selecione o estilo de tabela adequado. No **propriedades** caixa do editor de coleção, selecione o <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> coleção e, em seguida, clique no botão de reticências (![de tela de VisualStudioEllipsesButton] (../../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) ao lado da propriedade para exibir o **DataGridColumnStyle Collection Editor**.  
  
2.  No editor de coleção, clique em **Adicionar** para inserir um estilo de coluna ou clique na seta para baixo ao lado de **Adicionar** para especificar um tipo de coluna.  
  
     Na caixa suspensa, você pode selecionar o <xref:System.Windows.Forms.DataGridTextBoxColumn> ou <xref:System.Windows.Forms.DataGridBoolColumn> tipo.  
  
3.  Clique em Okey para fechar o **DataGridColumnStyle Collection Editor**e, em seguida, reabra-o clicando no botão de reticências ao lado de <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> propriedade.  
  
     Quando você reabrir o editor de coleção, quaisquer colunas de dados na tabela de dados associada serão exibido na lista suspensa para o <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> propriedade do estilo de coluna.  
  
4.  Na caixa **Membros** do editor de coleção, clique no estilo de coluna.  
  
5.  No **propriedades** caixa do editor de coleção, selecione o <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> valor para a coluna que você deseja exibir.  
  
## <a name="see-also"></a>Consulte também  
 [Controle DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Como excluir ou ocultar colunas no controle DataGrid do Windows Forms](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)

---
title: Excluir ou ocultar colunas no controle DataGrid
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], deleting columns
- DataGrid control [Windows Forms], deleting columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
- columns [Windows Forms], deleting in data grids
- DataGrid control [Windows Forms], hiding columns
ms.assetid: bcd0dd96-6687-4c48-b0e1-d5287b93ac91
ms.openlocfilehash: c730be934e9b978bdaf09bc7e668b4318077fba5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743301"
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a>Como excluir ou ocultar colunas no controle DataGrid dos Windows Forms
> [!NOTE]
> O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado. Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Você pode excluir ou ocultar programaticamente colunas no controle de <xref:System.Windows.Forms.DataGrid> Windows Forms usando as propriedades e métodos dos objetos <xref:System.Windows.Forms.GridColumnStylesCollection> e <xref:System.Windows.Forms.DataGridColumnStyle> (que são membros da classe <xref:System.Windows.Forms.DataGridTableStyle>).  
  
 As colunas excluídas ou ocultas ainda existem na fonte de dados à qual a grade está associada e ainda podem ser acessados por meio de programação. Elas simplesmente não são visíveis no datagrid.  
  
> [!NOTE]
> Se seu aplicativo não acessar determinadas colunas de dados e você não desejar exibi-los no datagrid, provavelmente não será necessário nem mesmo incluí-los na fonte de dados.  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a>Excluir uma coluna do DataGrid com programação  
  
1. Na área declarações do formulário, declare uma nova instância da classe <xref:System.Windows.Forms.DataGridTableStyle>.  
  
2. Defina a propriedade <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> como a tabela na fonte de dados à qual você deseja aplicar o estilo. O exemplo a seguir usa a propriedade <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType>, que pressupõe que já está definida.  
  
3. Adicione o novo objeto <xref:System.Windows.Forms.DataGridTableStyle> à coleção de estilos de tabela do DataGrid.  
  
4. Chame o método <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> da coleção de <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> do <xref:System.Windows.Forms.DataGrid>, especificando o índice de coluna da coluna a ser excluída.  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub DeleteColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Delete the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles.RemoveAt(0)  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void deleteColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Delete the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles.RemoveAt(0);  
    }  
    ```  
  
### <a name="to-hide-a-column-in-the-datagrid-programmatically"></a>Ocultar uma coluna do DataGrid com programação  
  
1. Na área declarações do formulário, declare uma nova instância da classe <xref:System.Windows.Forms.DataGridTableStyle>.  
  
2. Defina a propriedade <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> do <xref:System.Windows.Forms.DataGridTableStyle> para a tabela na fonte de dados à qual você deseja aplicar o estilo. O exemplo de código a seguir usa a propriedade <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType>, que supõe que já esteja definido.  
  
3. Adicione o novo objeto <xref:System.Windows.Forms.DataGridTableStyle> à coleção de estilos de tabela do DataGrid.  
  
4. Oculte a coluna definindo sua propriedade `Width` como 0, especificando o índice de coluna da coluna a ser ocultada.  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub HideColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Hide the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles(0).Width = 0  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void hideColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Hide the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles[0].Width = 0;  
    }  
    ```  
  
## <a name="see-also"></a>Veja também

- [Como alterar dados exibidos no tempo de execução no controle DataGrid do Windows Forms](change-displayed-data-at-run-time-wf-datagrid-control.md)
- [Como adicionar tabelas e colunas ao controle DataGrid do Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)

---
title: 'Como: Excluir ou ocultar colunas no controle DataGrid do Windows Forms'
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
ms.openlocfilehash: 70229abddb831788f521f85747db1093c941ba8a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967383"
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a>Como: Excluir ou ocultar colunas no controle DataGrid do Windows Forms
> [!NOTE]
> O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado. Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Você pode excluir ou ocultar programaticamente colunas no <xref:System.Windows.Forms.DataGrid> controle de Windows Forms usando as propriedades e métodos <xref:System.Windows.Forms.GridColumnStylesCollection> dos objetos <xref:System.Windows.Forms.DataGridColumnStyle> e (que são membros da <xref:System.Windows.Forms.DataGridTableStyle> classe).  
  
 As colunas excluídas ou ocultas ainda existem na fonte de dados à qual a grade está associada e ainda podem ser acessados por meio de programação. Elas simplesmente não são visíveis no datagrid.  
  
> [!NOTE]
> Se seu aplicativo não acessar determinadas colunas de dados e você não desejar exibi-los no datagrid, provavelmente não será necessário nem mesmo incluí-los na fonte de dados.  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a>Excluir uma coluna do DataGrid com programação  
  
1. Na área declarações do formulário, declare uma nova instância da <xref:System.Windows.Forms.DataGridTableStyle> classe.  
  
2. Defina a <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> propriedade para a tabela na fonte de dados à qual você deseja aplicar o estilo. O exemplo a seguir usa <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> a propriedade, que pressupõe que já está definida.  
  
3. Adicione o novo <xref:System.Windows.Forms.DataGridTableStyle> objeto à coleção de estilos de tabela do DataGrid.  
  
4. Chame o <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> método <xref:System.Windows.Forms.DataGrid>da <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> coleção de, especificando o índice de coluna da coluna a ser excluída.  
  
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
  
1. Na área declarações do formulário, declare uma nova instância da <xref:System.Windows.Forms.DataGridTableStyle> classe.  
  
2. Defina a <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> propriedade <xref:System.Windows.Forms.DataGridTableStyle> do para a tabela na fonte de dados à qual você deseja aplicar o estilo. O exemplo de código a seguir <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> usa a propriedade, que pressupõe que já está definida.  
  
3. Adicione o novo <xref:System.Windows.Forms.DataGridTableStyle> objeto à coleção de estilos de tabela do DataGrid.  
  
4. Oculte a coluna definindo sua `Width` Propriedade como 0, especificando o índice de coluna da coluna a ser ocultada.  
  
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
  
## <a name="see-also"></a>Consulte também

- [Como: Alterar os dados exibidos em tempo de execução no controle DataGrid Windows Forms](change-displayed-data-at-run-time-wf-datagrid-control.md)
- [Como: Adicionar tabelas e colunas ao controle DataGrid de Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)

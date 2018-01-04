---
title: Como excluir ou ocultar colunas no controle DataGrid dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 65257ec5f9ca51a795abca119e5449d6219042bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a>Como excluir ou ocultar colunas no controle DataGrid dos Windows Forms
> [!NOTE]
>  O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado. Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Programaticamente, você pode excluir ou ocultar colunas no Windows Forms <xref:System.Windows.Forms.DataGrid> controle usando as propriedades e métodos do <xref:System.Windows.Forms.GridColumnStylesCollection> e <xref:System.Windows.Forms.DataGridColumnStyle> objetos (que são membros do <xref:System.Windows.Forms.DataGridTableStyle> classe).  
  
 As colunas excluídas ou ocultas ainda existem na fonte de dados à qual a grade está associada e ainda podem ser acessados por meio de programação. Elas simplesmente não são visíveis no datagrid.  
  
> [!NOTE]
>  Se seu aplicativo não acessar determinadas colunas de dados e você não desejar exibi-los no datagrid, provavelmente não será necessário nem mesmo incluí-los na fonte de dados.  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a>Excluir uma coluna do DataGrid com programação  
  
1.  Na área de declarações do formulário, declarar uma nova instância do <xref:System.Windows.Forms.DataGridTableStyle> classe.  
  
2.  Definir o <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> propriedade para a tabela na fonte de dados que você deseja aplicar o estilo. O exemplo a seguir usa o <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> propriedade, que ele pressupõe que já está definida.  
  
3.  Adicionar o novo <xref:System.Windows.Forms.DataGridTableStyle> objeto à coleção de estilos de tabela de grade.  
  
4.  Chamar o <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> método o <xref:System.Windows.Forms.DataGrid>do <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> coleção, que especifica o índice de coluna da coluna para excluir.  
  
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
  
1.  Na área de declarações do formulário, declarar uma nova instância do <xref:System.Windows.Forms.DataGridTableStyle> classe.  
  
2.  Definir o <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> propriedade do <xref:System.Windows.Forms.DataGridTableStyle> para a tabela na fonte de dados que você deseja aplicar o estilo. O seguinte exemplo de código usa o <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> propriedade, que ele pressupõe que já está definida.  
  
3.  Adicionar o novo <xref:System.Windows.Forms.DataGridTableStyle> objeto à coleção de estilos de tabela de grade.  
  
4.  Ocultar a coluna, definindo seu `Width` propriedade como 0, que especifica o índice de coluna da coluna para ocultar.  
  
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
 [Como alterar os dados exibidos em tempo de execução no controle DataGrid dos Windows Forms](../../../../docs/framework/winforms/controls/change-displayed-data-at-run-time-wf-datagrid-control.md)  
 [Como adicionar tabelas e colunas ao controle DataGrid do Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)

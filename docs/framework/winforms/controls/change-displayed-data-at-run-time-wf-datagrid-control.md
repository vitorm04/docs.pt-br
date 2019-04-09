---
title: 'Como: Alterar os dados exibidos em tempo de execução no controle DataGrid do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DataGrid control [Windows Forms], dynamically changing at run time
- DataGrid control [Windows Forms], data binding
- cells [Windows Forms], changing DataGrid cell values
ms.assetid: 0c7a6d00-30de-416e-8223-0a81ddb4c1f8
ms.openlocfilehash: 27608a7fbce5e9aa815b43e1d7202fa11e52ee1c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175598"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a>Como: Alterar os dados exibidos em tempo de execução no controle DataGrid do Windows Forms
> [!NOTE]
>  O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado. Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Depois de criar um Windows Forms <xref:System.Windows.Forms.DataGrid> usando os recursos de tempo de design, você também poderá alterar dinamicamente os elementos do <xref:System.Data.DataSet> objeto da grade em tempo de execução. Isso pode incluir alterações em valores individuais da tabela ou alterar a fonte de dados está vinculado a <xref:System.Windows.Forms.DataGrid> controle. Alterações em valores individuais são feitas por meio de <xref:System.Data.DataSet> do objeto, não o <xref:System.Windows.Forms.DataGrid> controle.  
  
### <a name="to-change-data-programmatically"></a>Alterar dados com programação  
  
1.  Especifique a tabela desejada do <xref:System.Data.DataSet> objeto e o estado desejado de linhas e de campo da tabela e defina a célula igual para o novo valor.  
  
    > [!NOTE]
    >  Para especificar o primeiro índice da <xref:System.Data.DataSet> ou a primeira linha da tabela, use 0.  
  
     O exemplo a seguir mostra como alterar a segunda entrada da primeira linha da primeira tabela de um conjunto de dados, clicando em `Button1`. O <xref:System.Data.DataSet> (`ds`) e tabelas (`0` e `1`) foram criados anteriormente.  
  
    ```vb  
    Protected Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       ds.tables(0).rows(0)(1) = "NewEntry"  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       ds.Tables[0].Rows[0][1]="NewEntry";  
    }  
    ```  
  
    ```cpp  
    private:   
       void button1_Click(System::Object^ sender, System::EventArgs^ e)  
       {  
          dataSet1->Tables[0]->Rows[0][1] = "NewEntry";  
       }  
    ```  
  
     (Visual c#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     No tempo, você pode usar de execução de <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> método para associar o <xref:System.Windows.Forms.DataGrid> controle a uma fonte de dados diferentes. Por exemplo, você pode ter vários controles de dados [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], cada um conectado a um banco de dados diferente.  
  
### <a name="to-change-the-datasource-programmatically"></a>Alterar o DataSource com programação  
  
1.  Defina o <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> método com o nome da fonte de dados e tabela que você deseja associar.  
  
     O exemplo a seguir mostra como alterar a fonte de data usando o <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> método para um [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] controle de dados (adoPubsAuthors) conectado à tabela autores no banco de dados Pubs.  
  
    ```vb  
    Private Sub ResetSource()  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors")  
    End Sub  
    ```  
  
    ```csharp  
    private void ResetSource()  
    {  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors");  
    }  
    ```  
  
    ```cpp  
    private:  
       void ResetSource()  
       {  
          dataGrid1->SetDataBinding(adoPubsAuthors, "Authors");  
       }  
    ```  
  
## <a name="see-also"></a>Consulte também

- [DataSets ADO.NET](../../data/adonet/ado-net-datasets.md)
- [Como: Excluir ou ocultar colunas no controle DataGrid do Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Como: Adicionar tabelas e colunas ao controle DataGrid do Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Como: Associar o controle DataGrid do Windows Forms a uma fonte de dados](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)

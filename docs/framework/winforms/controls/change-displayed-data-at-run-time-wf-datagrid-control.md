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
ms.openlocfilehash: c7bf70a67729744f4cf96318f6b270a5ea81b812
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917719"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a>Como: Alterar os dados exibidos em tempo de execução no controle DataGrid do Windows Forms
> [!NOTE]
> O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado. Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Depois de criar um Windows Forms <xref:System.Windows.Forms.DataGrid> usando os recursos de tempo de design, você também pode querer alterar dinamicamente os <xref:System.Data.DataSet> elementos do objeto da grade em tempo de execução. Isso pode incluir alterações nos valores individuais da tabela ou na alteração de qual fonte de dados está associada ao <xref:System.Windows.Forms.DataGrid> controle. As alterações em valores individuais são feitas por <xref:System.Data.DataSet> meio do objeto, <xref:System.Windows.Forms.DataGrid> não do controle.  
  
### <a name="to-change-data-programmatically"></a>Alterar dados com programação  
  
1. Especifique a tabela desejada do <xref:System.Data.DataSet> objeto e a linha e o campo desejados da tabela e defina a célula igual ao novo valor.  
  
    > [!NOTE]
    > Para especificar a primeira tabela do <xref:System.Data.DataSet> ou a primeira linha da tabela, use 0.  
  
     O exemplo a seguir mostra como alterar a segunda entrada da primeira linha da primeira tabela de um conjunto de um, clicando `Button1`em. As <xref:System.Data.DataSet> tabelas`ds`() e (`0` e `1`) foram criadas anteriormente.  
  
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
  
     (Visual C#, Visual C++) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     Em tempo de execução, você pode <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> usar o método para <xref:System.Windows.Forms.DataGrid> associar o controle a uma fonte de dados diferente. Por exemplo, você pode ter vários controles de dados ADO.NET, cada um conectado a um banco de dado diferente.  
  
### <a name="to-change-the-datasource-programmatically"></a>Alterar o DataSource com programação  
  
1. Defina o <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> método como o nome da fonte de dados e da tabela que você deseja associar.  
  
     O exemplo a seguir mostra como alterar a fonte de data usando <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> o método para um controle de dados ADO.net (adoPubsAuthors) que está conectado à tabela autores no banco de dados pubs.  
  
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
- [Como: Excluir ou ocultar colunas no controle DataGrid de Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Como: Adicionar tabelas e colunas ao controle DataGrid de Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Como: Associar o Windows Forms controle DataGrid a uma fonte de dados](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)

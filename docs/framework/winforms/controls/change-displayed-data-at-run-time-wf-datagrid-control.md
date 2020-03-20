---
title: Alterar dados exibidos em tempo de execução no controle datagrid
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
ms.openlocfilehash: 6b788c10784082a0c74ee09f8cd85d540c670b84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142375"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a>Como alterar dados exibidos no tempo de execução no controle DataGrid dos Windows Forms
> [!NOTE]
> O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado. Para obter mais informações, consulte [Diferenças entre os formulários do Windows DataGridView e controles datagrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Depois de criar um <xref:System.Windows.Forms.DataGrid> Formulário do Windows usando os recursos de tempo de <xref:System.Data.DataSet> design, você também pode querer alterar dinamicamente elementos do objeto da grade em tempo de execução. Isso pode incluir alterações nos valores individuais da tabela <xref:System.Windows.Forms.DataGrid> ou alterar qual fonte de dados está vinculada ao controle. As alterações nos valores individuais são feitas através do <xref:System.Data.DataSet> objeto, não do <xref:System.Windows.Forms.DataGrid> controle.  
  
### <a name="to-change-data-programmatically"></a>Alterar dados com programação  
  
1. Especifique a <xref:System.Data.DataSet> tabela desejada do objeto e a linha e o campo desejados da tabela e defina a célula igual ao novo valor.  
  
    > [!NOTE]
    > Para especificar a <xref:System.Data.DataSet> primeira tabela da primeira linha da tabela, use 0.  
  
     O exemplo a seguir mostra como alterar a segunda entrada da primeira linha `Button1`da primeira tabela de um conjunto de dados clicando em . As <xref:System.Data.DataSet> `ds`tabelas (`0` `1`e tabelas ) foram previamente criadas.  
  
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
  
     No tempo de execução, você pode usar o <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> método para vincular o <xref:System.Windows.Forms.DataGrid> controle a uma fonte de dados diferente. Por exemplo, você pode ter vários controles de dados ADO.NET, cada um conectado a um banco de dados diferente.  
  
### <a name="to-change-the-datasource-programmatically"></a>Alterar o DataSource com programação  
  
1. Defina <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> o método para o nome da fonte de dados e da tabela a que deseja vincular.  
  
     O exemplo a seguir mostra como <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> alterar a fonte de data usando o método para um ADO.NET controle de dados (adoPubsAuthors) que está conectado à tabela Autores no banco de dados pubs.  
  
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
  
## <a name="see-also"></a>Confira também

- [DataSets ADO.NET](../../data/adonet/ado-net-datasets.md)
- [Como excluir ou ocultar colunas no controle DataGrid do Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Como adicionar tabelas e colunas ao controle DataGrid do Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Como associar o controle DataGrid do Windows Forms a uma fonte de dados](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)

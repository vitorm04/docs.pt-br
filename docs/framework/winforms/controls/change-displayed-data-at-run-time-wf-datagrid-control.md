---
title: "Como alterar dados exibidos no tempo de execução no controle DataGrid dos Windows Forms"
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
- cpp
helpviewer_keywords:
- DataGrid control [Windows Forms], dynamically changing at run time
- DataGrid control [Windows Forms], data binding
- cells [Windows Forms], changing DataGrid cell values
ms.assetid: 0c7a6d00-30de-416e-8223-0a81ddb4c1f8
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c34c6207c29f008606cc4ace83aa4f94c41f6851
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a>Como alterar dados exibidos no tempo de execução no controle DataGrid dos Windows Forms
> [!NOTE]
>  O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado. Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Depois de ter criado uma Windows Forms <xref:System.Windows.Forms.DataGrid> usando os recursos de tempo de design, você também poderá alterar dinamicamente os elementos do <xref:System.Data.DataSet> objeto da grade em tempo de execução. Isso pode incluir as alterações para qualquer um dos valores individuais da tabela ou alterar a fonte de dados está vinculado a <xref:System.Windows.Forms.DataGrid> controle. Alterações em valores individuais são feitas por meio de <xref:System.Data.DataSet> do objeto, não o <xref:System.Windows.Forms.DataGrid> controle.  
  
### <a name="to-change-data-programmatically"></a>Alterar dados com programação  
  
1.  Especifique a tabela desejada a partir de <xref:System.Data.DataSet> desejados de linha e campo da tabela e defina a célula como o novo valor e objeto.  
  
    > [!NOTE]
    >  Para especificar a primeira tabela do <xref:System.Data.DataSet> ou a primeira linha da tabela, use 0.  
  
     O exemplo a seguir mostra como alterar a segunda entrada da primeira linha da primeira tabela de um conjunto de dados clicando em `Button1`. O <xref:System.Data.DataSet> (`ds`) e tabelas (`0` e `1`) foram criadas anteriormente.  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Coloque o seguinte código no construtor de formulários para registrar o manipulador de eventos.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     No tempo, você pode usar de execução de <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> método para associar o <xref:System.Windows.Forms.DataGrid> controle a uma fonte de dados diferente. Por exemplo, você pode ter vários controles de dados [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], cada um conectado a um banco de dados diferente.  
  
### <a name="to-change-the-datasource-programmatically"></a>Alterar o DataSource com programação  
  
1.  Definir o <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> método com o nome da fonte de dados e da tabela que você deseja associar a.  
  
     O exemplo a seguir mostra como alterar a fonte de data usando o <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> método para um [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] controle de dados (adoPubsAuthors) que está conectada à tabela de autores no banco de dados Pubs.  
  
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
 [DataSets ADO.NET](../../../../docs/framework/data/adonet/ado-net-datasets.md)  
 [Como excluir ou ocultar colunas no controle DataGrid do Windows Forms](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [Como adicionar tabelas e colunas ao controle DataGrid do Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [Como associar o controle DataGrid dos Windows Forms a uma fonte de dados](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)

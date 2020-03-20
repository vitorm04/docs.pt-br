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
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="8105e-102">Como alterar dados exibidos no tempo de execução no controle DataGrid dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8105e-102">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="8105e-103">O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="8105e-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="8105e-104">Para obter mais informações, consulte [Diferenças entre os formulários do Windows DataGridView e controles datagrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="8105e-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="8105e-105">Depois de criar um <xref:System.Windows.Forms.DataGrid> Formulário do Windows usando os recursos de tempo de <xref:System.Data.DataSet> design, você também pode querer alterar dinamicamente elementos do objeto da grade em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8105e-105">After you have created a Windows Forms <xref:System.Windows.Forms.DataGrid> using the design-time features, you may also wish to dynamically change elements of the <xref:System.Data.DataSet> object of the grid at run time.</span></span> <span data-ttu-id="8105e-106">Isso pode incluir alterações nos valores individuais da tabela <xref:System.Windows.Forms.DataGrid> ou alterar qual fonte de dados está vinculada ao controle.</span><span class="sxs-lookup"><span data-stu-id="8105e-106">This can include changes to either individual values of the table or changing which data source is bound to the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="8105e-107">As alterações nos valores individuais são feitas através do <xref:System.Data.DataSet> objeto, não do <xref:System.Windows.Forms.DataGrid> controle.</span><span class="sxs-lookup"><span data-stu-id="8105e-107">Changes to individual values are done through the <xref:System.Data.DataSet> object, not the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
### <a name="to-change-data-programmatically"></a><span data-ttu-id="8105e-108">Alterar dados com programação</span><span class="sxs-lookup"><span data-stu-id="8105e-108">To change data programmatically</span></span>  
  
1. <span data-ttu-id="8105e-109">Especifique a <xref:System.Data.DataSet> tabela desejada do objeto e a linha e o campo desejados da tabela e defina a célula igual ao novo valor.</span><span class="sxs-lookup"><span data-stu-id="8105e-109">Specify the desired table from the <xref:System.Data.DataSet> object and the desired row and field from the table and set the cell equal to the new value.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8105e-110">Para especificar a <xref:System.Data.DataSet> primeira tabela da primeira linha da tabela, use 0.</span><span class="sxs-lookup"><span data-stu-id="8105e-110">To specify the first table of the <xref:System.Data.DataSet> or the first row of the table, use 0.</span></span>  
  
     <span data-ttu-id="8105e-111">O exemplo a seguir mostra como alterar a segunda entrada da primeira linha `Button1`da primeira tabela de um conjunto de dados clicando em .</span><span class="sxs-lookup"><span data-stu-id="8105e-111">The following example shows how to change the second entry of the first row of the first table of a dataset by clicking `Button1`.</span></span> <span data-ttu-id="8105e-112">As <xref:System.Data.DataSet> `ds`tabelas (`0` `1`e tabelas ) foram previamente criadas.</span><span class="sxs-lookup"><span data-stu-id="8105e-112">The <xref:System.Data.DataSet> (`ds`) and Tables (`0` and `1`) were previously created.</span></span>  
  
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
  
     <span data-ttu-id="8105e-113">(Visual C#, Visual C++) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="8105e-113">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="8105e-114">No tempo de execução, você pode usar o <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> método para vincular o <xref:System.Windows.Forms.DataGrid> controle a uma fonte de dados diferente.</span><span class="sxs-lookup"><span data-stu-id="8105e-114">At run time you can use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to bind the <xref:System.Windows.Forms.DataGrid> control to a different data source.</span></span> <span data-ttu-id="8105e-115">Por exemplo, você pode ter vários controles de dados ADO.NET, cada um conectado a um banco de dados diferente.</span><span class="sxs-lookup"><span data-stu-id="8105e-115">For example, you may have several ADO.NET data controls, each connected to a different database.</span></span>  
  
### <a name="to-change-the-datasource-programmatically"></a><span data-ttu-id="8105e-116">Alterar o DataSource com programação</span><span class="sxs-lookup"><span data-stu-id="8105e-116">To change the DataSource programmatically</span></span>  
  
1. <span data-ttu-id="8105e-117">Defina <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> o método para o nome da fonte de dados e da tabela a que deseja vincular.</span><span class="sxs-lookup"><span data-stu-id="8105e-117">Set the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to the name of the data source and table you want to bind to.</span></span>  
  
     <span data-ttu-id="8105e-118">O exemplo a seguir mostra como <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> alterar a fonte de data usando o método para um ADO.NET controle de dados (adoPubsAuthors) que está conectado à tabela Autores no banco de dados pubs.</span><span class="sxs-lookup"><span data-stu-id="8105e-118">The following example shows how to change the date source using the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to an ADO.NET data control (adoPubsAuthors) that is connected to the Authors table in the Pubs database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8105e-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="8105e-119">See also</span></span>

- [<span data-ttu-id="8105e-120">DataSets ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8105e-120">ADO.NET DataSets</span></span>](../../data/adonet/ado-net-datasets.md)
- [<span data-ttu-id="8105e-121">Como excluir ou ocultar colunas no controle DataGrid do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8105e-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="8105e-122">Como adicionar tabelas e colunas ao controle DataGrid do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8105e-122">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="8105e-123">Como associar o controle DataGrid do Windows Forms a uma fonte de dados</span><span class="sxs-lookup"><span data-stu-id="8105e-123">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)

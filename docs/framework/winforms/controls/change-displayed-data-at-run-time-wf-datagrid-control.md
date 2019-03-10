---
title: 'Como: Alterar os dados exibidos em tempo de execução no controle DataGrid dos Windows Forms'
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
ms.openlocfilehash: 3ba23dd3966591777c7e354f79dd45ec4530955a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714951"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="4fa02-102">Como: Alterar os dados exibidos em tempo de execução no controle DataGrid dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4fa02-102">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="4fa02-103">O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="4fa02-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="4fa02-104">Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="4fa02-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="4fa02-105">Depois de criar um Windows Forms <xref:System.Windows.Forms.DataGrid> usando os recursos de tempo de design, você também poderá alterar dinamicamente os elementos do <xref:System.Data.DataSet> objeto da grade em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4fa02-105">After you have created a Windows Forms <xref:System.Windows.Forms.DataGrid> using the design-time features, you may also wish to dynamically change elements of the <xref:System.Data.DataSet> object of the grid at run time.</span></span> <span data-ttu-id="4fa02-106">Isso pode incluir alterações em valores individuais da tabela ou alterar a fonte de dados está vinculado a <xref:System.Windows.Forms.DataGrid> controle.</span><span class="sxs-lookup"><span data-stu-id="4fa02-106">This can include changes to either individual values of the table or changing which data source is bound to the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="4fa02-107">Alterações em valores individuais são feitas por meio de <xref:System.Data.DataSet> do objeto, não o <xref:System.Windows.Forms.DataGrid> controle.</span><span class="sxs-lookup"><span data-stu-id="4fa02-107">Changes to individual values are done through the <xref:System.Data.DataSet> object, not the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
### <a name="to-change-data-programmatically"></a><span data-ttu-id="4fa02-108">Alterar dados com programação</span><span class="sxs-lookup"><span data-stu-id="4fa02-108">To change data programmatically</span></span>  
  
1.  <span data-ttu-id="4fa02-109">Especifique a tabela desejada do <xref:System.Data.DataSet> objeto e o estado desejado de linhas e de campo da tabela e defina a célula igual para o novo valor.</span><span class="sxs-lookup"><span data-stu-id="4fa02-109">Specify the desired table from the <xref:System.Data.DataSet> object and the desired row and field from the table and set the cell equal to the new value.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4fa02-110">Para especificar o primeiro índice da <xref:System.Data.DataSet> ou a primeira linha da tabela, use 0.</span><span class="sxs-lookup"><span data-stu-id="4fa02-110">To specify the first table of the <xref:System.Data.DataSet> or the first row of the table, use 0.</span></span>  
  
     <span data-ttu-id="4fa02-111">O exemplo a seguir mostra como alterar a segunda entrada da primeira linha da primeira tabela de um conjunto de dados, clicando em `Button1`.</span><span class="sxs-lookup"><span data-stu-id="4fa02-111">The following example shows how to change the second entry of the first row of the first table of a dataset by clicking `Button1`.</span></span> <span data-ttu-id="4fa02-112">O <xref:System.Data.DataSet> (`ds`) e tabelas (`0` e `1`) foram criados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="4fa02-112">The <xref:System.Data.DataSet> (`ds`) and Tables (`0` and `1`) were previously created.</span></span>  
  
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
  
     <span data-ttu-id="4fa02-113">(Visual c#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="4fa02-113">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="4fa02-114">No tempo, você pode usar de execução de <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> método para associar o <xref:System.Windows.Forms.DataGrid> controle a uma fonte de dados diferentes.</span><span class="sxs-lookup"><span data-stu-id="4fa02-114">At run time you can use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to bind the <xref:System.Windows.Forms.DataGrid> control to a different data source.</span></span> <span data-ttu-id="4fa02-115">Por exemplo, você pode ter vários controles de dados [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], cada um conectado a um banco de dados diferente.</span><span class="sxs-lookup"><span data-stu-id="4fa02-115">For example, you may have several [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] data controls, each connected to a different database.</span></span>  
  
### <a name="to-change-the-datasource-programmatically"></a><span data-ttu-id="4fa02-116">Alterar o DataSource com programação</span><span class="sxs-lookup"><span data-stu-id="4fa02-116">To change the DataSource programmatically</span></span>  
  
1.  <span data-ttu-id="4fa02-117">Defina o <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> método com o nome da fonte de dados e tabela que você deseja associar.</span><span class="sxs-lookup"><span data-stu-id="4fa02-117">Set the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to the name of the data source and table you want to bind to.</span></span>  
  
     <span data-ttu-id="4fa02-118">O exemplo a seguir mostra como alterar a fonte de data usando o <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> método para um [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] controle de dados (adoPubsAuthors) conectado à tabela autores no banco de dados Pubs.</span><span class="sxs-lookup"><span data-stu-id="4fa02-118">The following example shows how to change the date source using the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to an [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] data control (adoPubsAuthors) that is connected to the Authors table in the Pubs database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4fa02-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4fa02-119">See also</span></span>
- [<span data-ttu-id="4fa02-120">DataSets ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4fa02-120">ADO.NET DataSets</span></span>](../../data/adonet/ado-net-datasets.md)
- [<span data-ttu-id="4fa02-121">Como: Excluir ou ocultar colunas no controle DataGrid dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4fa02-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="4fa02-122">Como: Adicionar tabelas e colunas para o controle DataGrid dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4fa02-122">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="4fa02-123">Como: Associar o controle DataGrid dos Windows Forms a uma fonte de dados</span><span class="sxs-lookup"><span data-stu-id="4fa02-123">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)

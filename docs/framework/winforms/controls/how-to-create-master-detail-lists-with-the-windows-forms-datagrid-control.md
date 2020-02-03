---
title: Criar listas mestras-de detalhes com controle DataGrid
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 20388c6a-94f9-4d96-be18-8c200491247f
ms.openlocfilehash: e8ab63d52d97a8a6e6f60da741186e3937350e1e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76730988"
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a><span data-ttu-id="c83d1-102">Como criar listas mestre/detalhes com o controle DataGrid dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c83d1-102">How to: Create Master/Detail Lists with the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="c83d1-103">O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="c83d1-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="c83d1-104">Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="c83d1-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="c83d1-105">Se sua <xref:System.Data.DataSet> contiver uma série de tabelas relacionadas, você poderá usar dois controles de <xref:System.Windows.Forms.DataGrid> para exibir os dados em um formato mestre/de detalhes.</span><span class="sxs-lookup"><span data-stu-id="c83d1-105">If your <xref:System.Data.DataSet> contains a series of related tables, you can use two <xref:System.Windows.Forms.DataGrid> controls to display the data in a master/detail format.</span></span> <span data-ttu-id="c83d1-106">Uma <xref:System.Windows.Forms.DataGrid> é designada para ser a grade mestre e a segunda é designada para ser a grade de detalhes.</span><span class="sxs-lookup"><span data-stu-id="c83d1-106">One <xref:System.Windows.Forms.DataGrid> is designated to be the master grid, and the second is designated to be the details grid.</span></span> <span data-ttu-id="c83d1-107">Quando você seleciona uma entrada na lista mestra, todas as entradas filho relacionados são mostradas na lista de detalhes.</span><span class="sxs-lookup"><span data-stu-id="c83d1-107">When you select an entry in the master list, all of the related child entries are shown in the details list.</span></span> <span data-ttu-id="c83d1-108">Por exemplo, se sua <xref:System.Data.DataSet> contiver uma tabela Customers e uma tabela Orders relacionadas, você deverá especificar a tabela Customers como a grade mestre e a tabela Orders como a grade details.</span><span class="sxs-lookup"><span data-stu-id="c83d1-108">For example, if your <xref:System.Data.DataSet> contains a Customers table and a related Orders table, you would specify the Customers table to be the master grid and the Orders table to be the details grid.</span></span> <span data-ttu-id="c83d1-109">Quando um cliente é selecionado na grade principal, todos os pedidos associados a ele na tabela Pedidos serão exibidos na grade de detalhes.</span><span class="sxs-lookup"><span data-stu-id="c83d1-109">When a customer is selected from the master grid, all of the orders associated with that customer in the Orders table would be displayed in the details grid.</span></span>  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a><span data-ttu-id="c83d1-110">Definir uma relação mestre/detalhes com programação</span><span class="sxs-lookup"><span data-stu-id="c83d1-110">To set a master/detail relationship programmatically</span></span>  
  
1. <span data-ttu-id="c83d1-111">Crie dois novos controles de <xref:System.Windows.Forms.DataGrid> e defina suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="c83d1-111">Create two new <xref:System.Windows.Forms.DataGrid> controls and set their properties.</span></span>  
  
2. <span data-ttu-id="c83d1-112">Adicione tabelas ao conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="c83d1-112">Add tables to the dataset.</span></span>  
  
3. <span data-ttu-id="c83d1-113">Declare uma variável do tipo <xref:System.Data.DataRelation> para representar a relação que você deseja criar.</span><span class="sxs-lookup"><span data-stu-id="c83d1-113">Declare a variable of type <xref:System.Data.DataRelation> to represent the relation you want to create.</span></span>  
  
4. <span data-ttu-id="c83d1-114">Instancie o relacionamento especificando um nome para o relacionamento e especificando a tabela, coluna e item que associará as duas tabelas.</span><span class="sxs-lookup"><span data-stu-id="c83d1-114">Instantiate the relationship by specifying a name for the relationship and specifying the table, column, and item that will tie the two tables.</span></span>  
  
5. <span data-ttu-id="c83d1-115">Adicione a relação à coleção de <xref:System.Data.DataSet.Relations%2A> do objeto de <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="c83d1-115">Add the relationship to the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Relations%2A> collection.</span></span>  
  
6. <span data-ttu-id="c83d1-116">Use o método <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> da <xref:System.Windows.Forms.DataGrid> para associar cada uma das grades à <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="c83d1-116">Use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method of the <xref:System.Windows.Forms.DataGrid> to bind each of the grids to the <xref:System.Data.DataSet>.</span></span>  
  
     <span data-ttu-id="c83d1-117">O exemplo a seguir mostra como definir uma relação de mestre/detalhes entre as tabelas Customers e Orders em um <xref:System.Data.DataSet> gerado anteriormente (`ds`).</span><span class="sxs-lookup"><span data-stu-id="c83d1-117">The following example shows how to set a master/detail relationship between the Customers and Orders tables in a previously generated <xref:System.Data.DataSet> (`ds`).</span></span>  
  
    ```vb  
    Dim myDataRelation As DataRelation  
    myDataRelation = New DataRelation _  
       ("CustOrd", ds.Tables("Customers").Columns("CustomerID"), _  
       ds.Tables("Orders").Columns("CustomerID"))  
    ' Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation)  
    GridOrders.SetDataBinding(ds, "Customers")  
    GridDetails.SetDataBinding(ds, "Customers.CustOrd")  
    ```  
  
    ```csharp  
    DataRelation myDataRelation;  
    myDataRelation = new DataRelation("CustOrd", ds.Tables["Customers"].Columns["CustomerID"], ds.Tables["Orders"].Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation);  
    GridOrders.SetDataBinding(ds,"Customers");  
    GridDetails.SetDataBinding(ds,"Customers.CustOrd");  
    ```  
  
    ```cpp  
    DataRelation^ myDataRelation;  
    myDataRelation = gcnew DataRelation("CustOrd",  
       ds->Tables["Customers"]->Columns["CustomerID"],  
       ds->Tables["Orders"]->Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds->Relations->Add(myDataRelation);  
    GridOrders->SetDataBinding(ds, "Customers");  
    GridDetails->SetDataBinding(ds, "Customers.CustOrd");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c83d1-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c83d1-118">See also</span></span>

- [<span data-ttu-id="c83d1-119">Controle DataGrid</span><span class="sxs-lookup"><span data-stu-id="c83d1-119">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="c83d1-120">Visão geral do controle DataGrid</span><span class="sxs-lookup"><span data-stu-id="c83d1-120">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="c83d1-121">Como associar o controle DataGrid dos Windows Forms a uma fonte de dados</span><span class="sxs-lookup"><span data-stu-id="c83d1-121">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)

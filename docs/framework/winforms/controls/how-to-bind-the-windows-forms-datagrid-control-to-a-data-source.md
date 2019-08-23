---
title: 'Como: Associar o controle DataGrid do Windows Forms a uma fonte de dados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- bound controls [Windows Forms], DataGrid control
- Windows Forms controls, data binding
- bound controls [Windows Forms]
- data-bound controls [Windows Forms], DataGrid
ms.assetid: 128cdb07-dfd3-4d60-9d6a-902847667c36
ms.openlocfilehash: bac24c2dd622ea780408e902d08708ac09561044
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922733"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a><span data-ttu-id="91fd2-102">Como: Associar o controle DataGrid do Windows Forms a uma fonte de dados</span><span class="sxs-lookup"><span data-stu-id="91fd2-102">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>
> [!NOTE]
> <span data-ttu-id="91fd2-103">O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="91fd2-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="91fd2-104">Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="91fd2-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="91fd2-105">O controle <xref:System.Windows.Forms.DataGrid> de Windows Forms foi projetado especificamente para exibir informações de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="91fd2-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="91fd2-106">Você associa o controle em tempo de execução chamando o <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> método.</span><span class="sxs-lookup"><span data-stu-id="91fd2-106">You bind the control at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="91fd2-107">Embora seja possível exibir dados de uma variedade de fontes de dados, as fontes mais comuns são conjuntos de dados e exibições de dados.</span><span class="sxs-lookup"><span data-stu-id="91fd2-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a><span data-ttu-id="91fd2-108">Associar dados ao controle DataGrid por com programação</span><span class="sxs-lookup"><span data-stu-id="91fd2-108">To data-bind the DataGrid control programmatically</span></span>  
  
1. <span data-ttu-id="91fd2-109">Grave código para preencher o conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="91fd2-109">Write code to fill the dataset.</span></span>  
  
     <span data-ttu-id="91fd2-110">Se a fonte de dados for um conjunto de dados ou uma exibição de dados com base em uma tabela de conjunto de dados, adicione código ao formulário para preencher o conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="91fd2-110">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>  
  
     <span data-ttu-id="91fd2-111">O código exato usado depende do local em que o conjunto de dados está recebendo dados.</span><span class="sxs-lookup"><span data-stu-id="91fd2-111">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="91fd2-112">Se o conjunto de dados estiver sendo populado diretamente de um banco de `Fill` dado, você normalmente chamará o método de um adaptador, como no exemplo a seguir, `DsCategories1`que popula um DataSet chamado:</span><span class="sxs-lookup"><span data-stu-id="91fd2-112">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following example, which populates a dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     <span data-ttu-id="91fd2-113">Se o conjunto de dados estiver sendo preenchido de um serviço Web XML, geralmente uma instância do serviço será criada no seu código e uma chamada será feita para um de seus métodos retornar um conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="91fd2-113">If the dataset is being filled from an XML Web service, you typically create an instance of the service in your code and then call one of its methods to return a dataset.</span></span> <span data-ttu-id="91fd2-114">Em seguida, mescle o conjunto de dados do serviço Web XML ao seu conjunto de dados local.</span><span class="sxs-lookup"><span data-stu-id="91fd2-114">You then merge the dataset from the XML Web service into your local dataset.</span></span> <span data-ttu-id="91fd2-115">O exemplo a seguir mostra como você pode criar uma instância de um serviço Web XML `CategoriesService`chamado, chamar `GetCategories` seu método e mesclar o conjunto de resultados resultante em um `DsCategories1`conjunto de um DataSet local chamado:</span><span class="sxs-lookup"><span data-stu-id="91fd2-115">The following example shows how you can create an instance of an XML Web service called `CategoriesService`, call its `GetCategories` method, and merge the resulting dataset into a local dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    Dim ws As New MyProject.localhost.CategoriesService()  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials  
    DsCategories1.Merge(ws.GetCategories())  
    ```  
  
    ```csharp  
    MyProject.localhost.CategoriesService ws = new MyProject.localhost.CategoriesService();  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials;  
    DsCategories1.Merge(ws.GetCategories());  
    ```  
  
    ```cpp  
    MyProject::localhost::CategoriesService^ ws =   
       new MyProject::localhost::CategoriesService();  
    ws->Credentials = System::Net::CredentialCache::DefaultCredentials;  
    dsCategories1->Merge(ws->GetCategories());  
    ```  
  
2. <span data-ttu-id="91fd2-116">Chame o <xref:System.Windows.Forms.DataGrid> método do <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> controle, passando-o para a fonte de dados e um membro de dados.</span><span class="sxs-lookup"><span data-stu-id="91fd2-116">Call the <xref:System.Windows.Forms.DataGrid> control's <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method, passing it the data source and a data member.</span></span> <span data-ttu-id="91fd2-117">Se você não precisar passar explicitamente um membro de dados, passe uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="91fd2-117">If you do not need to explicitly pass a data member, pass an empty string.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="91fd2-118">Se você estiver ligando a grade pela primeira vez, poderá definir as propriedades e <xref:System.Windows.Forms.DataGrid.DataSource%2A> <xref:System.Windows.Forms.DataGrid.DataMember%2A> do controle.</span><span class="sxs-lookup"><span data-stu-id="91fd2-118">If you are binding the grid for the first time, you can set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties.</span></span> <span data-ttu-id="91fd2-119">No entanto, não será possível redefinir essas propriedades depois de serem definidas.</span><span class="sxs-lookup"><span data-stu-id="91fd2-119">However, you cannot reset these properties once they have been set.</span></span> <span data-ttu-id="91fd2-120">Portanto, é recomendável que você sempre use o <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> método.</span><span class="sxs-lookup"><span data-stu-id="91fd2-120">Therefore, it is recommended that you always use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span>  
  
     <span data-ttu-id="91fd2-121">O exemplo a seguir mostra como você pode associar programaticamente à tabela Customers em `DsCustomers1`um DataSet chamado:</span><span class="sxs-lookup"><span data-stu-id="91fd2-121">The following example shows how you can programmatically bind to the Customers table in a dataset called `DsCustomers1`:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     <span data-ttu-id="91fd2-122">Se a tabela Clientes for a única tabela no conjunto de dados, também seria possível associar a grade da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="91fd2-122">If the Customers table is the only table in the dataset, you could alternatively bind the grid this way:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3. <span data-ttu-id="91fd2-123">(Opcional) Adicione os estilos apropriados de tabela e coluna à grade.</span><span class="sxs-lookup"><span data-stu-id="91fd2-123">(Optional) Add the appropriate table styles and column styles to the grid.</span></span> <span data-ttu-id="91fd2-124">Se não houver nenhum estilo de tabela, a tabela ainda será vista, mas com formatação mínima e todas as colunas visíveis.</span><span class="sxs-lookup"><span data-stu-id="91fd2-124">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91fd2-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91fd2-125">See also</span></span>

- [<span data-ttu-id="91fd2-126">Visão geral do controle DataGrid</span><span class="sxs-lookup"><span data-stu-id="91fd2-126">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="91fd2-127">Como: Adicionar tabelas e colunas ao controle DataGrid de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="91fd2-127">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="91fd2-128">Controle DataGrid</span><span class="sxs-lookup"><span data-stu-id="91fd2-128">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="91fd2-129">Associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="91fd2-129">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)

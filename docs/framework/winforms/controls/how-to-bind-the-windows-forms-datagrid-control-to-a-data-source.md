---
title: Vincular o controle datagrid a uma fonte de dados
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
ms.openlocfilehash: 42514c6a0ab9cf912a32b13675a069976632ece5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182249"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a><span data-ttu-id="8981a-102">Como associar o controle DataGrid dos Windows Forms a uma fonte de dados</span><span class="sxs-lookup"><span data-stu-id="8981a-102">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>
> [!NOTE]
> <span data-ttu-id="8981a-103">O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="8981a-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="8981a-104">Para obter mais informações, consulte [Diferenças entre os formulários do Windows DataGridView e controles datagrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="8981a-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="8981a-105">O controle <xref:System.Windows.Forms.DataGrid> do Windows Forms foi projetado especificamente para exibir informações de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="8981a-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="8981a-106">Você vincula o controle no <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> tempo de execução chamando o método.</span><span class="sxs-lookup"><span data-stu-id="8981a-106">You bind the control at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="8981a-107">Embora seja possível exibir dados de uma variedade de fontes de dados, as fontes mais comuns são conjuntos de dados e exibições de dados.</span><span class="sxs-lookup"><span data-stu-id="8981a-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a><span data-ttu-id="8981a-108">Associar dados ao controle DataGrid por com programação</span><span class="sxs-lookup"><span data-stu-id="8981a-108">To data-bind the DataGrid control programmatically</span></span>  
  
1. <span data-ttu-id="8981a-109">Grave código para preencher o conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="8981a-109">Write code to fill the dataset.</span></span>  
  
     <span data-ttu-id="8981a-110">Se a fonte de dados for um conjunto de dados ou uma exibição de dados com base em uma tabela de conjunto de dados, adicione código ao formulário para preencher o conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="8981a-110">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>  
  
     <span data-ttu-id="8981a-111">O código exato usado depende do local em que o conjunto de dados está recebendo dados.</span><span class="sxs-lookup"><span data-stu-id="8981a-111">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="8981a-112">Se o conjunto de dados estiver sendo preenchido diretamente `Fill` a partir de um banco de dados, você normalmente `DsCategories1`chamará o método de um adaptador de dados, como no exemplo a seguir, que preenche um conjunto de dados chamado :</span><span class="sxs-lookup"><span data-stu-id="8981a-112">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following example, which populates a dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     <span data-ttu-id="8981a-113">Se o conjunto de dados estiver sendo preenchido de um serviço Web XML, geralmente uma instância do serviço será criada no seu código e uma chamada será feita para um de seus métodos retornar um conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="8981a-113">If the dataset is being filled from an XML Web service, you typically create an instance of the service in your code and then call one of its methods to return a dataset.</span></span> <span data-ttu-id="8981a-114">Em seguida, mescle o conjunto de dados do serviço Web XML ao seu conjunto de dados local.</span><span class="sxs-lookup"><span data-stu-id="8981a-114">You then merge the dataset from the XML Web service into your local dataset.</span></span> <span data-ttu-id="8981a-115">O exemplo a seguir mostra como você pode criar `CategoriesService`uma `GetCategories` instância de um serviço Web XML chamado `DsCategories1`, chamar seu método e mesclar o conjunto de dados resultante em um conjunto de dados local chamado :</span><span class="sxs-lookup"><span data-stu-id="8981a-115">The following example shows how you can create an instance of an XML Web service called `CategoriesService`, call its `GetCategories` method, and merge the resulting dataset into a local dataset called `DsCategories1`:</span></span>  
  
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
  
2. <span data-ttu-id="8981a-116">Ligue <xref:System.Windows.Forms.DataGrid> para o <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> método do controle, passando-o pela fonte de dados e um membro de dados.</span><span class="sxs-lookup"><span data-stu-id="8981a-116">Call the <xref:System.Windows.Forms.DataGrid> control's <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method, passing it the data source and a data member.</span></span> <span data-ttu-id="8981a-117">Se você não precisar passar explicitamente um membro de dados, passe uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="8981a-117">If you do not need to explicitly pass a data member, pass an empty string.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8981a-118">Se você estiver vinculando a grade pela primeira <xref:System.Windows.Forms.DataGrid.DataSource%2A> vez, você pode definir os controles e <xref:System.Windows.Forms.DataGrid.DataMember%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="8981a-118">If you are binding the grid for the first time, you can set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties.</span></span> <span data-ttu-id="8981a-119">No entanto, não será possível redefinir essas propriedades depois de serem definidas.</span><span class="sxs-lookup"><span data-stu-id="8981a-119">However, you cannot reset these properties once they have been set.</span></span> <span data-ttu-id="8981a-120">Portanto, recomenda-se que você sempre <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> use o método.</span><span class="sxs-lookup"><span data-stu-id="8981a-120">Therefore, it is recommended that you always use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span>  
  
     <span data-ttu-id="8981a-121">O exemplo a seguir mostra como você pode se vincular `DsCustomers1`programáticamente à tabela Clientes em um conjunto de dados chamado :</span><span class="sxs-lookup"><span data-stu-id="8981a-121">The following example shows how you can programmatically bind to the Customers table in a dataset called `DsCustomers1`:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     <span data-ttu-id="8981a-122">Se a tabela Clientes for a única tabela no conjunto de dados, também seria possível associar a grade da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="8981a-122">If the Customers table is the only table in the dataset, you could alternatively bind the grid this way:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3. <span data-ttu-id="8981a-123">(Opcional) Adicione os estilos apropriados de tabela e coluna à grade.</span><span class="sxs-lookup"><span data-stu-id="8981a-123">(Optional) Add the appropriate table styles and column styles to the grid.</span></span> <span data-ttu-id="8981a-124">Se não houver nenhum estilo de tabela, a tabela ainda será vista, mas com formatação mínima e todas as colunas visíveis.</span><span class="sxs-lookup"><span data-stu-id="8981a-124">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8981a-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="8981a-125">See also</span></span>

- [<span data-ttu-id="8981a-126">Visão geral do controle DataGrid</span><span class="sxs-lookup"><span data-stu-id="8981a-126">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="8981a-127">Como adicionar tabelas e colunas ao controle DataGrid do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8981a-127">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="8981a-128">Controle DataGrid</span><span class="sxs-lookup"><span data-stu-id="8981a-128">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="8981a-129">Vinculação de dados dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8981a-129">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)

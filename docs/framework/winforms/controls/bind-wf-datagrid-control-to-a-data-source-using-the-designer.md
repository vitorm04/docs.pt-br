---
title: 'Como: Associar o controle DataGrid do Windows Forms a uma fonte de dados usando o Designer'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- Windows Forms controls, data binding
- bound controls [Windows Forms]
ms.assetid: 4e96e3d0-b1cc-4de1-8774-bc9970ec4554
ms.openlocfilehash: de8b8d16f45221fbafe9f61ca634f144d8f6f6ae
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040007"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a><span data-ttu-id="e1253-102">Como: Associar o controle DataGrid do Windows Forms a uma fonte de dados usando o Designer</span><span class="sxs-lookup"><span data-stu-id="e1253-102">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>

> [!NOTE]
>  <span data-ttu-id="e1253-103">O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="e1253-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="e1253-104">Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="e1253-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>

 <span data-ttu-id="e1253-105">O controle <xref:System.Windows.Forms.DataGrid> de Windows Forms foi projetado especificamente para exibir informações de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="e1253-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="e1253-106">Você associa o controle em tempo de design definindo as <xref:System.Windows.Forms.DataGrid.DataSource%2A> propriedades <xref:System.Windows.Forms.DataGrid.DataMember%2A> e, ou em tempo de execução, chamando <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> o método.</span><span class="sxs-lookup"><span data-stu-id="e1253-106">You bind the control at design time by setting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties, or at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="e1253-107">Embora seja possível exibir dados de uma variedade de fontes de dados, as fontes mais comuns são conjuntos de dados e exibições de dados.</span><span class="sxs-lookup"><span data-stu-id="e1253-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>

 <span data-ttu-id="e1253-108">Se a fonte de dados estiver disponível em tempo de design – por exemplo, se o formulário contiver uma instância de um conjunto ou exibição de dados –, será possível associar a grade à fonte de dados em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="e1253-108">If the data source is available at design time—for example, if the form contains an instance of a dataset or a data view—you can bind the grid to the data source at design time.</span></span> <span data-ttu-id="e1253-109">Então, será possível visualizar a aparência dos dados na grade.</span><span class="sxs-lookup"><span data-stu-id="e1253-109">You can then preview what the data will look like in the grid.</span></span>

 <span data-ttu-id="e1253-110">Também é possível associar a grade programaticamente, em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e1253-110">You can also bind the grid programmatically, at run time.</span></span> <span data-ttu-id="e1253-111">Isso é útil quando se deseja definir uma fonte de dados com base nas informações obtidas em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e1253-111">This is useful when you want to set a data source based on information you get at run time.</span></span> <span data-ttu-id="e1253-112">Por exemplo, o aplicativo pode permitir que o usuário especifique o nome de uma tabela para exibir.</span><span class="sxs-lookup"><span data-stu-id="e1253-112">For example, the application might let the user specify the name of a table to view.</span></span> <span data-ttu-id="e1253-113">Também é necessário em situações em que a fonte de dados não existe em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="e1253-113">It is also necessary in situations where the data source does not exist at design time.</span></span> <span data-ttu-id="e1253-114">Isso inclui fontes de dados como matrizes, coleções, conjuntos de dados não tipados e leitores de dados.</span><span class="sxs-lookup"><span data-stu-id="e1253-114">This includes data sources such as arrays, collections, untyped datasets, and data readers.</span></span>

 <span data-ttu-id="e1253-115">O procedimento a seguir requer um projeto de **aplicativo do Windows** com um <xref:System.Windows.Forms.DataGrid> formulário que contém um controle.</span><span class="sxs-lookup"><span data-stu-id="e1253-115">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="e1253-116">Para obter informações sobre como configurar esse projeto, consulte [como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms [e como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e1253-116">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span> <span data-ttu-id="e1253-117">No Visual Studio 2005, o <xref:System.Windows.Forms.DataGrid> controle não está na **caixa de ferramentas** por padrão.</span><span class="sxs-lookup"><span data-stu-id="e1253-117">In Visual Studio 2005, the <xref:System.Windows.Forms.DataGrid> control is not in the **Toolbox** by default.</span></span> <span data-ttu-id="e1253-118">Para obter informações sobre como adicioná- [lo, consulte Como: Adicionar itens à caixa de](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))ferramentas.</span><span class="sxs-lookup"><span data-stu-id="e1253-118">For information about adding it, see [How to: Add Items to the Toolbox](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).</span></span> <span data-ttu-id="e1253-119">Além disso, no Visual Studio 2005, você pode usar a janela **fontes de dados** para associação de dados de tempo de design.</span><span class="sxs-lookup"><span data-stu-id="e1253-119">Additionally in Visual Studio 2005, you can use the **Data Sources** window for design-time data binding.</span></span> <span data-ttu-id="e1253-120">Para obter mais informações, consulte [Associar Controles a Dados no Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="e1253-120">For more information see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span></span>

## <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a><span data-ttu-id="e1253-121">Associar os dados do controle DataGrid a uma única tabela no designer</span><span class="sxs-lookup"><span data-stu-id="e1253-121">To data-bind the DataGrid control to a single table in the designer</span></span>

1. <span data-ttu-id="e1253-122">Defina a propriedade do <xref:System.Windows.Forms.DataGrid.DataSource%2A> controle como o objeto que contém os itens de dados aos quais você deseja associar.</span><span class="sxs-lookup"><span data-stu-id="e1253-122">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>

2. <span data-ttu-id="e1253-123">Se a fonte de dados for um DataSet, defina <xref:System.Windows.Forms.DataGrid.DataMember%2A> a propriedade como o nome da tabela à qual associar.</span><span class="sxs-lookup"><span data-stu-id="e1253-123">If the data source is a dataset, set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the table to bind to.</span></span>

3. <span data-ttu-id="e1253-124">Se a fonte de dados for um conjunto de dados ou uma exibição de dados com base em uma tabela de conjunto de dados, adicione código ao formulário para preencher o conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="e1253-124">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>

     <span data-ttu-id="e1253-125">O código exato usado depende do local em que o conjunto de dados está recebendo dados.</span><span class="sxs-lookup"><span data-stu-id="e1253-125">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="e1253-126">Se o conjunto de dados estiver sendo preenchido diretamente de um banco de dados, normalmente, chama-se o método `Fill` de um adaptador de dados, como no exemplo de código a seguir, que preenche um conjunto de dados chamado `DsCategories1`:</span><span class="sxs-lookup"><span data-stu-id="e1253-126">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following code example, which populates a dataset called `DsCategories1`:</span></span>

    ```vb
    sqlDataAdapter1.Fill(DsCategories1)
    ```

    ```csharp
    sqlDataAdapter1.Fill(DsCategories1);
    ```

    ```cpp
    sqlDataAdapter1->Fill(dsCategories1);
    ```

4. <span data-ttu-id="e1253-127">(Opcional) Adicione os estilos apropriados de tabela e coluna à grade.</span><span class="sxs-lookup"><span data-stu-id="e1253-127">(Optional) Add the appropriate table styles and column styles to the grid.</span></span>

     <span data-ttu-id="e1253-128">Se não houver nenhum estilo de tabela, a tabela ainda será vista, mas com formatação mínima e todas as colunas visíveis.</span><span class="sxs-lookup"><span data-stu-id="e1253-128">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>

## <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a><span data-ttu-id="e1253-129">Associar os dados do controle DataGrid a várias tabelas em um conjunto de dados no designer</span><span class="sxs-lookup"><span data-stu-id="e1253-129">To data-bind the DataGrid control to multiple tables in a dataset in the designer</span></span>

1. <span data-ttu-id="e1253-130">Defina a propriedade do <xref:System.Windows.Forms.DataGrid.DataSource%2A> controle como o objeto que contém os itens de dados aos quais você deseja associar.</span><span class="sxs-lookup"><span data-stu-id="e1253-130">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>

2. <span data-ttu-id="e1253-131">Se o conjunto de conteúdo contiver tabelas relacionadas (ou seja, se contiver um objeto relation) <xref:System.Windows.Forms.DataGrid.DataMember%2A> , defina a propriedade como o nome da tabela pai.</span><span class="sxs-lookup"><span data-stu-id="e1253-131">If the dataset contains related tables (that is, if it contains a relation object), set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the parent table.</span></span>

3. <span data-ttu-id="e1253-132">Grave código para preencher o conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="e1253-132">Write code to fill the dataset.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1253-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e1253-133">See also</span></span>

- [<span data-ttu-id="e1253-134">Visão geral do controle DataGrid</span><span class="sxs-lookup"><span data-stu-id="e1253-134">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="e1253-135">Como: Adicionar tabelas e colunas ao controle DataGrid de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e1253-135">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="e1253-136">Controle DataGrid</span><span class="sxs-lookup"><span data-stu-id="e1253-136">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="e1253-137">Associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e1253-137">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="e1253-138">Acessando dados no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e1253-138">Accessing data in Visual Studio</span></span>](/visualstudio/data-tools/accessing-data-in-visual-studio)

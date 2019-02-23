---
title: 'Passo a passo: Exibir dados de um banco de dados do SQL Server em um controle DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], displaying data from SQL Server
- controls [WPF], DataGrid
ms.assetid: 6810b048-0a23-4f86-bfa5-97f92b3cfab4
ms.openlocfilehash: 6cf56a853377a9c062009fb8a4082cd5380905c6
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748408"
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a><span data-ttu-id="fb027-102">Passo a passo: Exibir dados de um banco de dados do SQL Server em um controle DataGrid</span><span class="sxs-lookup"><span data-stu-id="fb027-102">Walkthrough: Display data from a SQL Server database in a DataGrid control</span></span>

<span data-ttu-id="fb027-103">Neste passo a passo, você pode recuperar dados de um banco de dados do SQL Server e exibi-los em um <xref:System.Windows.Controls.DataGrid> controle.</span><span class="sxs-lookup"><span data-stu-id="fb027-103">In this walkthrough, you retrieve data from a SQL Server database and display that data in a <xref:System.Windows.Controls.DataGrid> control.</span></span> <span data-ttu-id="fb027-104">O ADO.NET Entity Framework é usado para criar as classes de entidade que representam os dados e o LINQ é usado para gravar uma consulta que recupera os dados especificados de uma classe de entidade.</span><span class="sxs-lookup"><span data-stu-id="fb027-104">You use the ADO.NET Entity Framework to create the entity classes that represent the data, and use LINQ to write a query that retrieves the specified data from an entity class.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fb027-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="fb027-105">Prerequisites</span></span>

<span data-ttu-id="fb027-106">Você precisa dos seguintes componentes para concluir esta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="fb027-106">You need the following components to complete this walkthrough:</span></span>

-   <span data-ttu-id="fb027-107">Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fb027-107">Visual Studio.</span></span>

-   <span data-ttu-id="fb027-108">Acesso a uma instância em execução do SQL Server ou SQL Server Express que tem o banco de dados de exemplo AdventureWorks anexado a ele.</span><span class="sxs-lookup"><span data-stu-id="fb027-108">Access to a running instance of SQL Server or SQL Server Express that has the AdventureWorks sample database attached to it.</span></span> <span data-ttu-id="fb027-109">Você pode baixar o banco de dados AdventureWorks a [GitHub](https://github.com/Microsoft/sql-server-samples/releases).</span><span class="sxs-lookup"><span data-stu-id="fb027-109">You can download the AdventureWorks database from the [GitHub](https://github.com/Microsoft/sql-server-samples/releases).</span></span>

## <a name="create-entity-classes"></a><span data-ttu-id="fb027-110">Criar classes de entidade</span><span class="sxs-lookup"><span data-stu-id="fb027-110">Create entity classes</span></span>

1.  <span data-ttu-id="fb027-111">Crie um novo projeto de Aplicativo do WPF no Visual Basic ou no C#, chamado `DataGridSQLExample`.</span><span class="sxs-lookup"><span data-stu-id="fb027-111">Create a new WPF Application project in Visual Basic or C#, and name it `DataGridSQLExample`.</span></span>

2.  <span data-ttu-id="fb027-112">No Gerenciador de Soluções, clique com o botão direito do mouse no projeto, aponte para **Adicionar** e selecione **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="fb027-112">In Solution Explorer, right-click your project, point to **Add**, and then select **New Item**.</span></span>

     <span data-ttu-id="fb027-113">A caixa de diálogo Adicionar Novo Item é exibida.</span><span class="sxs-lookup"><span data-stu-id="fb027-113">The Add New Item dialog box appears.</span></span>

3.  <span data-ttu-id="fb027-114">No painel modelos instalados, selecione **dados** e, na lista de modelos, selecione **modelo de dados de entidade ADO.NET**.</span><span class="sxs-lookup"><span data-stu-id="fb027-114">In the Installed Templates pane, select **Data** and in the list of templates, select **ADO.NET Entity Data Model**.</span></span>

     ![Modelo de item de modelo de dados de entidade ADO.NET](../../wcf/feature-details/media/ado-net-entity-data-model-item-template.png)

4.  <span data-ttu-id="fb027-116">Nomeie o arquivo `AdventureWorksModel.edmx` e, em seguida, clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="fb027-116">Name the file `AdventureWorksModel.edmx` and then click **Add**.</span></span>

     <span data-ttu-id="fb027-117">O Assistente do Modelo de Dados de Entidade é aberto.</span><span class="sxs-lookup"><span data-stu-id="fb027-117">The Entity Data Model Wizard appears.</span></span>

5.  <span data-ttu-id="fb027-118">Na tela Escolher conteúdos modelo, selecione **EF Designer do banco de dados** e, em seguida, clique em **próxima**.</span><span class="sxs-lookup"><span data-stu-id="fb027-118">In the Choose Model Contents screen, select **EF Designer from database** and then click **Next**.</span></span>

6.  <span data-ttu-id="fb027-119">Na tela Escolher a Conexão de Dados, forneça a conexão ao banco de dados AdventureWorksLT2008.</span><span class="sxs-lookup"><span data-stu-id="fb027-119">In the Choose Your Data Connection screen, provide the connection to your AdventureWorksLT2008 database.</span></span> <span data-ttu-id="fb027-120">Para obter mais informações, consulte [Escolher uma Caixa de Diálogo de Conexão de Dados](https://go.microsoft.com/fwlink/?LinkId=160190).</span><span class="sxs-lookup"><span data-stu-id="fb027-120">For more information, see [Choose Your Data Connection Dialog Box](https://go.microsoft.com/fwlink/?LinkId=160190).</span></span>

    <span data-ttu-id="fb027-121">Certifique-se de que o nome é `AdventureWorksLT2008Entities` e que o **salvar configurações de conexão de entidade em App. config como** caixa de seleção está selecionada e, em seguida, clique em **próximo**.</span><span class="sxs-lookup"><span data-stu-id="fb027-121">Make sure that the name is `AdventureWorksLT2008Entities` and that the **Save entity connection settings in App.Config as** check box is selected, and then click **Next**.</span></span>

7.  <span data-ttu-id="fb027-122">Na tela Escolher Objetos de Banco de Dados, expanda o nó Tabelas e selecione as tabelas **Product** e **ProductCategory**.</span><span class="sxs-lookup"><span data-stu-id="fb027-122">In the Choose Your Database Objects screen, expand the Tables node, and select the **Product** and **ProductCategory** tables.</span></span>

     <span data-ttu-id="fb027-123">É possível gerar classes de entidade para todas as tabelas; no entanto, neste exemplo, somente os dados dessas duas tabelas serão recuperados.</span><span class="sxs-lookup"><span data-stu-id="fb027-123">You can generate entity classes for all of the tables; however, in this example you only retrieve data from those two tables.</span></span>

     <span data-ttu-id="fb027-124">![Selecione Product e ProductCategory nas tabelas](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span><span class="sxs-lookup"><span data-stu-id="fb027-124">![Select Product and ProductCategory from tables](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span></span>

8. <span data-ttu-id="fb027-125">Clique em **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="fb027-125">Click **Finish**.</span></span>

     <span data-ttu-id="fb027-126">As entidades Product e ProductCategory serão exibidas no Entity Designer.</span><span class="sxs-lookup"><span data-stu-id="fb027-126">The Product and ProductCategory entities are displayed in the Entity Designer.</span></span>

     <span data-ttu-id="fb027-127">![Modelos de entidade Product e ProductCategory](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span><span class="sxs-lookup"><span data-stu-id="fb027-127">![Product and ProductCategory entity models](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span></span>

## <a name="retrieve-and-present-the-data"></a><span data-ttu-id="fb027-128">Recuperar e apresentar os dados</span><span class="sxs-lookup"><span data-stu-id="fb027-128">Retrieve and present the data</span></span>

1.  <span data-ttu-id="fb027-129">Abra o arquivo MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="fb027-129">Open the MainWindow.xaml file.</span></span>

2.  <span data-ttu-id="fb027-130">Defina as <xref:System.Windows.FrameworkElement.Width%2A> propriedade no <xref:System.Windows.Window> para 450.</span><span class="sxs-lookup"><span data-stu-id="fb027-130">Set the <xref:System.Windows.FrameworkElement.Width%2A> property on the <xref:System.Windows.Window> to 450.</span></span>

3.  <span data-ttu-id="fb027-131">No editor de XAML, adicione o seguinte <xref:System.Windows.Controls.DataGrid> marcar entre o `<Grid>` e `</Grid>` marcas para adicionar um <xref:System.Windows.Controls.DataGrid> chamado `dataGrid1`.</span><span class="sxs-lookup"><span data-stu-id="fb027-131">In the XAML editor, add the following <xref:System.Windows.Controls.DataGrid> tag between the `<Grid>` and `</Grid>` tags to add a <xref:System.Windows.Controls.DataGrid> named `dataGrid1`.</span></span>

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]

     <span data-ttu-id="fb027-132">![Janela com DataGrid](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span><span class="sxs-lookup"><span data-stu-id="fb027-132">![Window with DataGrid](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span></span>

4.  <span data-ttu-id="fb027-133">Selecione o <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="fb027-133">Select the <xref:System.Windows.Window>.</span></span>

5.  <span data-ttu-id="fb027-134">Usando a janela Propriedades ou o editor XAML, crie um manipulador de eventos para o <xref:System.Windows.Window> nomeado `Window_Loaded` para o <xref:System.Windows.FrameworkElement.Loaded> eventos.</span><span class="sxs-lookup"><span data-stu-id="fb027-134">Using the Properties window or XAML editor, create an event handler for the <xref:System.Windows.Window> named `Window_Loaded` for the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span> <span data-ttu-id="fb027-135">Para obter mais informações, confira [Como: Crie um manipulador de eventos simples](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="fb027-135">For more information, see [How to: Create a Simple Event Handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

     <span data-ttu-id="fb027-136">O exemplo a seguir mostra o XAML de MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="fb027-136">The following shows the XAML for MainWindow.xaml.</span></span>

    > [!NOTE]
    > <span data-ttu-id="fb027-137">Se você estiver usando o Visual Basic, na primeira linha de MainWindow.xaml, substitua `x:Class="DataGridSQLExample.MainWindow"` por `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="fb027-137">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="DataGridSQLExample.MainWindow"` with `x:Class="MainWindow"`.</span></span>

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]

6.  <span data-ttu-id="fb027-138">Abra o arquivo code-behind (. XAML. vb ou MainWindow.xaml.cs) para o <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="fb027-138">Open the code-behind file (MainWindow.xaml.vb or MainWindow.xaml.cs) for the <xref:System.Windows.Window>.</span></span>

7.  <span data-ttu-id="fb027-139">Adicione o seguinte código para recuperar valores específicos das tabelas unidas e defina as <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriedade do <xref:System.Windows.Controls.DataGrid> aos resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="fb027-139">Add the following code to retrieve only specific values from the joined tables and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.DataGrid> to the results of the query.</span></span>

     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]

8.  <span data-ttu-id="fb027-140">Execute o exemplo.</span><span class="sxs-lookup"><span data-stu-id="fb027-140">Run the example.</span></span>

     <span data-ttu-id="fb027-141">Você deve ver um <xref:System.Windows.Controls.DataGrid> que exibe dados.</span><span class="sxs-lookup"><span data-stu-id="fb027-141">You should see a <xref:System.Windows.Controls.DataGrid> that displays data.</span></span>

     <span data-ttu-id="fb027-142">![DataGrid com os dados de banco de dados SQL](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span><span class="sxs-lookup"><span data-stu-id="fb027-142">![DataGrid with data from SQL database](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span></span>

## <a name="see-also"></a><span data-ttu-id="fb027-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb027-143">See also</span></span>

- <xref:System.Windows.Controls.DataGrid>
- [<span data-ttu-id="fb027-144">Como faço Introdução ao Entity Framework em aplicativos WPF?</span><span class="sxs-lookup"><span data-stu-id="fb027-144">How Do I: Get Started with Entity Framework in WPF Applications?</span></span>](https://go.microsoft.com/fwlink/?LinkId=159868)
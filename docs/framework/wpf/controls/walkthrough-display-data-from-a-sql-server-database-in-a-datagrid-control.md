---
title: 'Passo a passo: exibir dados de um banco de dados do SQL Server em um controle DataGrid'
description: Saiba como obter dados de um banco de SQL Server e exibi-los em um controle DataGrid Windows Presentation Foundation usando este passo a passos.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], displaying data from SQL Server
- controls [WPF], DataGrid
ms.assetid: 6810b048-0a23-4f86-bfa5-97f92b3cfab4
ms.openlocfilehash: cc41979c869021c9c363f3f68ce590d4702e068c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167549"
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a><span data-ttu-id="e2a35-103">Walkthrough: exibir dados de um SQL Server banco de dado em um controle DataGrid</span><span class="sxs-lookup"><span data-stu-id="e2a35-103">Walkthrough: Display data from a SQL Server database in a DataGrid control</span></span>

<span data-ttu-id="e2a35-104">Neste passo a passos, você recupera dados de um SQL Server um banco de dados e os exibe em um <xref:System.Windows.Controls.DataGrid> controle.</span><span class="sxs-lookup"><span data-stu-id="e2a35-104">In this walkthrough, you retrieve data from a SQL Server database and display that data in a <xref:System.Windows.Controls.DataGrid> control.</span></span> <span data-ttu-id="e2a35-105">O ADO.NET Entity Framework é usado para criar as classes de entidade que representam os dados e o LINQ é usado para gravar uma consulta que recupera os dados especificados de uma classe de entidade.</span><span class="sxs-lookup"><span data-stu-id="e2a35-105">You use the ADO.NET Entity Framework to create the entity classes that represent the data, and use LINQ to write a query that retrieves the specified data from an entity class.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e2a35-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="e2a35-106">Prerequisites</span></span>

<span data-ttu-id="e2a35-107">Você precisará dos seguintes componentes para concluir este passo a passo:</span><span class="sxs-lookup"><span data-stu-id="e2a35-107">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="e2a35-108">Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e2a35-108">Visual Studio.</span></span>

- <span data-ttu-id="e2a35-109">Acesso a uma instância em execução do SQL Server ou SQL Server Express que tem o banco de dados de exemplo AdventureWorks anexado a ele.</span><span class="sxs-lookup"><span data-stu-id="e2a35-109">Access to a running instance of SQL Server or SQL Server Express that has the AdventureWorks sample database attached to it.</span></span> <span data-ttu-id="e2a35-110">Você pode baixar o banco de dados AdventureWorks do [GitHub](https://github.com/Microsoft/sql-server-samples/releases).</span><span class="sxs-lookup"><span data-stu-id="e2a35-110">You can download the AdventureWorks database from the [GitHub](https://github.com/Microsoft/sql-server-samples/releases).</span></span>

## <a name="create-entity-classes"></a><span data-ttu-id="e2a35-111">Criar classes de entidade</span><span class="sxs-lookup"><span data-stu-id="e2a35-111">Create entity classes</span></span>

1. <span data-ttu-id="e2a35-112">Crie um novo projeto de Aplicativo do WPF no Visual Basic ou no C#, chamado `DataGridSQLExample`.</span><span class="sxs-lookup"><span data-stu-id="e2a35-112">Create a new WPF Application project in Visual Basic or C#, and name it `DataGridSQLExample`.</span></span>

2. <span data-ttu-id="e2a35-113">No Gerenciador de Soluções, clique com o botão direito do mouse no projeto, aponte para **Adicionar** e selecione **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="e2a35-113">In Solution Explorer, right-click your project, point to **Add**, and then select **New Item**.</span></span>

     <span data-ttu-id="e2a35-114">A caixa de diálogo Adicionar Novo Item é exibida.</span><span class="sxs-lookup"><span data-stu-id="e2a35-114">The Add New Item dialog box appears.</span></span>

3. <span data-ttu-id="e2a35-115">No painel modelos instalados, selecione **dados** e, na lista de modelos, selecione **ADO.NET modelo de dados de entidade**.</span><span class="sxs-lookup"><span data-stu-id="e2a35-115">In the Installed Templates pane, select **Data** and in the list of templates, select **ADO.NET Entity Data Model**.</span></span>

     ![ADO.NET modelo de item de Modelo de Dados de Entidade](../../wcf/feature-details/media/ado-net-entity-data-model-item-template.png)

4. <span data-ttu-id="e2a35-117">Nomeie o arquivo `AdventureWorksModel.edmx` e, em seguida, clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="e2a35-117">Name the file `AdventureWorksModel.edmx` and then click **Add**.</span></span>

     <span data-ttu-id="e2a35-118">O Assistente do Modelo de Dados de Entidade é aberto.</span><span class="sxs-lookup"><span data-stu-id="e2a35-118">The Entity Data Model Wizard appears.</span></span>

5. <span data-ttu-id="e2a35-119">Na tela escolher conteúdo do modelo, selecione **designer do EF no banco de dados** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e2a35-119">In the Choose Model Contents screen, select **EF Designer from database** and then click **Next**.</span></span>

6. <span data-ttu-id="e2a35-120">Na tela Escolher a Conexão de Dados, forneça a conexão ao banco de dados AdventureWorksLT2008.</span><span class="sxs-lookup"><span data-stu-id="e2a35-120">In the Choose Your Data Connection screen, provide the connection to your AdventureWorksLT2008 database.</span></span> <span data-ttu-id="e2a35-121">Para obter mais informações, consulte [Escolher uma Caixa de Diálogo de Conexão de Dados](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399244(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e2a35-121">For more information, see [Choose Your Data Connection Dialog Box](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399244(v=vs.100)).</span></span>

    <span data-ttu-id="e2a35-122">Verifique se o nome é `AdventureWorksLT2008Entities` e se a caixa de seleção **salvar configurações de conexão de entidade no App.Config como** está marcada e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e2a35-122">Make sure that the name is `AdventureWorksLT2008Entities` and that the **Save entity connection settings in App.Config as** check box is selected, and then click **Next**.</span></span>

7. <span data-ttu-id="e2a35-123">Na tela Escolher Objetos de Banco de Dados, expanda o nó Tabelas e selecione as tabelas **Product** e **ProductCategory**.</span><span class="sxs-lookup"><span data-stu-id="e2a35-123">In the Choose Your Database Objects screen, expand the Tables node, and select the **Product** and **ProductCategory** tables.</span></span>

     <span data-ttu-id="e2a35-124">É possível gerar classes de entidade para todas as tabelas; no entanto, neste exemplo, somente os dados dessas duas tabelas serão recuperados.</span><span class="sxs-lookup"><span data-stu-id="e2a35-124">You can generate entity classes for all of the tables; however, in this example you only retrieve data from those two tables.</span></span>

     <span data-ttu-id="e2a35-125">![Selecionar produto e ProductCategory de tabelas](./media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span><span class="sxs-lookup"><span data-stu-id="e2a35-125">![Select Product and ProductCategory from tables](./media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span></span>

8. <span data-ttu-id="e2a35-126">Clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="e2a35-126">Click **Finish**.</span></span>

     <span data-ttu-id="e2a35-127">As entidades Product e ProductCategory serão exibidas no Entity Designer.</span><span class="sxs-lookup"><span data-stu-id="e2a35-127">The Product and ProductCategory entities are displayed in the Entity Designer.</span></span>

     <span data-ttu-id="e2a35-128">![Modelos de entidade produto e ProductCategory](./media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span><span class="sxs-lookup"><span data-stu-id="e2a35-128">![Product and ProductCategory entity models](./media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span></span>

## <a name="retrieve-and-present-the-data"></a><span data-ttu-id="e2a35-129">Recuperar e apresentar os dados</span><span class="sxs-lookup"><span data-stu-id="e2a35-129">Retrieve and present the data</span></span>

1. <span data-ttu-id="e2a35-130">Abra o arquivo MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="e2a35-130">Open the MainWindow.xaml file.</span></span>

2. <span data-ttu-id="e2a35-131">Defina a <xref:System.Windows.FrameworkElement.Width%2A> propriedade no <xref:System.Windows.Window> como 450.</span><span class="sxs-lookup"><span data-stu-id="e2a35-131">Set the <xref:System.Windows.FrameworkElement.Width%2A> property on the <xref:System.Windows.Window> to 450.</span></span>

3. <span data-ttu-id="e2a35-132">No editor XAML, adicione a seguinte <xref:System.Windows.Controls.DataGrid> marca entre as `<Grid>` marcas e `</Grid>` para adicionar um <xref:System.Windows.Controls.DataGrid> nome `dataGrid1` .</span><span class="sxs-lookup"><span data-stu-id="e2a35-132">In the XAML editor, add the following <xref:System.Windows.Controls.DataGrid> tag between the `<Grid>` and `</Grid>` tags to add a <xref:System.Windows.Controls.DataGrid> named `dataGrid1`.</span></span>

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]

     <span data-ttu-id="e2a35-133">![Janela com DataGrid](./media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span><span class="sxs-lookup"><span data-stu-id="e2a35-133">![Window with DataGrid](./media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span></span>

4. <span data-ttu-id="e2a35-134">Selecione o <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="e2a35-134">Select the <xref:System.Windows.Window>.</span></span>

5. <span data-ttu-id="e2a35-135">Usando o editor de janela Propriedades ou XAML, crie um manipulador de eventos para o <xref:System.Windows.Window> nome do `Window_Loaded` <xref:System.Windows.FrameworkElement.Loaded> evento.</span><span class="sxs-lookup"><span data-stu-id="e2a35-135">Using the Properties window or XAML editor, create an event handler for the <xref:System.Windows.Window> named `Window_Loaded` for the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span> <span data-ttu-id="e2a35-136">Para obter mais informações, consulte [como: criar um manipulador de eventos simples](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e2a35-136">For more information, see [How to: Create a Simple Event Handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

     <span data-ttu-id="e2a35-137">O exemplo a seguir mostra o XAML de MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="e2a35-137">The following shows the XAML for MainWindow.xaml.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e2a35-138">Se você estiver usando o Visual Basic, na primeira linha de MainWindow.xaml, substitua `x:Class="DataGridSQLExample.MainWindow"` por `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="e2a35-138">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="DataGridSQLExample.MainWindow"` with `x:Class="MainWindow"`.</span></span>

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]

6. <span data-ttu-id="e2a35-139">Abra o arquivo code-behind (MainWindow. XAML. vb ou MainWindow.xaml.cs) para o <xref:System.Windows.Window> .</span><span class="sxs-lookup"><span data-stu-id="e2a35-139">Open the code-behind file (MainWindow.xaml.vb or MainWindow.xaml.cs) for the <xref:System.Windows.Window>.</span></span>

7. <span data-ttu-id="e2a35-140">Adicione o código a seguir para recuperar apenas valores específicos das tabelas Unidas e definir a <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> Propriedade do <xref:System.Windows.Controls.DataGrid> para os resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="e2a35-140">Add the following code to retrieve only specific values from the joined tables and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.DataGrid> to the results of the query.</span></span>

     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]

8. <span data-ttu-id="e2a35-141">Execute o exemplo.</span><span class="sxs-lookup"><span data-stu-id="e2a35-141">Run the example.</span></span>

     <span data-ttu-id="e2a35-142">Você deve ver um <xref:System.Windows.Controls.DataGrid> que exibe dados.</span><span class="sxs-lookup"><span data-stu-id="e2a35-142">You should see a <xref:System.Windows.Controls.DataGrid> that displays data.</span></span>

     <span data-ttu-id="e2a35-143">![DataGrid com dados do banco de dados SQL](./media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span><span class="sxs-lookup"><span data-stu-id="e2a35-143">![DataGrid with data from SQL database](./media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span></span>

## <a name="see-also"></a><span data-ttu-id="e2a35-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="e2a35-144">See also</span></span>

- <xref:System.Windows.Controls.DataGrid>

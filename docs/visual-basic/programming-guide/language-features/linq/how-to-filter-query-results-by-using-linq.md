---
title: Como filtrar resultados de consulta usando LINQ (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- filtering [Visual Basic]
- filtering data [LINQ in Visual Basic]
- filtering [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], filtering results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- filtering data [Visual Basic]
ms.assetid: ef103092-9bed-4134-97f4-2db696e83c12
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 80d4f05e9f90e8543c61af26080e66f9cf262f01
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-filter-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="347fc-102">Como filtrar resultados de consulta usando LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="347fc-102">How to: Filter Query Results by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="347fc-103">Consulta integrada à linguagem (LINQ) facilita o acesso a informações de banco de dados e executar consultas.</span><span class="sxs-lookup"><span data-stu-id="347fc-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="347fc-104">O exemplo a seguir mostra como criar um novo aplicativo que executa consultas em um banco de dados do SQL Server e filtra os resultados por um valor específico usando o `Where` cláusula.</span><span class="sxs-lookup"><span data-stu-id="347fc-104">The following example shows how to create a new application that performs queries against a SQL Server database and filters the results by a particular value by using the `Where` clause.</span></span> <span data-ttu-id="347fc-105">Para obter mais informações, consulte [cláusula Where](../../../../visual-basic/language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="347fc-105">For more information, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
 <span data-ttu-id="347fc-106">Os exemplos neste tópico usam o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="347fc-106">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="347fc-107">Se você não tiver o banco de dados de exemplo Northwind no computador de desenvolvimento, você pode baixá-lo do [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) site da Web.</span><span class="sxs-lookup"><span data-stu-id="347fc-107">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="347fc-108">Para obter instruções, consulte [baixando bancos de dados de exemplo](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="347fc-108">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="347fc-109">Para criar uma conexão para um banco de dados</span><span class="sxs-lookup"><span data-stu-id="347fc-109">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="347fc-110">No Visual Studio, abra **Server Explorer**/**Pesquisador de objetos de banco de dados** clicando **Server Explorer**/**banco de dados Gerenciador de** no **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="347fc-110">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="347fc-111">Clique com botão direito **conexões de dados** na **Server Explorer**/**Pesquisador de objetos de banco de dados** e, em seguida, clique em **Adicionar Conexão**.</span><span class="sxs-lookup"><span data-stu-id="347fc-111">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="347fc-112">Especifique uma conexão válida para o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="347fc-112">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="347fc-113">Para adicionar um projeto que contém um arquivo LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="347fc-113">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="347fc-114">No Visual Studio, no menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="347fc-114">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="347fc-115">Selecione Visual Basic **aplicativo do Windows Forms** como o tipo de projeto.</span><span class="sxs-lookup"><span data-stu-id="347fc-115">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="347fc-116">No menu **Projeto**, clique em **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="347fc-116">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="347fc-117">Selecione o **Classes LINQ to SQL** modelo de item.</span><span class="sxs-lookup"><span data-stu-id="347fc-117">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="347fc-118">Dê o nome `northwind.dbml` para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="347fc-118">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="347fc-119">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="347fc-119">Click **Add**.</span></span> <span data-ttu-id="347fc-120">O Object Relational Designer (O/R Designer) é aberto para o arquivo dbml.</span><span class="sxs-lookup"><span data-stu-id="347fc-120">The Object Relational Designer (O/R Designer) opens for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="347fc-121">Para adicionar tabelas de consulta para o O/R Designer</span><span class="sxs-lookup"><span data-stu-id="347fc-121">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="347fc-122">Em **Server Explorer**/**Pesquisador de objetos de banco de dados**, expanda a conexão ao banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="347fc-122">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="347fc-123">Expanda o **tabelas** pasta.</span><span class="sxs-lookup"><span data-stu-id="347fc-123">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="347fc-124">Se você fechou o Object Relational Designer, você poderá reabri-lo clicando no arquivo dbml que você adicionou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="347fc-124">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="347fc-125">Clique na tabela clientes e arraste-o no painel esquerdo do designer.</span><span class="sxs-lookup"><span data-stu-id="347fc-125">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="347fc-126">Clique na tabela Orders e arraste-o no painel esquerdo do designer.</span><span class="sxs-lookup"><span data-stu-id="347fc-126">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="347fc-127">O designer cria novos `Customer` e `Order` objetos para o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="347fc-127">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="347fc-128">Observe que o designer automaticamente detecta as relações entre as tabelas e cria propriedades filhas para objetos relacionados.</span><span class="sxs-lookup"><span data-stu-id="347fc-128">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="347fc-129">Por exemplo, o IntelliSense mostrará que o `Customer` objeto tem um `Orders` propriedade para todos os pedidos relacionados a esse cliente.</span><span class="sxs-lookup"><span data-stu-id="347fc-129">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="347fc-130">Salve suas alterações e fechar o designer.</span><span class="sxs-lookup"><span data-stu-id="347fc-130">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="347fc-131">Salve seu projeto.</span><span class="sxs-lookup"><span data-stu-id="347fc-131">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="347fc-132">Para adicionar código para consultar o banco de dados e exibir os resultados</span><span class="sxs-lookup"><span data-stu-id="347fc-132">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="347fc-133">Do **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.DataGridView> controle para o Windows Form padrão para seu projeto, Form1.</span><span class="sxs-lookup"><span data-stu-id="347fc-133">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="347fc-134">Clique duas vezes em Form1 para adicionar código para o `Load` evento do formulário.</span><span class="sxs-lookup"><span data-stu-id="347fc-134">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="347fc-135">Quando você adicionar tabelas ao / R Designer, o designer adicionará um <xref:System.Data.Linq.DataContext> objeto para o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="347fc-135">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="347fc-136">Este objeto contém o código que você deve ter para acessar essas tabelas, além de objetos individuais e coleções para cada tabela.</span><span class="sxs-lookup"><span data-stu-id="347fc-136">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="347fc-137">O <xref:System.Data.Linq.DataContext> objeto para seu projeto é nomeado com base no nome do seu arquivo dbml.</span><span class="sxs-lookup"><span data-stu-id="347fc-137">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="347fc-138">Para este projeto, o <xref:System.Data.Linq.DataContext> objeto é nomeado `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="347fc-138">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="347fc-139">Você pode criar uma instância do <xref:System.Data.Linq.DataContext> no seu código e consultar as tabelas especificadas pelo / R Designer.</span><span class="sxs-lookup"><span data-stu-id="347fc-139">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="347fc-140">Adicione o seguinte código para o `Load` evento para consultar as tabelas que são expostas como propriedades de seu contexto de dados.</span><span class="sxs-lookup"><span data-stu-id="347fc-140">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="347fc-141">A consulta filtra os resultados e retorna somente os clientes que estão localizados em `London`.</span><span class="sxs-lookup"><span data-stu-id="347fc-141">The query filters the results and returns only customers that are located in `London`.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#11](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-filter-query-results-by-using-linq_1.vb)]  
  
4.  <span data-ttu-id="347fc-142">Pressione F5 para executar seu projeto e exibir os resultados.</span><span class="sxs-lookup"><span data-stu-id="347fc-142">Press F5 to run your project and view the results.</span></span>  
  
5.  <span data-ttu-id="347fc-143">A seguir estão alguns outros filtros que você pode tentar.</span><span class="sxs-lookup"><span data-stu-id="347fc-143">Following are some other filters that you can try.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#12](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-filter-query-results-by-using-linq_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="347fc-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="347fc-144">See Also</span></span>  
 [<span data-ttu-id="347fc-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="347fc-145">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="347fc-146">Consultas</span><span class="sxs-lookup"><span data-stu-id="347fc-146">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="347fc-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="347fc-147">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="347fc-148">Métodos de DataContext (Object Relational Designer)</span><span class="sxs-lookup"><span data-stu-id="347fc-148">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)

---
title: "Como contar, somar ou fazer média de dados usando LINQ (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- average operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- queries [LINQ in Visual Basic], sum results
- Aggregate clause [Visual Basic]
- sum operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], counting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- count operator [LINQ in Visual Basic]
ms.assetid: 51ca1f59-7770-4884-8b76-113002e54fc0
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a8c77804a9813d6127edcf4bd8371e0de2b36074
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-count-sum-or-average-data-by-using-linq-visual-basic"></a><span data-ttu-id="576b0-102">Como contar, somar ou fazer média de dados usando LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="576b0-102">How to: Count, Sum, or Average Data by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="576b0-103">Consulta integrada à linguagem (LINQ) facilita o acesso a informações de banco de dados e executar consultas.</span><span class="sxs-lookup"><span data-stu-id="576b0-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="576b0-104">O exemplo a seguir mostra como criar um novo aplicativo que executa consultas em um banco de dados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="576b0-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="576b0-105">O exemplo conta, soma e calcula a média de resultados usando o `Aggregate` e `Group By` cláusulas.</span><span class="sxs-lookup"><span data-stu-id="576b0-105">The sample counts, sums, and averages the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="576b0-106">Para obter mais informações, consulte [cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md) e [grupo pela cláusula](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="576b0-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="576b0-107">Os exemplos neste tópico usam o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="576b0-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="576b0-108">Se você não tiver o banco de dados de exemplo Northwind no computador de desenvolvimento, você pode baixá-lo do [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) site da Web.</span><span class="sxs-lookup"><span data-stu-id="576b0-108">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="576b0-109">Para obter instruções, consulte [baixando bancos de dados de exemplo](../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="576b0-109">For instructions, see [Downloading Sample Databases](../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="576b0-110">Para criar uma conexão para um banco de dados</span><span class="sxs-lookup"><span data-stu-id="576b0-110">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="576b0-111">No Visual Studio, abra **Server Explorer**/**Pesquisador de objetos de banco de dados** clicando **Server Explorer**/**banco de dados Gerenciador de** no **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="576b0-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="576b0-112">Clique com botão direito **conexões de dados** na **Server Explorer**/**Pesquisador de objetos de banco de dados** e, em seguida, clique em **Adicionar Conexão**.</span><span class="sxs-lookup"><span data-stu-id="576b0-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="576b0-113">Especifique uma conexão válida para o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="576b0-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="576b0-114">Para adicionar um projeto que contém um arquivo LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="576b0-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="576b0-115">No Visual Studio, no menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="576b0-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="576b0-116">Selecione Visual Basic **aplicativo do Windows Forms** como o tipo de projeto.</span><span class="sxs-lookup"><span data-stu-id="576b0-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="576b0-117">No menu **Projeto**, clique em **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="576b0-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="576b0-118">Selecione o **Classes LINQ to SQL** modelo de item.</span><span class="sxs-lookup"><span data-stu-id="576b0-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="576b0-119">Dê o nome `northwind.dbml` para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="576b0-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="576b0-120">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="576b0-120">Click **Add**.</span></span> <span data-ttu-id="576b0-121">O Object Relational Designer (O/R Designer) é aberto para o arquivo dbml.</span><span class="sxs-lookup"><span data-stu-id="576b0-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="576b0-122">Para adicionar tabelas de consulta para o O/R Designer</span><span class="sxs-lookup"><span data-stu-id="576b0-122">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="576b0-123">Em **Server Explorer**/**Pesquisador de objetos de banco de dados**, expanda a conexão ao banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="576b0-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="576b0-124">Expanda o **tabelas** pasta.</span><span class="sxs-lookup"><span data-stu-id="576b0-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="576b0-125">Se você fechou o Object Relational Designer, você poderá reabri-lo clicando no arquivo dbml que você adicionou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="576b0-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="576b0-126">Clique na tabela clientes e arraste-o no painel esquerdo do designer.</span><span class="sxs-lookup"><span data-stu-id="576b0-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="576b0-127">Clique na tabela Orders e arraste-o no painel esquerdo do designer.</span><span class="sxs-lookup"><span data-stu-id="576b0-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="576b0-128">O designer cria novos `Customer` e `Order` objetos para o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="576b0-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="576b0-129">Observe que o designer automaticamente detecta as relações entre as tabelas e cria propriedades filhas para objetos relacionados.</span><span class="sxs-lookup"><span data-stu-id="576b0-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="576b0-130">Por exemplo, o IntelliSense mostrará que o `Customer` objeto tem um `Orders` propriedade para todos os pedidos relacionados a esse cliente.</span><span class="sxs-lookup"><span data-stu-id="576b0-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="576b0-131">Salve suas alterações e fechar o designer.</span><span class="sxs-lookup"><span data-stu-id="576b0-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="576b0-132">Salve seu projeto.</span><span class="sxs-lookup"><span data-stu-id="576b0-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="576b0-133">Para adicionar código para consultar o banco de dados e exibir os resultados</span><span class="sxs-lookup"><span data-stu-id="576b0-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="576b0-134">Do **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.DataGridView> controle para o Windows Form padrão para seu projeto, Form1.</span><span class="sxs-lookup"><span data-stu-id="576b0-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="576b0-135">Clique duas vezes em Form1 para adicionar código para o `Load` evento do formulário.</span><span class="sxs-lookup"><span data-stu-id="576b0-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="576b0-136">Quando você adicionar tabelas ao / R Designer, o designer adicionará um <xref:System.Data.Linq.DataContext> objeto para o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="576b0-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="576b0-137">Este objeto contém o código que você deve ter para acessar essas tabelas e para acessar objetos individuais e coleções para cada tabela.</span><span class="sxs-lookup"><span data-stu-id="576b0-137">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="576b0-138">O <xref:System.Data.Linq.DataContext> objeto para seu projeto é nomeado com base no nome do seu arquivo dbml.</span><span class="sxs-lookup"><span data-stu-id="576b0-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="576b0-139">Para este projeto, o <xref:System.Data.Linq.DataContext> objeto é nomeado `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="576b0-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="576b0-140">Você pode criar uma instância do <xref:System.Data.Linq.DataContext> no seu código e consultar as tabelas especificadas pelo / R Designer.</span><span class="sxs-lookup"><span data-stu-id="576b0-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="576b0-141">Adicione o seguinte código para o `Load` eventos para consultar as tabelas que são expostas como propriedades de seu <xref:System.Data.Linq.DataContext> contagem, soma e média de resultados.</span><span class="sxs-lookup"><span data-stu-id="576b0-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your <xref:System.Data.Linq.DataContext> and count, sum, and average the results.</span></span> <span data-ttu-id="576b0-142">O exemplo usa o `Aggregate` cláusula para consultar um único resultado e o `Group By` cláusula para mostrar uma média para resultados de agrupados.</span><span class="sxs-lookup"><span data-stu-id="576b0-142">The sample uses the `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#13](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-count-sum-or-average-data-by-using-linq_1.vb)]  
  
4.  <span data-ttu-id="576b0-143">Pressione F5 para executar seu projeto e exibir os resultados.</span><span class="sxs-lookup"><span data-stu-id="576b0-143">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="576b0-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="576b0-144">See Also</span></span>  
 [<span data-ttu-id="576b0-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="576b0-145">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="576b0-146">Consultas</span><span class="sxs-lookup"><span data-stu-id="576b0-146">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="576b0-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="576b0-147">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="576b0-148">Métodos de DataContext (Object Relational Designer)</span><span class="sxs-lookup"><span data-stu-id="576b0-148">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [<span data-ttu-id="576b0-149">Cláusula Aggregate</span><span class="sxs-lookup"><span data-stu-id="576b0-149">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="576b0-150">Cláusula Group By</span><span class="sxs-lookup"><span data-stu-id="576b0-150">Group By Clause</span></span>](../../../../visual-basic/language-reference/queries/group-by-clause.md)

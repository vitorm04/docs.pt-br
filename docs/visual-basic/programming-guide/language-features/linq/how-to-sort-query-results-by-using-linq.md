---
title: Como classificar resultados de consulta usando LINQ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- sorting query results, multiple columns
- sorting data [Visual Basic]
- sorting data [LINQ in Visual Basic]
- sorting query results [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], sorting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 07a4584d-9fd8-4a1d-b7d9-ccf2efa5c84e
ms.openlocfilehash: 5104ef5714819bd69cfd5b6d754e81b97f235e31
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43472092"
---
# <a name="how-to-sort-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="1aae9-102">Como classificar resultados de consulta usando LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1aae9-102">How to: Sort Query Results by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="1aae9-103">Consulta integrada à linguagem (LINQ) facilita o acesso às informações de banco de dados e executar consultas.</span><span class="sxs-lookup"><span data-stu-id="1aae9-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="1aae9-104">O exemplo a seguir mostra como criar um novo aplicativo que executa consultas em um banco de dados do SQL Server e classifica os resultados por vários campos usando o `Order By` cláusula.</span><span class="sxs-lookup"><span data-stu-id="1aae9-104">The following example shows how to create a new application that performs queries against a SQL Server database and sorts the results by multiple fields by using the `Order By` clause.</span></span> <span data-ttu-id="1aae9-105">A ordem de classificação para cada campo pode ser ordem crescente ou decrescente.</span><span class="sxs-lookup"><span data-stu-id="1aae9-105">The sort order for each field can be ascending order or descending order.</span></span> <span data-ttu-id="1aae9-106">Para obter mais informações, consulte [cláusula Order By](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="1aae9-106">For more information, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="1aae9-107">Os exemplos neste tópico usam o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="1aae9-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="1aae9-108">Se você não tiver esse banco de dados no computador de desenvolvimento, você pode baixá-lo do Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="1aae9-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="1aae9-109">Para obter instruções, consulte [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="1aae9-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="1aae9-110">Para criar uma conexão para um banco de dados</span><span class="sxs-lookup"><span data-stu-id="1aae9-110">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="1aae9-111">No Visual Studio, abra **Gerenciador de servidores**/**Database Explorer** clicando **Server Explorer**/**banco de dados Explorer** sobre o **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="1aae9-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="1aae9-112">Clique com botão direito **conexões de dados** na **Gerenciador de servidores**/**Database Explorer** e, em seguida, clique em **Adicionar Conexão**.</span><span class="sxs-lookup"><span data-stu-id="1aae9-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="1aae9-113">Especifique uma conexão válida para o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="1aae9-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="1aae9-114">Para adicionar um projeto que contém um arquivo LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="1aae9-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="1aae9-115">No Visual Studio, no menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="1aae9-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="1aae9-116">Selecione Visual Basic **aplicativo do Windows Forms** como o tipo de projeto.</span><span class="sxs-lookup"><span data-stu-id="1aae9-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="1aae9-117">No menu **Projeto**, clique em **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="1aae9-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="1aae9-118">Selecione o **Classes LINQ to SQL** modelo de item.</span><span class="sxs-lookup"><span data-stu-id="1aae9-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="1aae9-119">Dê o nome `northwind.dbml` para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="1aae9-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="1aae9-120">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="1aae9-120">Click **Add**.</span></span> <span data-ttu-id="1aae9-121">O Object Relational Designer (O/R Designer) é aberto para o arquivo Northwind dbml.</span><span class="sxs-lookup"><span data-stu-id="1aae9-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="1aae9-122">Para adicionar tabelas de consulta para o O/R Designer</span><span class="sxs-lookup"><span data-stu-id="1aae9-122">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="1aae9-123">Na **Gerenciador de servidores**/**Gerenciador de banco de dados**, expanda a conexão ao banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="1aae9-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="1aae9-124">Expanda o **tabelas** pasta.</span><span class="sxs-lookup"><span data-stu-id="1aae9-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="1aae9-125">Se você tiver fechado o O/R Designer, você poderá reabri-lo clicando duas vezes no arquivo dbml que você adicionou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1aae9-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="1aae9-126">Clique na tabela clientes e arraste-o no painel esquerdo do designer.</span><span class="sxs-lookup"><span data-stu-id="1aae9-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="1aae9-127">Clique na tabela Orders e arraste-o no painel esquerdo do designer.</span><span class="sxs-lookup"><span data-stu-id="1aae9-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="1aae9-128">O designer cria novos `Customer` e `Order` objetos para o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="1aae9-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="1aae9-129">Observe que o designer automaticamente detecta as relações entre as tabelas e cria propriedades filhas para objetos relacionados.</span><span class="sxs-lookup"><span data-stu-id="1aae9-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="1aae9-130">Por exemplo, o IntelliSense mostrará que o `Customer` objeto tem um `Orders` propriedade para todos os pedidos relacionados a esse cliente.</span><span class="sxs-lookup"><span data-stu-id="1aae9-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="1aae9-131">Salve suas alterações e feche o designer.</span><span class="sxs-lookup"><span data-stu-id="1aae9-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="1aae9-132">Salve seu projeto.</span><span class="sxs-lookup"><span data-stu-id="1aae9-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="1aae9-133">Para adicionar código para consultar o banco de dados e exibir os resultados</span><span class="sxs-lookup"><span data-stu-id="1aae9-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="1aae9-134">Dos **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.DataGridView> controle para o formulário do Windows padrão para seu projeto, Form1.</span><span class="sxs-lookup"><span data-stu-id="1aae9-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="1aae9-135">Clique duas vezes em Form1 para adicionar código para o `Load` evento do formulário.</span><span class="sxs-lookup"><span data-stu-id="1aae9-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="1aae9-136">Quando você adicionar tabelas ao Designer relacional de objetos, o designer adicionará um <xref:System.Data.Linq.DataContext> objeto ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="1aae9-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="1aae9-137">Este objeto contém o código que você deve ter para acessar essas tabelas e para acessar objetos individuais e coleções para cada tabela.</span><span class="sxs-lookup"><span data-stu-id="1aae9-137">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="1aae9-138">O <xref:System.Data.Linq.DataContext> objeto para seu projeto é nomeado com base no nome do seu arquivo. dbml.</span><span class="sxs-lookup"><span data-stu-id="1aae9-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="1aae9-139">Para este projeto, o <xref:System.Data.Linq.DataContext> objeto é nomeado `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="1aae9-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="1aae9-140">Você pode criar uma instância da <xref:System.Data.Linq.DataContext> no seu código e consultar as tabelas especificadas pelo Designer relacional de objetos.</span><span class="sxs-lookup"><span data-stu-id="1aae9-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="1aae9-141">Adicione o seguinte código para o `Load` eventos para consultar as tabelas que são expostas como propriedades de seu contexto de dados e classificar os resultados.</span><span class="sxs-lookup"><span data-stu-id="1aae9-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context and sort the results.</span></span> <span data-ttu-id="1aae9-142">A consulta classifica os resultados pelo número de pedidos de clientes, em ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="1aae9-142">The query sorts the results by the number of customer orders, in descending order.</span></span> <span data-ttu-id="1aae9-143">Os clientes que têm o mesmo número de pedidos são ordenados pelo nome da empresa em ordem (o padrão) crescente.</span><span class="sxs-lookup"><span data-stu-id="1aae9-143">Customers that have the same number of orders are ordered by company name in ascending order (the default).</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#10](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-sort-query-results-by-using-linq_1.vb)]  
  
4.  <span data-ttu-id="1aae9-144">Pressione F5 para executar seu projeto e exibir os resultados.</span><span class="sxs-lookup"><span data-stu-id="1aae9-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aae9-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1aae9-145">See Also</span></span>  
 [<span data-ttu-id="1aae9-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="1aae9-146">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="1aae9-147">Consultas</span><span class="sxs-lookup"><span data-stu-id="1aae9-147">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)  
 [<span data-ttu-id="1aae9-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="1aae9-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="1aae9-149">Métodos DataContext (Designer Relacional de Objetos)</span><span class="sxs-lookup"><span data-stu-id="1aae9-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)

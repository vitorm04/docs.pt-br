---
title: Como contar, somar ou fazer média de dados usando LINQ
ms.date: 07/20/2015
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
ms.openlocfilehash: 8be585c3e11bc3637b2dd1cfaf3437620aa2ba09
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405011"
---
# <a name="how-to-count-sum-or-average-data-by-using-linq-visual-basic"></a><span data-ttu-id="c21b6-102">Como contar, somar ou fazer média de dados usando LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c21b6-102">How to: Count, Sum, or Average Data by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="c21b6-103">A consulta integrada à linguagem (LINQ) facilita o acesso a informações do banco de dados e a execução de consultas.</span><span class="sxs-lookup"><span data-stu-id="c21b6-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="c21b6-104">O exemplo a seguir mostra como criar um novo aplicativo que executa consultas em um banco de dados SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c21b6-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="c21b6-105">O exemplo conta, soma e calcula a média dos resultados usando as `Aggregate` `Group By` cláusulas e.</span><span class="sxs-lookup"><span data-stu-id="c21b6-105">The sample counts, sums, and averages the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="c21b6-106">Para obter mais informações, consulte [cláusula Aggregate](../../../language-reference/queries/aggregate-clause.md) e [cláusula Group by](../../../language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c21b6-106">For more information, see [Aggregate Clause](../../../language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="c21b6-107">Os exemplos neste tópico usam o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="c21b6-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="c21b6-108">Caso não tenha esse banco de dados no seu computador de desenvolvimento, você poderá baixá-lo no Centro de Download da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c21b6-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="c21b6-109">Para obter instruções, consulte [baixar bancos de dados de exemplo](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="c21b6-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="c21b6-110">Para criar uma conexão com um banco de dados</span><span class="sxs-lookup"><span data-stu-id="c21b6-110">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="c21b6-111">No Visual Studio, abra **Gerenciador de servidores** / **Gerenciador de banco de dados** clicando em **Gerenciador de servidores** / **Gerenciador de banco de dados** no menu **Exibir** .</span><span class="sxs-lookup"><span data-stu-id="c21b6-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="c21b6-112">Clique com o botão direito do mouse em **conexões de dados** em **Gerenciador de servidores** / **Gerenciador de banco de dados** e clique em **Adicionar conexão**.</span><span class="sxs-lookup"><span data-stu-id="c21b6-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="c21b6-113">Especifique uma conexão válida para o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="c21b6-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="c21b6-114">Para adicionar um projeto que contém um arquivo de LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="c21b6-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="c21b6-115">No Visual Studio, no menu **arquivo** , aponte para **novo** e clique em **projeto**.</span><span class="sxs-lookup"><span data-stu-id="c21b6-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="c21b6-116">Selecione Visual Basic **aplicativo Windows Forms** como o tipo de projeto.</span><span class="sxs-lookup"><span data-stu-id="c21b6-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="c21b6-117">No menu **Projeto** , clique em **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="c21b6-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="c21b6-118">Selecione o modelo de item **classes de LINQ to SQL** .</span><span class="sxs-lookup"><span data-stu-id="c21b6-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="c21b6-119">Atribua um nome ao arquivo `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="c21b6-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="c21b6-120">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="c21b6-120">Click **Add**.</span></span> <span data-ttu-id="c21b6-121">O Object Relational Designer (O/R Designer) é aberto para o arquivo Northwind. dbml.</span><span class="sxs-lookup"><span data-stu-id="c21b6-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="c21b6-122">Para adicionar tabelas para consulta ao o/R Designer</span><span class="sxs-lookup"><span data-stu-id="c21b6-122">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="c21b6-123">Em **Gerenciador de servidores** / **Gerenciador de banco de dados**, expanda a conexão com o banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="c21b6-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="c21b6-124">Expanda a pasta **Tabelas** .</span><span class="sxs-lookup"><span data-stu-id="c21b6-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="c21b6-125">Se você fechou o o/R Designer, você pode reabri-lo clicando duas vezes no arquivo Northwind. dbml que você adicionou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c21b6-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="c21b6-126">Clique na tabela clientes e arraste-a para o painel esquerdo do designer.</span><span class="sxs-lookup"><span data-stu-id="c21b6-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="c21b6-127">Clique na tabela Orders e arraste-a para o painel esquerdo do designer.</span><span class="sxs-lookup"><span data-stu-id="c21b6-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="c21b6-128">O designer cria novos `Customer` `Order` objetos e para o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c21b6-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="c21b6-129">Observe que o designer detecta automaticamente as relações entre as tabelas e cria propriedades filhas para objetos relacionados.</span><span class="sxs-lookup"><span data-stu-id="c21b6-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="c21b6-130">Por exemplo, o IntelliSense mostrará que o `Customer` objeto tem uma `Orders` propriedade para todos os pedidos relacionados a esse cliente.</span><span class="sxs-lookup"><span data-stu-id="c21b6-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3. <span data-ttu-id="c21b6-131">Salve as alterações e feche o designer.</span><span class="sxs-lookup"><span data-stu-id="c21b6-131">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="c21b6-132">Salve seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c21b6-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="c21b6-133">Para adicionar código para consultar o banco de dados e exibir os resultados</span><span class="sxs-lookup"><span data-stu-id="c21b6-133">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="c21b6-134">Na **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.DataGridView> controle para o formulário padrão do Windows para seu projeto, Form1.</span><span class="sxs-lookup"><span data-stu-id="c21b6-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="c21b6-135">Clique duas vezes em Form1 para adicionar código ao `Load` evento do formulário.</span><span class="sxs-lookup"><span data-stu-id="c21b6-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3. <span data-ttu-id="c21b6-136">Quando você adicionou tabelas ao o/R Designer, o designer adicionou um <xref:System.Data.Linq.DataContext> objeto ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c21b6-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="c21b6-137">Esse objeto contém o código que você deve ter para acessar essas tabelas e para acessar objetos individuais e coleções para cada tabela.</span><span class="sxs-lookup"><span data-stu-id="c21b6-137">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="c21b6-138">O <xref:System.Data.Linq.DataContext> objeto para seu projeto é nomeado com base no nome do seu arquivo. dbml.</span><span class="sxs-lookup"><span data-stu-id="c21b6-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="c21b6-139">Para este projeto, o <xref:System.Data.Linq.DataContext> objeto é nomeado `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="c21b6-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="c21b6-140">Você pode criar uma instância do <xref:System.Data.Linq.DataContext> no seu código e consultar as tabelas especificadas pelo o/R Designer.</span><span class="sxs-lookup"><span data-stu-id="c21b6-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="c21b6-141">Adicione o código a seguir ao `Load` evento para consultar as tabelas que são expostas como propriedades de seu <xref:System.Data.Linq.DataContext> e contagem, soma e média dos resultados.</span><span class="sxs-lookup"><span data-stu-id="c21b6-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your <xref:System.Data.Linq.DataContext> and count, sum, and average the results.</span></span> <span data-ttu-id="c21b6-142">O exemplo usa a `Aggregate` cláusula para consultar um único resultado e a `Group By` cláusula para mostrar uma média para resultados agrupados.</span><span class="sxs-lookup"><span data-stu-id="c21b6-142">The sample uses the `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form6.vb#13)]  
  
4. <span data-ttu-id="c21b6-143">Pressione F5 para executar o projeto e exibir os resultados.</span><span class="sxs-lookup"><span data-stu-id="c21b6-143">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c21b6-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="c21b6-144">See also</span></span>

- [<span data-ttu-id="c21b6-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="c21b6-145">LINQ</span></span>](index.md)
- [<span data-ttu-id="c21b6-146">Consultas</span><span class="sxs-lookup"><span data-stu-id="c21b6-146">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="c21b6-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="c21b6-147">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="c21b6-148">Métodos DataContext (O/R Designer)</span><span class="sxs-lookup"><span data-stu-id="c21b6-148">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="c21b6-149">Cláusula Aggregate</span><span class="sxs-lookup"><span data-stu-id="c21b6-149">Aggregate Clause</span></span>](../../../language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="c21b6-150">Cláusula Group By</span><span class="sxs-lookup"><span data-stu-id="c21b6-150">Group By Clause</span></span>](../../../language-reference/queries/group-by-clause.md)

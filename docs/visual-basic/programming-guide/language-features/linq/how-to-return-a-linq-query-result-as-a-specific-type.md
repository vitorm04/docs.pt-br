---
title: Como retornar um resultado de consulta LINQ como um tipo específico
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
ms.openlocfilehash: c8ed792bf3ffefd903d60522f621958e44546d32
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404946"
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a><span data-ttu-id="a3427-102">Como retornar um resultado de consulta LINQ como um tipo específico (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3427-102">How to: Return a LINQ Query Result as a Specific Type (Visual Basic)</span></span>
<span data-ttu-id="a3427-103">A consulta integrada à linguagem (LINQ) facilita o acesso a informações do banco de dados e a execução de consultas.</span><span class="sxs-lookup"><span data-stu-id="a3427-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span> <span data-ttu-id="a3427-104">Por padrão, as consultas LINQ retornam uma lista de objetos como um tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="a3427-104">By default, LINQ queries return a list of objects as an anonymous type.</span></span> <span data-ttu-id="a3427-105">Você também pode especificar que uma consulta retorne uma lista de um tipo específico usando a `Select` cláusula.</span><span class="sxs-lookup"><span data-stu-id="a3427-105">You can also specify that a query return a list of a specific type by using the `Select` clause.</span></span>  
  
 <span data-ttu-id="a3427-106">O exemplo a seguir mostra como criar um novo aplicativo que executa consultas em um banco de dados SQL Server e projeta os resultados como um tipo nomeado específico.</span><span class="sxs-lookup"><span data-stu-id="a3427-106">The following example shows how to create a new application that performs queries against a SQL Server database and projects the results as a specific named type.</span></span> <span data-ttu-id="a3427-107">Para obter mais informações, consulte [tipos anônimos](../objects-and-classes/anonymous-types.md) e [cláusula SELECT](../../../language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="a3427-107">For more information, see [Anonymous Types](../objects-and-classes/anonymous-types.md) and [Select Clause](../../../language-reference/queries/select-clause.md).</span></span>  
  
 <span data-ttu-id="a3427-108">Os exemplos neste tópico usam o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="a3427-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="a3427-109">Caso não tenha esse banco de dados no seu computador de desenvolvimento, você poderá baixá-lo no Centro de Download da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a3427-109">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="a3427-110">Para obter instruções, consulte [baixar bancos de dados de exemplo](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="a3427-110">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="a3427-111">Para criar uma conexão com um banco de dados</span><span class="sxs-lookup"><span data-stu-id="a3427-111">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="a3427-112">No Visual Studio, abra **Gerenciador de servidores** / **Gerenciador de banco de dados** clicando em **Gerenciador de servidores** / **Gerenciador de banco de dados** no menu **Exibir** .</span><span class="sxs-lookup"><span data-stu-id="a3427-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="a3427-113">Clique com o botão direito do mouse em **conexões de dados** em **Gerenciador de servidores** / **Gerenciador de banco de dados** e clique em **Adicionar conexão**.</span><span class="sxs-lookup"><span data-stu-id="a3427-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="a3427-114">Especifique uma conexão válida para o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="a3427-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="a3427-115">Para adicionar um projeto que contém um arquivo de LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="a3427-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="a3427-116">No Visual Studio, no menu **arquivo** , aponte para **novo** e clique em **projeto**.</span><span class="sxs-lookup"><span data-stu-id="a3427-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="a3427-117">Selecione Visual Basic **aplicativo Windows Forms** como o tipo de projeto.</span><span class="sxs-lookup"><span data-stu-id="a3427-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="a3427-118">No menu **Projeto** , clique em **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="a3427-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="a3427-119">Selecione o modelo de item **classes de LINQ to SQL** .</span><span class="sxs-lookup"><span data-stu-id="a3427-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="a3427-120">Atribua um nome ao arquivo `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="a3427-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="a3427-121">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="a3427-121">Click **Add**.</span></span> <span data-ttu-id="a3427-122">O Object Relational Designer (O/R Designer) é aberto para o arquivo Northwind. dbml.</span><span class="sxs-lookup"><span data-stu-id="a3427-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="a3427-123">Para adicionar tabelas para consulta ao o/R Designer</span><span class="sxs-lookup"><span data-stu-id="a3427-123">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="a3427-124">Em **Gerenciador de servidores** / **Gerenciador de banco de dados**, expanda a conexão com o banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="a3427-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="a3427-125">Expanda a pasta **Tabelas** .</span><span class="sxs-lookup"><span data-stu-id="a3427-125">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="a3427-126">Se você fechou o o/R Designer, você pode reabri-lo clicando duas vezes no arquivo Northwind. dbml que você adicionou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a3427-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="a3427-127">Clique na tabela clientes e arraste-a para o painel esquerdo do designer.</span><span class="sxs-lookup"><span data-stu-id="a3427-127">Click the Customers table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="a3427-128">O designer cria um novo `Customer` objeto para o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="a3427-128">The designer creates a new `Customer` object for your project.</span></span> <span data-ttu-id="a3427-129">Você pode projetar um resultado de consulta como o `Customer` tipo ou como um tipo que você cria.</span><span class="sxs-lookup"><span data-stu-id="a3427-129">You can project a query result as the `Customer` type or as a type that you create.</span></span> <span data-ttu-id="a3427-130">Este exemplo criará um novo tipo em um procedimento posterior e projetará um resultado de consulta como esse tipo.</span><span class="sxs-lookup"><span data-stu-id="a3427-130">This sample will create a new type in a later procedure and project a query result as that type.</span></span>  
  
3. <span data-ttu-id="a3427-131">Salve as alterações e feche o designer.</span><span class="sxs-lookup"><span data-stu-id="a3427-131">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="a3427-132">Salve seu projeto.</span><span class="sxs-lookup"><span data-stu-id="a3427-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="a3427-133">Para adicionar código para consultar o banco de dados e exibir os resultados</span><span class="sxs-lookup"><span data-stu-id="a3427-133">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="a3427-134">Na **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.DataGridView> controle para o formulário padrão do Windows para seu projeto, Form1.</span><span class="sxs-lookup"><span data-stu-id="a3427-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="a3427-135">Clique duas vezes em Form1 para modificar a classe Form1.</span><span class="sxs-lookup"><span data-stu-id="a3427-135">Double-click Form1 to modify the Form1 class.</span></span>  
  
3. <span data-ttu-id="a3427-136">Após a `End Class` instrução da classe Form1, adicione o código a seguir para criar um `CustomerInfo` tipo para manter os resultados da consulta para este exemplo.</span><span class="sxs-lookup"><span data-stu-id="a3427-136">After the `End Class` statement of the Form1 class, add the following code to create a `CustomerInfo` type to hold the query results for this sample.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#16)]  
  
4. <span data-ttu-id="a3427-137">Quando você adicionou tabelas ao o/R Designer, o designer adicionou um <xref:System.Data.Linq.DataContext> objeto ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="a3427-137">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="a3427-138">Esse objeto contém o código que você deve ter para acessar essas tabelas e para acessar objetos individuais e coleções para cada tabela.</span><span class="sxs-lookup"><span data-stu-id="a3427-138">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="a3427-139">O <xref:System.Data.Linq.DataContext> objeto para seu projeto é nomeado com base no nome do seu arquivo. dbml.</span><span class="sxs-lookup"><span data-stu-id="a3427-139">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="a3427-140">Para este projeto, o <xref:System.Data.Linq.DataContext> objeto é nomeado `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="a3427-140">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="a3427-141">Você pode criar uma instância do <xref:System.Data.Linq.DataContext> no seu código e consultar as tabelas especificadas pelo o/R Designer.</span><span class="sxs-lookup"><span data-stu-id="a3427-141">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="a3427-142">No `Load` caso da classe Form1, adicione o código a seguir para consultar as tabelas que são expostas como propriedades do seu contexto de dados.</span><span class="sxs-lookup"><span data-stu-id="a3427-142">In the `Load` event of the Form1 class, add the following code to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="a3427-143">A `Select` cláusula da consulta criará um novo `CustomerInfo` tipo em vez de um tipo anônimo para cada item do resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="a3427-143">The `Select` clause of the query will create a new `CustomerInfo` type instead of an anonymous type for each item of the query result.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#15)]  
  
5. <span data-ttu-id="a3427-144">Pressione F5 para executar o projeto e exibir os resultados.</span><span class="sxs-lookup"><span data-stu-id="a3427-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3427-145">Confira também</span><span class="sxs-lookup"><span data-stu-id="a3427-145">See also</span></span>

- [<span data-ttu-id="a3427-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="a3427-146">LINQ</span></span>](index.md)
- [<span data-ttu-id="a3427-147">Consultas</span><span class="sxs-lookup"><span data-stu-id="a3427-147">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="a3427-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="a3427-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="a3427-149">Métodos DataContext (O/R Designer)</span><span class="sxs-lookup"><span data-stu-id="a3427-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)

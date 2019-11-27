---
title: 'Como: classificar os resultados da consulta usando o LINQ'
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
ms.openlocfilehash: 020e4a3800515329b29e2941baf50d3d8add4605
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354162"
---
# <a name="how-to-sort-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="d5fbc-102">Como classificar resultados de consulta usando LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5fbc-102">How to: Sort Query Results by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="d5fbc-103">A consulta integrada à linguagem (LINQ) facilita o acesso a informações do banco de dados e a execução de consultas.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="d5fbc-104">O exemplo a seguir mostra como criar um novo aplicativo que executa consultas em um banco de dados SQL Server e classifica os resultados por vários campos usando a cláusula `Order By`.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-104">The following example shows how to create a new application that performs queries against a SQL Server database and sorts the results by multiple fields by using the `Order By` clause.</span></span> <span data-ttu-id="d5fbc-105">A ordem de classificação de cada campo pode ser ordem crescente ou decrescente.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-105">The sort order for each field can be ascending order or descending order.</span></span> <span data-ttu-id="d5fbc-106">Para obter mais informações, consulte [cláusula order by](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d5fbc-106">For more information, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="d5fbc-107">Os exemplos neste tópico usam o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="d5fbc-108">Caso não tenha esse banco de dados no seu computador de desenvolvimento, você poderá baixá-lo no Centro de Download da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="d5fbc-109">Para obter instruções, consulte [baixar bancos de dados de exemplo](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="d5fbc-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="d5fbc-110">Para criar uma conexão com um banco de dados</span><span class="sxs-lookup"><span data-stu-id="d5fbc-110">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="d5fbc-111">No Visual Studio, abra **Gerenciador de Servidores**/**Gerenciador de Banco de Dados** clicando em **Gerenciador de servidores**/**Gerenciador de banco de dados** no menu **Exibir** .</span><span class="sxs-lookup"><span data-stu-id="d5fbc-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="d5fbc-112">Clique com o botão direito do mouse em **conexões de dados** no **Gerenciador de servidores**/**Gerenciador de banco de dados** e clique em **Adicionar conexão**.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="d5fbc-113">Especifique uma conexão válida para o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="d5fbc-114">Para adicionar um projeto que contém um arquivo de LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="d5fbc-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="d5fbc-115">No Visual Studio, no menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="d5fbc-116">Selecione Visual Basic **aplicativo Windows Forms** como o tipo de projeto.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="d5fbc-117">No menu **Projeto**, clique em **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="d5fbc-118">Selecione o modelo de item **classes de LINQ to SQL** .</span><span class="sxs-lookup"><span data-stu-id="d5fbc-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="d5fbc-119">Dê o nome `northwind.dbml` para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="d5fbc-120">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-120">Click **Add**.</span></span> <span data-ttu-id="d5fbc-121">O Object Relational Designer (O/R Designer) é aberto para o arquivo Northwind. dbml.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="d5fbc-122">Para adicionar tabelas para consulta ao o/R Designer</span><span class="sxs-lookup"><span data-stu-id="d5fbc-122">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="d5fbc-123">Em **Gerenciador de Servidores**/**Gerenciador de banco de dados**, expanda a conexão com o banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="d5fbc-124">Expanda a pasta **tabelas** .</span><span class="sxs-lookup"><span data-stu-id="d5fbc-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="d5fbc-125">Se você fechou o o/R Designer, você pode reabri-lo clicando duas vezes no arquivo Northwind. dbml que você adicionou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="d5fbc-126">Clique na tabela clientes e arraste-a para o painel esquerdo do designer.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="d5fbc-127">Clique na tabela Orders e arraste-a para o painel esquerdo do designer.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="d5fbc-128">O designer cria novos objetos `Customer` e `Order` para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="d5fbc-129">Observe que o designer detecta automaticamente as relações entre as tabelas e cria propriedades filhas para objetos relacionados.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="d5fbc-130">Por exemplo, o IntelliSense mostrará que o objeto `Customer` tem uma propriedade `Orders` para todos os pedidos relacionados a esse cliente.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3. <span data-ttu-id="d5fbc-131">Salve as alterações e feche o designer.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-131">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="d5fbc-132">Salve seu projeto.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="d5fbc-133">Para adicionar código para consultar o banco de dados e exibir os resultados</span><span class="sxs-lookup"><span data-stu-id="d5fbc-133">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="d5fbc-134">Na **caixa de ferramentas**, arraste um controle de <xref:System.Windows.Forms.DataGridView> para o formulário padrão do Windows para seu projeto, Form1.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="d5fbc-135">Clique duas vezes em Form1 para adicionar código ao evento `Load` do formulário.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3. <span data-ttu-id="d5fbc-136">Quando você adicionou tabelas ao o/R Designer, o designer adicionou um objeto <xref:System.Data.Linq.DataContext> ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="d5fbc-137">Esse objeto contém o código que você deve ter para acessar essas tabelas e para acessar objetos individuais e coleções para cada tabela.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-137">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="d5fbc-138">O objeto <xref:System.Data.Linq.DataContext> para seu projeto é nomeado com base no nome do seu arquivo. dbml.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="d5fbc-139">Para este projeto, o objeto <xref:System.Data.Linq.DataContext> é nomeado `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="d5fbc-140">Você pode criar uma instância do <xref:System.Data.Linq.DataContext> em seu código e consultar as tabelas especificadas pelo o/R Designer.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="d5fbc-141">Adicione o código a seguir ao evento `Load` para consultar as tabelas que são expostas como propriedades de seu contexto de dados e classificar os resultados.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context and sort the results.</span></span> <span data-ttu-id="d5fbc-142">A consulta classifica os resultados pelo número de pedidos de clientes, em ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-142">The query sorts the results by the number of customer orders, in descending order.</span></span> <span data-ttu-id="d5fbc-143">Os clientes que têm o mesmo número de pedidos são ordenados pelo nome da empresa em ordem crescente (o padrão).</span><span class="sxs-lookup"><span data-stu-id="d5fbc-143">Customers that have the same number of orders are ordered by company name in ascending order (the default).</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form4.vb#10)]  
  
4. <span data-ttu-id="d5fbc-144">Pressione F5 para executar o projeto e exibir os resultados.</span><span class="sxs-lookup"><span data-stu-id="d5fbc-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5fbc-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5fbc-145">See also</span></span>

- [<span data-ttu-id="d5fbc-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="d5fbc-146">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="d5fbc-147">Consultas</span><span class="sxs-lookup"><span data-stu-id="d5fbc-147">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="d5fbc-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="d5fbc-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="d5fbc-149">Métodos DataContext (Designer Relacional de Objetos)</span><span class="sxs-lookup"><span data-stu-id="d5fbc-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)

---
title: 'Como: classificar resultados de consulta usando LINQ (Visual Basic) | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
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
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 0c728d9e52add00c9d3241a9f598c15eb2db17a5
ms.contentlocale: pt-br
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-sort-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="e6e7e-102">Como classificar resultados de consulta usando LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6e7e-102">How to: Sort Query Results by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="e6e7e-103">Consulta integrada à linguagem (LINQ) facilita o acesso às informações de banco de dados e executar consultas.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="e6e7e-104">O exemplo a seguir mostra como criar um novo aplicativo que executa consultas em um banco de dados do SQL Server e classifica os resultados por vários campos usando o `Order By` cláusula.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-104">The following example shows how to create a new application that performs queries against a SQL Server database and sorts the results by multiple fields by using the `Order By` clause.</span></span> <span data-ttu-id="e6e7e-105">A ordem de classificação para cada campo pode ser ordem crescente ou decrescente.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-105">The sort order for each field can be ascending order or descending order.</span></span> <span data-ttu-id="e6e7e-106">Para obter mais informações, consulte [cláusula Order By](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e6e7e-106">For more information, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="e6e7e-107">Os exemplos neste tópico usam o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="e6e7e-108">Se você não tiver o banco de dados de exemplo Northwind no seu computador de desenvolvimento, você pode baixá-lo do [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) site da Web.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-108">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="e6e7e-109">Para obter instruções, consulte [baixando bancos de dados de exemplo](https://msdn.microsoft.com/library/bb399411).</span><span class="sxs-lookup"><span data-stu-id="e6e7e-109">For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/bb399411).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="e6e7e-110">Para criar uma conexão para um banco de dados</span><span class="sxs-lookup"><span data-stu-id="e6e7e-110">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="e6e7e-111">No Visual Studio, abra **Server Explorer**/**Database Explorer** clicando **Server Explorer**/**Database Explorer** sobre o **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="e6e7e-112">Clique com botão direito **conexões de dados** na **Server Explorer**/**Database Explorer** e, em seguida, clique em **Adicionar Conexão**.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="e6e7e-113">Especifique uma conexão válida para o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="e6e7e-114">Para adicionar um projeto que contém um arquivo LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e6e7e-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="e6e7e-115">No Visual Studio, no **arquivo** , aponte para **novo** e, em seguida, clique em **projeto**.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="e6e7e-116">Selecione Visual Basic **Windows Forms Application** como o tipo de projeto.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="e6e7e-117">No menu **Projeto**, clique em **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="e6e7e-118">Selecione o **Classes LINQ to SQL** modelo de item.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="e6e7e-119">Nomeie o arquivo `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="e6e7e-120">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-120">Click **Add**.</span></span> <span data-ttu-id="e6e7e-121">O Object Relational Designer (Object Relational Designer) é aberto para o arquivo Northwind dbml.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="e6e7e-122">Para adicionar tabelas de consulta para o Object Relational Designer</span><span class="sxs-lookup"><span data-stu-id="e6e7e-122">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="e6e7e-123">Em **Server Explorer**/**Database Explorer**, expanda a conexão ao banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="e6e7e-124">Expanda o **tabelas** pasta.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="e6e7e-125">Se você tiver fechado o Object Relational Designer, você poderá reabri-lo clicando no arquivo dbml que você adicionou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="e6e7e-126">Clique na tabela clientes e arraste-o para o painel esquerdo do designer.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="e6e7e-127">Clique na tabela Orders e arraste-o para o painel esquerdo do designer.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="e6e7e-128">O designer cria novos `Customer` e `Order` objetos para o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="e6e7e-129">Observe que o designer automaticamente detecta relacionamentos entre as tabelas e cria propriedades filhas para objetos relacionados.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="e6e7e-130">Por exemplo, o IntelliSense mostrará que o `Customer` objeto tem um `Orders` propriedade para todos os pedidos relacionados a esse cliente.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="e6e7e-131">Salve suas alterações e feche o designer.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="e6e7e-132">Salve seu projeto.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="e6e7e-133">Para adicionar código para consultar o banco de dados e exibir os resultados</span><span class="sxs-lookup"><span data-stu-id="e6e7e-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="e6e7e-134">Do **Toolbox**, arraste um <xref:System.Windows.Forms.DataGridView>controle para o Windows Form padrão para seu projeto, Form1.</xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="e6e7e-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="e6e7e-135">Clique duas vezes em Form1 para adicionar código para o `Load` eventos do formulário.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="e6e7e-136">Quando você adicionar tabelas ao / R Designer, o designer adicionará um <xref:System.Data.Linq.DataContext>objeto ao seu projeto.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="e6e7e-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="e6e7e-137">Este objeto contém o código que você deve ter para acessar essas tabelas e para acessar objetos individuais e coleções para cada tabela.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-137">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="e6e7e-138">O <xref:System.Data.Linq.DataContext>objeto para seu projeto é nomeado com base no nome do seu arquivo. dbml.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="e6e7e-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="e6e7e-139">Para este projeto, o <xref:System.Data.Linq.DataContext>objeto é denominado `northwindDataContext`.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="e6e7e-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="e6e7e-140">Você pode criar uma instância do <xref:System.Data.Linq.DataContext>no seu código e consultar as tabelas especificadas pelo / R Designer.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="e6e7e-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="e6e7e-141">Adicione o seguinte código para o `Load` eventos para consultar as tabelas que são expostas como propriedades de seu contexto de dados e classificar os resultados.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context and sort the results.</span></span> <span data-ttu-id="e6e7e-142">A consulta classifica os resultados pelo número de pedidos de clientes, em ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-142">The query sorts the results by the number of customer orders, in descending order.</span></span> <span data-ttu-id="e6e7e-143">Os clientes que têm o mesmo número de pedidos são ordenados pelo nome da empresa em ordem (o padrão) crescente.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-143">Customers that have the same number of orders are ordered by company name in ascending order (the default).</span></span>  
  
     <span data-ttu-id="e6e7e-144">[!code-vb[VbLINQToSQLHowTos n º&10;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-sort-query-results-by-using-linq_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e6e7e-144">[!code-vb[VbLINQToSQLHowTos#10](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-sort-query-results-by-using-linq_1.vb)]</span></span>  
  
4.  <span data-ttu-id="e6e7e-145">Pressione F5 para executar seu projeto e exibir os resultados.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-145">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6e7e-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6e7e-146">See Also</span></span>  
 <span data-ttu-id="e6e7e-147">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="e6e7e-147">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="e6e7e-148"> [Consultas](../../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="e6e7e-148"> [Queries](../../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="e6e7e-149"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span><span class="sxs-lookup"><span data-stu-id="e6e7e-149"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span></span>  
<span data-ttu-id="e6e7e-150"> [Métodos de DataContext (Object Relational Designer)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="e6e7e-150"> [DataContext Methods (O/R Designer)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)</span></span>


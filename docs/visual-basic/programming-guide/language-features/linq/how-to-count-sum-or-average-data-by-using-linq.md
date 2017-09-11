---
title: "Como: contar, somar ou fazer média de dados usando LINQ (Visual Basic) | Documentos do Microsoft"
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
- average operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- queries [LINQ in Visual Basic], sum results
- Aggregate clause
- sum operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], counting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- count operator [LINQ in Visual Basic]
ms.assetid: 51ca1f59-7770-4884-8b76-113002e54fc0
caps.latest.revision: 9
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
ms.openlocfilehash: 63ea6cd9eb2942ac80688cec6ea44e89c2a2b7f7
ms.contentlocale: pt-br
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-count-sum-or-average-data-by-using-linq-visual-basic"></a><span data-ttu-id="8bd1c-102">Como contar, somar ou fazer média de dados usando LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bd1c-102">How to: Count, Sum, or Average Data by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="8bd1c-103">Consulta integrada à linguagem (LINQ) facilita o acesso às informações de banco de dados e executar consultas.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="8bd1c-104">O exemplo a seguir mostra como criar um novo aplicativo que executa consultas em um banco de dados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="8bd1c-105">O exemplo conta, soma e calcula a média de resultados usando o `Aggregate` e `Group By` cláusulas.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-105">The sample counts, sums, and averages the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="8bd1c-106">Para obter mais informações, consulte [cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md) e [grupo pela cláusula](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="8bd1c-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="8bd1c-107">Os exemplos neste tópico usam o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="8bd1c-108">Se você não tiver o banco de dados de exemplo Northwind no seu computador de desenvolvimento, você pode baixá-lo do [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) site da Web.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-108">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="8bd1c-109">Para obter instruções, consulte [baixando bancos de dados de exemplo](https://msdn.microsoft.com/library/bb399411).</span><span class="sxs-lookup"><span data-stu-id="8bd1c-109">For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/bb399411).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="8bd1c-110">Para criar uma conexão para um banco de dados</span><span class="sxs-lookup"><span data-stu-id="8bd1c-110">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="8bd1c-111">No Visual Studio, abra **Server Explorer**/**Database Explorer** clicando **Server Explorer**/**Database Explorer** sobre o **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="8bd1c-112">Clique com botão direito **conexões de dados** na **Server Explorer**/**Database Explorer** e, em seguida, clique em **Adicionar Conexão**.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="8bd1c-113">Especifique uma conexão válida para o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="8bd1c-114">Para adicionar um projeto que contém um arquivo LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="8bd1c-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="8bd1c-115">No Visual Studio, no **arquivo** , aponte para **novo** e, em seguida, clique em **projeto**.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="8bd1c-116">Selecione Visual Basic **Windows Forms Application** como o tipo de projeto.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="8bd1c-117">No menu **Projeto**, clique em **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="8bd1c-118">Selecione o **Classes LINQ to SQL** modelo de item.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="8bd1c-119">Nomeie o arquivo `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="8bd1c-120">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-120">Click **Add**.</span></span> <span data-ttu-id="8bd1c-121">O Object Relational Designer (Object Relational Designer) é aberto para o arquivo Northwind dbml.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="8bd1c-122">Para adicionar tabelas de consulta para o Object Relational Designer</span><span class="sxs-lookup"><span data-stu-id="8bd1c-122">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="8bd1c-123">Em **Server Explorer**/**Database Explorer**, expanda a conexão ao banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="8bd1c-124">Expanda o **tabelas** pasta.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="8bd1c-125">Se você tiver fechado o Object Relational Designer, você poderá reabri-lo clicando no arquivo dbml que você adicionou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="8bd1c-126">Clique na tabela clientes e arraste-o para o painel esquerdo do designer.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="8bd1c-127">Clique na tabela Orders e arraste-o para o painel esquerdo do designer.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="8bd1c-128">O designer cria novos `Customer` e `Order` objetos para o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="8bd1c-129">Observe que o designer automaticamente detecta relacionamentos entre as tabelas e cria propriedades filhas para objetos relacionados.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="8bd1c-130">Por exemplo, o IntelliSense mostrará que o `Customer` objeto tem um `Orders` propriedade para todos os pedidos relacionados a esse cliente.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="8bd1c-131">Salve suas alterações e feche o designer.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="8bd1c-132">Salve seu projeto.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="8bd1c-133">Para adicionar código para consultar o banco de dados e exibir os resultados</span><span class="sxs-lookup"><span data-stu-id="8bd1c-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="8bd1c-134">Do **Toolbox**, arraste um <xref:System.Windows.Forms.DataGridView>controle para o Windows Form padrão para seu projeto, Form1.</xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="8bd1c-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="8bd1c-135">Clique duas vezes em Form1 para adicionar código para o `Load` eventos do formulário.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="8bd1c-136">Quando você adicionar tabelas ao / R Designer, o designer adicionará um <xref:System.Data.Linq.DataContext>objeto para o seu projeto.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="8bd1c-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="8bd1c-137">Este objeto contém o código que você deve ter para acessar essas tabelas e para acessar objetos individuais e coleções para cada tabela.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-137">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="8bd1c-138">O <xref:System.Data.Linq.DataContext>objeto para seu projeto é nomeado com base no nome do seu arquivo. dbml.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="8bd1c-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="8bd1c-139">Para este projeto, o <xref:System.Data.Linq.DataContext>objeto é denominado `northwindDataContext`.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="8bd1c-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="8bd1c-140">Você pode criar uma instância do <xref:System.Data.Linq.DataContext>no seu código e consultar as tabelas especificadas pelo / R Designer.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="8bd1c-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="8bd1c-141">Adicione o seguinte código para o `Load` eventos para consultar as tabelas que são expostas como propriedades de seu <xref:System.Data.Linq.DataContext>e contar, soma e média de resultados.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="8bd1c-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your <xref:System.Data.Linq.DataContext> and count, sum, and average the results.</span></span> <span data-ttu-id="8bd1c-142">O exemplo usa o `Aggregate` cláusula para consultar um único resultado e o `Group By` cláusula para mostrar uma média para resultados agrupados.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-142">The sample uses the `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     <span data-ttu-id="8bd1c-143">[!code-vb[VbLINQToSQLHowTos&13;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-count-sum-or-average-data-by-using-linq_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="8bd1c-143">[!code-vb[VbLINQToSQLHowTos#13](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-count-sum-or-average-data-by-using-linq_1.vb)]</span></span>  
  
4.  <span data-ttu-id="8bd1c-144">Pressione F5 para executar seu projeto e exibir os resultados.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bd1c-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8bd1c-145">See Also</span></span>  
 <span data-ttu-id="8bd1c-146">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="8bd1c-146">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="8bd1c-147"> [Consultas](../../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="8bd1c-147"> [Queries](../../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="8bd1c-148"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span><span class="sxs-lookup"><span data-stu-id="8bd1c-148"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span></span>  
<span data-ttu-id="8bd1c-149"> [Métodos de DataContext (Object Relational Designer)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="8bd1c-149"> [DataContext Methods (O/R Designer)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)</span></span>  
<span data-ttu-id="8bd1c-150"> [Cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md) </span><span class="sxs-lookup"><span data-stu-id="8bd1c-150"> [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) </span></span>  
<span data-ttu-id="8bd1c-151"> [Cláusula Group By](../../../../visual-basic/language-reference/queries/group-by-clause.md)</span><span class="sxs-lookup"><span data-stu-id="8bd1c-151"> [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md)</span></span>


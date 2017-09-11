---
title: 'Como: consultar um banco de dados usando LINQ (Visual Basic) | Documentos do Microsoft'
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
- query samples [LINQ]
- database querying [LINQ]
- queries [LINQ in Visual Basic], database querying
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: bcf5e9c3-a236-4399-9a7f-3991eca7cf56
caps.latest.revision: 12
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
ms.openlocfilehash: a645a71dd0489d6bf2cc0cd4fe5898eb7293f13c
ms.contentlocale: pt-br
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-query-a-database-by-using-linq-visual-basic"></a><span data-ttu-id="72b60-102">Como consultar um banco de dados usando LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72b60-102">How to: Query a Database by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="72b60-103">Consulta integrada à linguagem (LINQ) facilita o acesso às informações de banco de dados e executar consultas.</span><span class="sxs-lookup"><span data-stu-id="72b60-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="72b60-104">O exemplo a seguir mostra como criar um novo aplicativo que executa consultas em um banco de dados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="72b60-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span>  
  
 <span data-ttu-id="72b60-105">Os exemplos neste tópico usam o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="72b60-105">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="72b60-106">Se você não tiver o banco de dados de exemplo Northwind no seu computador de desenvolvimento, você pode baixá-lo do [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) site da Web.</span><span class="sxs-lookup"><span data-stu-id="72b60-106">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="72b60-107">Para obter instruções, consulte [baixando bancos de dados de exemplo](https://msdn.microsoft.com/library/bb399411).</span><span class="sxs-lookup"><span data-stu-id="72b60-107">For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/bb399411).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="72b60-108">Para criar uma conexão para um banco de dados</span><span class="sxs-lookup"><span data-stu-id="72b60-108">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="72b60-109">No Visual Studio, abra **Server Explorer**/**Database Explorer** clicando **Server Explorer**/**Database Explorer** sobre o **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="72b60-109">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="72b60-110">Clique com botão direito **conexões de dados** na **Server Explorer**/**Database Explorer** e, em seguida, clique em **Adicionar Conexão**.</span><span class="sxs-lookup"><span data-stu-id="72b60-110">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="72b60-111">Especifique uma conexão válida para o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="72b60-111">Specify a valid connection to the Northwind sample database.</span></span>  
  
## <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="72b60-112">Para adicionar um projeto que contém um arquivo LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="72b60-112">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="72b60-113">No Visual Studio, no **arquivo** , aponte para **novo** e, em seguida, clique em **projeto**.</span><span class="sxs-lookup"><span data-stu-id="72b60-113">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="72b60-114">Selecione Visual Basic **Windows Forms Application** como o tipo de projeto.</span><span class="sxs-lookup"><span data-stu-id="72b60-114">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="72b60-115">No menu **Projeto**, clique em **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="72b60-115">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="72b60-116">Selecione o **Classes LINQ to SQL** modelo de item.</span><span class="sxs-lookup"><span data-stu-id="72b60-116">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="72b60-117">Nomeie o arquivo `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="72b60-117">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="72b60-118">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="72b60-118">Click **Add**.</span></span> <span data-ttu-id="72b60-119">O Object Relational Designer (Object Relational Designer) é aberto para o arquivo Northwind dbml.</span><span class="sxs-lookup"><span data-stu-id="72b60-119">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
## <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="72b60-120">Para adicionar tabelas de consulta para o Object Relational Designer</span><span class="sxs-lookup"><span data-stu-id="72b60-120">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="72b60-121">Em **Server Explorer**/**Database Explorer**, expanda a conexão ao banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="72b60-121">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="72b60-122">Expanda o **tabelas** pasta.</span><span class="sxs-lookup"><span data-stu-id="72b60-122">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="72b60-123">Se você tiver fechado o Object Relational Designer, você poderá reabri-lo clicando no arquivo dbml que você adicionou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="72b60-123">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="72b60-124">Clique na tabela clientes e arraste-o para o painel esquerdo do designer.</span><span class="sxs-lookup"><span data-stu-id="72b60-124">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="72b60-125">Clique na tabela Orders e arraste-o para o painel esquerdo do designer.</span><span class="sxs-lookup"><span data-stu-id="72b60-125">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="72b60-126">O designer cria novos `Customer` e `Order` objetos para o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="72b60-126">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="72b60-127">Observe que o designer automaticamente detecta relacionamentos entre as tabelas e cria propriedades filhas para objetos relacionados.</span><span class="sxs-lookup"><span data-stu-id="72b60-127">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="72b60-128">Por exemplo, o IntelliSense mostrará que o `Customer` objeto tem um `Orders` propriedade para todos os pedidos relacionados a esse cliente.</span><span class="sxs-lookup"><span data-stu-id="72b60-128">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="72b60-129">Salve suas alterações e feche o designer.</span><span class="sxs-lookup"><span data-stu-id="72b60-129">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="72b60-130">Salve seu projeto.</span><span class="sxs-lookup"><span data-stu-id="72b60-130">Save your project.</span></span>  
  
## <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="72b60-131">Para adicionar código para consultar o banco de dados e exibir os resultados</span><span class="sxs-lookup"><span data-stu-id="72b60-131">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="72b60-132">Do **Toolbox**, arraste um <xref:System.Windows.Forms.DataGridView>controle para o Windows Form padrão para seu projeto, Form1.</xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="72b60-132">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="72b60-133">Clique duas vezes em Form1 para adicionar código para o `Load` eventos do formulário.</span><span class="sxs-lookup"><span data-stu-id="72b60-133">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="72b60-134">Quando você adicionar tabelas ao / R Designer, o designer adicionará um <xref:System.Data.Linq.DataContext>objeto para o seu projeto.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="72b60-134">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="72b60-135">Este objeto contém o código que você deve ter para acessar essas tabelas, além de objetos individuais e coleções para cada tabela.</span><span class="sxs-lookup"><span data-stu-id="72b60-135">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="72b60-136">O <xref:System.Data.Linq.DataContext>objeto para seu projeto é nomeado com base no nome do seu arquivo. dbml.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="72b60-136">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="72b60-137">Para este projeto, o <xref:System.Data.Linq.DataContext>objeto é denominado `northwindDataContext`.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="72b60-137">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="72b60-138">Você pode criar uma instância do <xref:System.Data.Linq.DataContext>no seu código e consultar as tabelas especificadas pelo / R Designer.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="72b60-138">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="72b60-139">Adicione o seguinte código para o `Load` eventos para consultar as tabelas que são expostas como propriedades de seu contexto de dados.</span><span class="sxs-lookup"><span data-stu-id="72b60-139">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context.</span></span>  
  
     <span data-ttu-id="72b60-140">[!code-vb[VbLINQToSQLHowTos n º&3;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-query-a-database-by-using-linq_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="72b60-140">[!code-vb[VbLINQToSQLHowTos#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-query-a-database-by-using-linq_1.vb)]</span></span>  
  
4.  <span data-ttu-id="72b60-141">Pressione F5 para executar seu projeto e exibir os resultados.</span><span class="sxs-lookup"><span data-stu-id="72b60-141">Press F5 to run your project and view the results.</span></span>  
  
5.  <span data-ttu-id="72b60-142">A seguir estão algumas consultas adicionais que você pode tentar:</span><span class="sxs-lookup"><span data-stu-id="72b60-142">Following are some additional queries that you can try:</span></span>  
  
     <span data-ttu-id="72b60-143">[!code-vb[VbLINQToSQLHowTos n º&4;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-query-a-database-by-using-linq_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="72b60-143">[!code-vb[VbLINQToSQLHowTos#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-query-a-database-by-using-linq_2.vb)]</span></span>  
    <span data-ttu-id="72b60-144">[!code-vb[VbLINQToSQLHowTos n º&5;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-query-a-database-by-using-linq_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="72b60-144">[!code-vb[VbLINQToSQLHowTos#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-query-a-database-by-using-linq_3.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72b60-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72b60-145">See Also</span></span>  
 <span data-ttu-id="72b60-146">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="72b60-146">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="72b60-147"> [Consultas](../../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="72b60-147"> [Queries](../../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="72b60-148"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span><span class="sxs-lookup"><span data-stu-id="72b60-148"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span></span>  
<span data-ttu-id="72b60-149"> [Métodos de DataContext (Object Relational Designer)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="72b60-149"> [DataContext Methods (O/R Designer)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)</span></span>


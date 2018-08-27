---
title: Como consultar um banco de dados usando LINQ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- query samples [LINQ]
- database querying [LINQ]
- queries [LINQ in Visual Basic], database querying
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: bcf5e9c3-a236-4399-9a7f-3991eca7cf56
ms.openlocfilehash: 75f3d71e76c81a016a4e2c6fac754b91db31873e
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2018
ms.locfileid: "42924871"
---
# <a name="how-to-query-a-database-by-using-linq-visual-basic"></a><span data-ttu-id="33fdd-102">Como consultar um banco de dados usando LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33fdd-102">How to: Query a Database by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="33fdd-103">Consulta integrada à linguagem (LINQ) facilita o acesso às informações de banco de dados e executar consultas.</span><span class="sxs-lookup"><span data-stu-id="33fdd-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="33fdd-104">O exemplo a seguir mostra como criar um novo aplicativo que executa consultas em um banco de dados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="33fdd-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span>  
  
 <span data-ttu-id="33fdd-105">Os exemplos neste tópico usam o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="33fdd-105">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="33fdd-106">Se você não tiver esse banco de dados no computador de desenvolvimento, você pode baixá-lo do Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="33fdd-106">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="33fdd-107">Para obter instruções, consulte [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="33fdd-107">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="33fdd-108">Para criar uma conexão para um banco de dados</span><span class="sxs-lookup"><span data-stu-id="33fdd-108">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="33fdd-109">No Visual Studio, abra **Gerenciador de servidores**/**Database Explorer** clicando **Server Explorer**/**banco de dados Explorer** sobre o **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="33fdd-109">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="33fdd-110">Clique com botão direito **conexões de dados** na **Gerenciador de servidores**/**Database Explorer** e, em seguida, clique em **Adicionar Conexão**.</span><span class="sxs-lookup"><span data-stu-id="33fdd-110">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="33fdd-111">Especifique uma conexão válida para o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="33fdd-111">Specify a valid connection to the Northwind sample database.</span></span>  
  
## <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="33fdd-112">Para adicionar um projeto que contém um arquivo LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="33fdd-112">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="33fdd-113">No Visual Studio, no menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="33fdd-113">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="33fdd-114">Selecione Visual Basic **aplicativo do Windows Forms** como o tipo de projeto.</span><span class="sxs-lookup"><span data-stu-id="33fdd-114">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="33fdd-115">No menu **Projeto**, clique em **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="33fdd-115">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="33fdd-116">Selecione o **Classes LINQ to SQL** modelo de item.</span><span class="sxs-lookup"><span data-stu-id="33fdd-116">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="33fdd-117">Dê o nome `northwind.dbml` para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="33fdd-117">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="33fdd-118">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="33fdd-118">Click **Add**.</span></span> <span data-ttu-id="33fdd-119">O Object Relational Designer (O/R Designer) é aberto para o arquivo Northwind dbml.</span><span class="sxs-lookup"><span data-stu-id="33fdd-119">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
## <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="33fdd-120">Para adicionar tabelas de consulta para o O/R Designer</span><span class="sxs-lookup"><span data-stu-id="33fdd-120">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="33fdd-121">Na **Gerenciador de servidores**/**Gerenciador de banco de dados**, expanda a conexão ao banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="33fdd-121">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="33fdd-122">Expanda o **tabelas** pasta.</span><span class="sxs-lookup"><span data-stu-id="33fdd-122">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="33fdd-123">Se você tiver fechado o O/R Designer, você poderá reabri-lo clicando duas vezes no arquivo dbml que você adicionou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="33fdd-123">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="33fdd-124">Clique na tabela clientes e arraste-o no painel esquerdo do designer.</span><span class="sxs-lookup"><span data-stu-id="33fdd-124">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="33fdd-125">Clique na tabela Orders e arraste-o no painel esquerdo do designer.</span><span class="sxs-lookup"><span data-stu-id="33fdd-125">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="33fdd-126">O designer cria novos `Customer` e `Order` objetos para o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="33fdd-126">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="33fdd-127">Observe que o designer automaticamente detecta as relações entre as tabelas e cria propriedades filhas para objetos relacionados.</span><span class="sxs-lookup"><span data-stu-id="33fdd-127">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="33fdd-128">Por exemplo, o IntelliSense mostrará que o `Customer` objeto tem um `Orders` propriedade para todos os pedidos relacionados a esse cliente.</span><span class="sxs-lookup"><span data-stu-id="33fdd-128">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="33fdd-129">Salve suas alterações e feche o designer.</span><span class="sxs-lookup"><span data-stu-id="33fdd-129">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="33fdd-130">Salve seu projeto.</span><span class="sxs-lookup"><span data-stu-id="33fdd-130">Save your project.</span></span>  
  
## <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="33fdd-131">Para adicionar código para consultar o banco de dados e exibir os resultados</span><span class="sxs-lookup"><span data-stu-id="33fdd-131">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="33fdd-132">Dos **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.DataGridView> controle para o formulário do Windows padrão para seu projeto, Form1.</span><span class="sxs-lookup"><span data-stu-id="33fdd-132">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="33fdd-133">Clique duas vezes em Form1 para adicionar código para o `Load` evento do formulário.</span><span class="sxs-lookup"><span data-stu-id="33fdd-133">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="33fdd-134">Quando você adicionar tabelas ao Designer relacional de objetos, o designer adicionará um <xref:System.Data.Linq.DataContext> objeto para o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="33fdd-134">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="33fdd-135">Este objeto contém o código que você deve ter para acessar essas tabelas, além de objetos individuais e coleções para cada tabela.</span><span class="sxs-lookup"><span data-stu-id="33fdd-135">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="33fdd-136">O <xref:System.Data.Linq.DataContext> objeto para seu projeto é nomeado com base no nome do seu arquivo. dbml.</span><span class="sxs-lookup"><span data-stu-id="33fdd-136">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="33fdd-137">Para este projeto, o <xref:System.Data.Linq.DataContext> objeto é nomeado `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="33fdd-137">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="33fdd-138">Você pode criar uma instância da <xref:System.Data.Linq.DataContext> no seu código e consultar as tabelas especificadas pelo Designer relacional de objetos.</span><span class="sxs-lookup"><span data-stu-id="33fdd-138">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="33fdd-139">Adicione o seguinte código para o `Load` eventos para consultar as tabelas que são expostas como propriedades de seu contexto de dados.</span><span class="sxs-lookup"><span data-stu-id="33fdd-139">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-query-a-database-by-using-linq_1.vb)]  
  
4.  <span data-ttu-id="33fdd-140">Pressione F5 para executar seu projeto e exibir os resultados.</span><span class="sxs-lookup"><span data-stu-id="33fdd-140">Press F5 to run your project and view the results.</span></span>  
  
5.  <span data-ttu-id="33fdd-141">A seguir estão algumas consultas adicionais que você pode tentar:</span><span class="sxs-lookup"><span data-stu-id="33fdd-141">Following are some additional queries that you can try:</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-query-a-database-by-using-linq_2.vb)]  
    [!code-vb[VbLINQToSQLHowTos#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-query-a-database-by-using-linq_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="33fdd-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33fdd-142">See Also</span></span>  
 [<span data-ttu-id="33fdd-143">LINQ</span><span class="sxs-lookup"><span data-stu-id="33fdd-143">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="33fdd-144">Consultas</span><span class="sxs-lookup"><span data-stu-id="33fdd-144">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)  
 [<span data-ttu-id="33fdd-145">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="33fdd-145">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="33fdd-146">Métodos DataContext (Designer Relacional de Objetos)</span><span class="sxs-lookup"><span data-stu-id="33fdd-146">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)

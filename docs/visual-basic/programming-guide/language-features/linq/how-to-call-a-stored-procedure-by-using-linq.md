---
title: Como chamar um procedimento armazenado usando LINQ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
ms.openlocfilehash: 50a4dff90dc1ce02869978f1da147e530cefc3e1
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47079734"
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a><span data-ttu-id="3ce95-102">Como chamar um procedimento armazenado usando LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ce95-102">How to: Call a Stored Procedure by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="3ce95-103">Consulta integrada à linguagem (LINQ) facilita o acesso a informações de banco de dados, incluindo o banco de dados objetos como procedimentos armazenados.</span><span class="sxs-lookup"><span data-stu-id="3ce95-103">Language-Integrated Query (LINQ) makes it easy to access database information, including database objects such as stored procedures.</span></span>  
  
 <span data-ttu-id="3ce95-104">O exemplo a seguir mostra como criar um aplicativo que chama um procedimento armazenado em um banco de dados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3ce95-104">The following example shows how to create an application that calls a stored procedure in a SQL Server database.</span></span> <span data-ttu-id="3ce95-105">O exemplo mostra como chamar dois diferentes procedimentos armazenados no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="3ce95-105">The sample shows how to call two different stored procedures in the database.</span></span> <span data-ttu-id="3ce95-106">Cada procedimento retorna os resultados de uma consulta.</span><span class="sxs-lookup"><span data-stu-id="3ce95-106">Each procedure returns the results of a query.</span></span> <span data-ttu-id="3ce95-107">Um procedimento utiliza parâmetros de entrada e o outro procedimento não aceita parâmetros.</span><span class="sxs-lookup"><span data-stu-id="3ce95-107">One procedure takes input parameters, and the other procedure does not take parameters.</span></span>  
  
 <span data-ttu-id="3ce95-108">Os exemplos neste tópico usam o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="3ce95-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="3ce95-109">Se você não tiver esse banco de dados no computador de desenvolvimento, você pode baixá-lo do Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="3ce95-109">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="3ce95-110">Para obter instruções, consulte [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="3ce95-110">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="3ce95-111">Para criar uma conexão para um banco de dados</span><span class="sxs-lookup"><span data-stu-id="3ce95-111">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="3ce95-112">No Visual Studio, abra **Gerenciador de servidores**/**Database Explorer** clicando **Server Explorer**/**banco de dados Explorer** sobre o **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="3ce95-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="3ce95-113">Clique com botão direito **conexões de dados** na **Gerenciador de servidores**/**Database Explorer** e, em seguida, clique em **Adicionar Conexão**.</span><span class="sxs-lookup"><span data-stu-id="3ce95-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="3ce95-114">Especifique uma conexão válida para o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="3ce95-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="3ce95-115">Para adicionar um projeto que contém um arquivo LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="3ce95-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="3ce95-116">No Visual Studio, no menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="3ce95-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="3ce95-117">Selecione Visual Basic **aplicativo do Windows Forms** como o tipo de projeto.</span><span class="sxs-lookup"><span data-stu-id="3ce95-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="3ce95-118">No menu **Projeto**, clique em **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="3ce95-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="3ce95-119">Selecione o **Classes LINQ to SQL** modelo de item.</span><span class="sxs-lookup"><span data-stu-id="3ce95-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="3ce95-120">Dê o nome `northwind.dbml` para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="3ce95-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="3ce95-121">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="3ce95-121">Click **Add**.</span></span> <span data-ttu-id="3ce95-122">O Object Relational Designer (O/R Designer) é aberto para o arquivo Northwind dbml.</span><span class="sxs-lookup"><span data-stu-id="3ce95-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a><span data-ttu-id="3ce95-123">Para adicionar os procedimentos armazenados para o O/R Designer</span><span class="sxs-lookup"><span data-stu-id="3ce95-123">To add stored procedures to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="3ce95-124">Na **Gerenciador de servidores**/**Gerenciador de banco de dados**, expanda a conexão ao banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="3ce95-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="3ce95-125">Expanda o **procedimentos armazenados** pasta.</span><span class="sxs-lookup"><span data-stu-id="3ce95-125">Expand the **Stored Procedures** folder.</span></span>  
  
     <span data-ttu-id="3ce95-126">Se você tiver fechado o O/R Designer, você poderá reabri-lo clicando duas vezes no arquivo dbml que você adicionou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="3ce95-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="3ce95-127">Clique o **vendas por ano** procedimento armazenado e arraste-o para o painel à direita do designer.</span><span class="sxs-lookup"><span data-stu-id="3ce95-127">Click the **Sales by Year** stored procedure and drag it to the right pane of the designer.</span></span> <span data-ttu-id="3ce95-128">Clique o **dez produtos mais caros** procedimento armazenado arraste-o para o painel à direita do designer.</span><span class="sxs-lookup"><span data-stu-id="3ce95-128">Click the **Ten Most Expensive Products** stored procedure drag it to the right pane of the designer.</span></span>  
  
3.  <span data-ttu-id="3ce95-129">Salve suas alterações e feche o designer.</span><span class="sxs-lookup"><span data-stu-id="3ce95-129">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="3ce95-130">Salve seu projeto.</span><span class="sxs-lookup"><span data-stu-id="3ce95-130">Save your project.</span></span>  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a><span data-ttu-id="3ce95-131">Para adicionar código para exibir os resultados dos procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="3ce95-131">To add code to display the results of the stored procedures</span></span>  
  
1.  <span data-ttu-id="3ce95-132">Dos **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.DataGridView> controle para o formulário do Windows padrão para seu projeto, Form1.</span><span class="sxs-lookup"><span data-stu-id="3ce95-132">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="3ce95-133">Clique duas vezes em Form1 para adicionar código ao seu `Load` eventos.</span><span class="sxs-lookup"><span data-stu-id="3ce95-133">Double-click Form1 to add code to its `Load` event.</span></span>  
  
3.  <span data-ttu-id="3ce95-134">Quando você adicionou os procedimentos armazenados para o Designer relacional de objetos, o designer adicionará um <xref:System.Data.Linq.DataContext> objeto para o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="3ce95-134">When you added stored procedures to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="3ce95-135">Este objeto contém o código que você deve ter para acessar esses procedimentos.</span><span class="sxs-lookup"><span data-stu-id="3ce95-135">This object contains the code that you must have to access those procedures.</span></span> <span data-ttu-id="3ce95-136">O <xref:System.Data.Linq.DataContext> objeto para o projeto é nomeado com base no nome do arquivo. dbml.</span><span class="sxs-lookup"><span data-stu-id="3ce95-136">The <xref:System.Data.Linq.DataContext> object for the project is named based on the name of the .dbml file.</span></span> <span data-ttu-id="3ce95-137">Para este projeto, o <xref:System.Data.Linq.DataContext> objeto é nomeado `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="3ce95-137">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="3ce95-138">Você pode criar uma instância da <xref:System.Data.Linq.DataContext> no seu código e chamar os métodos de procedimento armazenado especificado pelo Designer relacional de objetos.</span><span class="sxs-lookup"><span data-stu-id="3ce95-138">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and call the stored procedure methods specified by the O/R Designer.</span></span> <span data-ttu-id="3ce95-139">Para associar à <xref:System.Windows.Forms.DataGridView> do objeto, você pode ter que forçar a consulta seja executada imediatamente, chamando o <xref:System.Linq.Enumerable.ToList%2A> método nos resultados do procedimento armazenado.</span><span class="sxs-lookup"><span data-stu-id="3ce95-139">To bind to the <xref:System.Windows.Forms.DataGridView> object, you may have to force the query to execute immediately by calling the <xref:System.Linq.Enumerable.ToList%2A> method on the results of the stored procedure.</span></span>  
  
     <span data-ttu-id="3ce95-140">Adicione o seguinte código para o `Load` eventos para chamar um dos procedimentos armazenados expostos como métodos para o contexto de dados.</span><span class="sxs-lookup"><span data-stu-id="3ce95-140">Add the following code to the `Load` event to call either of the stored procedures exposed as methods for your data context.</span></span>  
  
     [!code-vb[VbLINQtoSQLHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_1.vb)]  
    [!code-vb[VbLINQtoSQLHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_2.vb)]  
  
4.  <span data-ttu-id="3ce95-141">Pressione F5 para executar seu projeto e exibir os resultados.</span><span class="sxs-lookup"><span data-stu-id="3ce95-141">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ce95-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ce95-142">See Also</span></span>  
 [<span data-ttu-id="3ce95-143">LINQ</span><span class="sxs-lookup"><span data-stu-id="3ce95-143">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="3ce95-144">Consultas</span><span class="sxs-lookup"><span data-stu-id="3ce95-144">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)  
 [<span data-ttu-id="3ce95-145">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="3ce95-145">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="3ce95-146">Métodos DataContext (Designer Relacional de Objetos)</span><span class="sxs-lookup"><span data-stu-id="3ce95-146">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [<span data-ttu-id="3ce95-147">Como atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Designer Relacional de Objetos)</span><span class="sxs-lookup"><span data-stu-id="3ce95-147">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](https://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)

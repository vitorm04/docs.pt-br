---
title: 'Como: chamar um procedimento armazenado usando LINQ (Visual Basic) | Documentos do Microsoft'
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
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
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
ms.openlocfilehash: 40e72ece8399b1ffbe8c5457c63113d563c9f7f8
ms.contentlocale: pt-br
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a><span data-ttu-id="0b591-102">Como chamar um procedimento armazenado usando LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b591-102">How to: Call a Stored Procedure by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="0b591-103">Consulta integrada à linguagem (LINQ) facilita o acesso a informações do banco de dados, incluindo o banco de dados objetos como procedimentos armazenados.</span><span class="sxs-lookup"><span data-stu-id="0b591-103">Language-Integrated Query (LINQ) makes it easy to access database information, including database objects such as stored procedures.</span></span>  
  
 <span data-ttu-id="0b591-104">O exemplo a seguir mostra como criar um aplicativo que chama um procedimento armazenado em um banco de dados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0b591-104">The following example shows how to create an application that calls a stored procedure in a SQL Server database.</span></span> <span data-ttu-id="0b591-105">O exemplo mostra como chamar dois procedimentos diferentes armazenados no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="0b591-105">The sample shows how to call two different stored procedures in the database.</span></span> <span data-ttu-id="0b591-106">Cada procedimento retorna os resultados de uma consulta.</span><span class="sxs-lookup"><span data-stu-id="0b591-106">Each procedure returns the results of a query.</span></span> <span data-ttu-id="0b591-107">Um procedimento utiliza parâmetros de entrada e o outro procedimento não aceita parâmetros.</span><span class="sxs-lookup"><span data-stu-id="0b591-107">One procedure takes input parameters, and the other procedure does not take parameters.</span></span>  
  
 <span data-ttu-id="0b591-108">Os exemplos neste tópico usam o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="0b591-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="0b591-109">Se você não tiver o banco de dados de exemplo Northwind no seu computador de desenvolvimento, você pode baixá-lo do [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) site da Web.</span><span class="sxs-lookup"><span data-stu-id="0b591-109">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="0b591-110">Para obter instruções, consulte [baixando bancos de dados de exemplo](https://msdn.microsoft.com/library/bb399411).</span><span class="sxs-lookup"><span data-stu-id="0b591-110">For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/bb399411).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="0b591-111">Para criar uma conexão para um banco de dados</span><span class="sxs-lookup"><span data-stu-id="0b591-111">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="0b591-112">No Visual Studio, abra **Server Explorer**/**Database Explorer** clicando **Server Explorer**/**Database Explorer** sobre o **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="0b591-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="0b591-113">Clique com botão direito **conexões de dados** na **Server Explorer**/**Database Explorer** e, em seguida, clique em **Adicionar Conexão**.</span><span class="sxs-lookup"><span data-stu-id="0b591-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="0b591-114">Especifique uma conexão válida para o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="0b591-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="0b591-115">Para adicionar um projeto que contém um arquivo LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="0b591-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="0b591-116">No Visual Studio, no **arquivo** , aponte para **novo** e, em seguida, clique em **projeto**.</span><span class="sxs-lookup"><span data-stu-id="0b591-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="0b591-117">Selecione Visual Basic **Windows Forms Application** como o tipo de projeto.</span><span class="sxs-lookup"><span data-stu-id="0b591-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="0b591-118">No menu **Projeto**, clique em **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="0b591-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="0b591-119">Selecione o **Classes LINQ to SQL** modelo de item.</span><span class="sxs-lookup"><span data-stu-id="0b591-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="0b591-120">Nomeie o arquivo `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="0b591-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="0b591-121">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="0b591-121">Click **Add**.</span></span> <span data-ttu-id="0b591-122">O Object Relational Designer (Object Relational Designer) é aberto para o arquivo Northwind dbml.</span><span class="sxs-lookup"><span data-stu-id="0b591-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a><span data-ttu-id="0b591-123">Adicionar procedimentos armazenados para o Object Relational Designer</span><span class="sxs-lookup"><span data-stu-id="0b591-123">To add stored procedures to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="0b591-124">Em **Server Explorer**/**Database Explorer**, expanda a conexão ao banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="0b591-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="0b591-125">Expanda o **procedimentos armazenados** pasta.</span><span class="sxs-lookup"><span data-stu-id="0b591-125">Expand the **Stored Procedures** folder.</span></span>  
  
     <span data-ttu-id="0b591-126">Se você tiver fechado o Object Relational Designer, você poderá reabri-lo clicando no arquivo dbml que você adicionou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0b591-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="0b591-127">Clique o **Sales by Year** procedimento armazenado e arraste-o para o painel à direita do designer.</span><span class="sxs-lookup"><span data-stu-id="0b591-127">Click the **Sales by Year** stored procedure and drag it to the right pane of the designer.</span></span> <span data-ttu-id="0b591-128">Clique o **dez produtos mais caros** procedimento armazenado arraste-o para o painel à direita do designer.</span><span class="sxs-lookup"><span data-stu-id="0b591-128">Click the **Ten Most Expensive Products** stored procedure drag it to the right pane of the designer.</span></span>  
  
3.  <span data-ttu-id="0b591-129">Salve suas alterações e feche o designer.</span><span class="sxs-lookup"><span data-stu-id="0b591-129">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="0b591-130">Salve seu projeto.</span><span class="sxs-lookup"><span data-stu-id="0b591-130">Save your project.</span></span>  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a><span data-ttu-id="0b591-131">Para adicionar código para exibir os resultados dos procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="0b591-131">To add code to display the results of the stored procedures</span></span>  
  
1.  <span data-ttu-id="0b591-132">Do **Toolbox**, arraste um <xref:System.Windows.Forms.DataGridView>controle para o Windows Form padrão para seu projeto, Form1.</xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="0b591-132">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="0b591-133">Clique duas vezes em Form1 para adicionar código ao seu `Load` eventos.</span><span class="sxs-lookup"><span data-stu-id="0b591-133">Double-click Form1 to add code to its `Load` event.</span></span>  
  
3.  <span data-ttu-id="0b591-134">Quando você adicionou procedimentos armazenados ao / R Designer, o designer adicionará um <xref:System.Data.Linq.DataContext>objeto para o seu projeto.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="0b591-134">When you added stored procedures to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="0b591-135">Este objeto contém o código que você deve ter para acessar esses procedimentos.</span><span class="sxs-lookup"><span data-stu-id="0b591-135">This object contains the code that you must have to access those procedures.</span></span> <span data-ttu-id="0b591-136">O <xref:System.Data.Linq.DataContext>objeto para o projeto é nomeado com base no nome do arquivo. dbml.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="0b591-136">The <xref:System.Data.Linq.DataContext> object for the project is named based on the name of the .dbml file.</span></span> <span data-ttu-id="0b591-137">Para este projeto, o <xref:System.Data.Linq.DataContext>objeto é denominado `northwindDataContext`.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="0b591-137">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="0b591-138">Você pode criar uma instância do <xref:System.Data.Linq.DataContext>em seu código e chamar os métodos de procedimento armazenado especificado por Object Relational Designer.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="0b591-138">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and call the stored procedure methods specified by the O/R Designer.</span></span> <span data-ttu-id="0b591-139">Ligar para o <xref:System.Windows.Forms.DataGridView>do objeto, talvez você precise forçar a consulta seja executada imediatamente chamando o <xref:System.Linq.Enumerable.ToList%2A>método nos resultados do procedimento armazenado.</xref:System.Linq.Enumerable.ToList%2A> </xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="0b591-139">To bind to the <xref:System.Windows.Forms.DataGridView> object, you may have to force the query to execute immediately by calling the <xref:System.Linq.Enumerable.ToList%2A> method on the results of the stored procedure.</span></span>  
  
     <span data-ttu-id="0b591-140">Adicione o seguinte código para o `Load` eventos para chamar um dos procedimentos armazenados expostos como métodos para o contexto de dados.</span><span class="sxs-lookup"><span data-stu-id="0b591-140">Add the following code to the `Load` event to call either of the stored procedures exposed as methods for your data context.</span></span>  
  
     <span data-ttu-id="0b591-141">[!code-vb[VbLINQtoSQLHowTos n º&1;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="0b591-141">[!code-vb[VbLINQtoSQLHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_1.vb)]</span></span>  
    <span data-ttu-id="0b591-142">[!code-vb[VbLINQtoSQLHowTos n º&2;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="0b591-142">[!code-vb[VbLINQtoSQLHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_2.vb)]</span></span>  
  
4.  <span data-ttu-id="0b591-143">Pressione F5 para executar seu projeto e exibir os resultados.</span><span class="sxs-lookup"><span data-stu-id="0b591-143">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b591-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0b591-144">See Also</span></span>  
 <span data-ttu-id="0b591-145">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="0b591-145">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="0b591-146"> [Consultas](../../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="0b591-146"> [Queries](../../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="0b591-147"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span><span class="sxs-lookup"><span data-stu-id="0b591-147"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span></span>  
<span data-ttu-id="0b591-148"> [Métodos de DataContext (Object Relational Designer)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer) </span><span class="sxs-lookup"><span data-stu-id="0b591-148"> [DataContext Methods (O/R Designer)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer) </span></span>  
<span data-ttu-id="0b591-149"> [Como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Object Relational Designer)](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)</span><span class="sxs-lookup"><span data-stu-id="0b591-149"> [How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)</span></span>


---
title: 'Como: chamar um procedimento armazenado usando o LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
ms.openlocfilehash: f91ccda1842887b3785ce304fd41bdd020a55479
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345022"
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a><span data-ttu-id="2ada1-102">Como chamar um procedimento armazenado usando LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ada1-102">How to: Call a Stored Procedure by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="2ada1-103">A consulta integrada à linguagem (LINQ) facilita o acesso a informações do banco de dados, incluindo objetos de banco de dados, como procedimentos armazenados.</span><span class="sxs-lookup"><span data-stu-id="2ada1-103">Language-Integrated Query (LINQ) makes it easy to access database information, including database objects such as stored procedures.</span></span>  
  
 <span data-ttu-id="2ada1-104">O exemplo a seguir mostra como criar um aplicativo que chama um procedimento armazenado em um banco de dados SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2ada1-104">The following example shows how to create an application that calls a stored procedure in a SQL Server database.</span></span> <span data-ttu-id="2ada1-105">O exemplo mostra como chamar dois procedimentos armazenados diferentes no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="2ada1-105">The sample shows how to call two different stored procedures in the database.</span></span> <span data-ttu-id="2ada1-106">Cada procedimento retorna os resultados de uma consulta.</span><span class="sxs-lookup"><span data-stu-id="2ada1-106">Each procedure returns the results of a query.</span></span> <span data-ttu-id="2ada1-107">Um procedimento usa parâmetros de entrada e o outro procedimento não usa parâmetros.</span><span class="sxs-lookup"><span data-stu-id="2ada1-107">One procedure takes input parameters, and the other procedure does not take parameters.</span></span>  
  
 <span data-ttu-id="2ada1-108">Os exemplos neste tópico usam o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="2ada1-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="2ada1-109">Caso não tenha esse banco de dados no seu computador de desenvolvimento, você poderá baixá-lo no Centro de Download da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2ada1-109">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="2ada1-110">Para obter instruções, consulte [baixar bancos de dados de exemplo](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="2ada1-110">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="2ada1-111">Para criar uma conexão com um banco de dados</span><span class="sxs-lookup"><span data-stu-id="2ada1-111">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="2ada1-112">No Visual Studio, abra **Gerenciador de Servidores**/**Gerenciador de Banco de Dados** clicando em **Gerenciador de servidores**/**Gerenciador de banco de dados** no menu **Exibir** .</span><span class="sxs-lookup"><span data-stu-id="2ada1-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="2ada1-113">Clique com o botão direito do mouse em **conexões de dados** no **Gerenciador de servidores**/**Gerenciador de banco de dados** e clique em **Adicionar conexão**.</span><span class="sxs-lookup"><span data-stu-id="2ada1-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="2ada1-114">Especifique uma conexão válida para o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="2ada1-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="2ada1-115">Para adicionar um projeto que contém um arquivo de LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="2ada1-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="2ada1-116">No Visual Studio, no menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="2ada1-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="2ada1-117">Selecione Visual Basic **aplicativo Windows Forms** como o tipo de projeto.</span><span class="sxs-lookup"><span data-stu-id="2ada1-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="2ada1-118">No menu **Projeto**, clique em **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="2ada1-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="2ada1-119">Selecione o modelo de item **classes de LINQ to SQL** .</span><span class="sxs-lookup"><span data-stu-id="2ada1-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="2ada1-120">Dê o nome `northwind.dbml` para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="2ada1-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="2ada1-121">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="2ada1-121">Click **Add**.</span></span> <span data-ttu-id="2ada1-122">O Object Relational Designer (O/R Designer) é aberto para o arquivo Northwind. dbml.</span><span class="sxs-lookup"><span data-stu-id="2ada1-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a><span data-ttu-id="2ada1-123">Para adicionar procedimentos armazenados ao o/R Designer</span><span class="sxs-lookup"><span data-stu-id="2ada1-123">To add stored procedures to the O/R Designer</span></span>  
  
1. <span data-ttu-id="2ada1-124">Em **Gerenciador de Servidores**/**Gerenciador de banco de dados**, expanda a conexão com o banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="2ada1-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="2ada1-125">Expanda a pasta **procedimentos armazenados** .</span><span class="sxs-lookup"><span data-stu-id="2ada1-125">Expand the **Stored Procedures** folder.</span></span>  
  
     <span data-ttu-id="2ada1-126">Se você fechou o o/R Designer, você pode reabri-lo clicando duas vezes no arquivo Northwind. dbml que você adicionou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="2ada1-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="2ada1-127">Clique no procedimento armazenado **vendas por ano** e arraste-o para o painel direito do designer.</span><span class="sxs-lookup"><span data-stu-id="2ada1-127">Click the **Sales by Year** stored procedure and drag it to the right pane of the designer.</span></span> <span data-ttu-id="2ada1-128">Clique no procedimento armazenado **dez produtos mais caros** arraste-o para o painel direito do designer.</span><span class="sxs-lookup"><span data-stu-id="2ada1-128">Click the **Ten Most Expensive Products** stored procedure drag it to the right pane of the designer.</span></span>  
  
3. <span data-ttu-id="2ada1-129">Salve as alterações e feche o designer.</span><span class="sxs-lookup"><span data-stu-id="2ada1-129">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="2ada1-130">Salve seu projeto.</span><span class="sxs-lookup"><span data-stu-id="2ada1-130">Save your project.</span></span>  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a><span data-ttu-id="2ada1-131">Para adicionar código para exibir os resultados dos procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="2ada1-131">To add code to display the results of the stored procedures</span></span>  
  
1. <span data-ttu-id="2ada1-132">Na **caixa de ferramentas**, arraste um controle de <xref:System.Windows.Forms.DataGridView> para o formulário padrão do Windows para seu projeto, Form1.</span><span class="sxs-lookup"><span data-stu-id="2ada1-132">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="2ada1-133">Clique duas vezes em Form1 para adicionar código ao seu evento de `Load`.</span><span class="sxs-lookup"><span data-stu-id="2ada1-133">Double-click Form1 to add code to its `Load` event.</span></span>  
  
3. <span data-ttu-id="2ada1-134">Quando você adicionou procedimentos armazenados ao o/R Designer, o designer adicionou um objeto de <xref:System.Data.Linq.DataContext> para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="2ada1-134">When you added stored procedures to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="2ada1-135">Esse objeto contém o código que você deve ter para acessar esses procedimentos.</span><span class="sxs-lookup"><span data-stu-id="2ada1-135">This object contains the code that you must have to access those procedures.</span></span> <span data-ttu-id="2ada1-136">O objeto <xref:System.Data.Linq.DataContext> para o projeto é nomeado com base no nome do arquivo. dbml.</span><span class="sxs-lookup"><span data-stu-id="2ada1-136">The <xref:System.Data.Linq.DataContext> object for the project is named based on the name of the .dbml file.</span></span> <span data-ttu-id="2ada1-137">Para este projeto, o objeto <xref:System.Data.Linq.DataContext> é nomeado `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="2ada1-137">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="2ada1-138">Você pode criar uma instância do <xref:System.Data.Linq.DataContext> em seu código e chamar os métodos de procedimento armazenado especificados pelo o/R Designer.</span><span class="sxs-lookup"><span data-stu-id="2ada1-138">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and call the stored procedure methods specified by the O/R Designer.</span></span> <span data-ttu-id="2ada1-139">Para associar ao objeto <xref:System.Windows.Forms.DataGridView>, talvez seja necessário forçar a execução imediata da consulta chamando o método <xref:System.Linq.Enumerable.ToList%2A> nos resultados do procedimento armazenado.</span><span class="sxs-lookup"><span data-stu-id="2ada1-139">To bind to the <xref:System.Windows.Forms.DataGridView> object, you may have to force the query to execute immediately by calling the <xref:System.Linq.Enumerable.ToList%2A> method on the results of the stored procedure.</span></span>  
  
     <span data-ttu-id="2ada1-140">Adicione o seguinte código ao evento `Load` para chamar qualquer um dos procedimentos armazenados expostos como métodos para seu contexto de dados.</span><span class="sxs-lookup"><span data-stu-id="2ada1-140">Add the following code to the `Load` event to call either of the stored procedures exposed as methods for your data context.</span></span>  
  
     [!code-vb[VbLINQtoSQLHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#1)]  
    [!code-vb[VbLINQtoSQLHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#2)]  
  
4. <span data-ttu-id="2ada1-141">Pressione F5 para executar o projeto e exibir os resultados.</span><span class="sxs-lookup"><span data-stu-id="2ada1-141">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ada1-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ada1-142">See also</span></span>

- [<span data-ttu-id="2ada1-143">LINQ</span><span class="sxs-lookup"><span data-stu-id="2ada1-143">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="2ada1-144">Consultas</span><span class="sxs-lookup"><span data-stu-id="2ada1-144">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="2ada1-145">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="2ada1-145">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="2ada1-146">Métodos DataContext (Designer Relacional de Objetos)</span><span class="sxs-lookup"><span data-stu-id="2ada1-146">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="2ada1-147">Como atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Designer Relacional de Objetos)</span><span class="sxs-lookup"><span data-stu-id="2ada1-147">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)

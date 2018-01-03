---
title: Como modificar dados em um banco de dados usando LINQ (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- inserting rows [LINQ to SQL]
- deleting rows [LINQ to SQL]
- updating rows [LINQ to SQL]
- inserting data [Visual Basic]
- deleting data
- data [Visual Basic], updating
- updating data [LINQ]
- queries [LINQ in Visual Basic], data changes in database
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: cf52635f-0c1b-46c3-aff1-bdf181cf19b1
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 66f21b2a47d3890875062bbdf45e1c4507e1d603
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a><span data-ttu-id="66c58-102">Como modificar dados em um banco de dados usando LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66c58-102">How to: Modify Data in a Database by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="66c58-103">Consultas integradas à linguagem de consulta (LINQ) tornam mais fácil acessar as informações do banco de dados e modificar valores no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="66c58-103">Language-Integrated Query (LINQ) queries make it easy to access database information and modify values in the database.</span></span>  
  
 <span data-ttu-id="66c58-104">O exemplo a seguir mostra como criar um novo aplicativo que recupera e atualiza as informações em um banco de dados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="66c58-104">The following example shows how to create a new application that retrieves and updates information in a SQL Server database.</span></span>  
  
 <span data-ttu-id="66c58-105">Os exemplos neste tópico usam o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="66c58-105">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="66c58-106">Se você não tiver o banco de dados de exemplo Northwind no computador de desenvolvimento, você pode baixá-lo do [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) site da Web.</span><span class="sxs-lookup"><span data-stu-id="66c58-106">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="66c58-107">Para obter instruções, consulte [baixando bancos de dados de exemplo](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="66c58-107">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="66c58-108">Para criar uma conexão para um banco de dados</span><span class="sxs-lookup"><span data-stu-id="66c58-108">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="66c58-109">No Visual Studio, abra **Server Explorer**/**Pesquisador de objetos de banco de dados** clicando o **exibição** menu e, em seguida, selecione **doGerenciadordeservidores** / **Pesquisador de objetos de banco de dados**.</span><span class="sxs-lookup"><span data-stu-id="66c58-109">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking the **View** menu, and then select **Server Explorer**/**Database Explorer**.</span></span>  
  
2.  <span data-ttu-id="66c58-110">Clique com botão direito **conexões de dados** na **Server Explorer**/**Pesquisador de objetos de banco de dados**e clique em **Adicionar Conexão**.</span><span class="sxs-lookup"><span data-stu-id="66c58-110">Right-click **Data Connections** in **Server Explorer**/**Database Explorer**, and click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="66c58-111">Especifique uma conexão válida para o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="66c58-111">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-with-a-linq-to-sql-file"></a><span data-ttu-id="66c58-112">Para adicionar um projeto com uma LINQ ao arquivo SQL</span><span class="sxs-lookup"><span data-stu-id="66c58-112">To add a Project with a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="66c58-113">No Visual Studio, no menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="66c58-113">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="66c58-114">Selecione Visual Basic **aplicativo do Windows Forms** como o tipo de projeto.</span><span class="sxs-lookup"><span data-stu-id="66c58-114">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="66c58-115">No menu **Projeto**, clique em **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="66c58-115">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="66c58-116">Selecione o **Classes LINQ to SQL** modelo de item.</span><span class="sxs-lookup"><span data-stu-id="66c58-116">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="66c58-117">Dê o nome `northwind.dbml` para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="66c58-117">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="66c58-118">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="66c58-118">Click **Add**.</span></span> <span data-ttu-id="66c58-119">O Object Relational Designer (O/R Designer) é aberto para o `northwind.dbml` arquivo.</span><span class="sxs-lookup"><span data-stu-id="66c58-119">The Object Relational Designer (O/R Designer) is opened for the `northwind.dbml` file.</span></span>  
  
### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a><span data-ttu-id="66c58-120">Para adicionar tabelas para consultar e modificar para o designer</span><span class="sxs-lookup"><span data-stu-id="66c58-120">To add tables to query and modify to the designer</span></span>  
  
1.  <span data-ttu-id="66c58-121">Em **Server Explorer**/**Pesquisador de objetos de banco de dados**, expanda a conexão ao banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="66c58-121">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="66c58-122">Expanda o **tabelas** pasta.</span><span class="sxs-lookup"><span data-stu-id="66c58-122">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="66c58-123">Se você fechou o Object Relational Designer, você poderá reabri-la clicando duas vezes o `northwind.dbml` arquivo que você adicionou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="66c58-123">If you have closed the O/R Designer, you can reopen it by double-clicking the `northwind.dbml` file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="66c58-124">Clique na tabela clientes e arraste-o no painel esquerdo do designer.</span><span class="sxs-lookup"><span data-stu-id="66c58-124">Click the Customers table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="66c58-125">O designer cria um novo objeto de cliente para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="66c58-125">The designer creates a new Customer object for your project.</span></span>  
  
3.  <span data-ttu-id="66c58-126">Salve suas alterações e fechar o designer.</span><span class="sxs-lookup"><span data-stu-id="66c58-126">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="66c58-127">Salve seu projeto.</span><span class="sxs-lookup"><span data-stu-id="66c58-127">Save your project.</span></span>  
  
### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a><span data-ttu-id="66c58-128">Para adicionar código para modificar o banco de dados e exibir os resultados</span><span class="sxs-lookup"><span data-stu-id="66c58-128">To add code to modify the database and display the results</span></span>  
  
1.  <span data-ttu-id="66c58-129">Do **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.DataGridView> controle para o Windows Form padrão para seu projeto, Form1.</span><span class="sxs-lookup"><span data-stu-id="66c58-129">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="66c58-130">Quando você adicionar tabelas ao / R Designer, o designer adicionará um <xref:System.Data.Linq.DataContext> objeto ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="66c58-130">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="66c58-131">Este objeto contém o código que você pode usar para acessar a tabela de clientes.</span><span class="sxs-lookup"><span data-stu-id="66c58-131">This object contains code that you can use to access the Customers table.</span></span> <span data-ttu-id="66c58-132">Ele também contém o código que define um objeto de cliente local e uma coleção de clientes para a tabela.</span><span class="sxs-lookup"><span data-stu-id="66c58-132">It also contains code that defines  a local Customer object and a Customers collection for the table.</span></span> <span data-ttu-id="66c58-133">O <xref:System.Data.Linq.DataContext> objeto para seu projeto é nomeado com base no nome do seu arquivo dbml.</span><span class="sxs-lookup"><span data-stu-id="66c58-133">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="66c58-134">Para este projeto, o <xref:System.Data.Linq.DataContext> objeto é nomeado `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="66c58-134">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="66c58-135">Você pode criar uma instância do <xref:System.Data.Linq.DataContext> do objeto no seu código e consultar e modificar a coleção de clientes especificada por Object Relational Designer.</span><span class="sxs-lookup"><span data-stu-id="66c58-135">You can create an instance of the <xref:System.Data.Linq.DataContext> object in your code and query and modify the Customers collection specified by the O/R Designer.</span></span> <span data-ttu-id="66c58-136">As alterações feitas na coleção de clientes não são refletidas no banco de dados até que você os enviar ao chamar o <xref:System.Data.Linq.DataContext.SubmitChanges%2A> método o <xref:System.Data.Linq.DataContext> objeto.</span><span class="sxs-lookup"><span data-stu-id="66c58-136">Changes that you make to the Customers collection are not reflected in the database until you submit them by calling the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> method of the <xref:System.Data.Linq.DataContext> object.</span></span>  
  
     <span data-ttu-id="66c58-137">Clique duas vezes o formulário do Windows Form1, para adicionar código para o <xref:System.Windows.Forms.Form.Load> eventos para consultar a tabela de clientes que é exposto como uma propriedade de seu <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="66c58-137">Double-click the Windows Form, Form1, to add code to the <xref:System.Windows.Forms.Form.Load> event to query the Customers table that is exposed as a property of your <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="66c58-138">Adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="66c58-138">Add the following code:</span></span>  
  
    ```vb  
    Private db As northwindDataContext  
  
    Private Sub Form1_Load(ByVal sender As System.Object,   
                           ByVal e As System.EventArgs  
                          ) Handles MyBase.Load  
      db = New northwindDataContext()  
  
      RefreshData()  
    End Sub  
  
    Private Sub RefreshData()  
      Dim customers = From cust In db.Customers   
                      Where cust.City(0) = "W"   
                      Select cust  
  
      DataGridView1.DataSource = customers  
    End Sub  
    ```  
  
3.  <span data-ttu-id="66c58-139">Do **caixa de ferramentas**, arraste três <xref:System.Windows.Forms.Button> controles para o formulário.</span><span class="sxs-lookup"><span data-stu-id="66c58-139">From the **Toolbox**, drag three <xref:System.Windows.Forms.Button> controls onto the form.</span></span> <span data-ttu-id="66c58-140">Selecione a primeira `Button` controle.</span><span class="sxs-lookup"><span data-stu-id="66c58-140">Select the first `Button` control.</span></span> <span data-ttu-id="66c58-141">No **propriedades** janela, defina o `Name` do `Button` controle `AddButton` e `Text` para `Add`.</span><span class="sxs-lookup"><span data-stu-id="66c58-141">In the **Properties** window, set the `Name` of the `Button` control to `AddButton` and the `Text` to `Add`.</span></span> <span data-ttu-id="66c58-142">Selecione o segundo botão e defina o `Name` propriedade `UpdateButton` e `Text` propriedade `Update`.</span><span class="sxs-lookup"><span data-stu-id="66c58-142">Select the second button and set the `Name` property to `UpdateButton` and the `Text` property to `Update`.</span></span> <span data-ttu-id="66c58-143">Selecione o terceiro botão e defina o `Name` propriedade `DeleteButton` e `Text` propriedade `Delete`.</span><span class="sxs-lookup"><span data-stu-id="66c58-143">Select the third button and set the `Name` property to `DeleteButton` and the `Text` property to `Delete`.</span></span>  
  
4.  <span data-ttu-id="66c58-144">Clique duas vezes o **adicionar** botão para adicionar código ao seu `Click` eventos.</span><span class="sxs-lookup"><span data-stu-id="66c58-144">Double-click the **Add** button to add code to its `Click` event.</span></span> <span data-ttu-id="66c58-145">Adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="66c58-145">Add the following code:</span></span>  
  
    ```vb  
    Private Sub AddButton_Click(ByVal sender As System.Object,   
                                ByVal e As System.EventArgs  
                               ) Handles AddButton.Click  
      Dim cust As New Customer With {   
        .City = "Wellington",   
        .CompanyName = "Blue Yonder Airlines",   
        .ContactName = "Jill Frank",   
        .Country = "New Zealand",   
        .CustomerID = "JILLF"}  
  
      db.Customers.InsertOnSubmit(cust)  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
5.  <span data-ttu-id="66c58-146">Clique duas vezes o **atualização** botão para adicionar código ao seu `Click` eventos.</span><span class="sxs-lookup"><span data-stu-id="66c58-146">Double-click the **Update** button to add code to its `Click` event.</span></span> <span data-ttu-id="66c58-147">Adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="66c58-147">Add the following code:</span></span>  
  
    ```vb  
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles UpdateButton.Click  
      Dim updateCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      updateCust.ContactName = "Jill Shrader"  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
6.  <span data-ttu-id="66c58-148">Clique duas vezes o **excluir** botão para adicionar código ao seu `Click` eventos.</span><span class="sxs-lookup"><span data-stu-id="66c58-148">Double-click the **Delete** button to add code to its `Click` event.</span></span> <span data-ttu-id="66c58-149">Adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="66c58-149">Add the following code:</span></span>  
  
    ```vb  
    Private Sub DeleteButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles DeleteButton.Click  
      Dim deleteCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      db.Customers.DeleteOnSubmit(deleteCust)  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
7.  <span data-ttu-id="66c58-150">Pressione F5 para executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="66c58-150">Press F5 to run your project.</span></span> <span data-ttu-id="66c58-151">Clique em **adicionar** para adicionar um novo registro.</span><span class="sxs-lookup"><span data-stu-id="66c58-151">Click **Add** to add a new record.</span></span> <span data-ttu-id="66c58-152">Clique em **atualização** para modificar o novo registro.</span><span class="sxs-lookup"><span data-stu-id="66c58-152">Click **Update** to modify the new record.</span></span> <span data-ttu-id="66c58-153">Clique em **excluir** para excluir o registro de novo.</span><span class="sxs-lookup"><span data-stu-id="66c58-153">Click **Delete** to delete the new record.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66c58-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="66c58-154">See Also</span></span>  
 [<span data-ttu-id="66c58-155">LINQ</span><span class="sxs-lookup"><span data-stu-id="66c58-155">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="66c58-156">Consultas</span><span class="sxs-lookup"><span data-stu-id="66c58-156">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="66c58-157">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="66c58-157">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="66c58-158">Métodos de DataContext (Object Relational Designer)</span><span class="sxs-lookup"><span data-stu-id="66c58-158">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [<span data-ttu-id="66c58-159">Como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Object Relational Designer)</span><span class="sxs-lookup"><span data-stu-id="66c58-159">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)

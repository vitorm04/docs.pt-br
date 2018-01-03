---
title: 'Passo a passo: manipulando dados (C#)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24adfbe0-0ad6-449f-997d-8808e0770d2e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ac02ea6c07797c600fe9ce9c7b197a95fc84da61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-manipulating-data-c"></a><span data-ttu-id="ea271-102">Passo a passo: manipulando dados (C#)</span><span class="sxs-lookup"><span data-stu-id="ea271-102">Walkthrough: Manipulating Data (C#)</span></span>
<span data-ttu-id="ea271-103">Essa explicação passo a passo fornece um cenário completo fundamental do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para adicionar, modificar e excluir dados em um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="ea271-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="ea271-104">Você usará uma cópia do banco de dados de exemplo Northwind para adicionar um cliente, alterar o nome de um cliente e excluir um pedido.</span><span class="sxs-lookup"><span data-stu-id="ea271-104">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="ea271-105">Esse passo a passo foi escrito usando as configurações de desenvolvimento do Visual C#.</span><span class="sxs-lookup"><span data-stu-id="ea271-105">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ea271-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ea271-106">Prerequisites</span></span>  
 <span data-ttu-id="ea271-107">Este passo a passo requer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ea271-107">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="ea271-108">Este passo a passo usa uma pasta dedicada ("c:\linqtest6") para armazenar arquivos.</span><span class="sxs-lookup"><span data-stu-id="ea271-108">This walkthrough uses a dedicated folder ("c:\linqtest6") to hold files.</span></span> <span data-ttu-id="ea271-109">Crie essa pasta antes de iniciar o passo a passo.</span><span class="sxs-lookup"><span data-stu-id="ea271-109">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="ea271-110">O banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="ea271-110">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="ea271-111">Se você não tiver esse banco de dados no seu computador de desenvolvimento, poderá baixá-lo no site de download da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ea271-111">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="ea271-112">Para obter instruções, consulte [baixando bancos de dados de exemplo](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="ea271-112">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="ea271-113">Depois de baixar o banco de dados, copie o arquivo northwnd.mdf para a pasta c:\linqtest6.</span><span class="sxs-lookup"><span data-stu-id="ea271-113">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest6 folder.</span></span>  
  
-   <span data-ttu-id="ea271-114">Um arquivo de código C# gerado no banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="ea271-114">A C# code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="ea271-115">Você pode gerar esse arquivo usando o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] ou a ferramenta SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="ea271-115">You can generate this file by using either the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] or the SQLMetal tool.</span></span> <span data-ttu-id="ea271-116">Este passo a passo foi escrito usando a ferramenta SQLMetal com a seguinte linha de comando:</span><span class="sxs-lookup"><span data-stu-id="ea271-116">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="ea271-117">**SqlMetal /code:"c:\linqtest6\northwind.cs" /language:csharp "C:\linqtest6\northwnd.mdf" / Pluralizar**</span><span class="sxs-lookup"><span data-stu-id="ea271-117">**sqlmetal /code:"c:\linqtest6\northwind.cs" /language:csharp "C:\linqtest6\northwnd.mdf" /pluralize**</span></span>  
  
     <span data-ttu-id="ea271-118">Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="ea271-118">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="ea271-119">Visão geral</span><span class="sxs-lookup"><span data-stu-id="ea271-119">Overview</span></span>  
 <span data-ttu-id="ea271-120">Este passo a passo consiste em seis tarefas principais:</span><span class="sxs-lookup"><span data-stu-id="ea271-120">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="ea271-121">Criar a solução de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] no [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ea271-121">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span></span>  
  
-   <span data-ttu-id="ea271-122">Adicionar o arquivo do código de banco de dados ao projeto.</span><span class="sxs-lookup"><span data-stu-id="ea271-122">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="ea271-123">Criar um novo objeto do cliente.</span><span class="sxs-lookup"><span data-stu-id="ea271-123">Creating a new customer object.</span></span>  
  
-   <span data-ttu-id="ea271-124">Alterar o nome de contato de um cliente.</span><span class="sxs-lookup"><span data-stu-id="ea271-124">Modifying the contact name of a customer.</span></span>  
  
-   <span data-ttu-id="ea271-125">Excluir um pedido.</span><span class="sxs-lookup"><span data-stu-id="ea271-125">Deleting an order.</span></span>  
  
-   <span data-ttu-id="ea271-126">Enviar essas alterações para o banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="ea271-126">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="ea271-127">Criando uma solução LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ea271-127">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="ea271-128">Nesta primeira tarefa, você cria uma solução do [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] que contém as referências necessárias para criar e executar um projeto do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ea271-128">In this first task, you create a [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="ea271-129">Para criar uma solução LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ea271-129">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="ea271-130">Sobre o [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **arquivo** , aponte para **novo**e, em seguida, clique em **projeto**.</span><span class="sxs-lookup"><span data-stu-id="ea271-130">On the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="ea271-131">No **tipos de projeto** painel o **novo projeto** caixa de diálogo, clique em **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="ea271-131">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3.  <span data-ttu-id="ea271-132">No painel **Modelos**, clique em **Aplicativo de Console**.</span><span class="sxs-lookup"><span data-stu-id="ea271-132">In the **Templates** pane, click **Console Application**.</span></span>  
  
4.  <span data-ttu-id="ea271-133">No **nome** , digite **LinqDataManipulationApp**.</span><span class="sxs-lookup"><span data-stu-id="ea271-133">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5.  <span data-ttu-id="ea271-134">No **local** , verifique se onde você deseja armazenar os arquivos de projeto.</span><span class="sxs-lookup"><span data-stu-id="ea271-134">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6.  <span data-ttu-id="ea271-135">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="ea271-135">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="ea271-136">Adicionando referências e diretivas LINQ</span><span class="sxs-lookup"><span data-stu-id="ea271-136">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="ea271-137">Este passo a passo usa assemblies que não podem ser instalados por padrão em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="ea271-137">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="ea271-138">Se System.Data.Linq não estiver listado como uma referência em seu projeto, adicione-o, conforme explicado nas seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="ea271-138">If System.Data.Linq is not listed as a reference in your project, add it, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="ea271-139">Para adicionar System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="ea271-139">To add System.Data.Linq</span></span>  
  
1.  <span data-ttu-id="ea271-140">Em **Solution Explorer**, clique com botão direito **referências**e, em seguida, clique em **adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="ea271-140">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="ea271-141">No **adicionar referência** caixa de diálogo, clique em **.NET**, clique em assembly System.Data.Linq e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="ea271-141">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="ea271-142">O assembly é adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="ea271-142">The assembly is added to the project.</span></span>  
  
3.  <span data-ttu-id="ea271-143">Adicione as seguintes diretivas na parte superior de Program.cs:</span><span class="sxs-lookup"><span data-stu-id="ea271-143">Add the following directives at the top of Program.cs:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="ea271-144">Adicionando o arquivo do código Northwind ao projeto</span><span class="sxs-lookup"><span data-stu-id="ea271-144">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="ea271-145">Estas etapas presumem que você tenha usado a ferramenta SQLMetal para gerar um arquivo de código do banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="ea271-145">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="ea271-146">Para obter mais informações, consulte a seção de pré-requisitos anteriormente neste passo a passo.</span><span class="sxs-lookup"><span data-stu-id="ea271-146">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="ea271-147">Para adicionar o arquivo do código Northwind ao projeto</span><span class="sxs-lookup"><span data-stu-id="ea271-147">To add the northwind code file to the project</span></span>  
  
1.  <span data-ttu-id="ea271-148">Sobre o **projeto** menu, clique em **Add Existing Item**.</span><span class="sxs-lookup"><span data-stu-id="ea271-148">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2.  <span data-ttu-id="ea271-149">No **Add Existing Item** caixa de diálogo, navegue até c:\linqtest6\northwind.cs e, em seguida, clique em **adicionar**.</span><span class="sxs-lookup"><span data-stu-id="ea271-149">In the **Add Existing Item** dialog box, navigate to c:\linqtest6\northwind.cs, and then click **Add**.</span></span>  
  
     <span data-ttu-id="ea271-150">O arquivo northwind.cs é adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="ea271-150">The northwind.cs file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="ea271-151">Configurando a conexão de banco de dados</span><span class="sxs-lookup"><span data-stu-id="ea271-151">Setting Up the Database Connection</span></span>  
 <span data-ttu-id="ea271-152">Primeiro, teste sua conexão com o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="ea271-152">First, test your connection to the database.</span></span> <span data-ttu-id="ea271-153">Observe especialmente se o banco de dados, Northwnd, não tem nenhum caractere i.</span><span class="sxs-lookup"><span data-stu-id="ea271-153">Note especially that the database, Northwnd, has no i character.</span></span> <span data-ttu-id="ea271-154">Se você gerar erros nas próximas etapas, revise o arquivo northwind.cs para determinar como a classe parcial do Northwind é soletrada.</span><span class="sxs-lookup"><span data-stu-id="ea271-154">If you generate errors in the next steps, review the northwind.cs file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="ea271-155">Para configurar e testar a conexão com o banco de dados</span><span class="sxs-lookup"><span data-stu-id="ea271-155">To set up and test the database connection</span></span>  
  
1.  <span data-ttu-id="ea271-156">Digite ou cole o código a seguir no método `Main` na classe Program:</span><span class="sxs-lookup"><span data-stu-id="ea271-156">Type or paste the following code into the `Main` method in the Program class:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#2)]  
  
2.  <span data-ttu-id="ea271-157">Pressione F5 para testar o aplicativo neste ponto.</span><span class="sxs-lookup"><span data-stu-id="ea271-157">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="ea271-158">Um **Console** janela será aberta.</span><span class="sxs-lookup"><span data-stu-id="ea271-158">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="ea271-159">Você pode fechar o aplicativo pressionando Enter no **Console** janela, ou clicando em **parar depuração** no [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **depurar** menu.</span><span class="sxs-lookup"><span data-stu-id="ea271-159">You can close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="ea271-160">Criando uma nova entidade</span><span class="sxs-lookup"><span data-stu-id="ea271-160">Creating a New Entity</span></span>  
 <span data-ttu-id="ea271-161">Criar uma nova entidade é simples.</span><span class="sxs-lookup"><span data-stu-id="ea271-161">Creating a new entity is straightforward.</span></span> <span data-ttu-id="ea271-162">Você pode criar objetos (como `Customer`) usando a palavra-chave `new`.</span><span class="sxs-lookup"><span data-stu-id="ea271-162">You can create objects (such as `Customer`) by using the `new` keyword.</span></span>  
  
 <span data-ttu-id="ea271-163">Nessa seção e nas seguintes, você está fazendo alterações somente no cache local.</span><span class="sxs-lookup"><span data-stu-id="ea271-163">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="ea271-164">Nenhuma alteração será enviada para o banco de dados até que você chame <xref:System.Data.Linq.DataContext.SubmitChanges%2A> no final dessa explicação passo a passo.</span><span class="sxs-lookup"><span data-stu-id="ea271-164">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="ea271-165">Para adicionar um novo objeto de entidade de cliente</span><span class="sxs-lookup"><span data-stu-id="ea271-165">To add a new Customer entity object</span></span>  
  
1.  <span data-ttu-id="ea271-166">Crie um novo `Customer` adicionando o seguinte código antes de `Console.ReadLine();` no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="ea271-166">Create a new `Customer` by adding the following code before `Console.ReadLine();` in the `Main` method:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#3)]  
  
2.  <span data-ttu-id="ea271-167">Pressione F5 para depurar a solução.</span><span class="sxs-lookup"><span data-stu-id="ea271-167">Press F5 to debug the solution.</span></span>  
  
3.  <span data-ttu-id="ea271-168">Pressione Enter no **Console** janela para parar a depuração e continuar o passo a passo.</span><span class="sxs-lookup"><span data-stu-id="ea271-168">Press Enter in the **Console** window to stop debugging and continue the walkthrough.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="ea271-169">Atualizando uma entidade</span><span class="sxs-lookup"><span data-stu-id="ea271-169">Updating an Entity</span></span>  
 <span data-ttu-id="ea271-170">Nas etapas a seguir, você recuperará um objeto `Customer` e alterará uma de suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="ea271-170">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="ea271-171">Para alterar o nome de um cliente</span><span class="sxs-lookup"><span data-stu-id="ea271-171">To change the name of a Customer</span></span>  
  
-   <span data-ttu-id="ea271-172">Adicione o seguinte código acima de `Console.ReadLine();`:</span><span class="sxs-lookup"><span data-stu-id="ea271-172">Add the following code above `Console.ReadLine();`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="ea271-173">Excluindo uma entidade</span><span class="sxs-lookup"><span data-stu-id="ea271-173">Deleting an Entity</span></span>  
 <span data-ttu-id="ea271-174">Usando o mesmo objeto de cliente, você poderá excluir o primeiro pedido.</span><span class="sxs-lookup"><span data-stu-id="ea271-174">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="ea271-175">O código a seguir demonstra como separar relações entre linhas, e como excluir uma linha do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="ea271-175">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span> <span data-ttu-id="ea271-176">Adicione o seguinte código antes de `Console.ReadLine` para ver como os objetos podem ser excluídos:</span><span class="sxs-lookup"><span data-stu-id="ea271-176">Add the following code before `Console.ReadLine` to see how objects can be deleted:</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="ea271-177">Para excluir uma linha</span><span class="sxs-lookup"><span data-stu-id="ea271-177">To delete a row</span></span>  
  
-   <span data-ttu-id="ea271-178">Adicione o seguinte código bem acima de `Console.ReadLine();`:</span><span class="sxs-lookup"><span data-stu-id="ea271-178">Add the following code just above `Console.ReadLine();`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="ea271-179">Enviando alterações para o banco de dados</span><span class="sxs-lookup"><span data-stu-id="ea271-179">Submitting Changes to the Database</span></span>  
 <span data-ttu-id="ea271-180">A etapa final necessária para criar, atualizar e excluir objetos é realmente enviar as alterações para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="ea271-180">The final step required for creating, updating, and deleting objects, is to actually submit the changes to the database.</span></span> <span data-ttu-id="ea271-181">Sem esta etapa, suas alterações serão somente locais e não aparecerão nos resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="ea271-181">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="ea271-182">Para enviar alterações para o banco de dados</span><span class="sxs-lookup"><span data-stu-id="ea271-182">To submit changes to the database</span></span>  
  
1.  <span data-ttu-id="ea271-183">Insira o seguinte código bem acima de `Console.ReadLine`:</span><span class="sxs-lookup"><span data-stu-id="ea271-183">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#6)]  
  
2.  <span data-ttu-id="ea271-184">Insira o código a seguir (após `SubmitChanges`) para mostrar os efeitos de antes e depois de enviar as alterações:</span><span class="sxs-lookup"><span data-stu-id="ea271-184">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#7)]  
  
3.  <span data-ttu-id="ea271-185">Pressione F5 para depurar a solução.</span><span class="sxs-lookup"><span data-stu-id="ea271-185">Press F5 to debug the solution.</span></span>  
  
4.  <span data-ttu-id="ea271-186">Pressione Enter no **Console** janela para fechar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea271-186">Press Enter in the **Console** window to close the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea271-187">Depois de adicionar o novo cliente enviando as alterações, você não poderá executar esta solução novamente como está.</span><span class="sxs-lookup"><span data-stu-id="ea271-187">After you have added the new customer by submitting the changes, you cannot execute this solution again as is.</span></span> <span data-ttu-id="ea271-188">Para executar novamente a solução, altere o nome do cliente e a ID do cliente a ser adicionada.</span><span class="sxs-lookup"><span data-stu-id="ea271-188">To execute the solution again, change the name of the customer and customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea271-189">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea271-189">See Also</span></span>  
 [<span data-ttu-id="ea271-190">Aprendendo com explicações passo a passo</span><span class="sxs-lookup"><span data-stu-id="ea271-190">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)

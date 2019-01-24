---
title: 'Passo a passo: Manipulando dados (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
ms.openlocfilehash: 0eab5fe5c9455badb7f538307cb827391b254a95
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626921"
---
# <a name="walkthrough-manipulating-data-visual-basic"></a><span data-ttu-id="384a0-102">Passo a passo: Manipulando dados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="384a0-102">Walkthrough: Manipulating Data (Visual Basic)</span></span>
<span data-ttu-id="384a0-103">Essa explicação passo a passo fornece um cenário completo fundamental do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para adicionar, modificar e excluir dados em um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="384a0-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="384a0-104">Você usará uma cópia do banco de dados de exemplo Northwind para adicionar um cliente, alterar o nome de um cliente e excluir um pedido.</span><span class="sxs-lookup"><span data-stu-id="384a0-104">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="384a0-105">Este passo a passo foi escrito usando as Configurações de Desenvolvimento do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="384a0-105">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="384a0-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="384a0-106">Prerequisites</span></span>  
 <span data-ttu-id="384a0-107">Este passo a passo requer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="384a0-107">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="384a0-108">Este passo a passo usa uma pasta dedicada ("c:\linqtest2") para armazenar arquivos.</span><span class="sxs-lookup"><span data-stu-id="384a0-108">This walkthrough uses a dedicated folder ("c:\linqtest2") to hold files.</span></span> <span data-ttu-id="384a0-109">Crie essa pasta antes de iniciar o passo a passo.</span><span class="sxs-lookup"><span data-stu-id="384a0-109">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="384a0-110">O banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="384a0-110">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="384a0-111">Se você não tiver esse banco de dados no seu computador de desenvolvimento, poderá baixá-lo no site de download da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="384a0-111">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="384a0-112">Para obter instruções, consulte [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="384a0-112">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="384a0-113">Depois de baixar o banco de dados, copie o arquivo northwnd.mdf para a pasta c:\linqtest2.</span><span class="sxs-lookup"><span data-stu-id="384a0-113">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest2 folder.</span></span>  
  
-   <span data-ttu-id="384a0-114">Um arquivo de código do Visual Basic gerado do banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="384a0-114">A Visual Basic code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="384a0-115">Você pode gerar esse arquivo usando o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] ou a ferramenta SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="384a0-115">You can generate this file by using either the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] or the SQLMetal tool.</span></span> <span data-ttu-id="384a0-116">Este passo a passo foi escrito usando a ferramenta SQLMetal com a seguinte linha de comando:</span><span class="sxs-lookup"><span data-stu-id="384a0-116">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="384a0-117">**sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**</span><span class="sxs-lookup"><span data-stu-id="384a0-117">**sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**</span></span>  
  
     <span data-ttu-id="384a0-118">Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="384a0-118">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="384a0-119">Visão geral</span><span class="sxs-lookup"><span data-stu-id="384a0-119">Overview</span></span>  
 <span data-ttu-id="384a0-120">Este passo a passo consiste em seis tarefas principais:</span><span class="sxs-lookup"><span data-stu-id="384a0-120">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="384a0-121">Criando o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solução no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="384a0-121">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
-   <span data-ttu-id="384a0-122">Adicionar o arquivo do código de banco de dados ao projeto.</span><span class="sxs-lookup"><span data-stu-id="384a0-122">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="384a0-123">Criar um novo objeto do cliente.</span><span class="sxs-lookup"><span data-stu-id="384a0-123">Creating a new customer object.</span></span>  
  
-   <span data-ttu-id="384a0-124">Alterar o nome de contato de um cliente.</span><span class="sxs-lookup"><span data-stu-id="384a0-124">Modifying the contact name of a customer.</span></span>  
  
-   <span data-ttu-id="384a0-125">Excluir um pedido.</span><span class="sxs-lookup"><span data-stu-id="384a0-125">Deleting an order.</span></span>  
  
-   <span data-ttu-id="384a0-126">Enviar essas alterações para o banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="384a0-126">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="384a0-127">Criando uma solução LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="384a0-127">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="384a0-128">A primeira tarefa, você cria uma solução do Visual Studio que contém as referências necessárias para compilar e executar um [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projeto.</span><span class="sxs-lookup"><span data-stu-id="384a0-128">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="384a0-129">Para criar uma solução LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="384a0-129">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="384a0-130">No Visual Studio **arquivo** menu, clique em **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="384a0-130">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="384a0-131">No **tipos de projeto** painel na **novo projeto** caixa de diálogo, clique em **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="384a0-131">In the **Project types** pane in the **New Project** dialog box, click **Visual Basic**.</span></span>  
  
3.  <span data-ttu-id="384a0-132">No painel **Modelos**, clique em **Aplicativo de Console**.</span><span class="sxs-lookup"><span data-stu-id="384a0-132">In the **Templates** pane, click **Console Application**.</span></span>  
  
4.  <span data-ttu-id="384a0-133">No **nome** , digite **LinqDataManipulationApp**.</span><span class="sxs-lookup"><span data-stu-id="384a0-133">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5.  <span data-ttu-id="384a0-134">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="384a0-134">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="384a0-135">Adicionando referências e diretivas LINQ</span><span class="sxs-lookup"><span data-stu-id="384a0-135">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="384a0-136">Este passo a passo usa assemblies que não podem ser instalados por padrão em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="384a0-136">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="384a0-137">Se `System.Data.Linq` não estiver listado como uma referência em seu projeto (clique em **Show All Files** na **Gerenciador de soluções** e expanda o **referências** nó), adicioná-lo, conforme explicado em as etapas a seguir.</span><span class="sxs-lookup"><span data-stu-id="384a0-137">If `System.Data.Linq` is not listed as a reference in your project (click **Show All Files** in **Solution Explorer** and expand the **References** node), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="384a0-138">Para adicionar System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="384a0-138">To add System.Data.Linq</span></span>  
  
1.  <span data-ttu-id="384a0-139">Na **Gerenciador de soluções**, clique com botão direito **referências**e, em seguida, clique em **Add Reference**.</span><span class="sxs-lookup"><span data-stu-id="384a0-139">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="384a0-140">No **adicionar referência** caixa de diálogo, clique em **.NET**, clique no assembly System e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="384a0-140">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="384a0-141">O assembly é adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="384a0-141">The assembly is added to the project.</span></span>  
  
3.  <span data-ttu-id="384a0-142">No editor de códigos, adicione as seguintes diretivas acima **Module1**:</span><span class="sxs-lookup"><span data-stu-id="384a0-142">In the code editor, add the following directives above **Module1**:</span></span>  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="384a0-143">Adicionando o arquivo do código Northwind ao projeto</span><span class="sxs-lookup"><span data-stu-id="384a0-143">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="384a0-144">Estas etapas presumem que você tenha usado a ferramenta SQLMetal para gerar um arquivo de código do banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="384a0-144">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="384a0-145">Para obter mais informações, consulte a seção de pré-requisitos anteriormente neste passo a passo.</span><span class="sxs-lookup"><span data-stu-id="384a0-145">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="384a0-146">Para adicionar o arquivo do código Northwind ao projeto</span><span class="sxs-lookup"><span data-stu-id="384a0-146">To add the northwind code file to the project</span></span>  
  
1.  <span data-ttu-id="384a0-147">Sobre o **Project** menu, clique em **Add Existing Item**.</span><span class="sxs-lookup"><span data-stu-id="384a0-147">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2.  <span data-ttu-id="384a0-148">No **Adicionar Item existente** caixa de diálogo, navegue até c:\linqtest2\northwind.vb e, em seguida, clique em **Add**.</span><span class="sxs-lookup"><span data-stu-id="384a0-148">In the **Add Existing Item** dialog box, navigate to c:\linqtest2\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="384a0-149">O arquivo northwind.vb é adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="384a0-149">The northwind.vb file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="384a0-150">Configurando a conexão de banco de dados</span><span class="sxs-lookup"><span data-stu-id="384a0-150">Setting Up the Database Connection</span></span>  
 <span data-ttu-id="384a0-151">Primeiro, teste sua conexão com o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="384a0-151">First, test your connection to the database.</span></span> <span data-ttu-id="384a0-152">Observe especialmente se o nome do banco de dados, Northwnd, não tem nenhum caractere i.</span><span class="sxs-lookup"><span data-stu-id="384a0-152">Note especially that the name of the database, Northwnd, has no i character.</span></span> <span data-ttu-id="384a0-153">Se você gerar erros nas próximas etapas, revise o arquivo northwind.vb para determinar como a classe parcial do Northwind é soletrada.</span><span class="sxs-lookup"><span data-stu-id="384a0-153">If you generate errors in the next steps, review the northwind.vb file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="384a0-154">Para configurar e testar a conexão com o banco de dados</span><span class="sxs-lookup"><span data-stu-id="384a0-154">To set up and test the database connection</span></span>  
  
1.  <span data-ttu-id="384a0-155">Digite ou cole o seguinte código em `Sub Main`:</span><span class="sxs-lookup"><span data-stu-id="384a0-155">Type or paste the following code into `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2.  <span data-ttu-id="384a0-156">Pressione F5 para testar o aplicativo neste ponto.</span><span class="sxs-lookup"><span data-stu-id="384a0-156">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="384a0-157">Um **Console** janela é aberta.</span><span class="sxs-lookup"><span data-stu-id="384a0-157">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="384a0-158">Feche o aplicativo pressionando Enter na **Console** janela, ou clicando em **parar depuração** no Visual Studio **depurar** menu.</span><span class="sxs-lookup"><span data-stu-id="384a0-158">Close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the Visual Studio **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="384a0-159">Criando uma nova entidade</span><span class="sxs-lookup"><span data-stu-id="384a0-159">Creating a New Entity</span></span>  
 <span data-ttu-id="384a0-160">Criar uma nova entidade é simples.</span><span class="sxs-lookup"><span data-stu-id="384a0-160">Creating a new entity is straightforward.</span></span> <span data-ttu-id="384a0-161">Você pode criar objetos (como `Customer`) usando a palavra-chave `New`.</span><span class="sxs-lookup"><span data-stu-id="384a0-161">You can create objects (such as `Customer`) by using the `New` keyword.</span></span>  
  
 <span data-ttu-id="384a0-162">Nessa seção e nas seguintes, você está fazendo alterações somente no cache local.</span><span class="sxs-lookup"><span data-stu-id="384a0-162">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="384a0-163">Nenhuma alteração será enviada para o banco de dados até que você chame <xref:System.Data.Linq.DataContext.SubmitChanges%2A> no final dessa explicação passo a passo.</span><span class="sxs-lookup"><span data-stu-id="384a0-163">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="384a0-164">Para adicionar um novo objeto de entidade de cliente</span><span class="sxs-lookup"><span data-stu-id="384a0-164">To add a new Customer entity object</span></span>  
  
1.  <span data-ttu-id="384a0-165">Crie um novo `Customer` adicionando o seguinte código antes de `Console.ReadLine` em `Sub Main`:</span><span class="sxs-lookup"><span data-stu-id="384a0-165">Create a new `Customer` by adding the following code before `Console.ReadLine` in `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2.  <span data-ttu-id="384a0-166">Pressione F5 para depurar a solução.</span><span class="sxs-lookup"><span data-stu-id="384a0-166">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="384a0-167">Os resultados mostrados na janela do console são:</span><span class="sxs-lookup"><span data-stu-id="384a0-167">The results that are shown in the console window are as follows:</span></span>  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     <span data-ttu-id="384a0-168">Observe que a nova linha não aparece nos resultados.</span><span class="sxs-lookup"><span data-stu-id="384a0-168">Note that the new row does not appear in the results.</span></span> <span data-ttu-id="384a0-169">Os novos dados ainda não foram enviados para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="384a0-169">The new data has not yet been submitted to the database.</span></span>  
  
3.  <span data-ttu-id="384a0-170">Pressione Enter na **Console** janela para parar a depuração.</span><span class="sxs-lookup"><span data-stu-id="384a0-170">Press Enter in the **Console** window to stop debugging.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="384a0-171">Atualizando uma entidade</span><span class="sxs-lookup"><span data-stu-id="384a0-171">Updating an Entity</span></span>  
 <span data-ttu-id="384a0-172">Nas etapas a seguir, você recuperará um objeto `Customer` e alterará uma de suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="384a0-172">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="384a0-173">Para alterar o nome de um cliente</span><span class="sxs-lookup"><span data-stu-id="384a0-173">To change the name of a Customer</span></span>  
  
-   <span data-ttu-id="384a0-174">Adicione o seguinte código acima de `Console.ReadLine()`:</span><span class="sxs-lookup"><span data-stu-id="384a0-174">Add the following code above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="384a0-175">Excluindo uma entidade</span><span class="sxs-lookup"><span data-stu-id="384a0-175">Deleting an Entity</span></span>  
 <span data-ttu-id="384a0-176">Usando o mesmo objeto de cliente, você poderá excluir o primeiro pedido.</span><span class="sxs-lookup"><span data-stu-id="384a0-176">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="384a0-177">O código a seguir demonstra como separar relações entre linhas, e como excluir uma linha do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="384a0-177">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="384a0-178">Para excluir uma linha</span><span class="sxs-lookup"><span data-stu-id="384a0-178">To delete a row</span></span>  
  
-   <span data-ttu-id="384a0-179">Adicione o seguinte código bem acima de `Console.ReadLine()`:</span><span class="sxs-lookup"><span data-stu-id="384a0-179">Add the following code just above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="384a0-180">Enviando alterações para o banco de dados</span><span class="sxs-lookup"><span data-stu-id="384a0-180">Submitting Changes to the Database</span></span>  
 <span data-ttu-id="384a0-181">A etapa final necessária para criar, atualizar e excluir objetos é realmente enviar as alterações para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="384a0-181">The final step required for creating, updating, and deleting objects is to actually submit the changes to the database.</span></span> <span data-ttu-id="384a0-182">Sem esta etapa, suas alterações serão somente locais e não aparecerão nos resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="384a0-182">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="384a0-183">Para enviar alterações para o banco de dados</span><span class="sxs-lookup"><span data-stu-id="384a0-183">To submit changes to the database</span></span>  
  
1.  <span data-ttu-id="384a0-184">Insira o seguinte código bem acima de `Console.ReadLine`:</span><span class="sxs-lookup"><span data-stu-id="384a0-184">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2.  <span data-ttu-id="384a0-185">Insira o código a seguir (após `SubmitChanges`) para mostrar os efeitos de antes e depois de enviar as alterações:</span><span class="sxs-lookup"><span data-stu-id="384a0-185">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3.  <span data-ttu-id="384a0-186">Pressione F5 para depurar a solução.</span><span class="sxs-lookup"><span data-stu-id="384a0-186">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="384a0-187">A janela do console aparece da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="384a0-187">The console window appears as follows:</span></span>  
  
    ```  
    Customers matching CA before update:  
    Customer ID: CACTU  
    Customer ID: RICAR  
  
    The Order Detail to be deleted is: OrderID = 10643  
  
    Customers matching CA after update:  
    Customer ID: A3VCA  
    Customer ID: CACTU  
    Customer ID: RICAR  
    ```  
  
4.  <span data-ttu-id="384a0-188">Pressione Enter na **Console** janela para parar a depuração.</span><span class="sxs-lookup"><span data-stu-id="384a0-188">Press Enter in the **Console** window to stop debugging.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="384a0-189">Depois de você ter adicionado o novo cliente enviando as alterações, você não poderá executar esta solução novamente desta forma, porque não poderá adicionar o mesmo cliente novamente.</span><span class="sxs-lookup"><span data-stu-id="384a0-189">After you have added the new customer by submitting the changes, you cannot execute this solution again as is, because you cannot add the same customer again as is.</span></span> <span data-ttu-id="384a0-190">Para executar novamente a solução, altere o valor da identificação do cliente a ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="384a0-190">To execute the solution again, change the value of the customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="384a0-191">Consulte também</span><span class="sxs-lookup"><span data-stu-id="384a0-191">See also</span></span>
- [<span data-ttu-id="384a0-192">Aprendendo com explicações passo a passo</span><span class="sxs-lookup"><span data-stu-id="384a0-192">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)

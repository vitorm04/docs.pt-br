---
title: 'Como: criar e executar um fluxo de trabalho de execução prolongada'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0043c89-2192-43c9-986d-3ecec4dd8c9c
ms.openlocfilehash: 7940d1d8869d3b82c1aa19cb038a68b8724345dd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320040"
---
# <a name="how-to-create-and-run-a-long-running-workflow"></a><span data-ttu-id="c3ac9-102">Como: criar e executar um fluxo de trabalho de execução prolongada</span><span class="sxs-lookup"><span data-stu-id="c3ac9-102">How to: Create and Run a Long Running Workflow</span></span>
<span data-ttu-id="c3ac9-103">Um dos recursos centrais do Windows Workflow Foundation (WF) é a capacidade de persistir e descarregar fluxos de trabalho ociosos para um banco de dados do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-103">One of the central features of Windows Workflow Foundation (WF) is the runtime’s ability to persist and unload idle workflows to a database.</span></span> <span data-ttu-id="c3ac9-104">As etapas em [como: Executar um fluxo de trabalho](how-to-run-a-workflow.md) demonstraram os fundamentos de hospedagem de fluxo de trabalho usando um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-104">The steps in [How to: Run a Workflow](how-to-run-a-workflow.md) demonstrated the basics of workflow hosting using a console application.</span></span> <span data-ttu-id="c3ac9-105">Foram mostrados exemplos de iniciação de fluxos de trabalho, manipuladores do ciclo de vida de fluxo de trabalho e retomada de indicadores.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-105">Examples were shown of starting workflows, workflow lifecycle handlers, and resuming bookmarks.</span></span> <span data-ttu-id="c3ac9-106">Para demonstrar efetivamente a persistência do fluxo de trabalho, um host de fluxo de trabalho mais complexo é necessário que dá suporte a início e retomada de várias instâncias de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-106">In order to demonstrate workflow persistence effectively, a more complex workflow host is required that supports starting and resuming multiple workflow instances.</span></span> <span data-ttu-id="c3ac9-107">Esta etapa no tutorial demonstra como criar um aplicativo de host do Windows Form que dê suporte ao início e à retomada de várias instâncias de fluxo de trabalho, persistência de fluxo de trabalho e fornece uma base para os recursos avançados como o rastreamento e o controle de versão que são demonstrados em etapas tutoriais subsequentes.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-107">This step in the tutorial demonstrates how to create a Windows form host application that supports starting and resuming multiple workflow instances, workflow persistence, and provides a basis for the advanced features such as tracking and versioning that are demonstrated in subsequent tutorial steps.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3ac9-108">Nesta etapa do tutorial e as etapas subsequentes usam todos os três tipos de fluxo de trabalho de [como: Criar um fluxo de trabalho](how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="c3ac9-108">This tutorial step and the subsequent steps use all three workflow types from [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span> <span data-ttu-id="c3ac9-109">Se você não tiver concluído todos os três tipos, você pode baixar uma versão completa das etapas da [Windows Workflow Foundation (WF45) - Tutorial de Introdução](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="c3ac9-109">If you did not complete all three types you can download a completed version of the steps from [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3ac9-110">Para baixar uma versão completa ou exibir uma vídeo passo a passo do tutorial, consulte [Windows Workflow Foundation (WF45) - Tutorial de Introdução](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="c3ac9-110">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="c3ac9-111">Neste tópico</span><span class="sxs-lookup"><span data-stu-id="c3ac9-111">In this topic</span></span>  
  
-   [<span data-ttu-id="c3ac9-112">Para criar o banco de dados de persistência</span><span class="sxs-lookup"><span data-stu-id="c3ac9-112">To create the persistence database</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_CreatePersistenceDatabase)  
  
-   [<span data-ttu-id="c3ac9-113">Para adicionar a referência aos assemblies do DurableInstancing</span><span class="sxs-lookup"><span data-stu-id="c3ac9-113">To add the reference to the DurableInstancing assemblies</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddReference)  
  
-   [<span data-ttu-id="c3ac9-114">Para criar o formulário de host de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c3ac9-114">To create the workflow host form</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_CreateForm)  
  
-   [<span data-ttu-id="c3ac9-115">Para adicionar as propriedades e métodos auxiliares do formulário</span><span class="sxs-lookup"><span data-stu-id="c3ac9-115">To add the properties and helper methods of the form</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods)  
  
-   [<span data-ttu-id="c3ac9-116">Para configurar o armazenamento de instância, manipuladores de ciclo de vida de fluxo de trabalho e extensões</span><span class="sxs-lookup"><span data-stu-id="c3ac9-116">To configure the instance store, workflow lifecycle handlers, and extensions</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_ConfigureWorkflowApplication)  
  
-   [<span data-ttu-id="c3ac9-117">Para habilitar o início e retomada de vários tipos de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c3ac9-117">To enable starting and resuming multiple workflow types</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_WorkflowVersionMap)  
  
-   [<span data-ttu-id="c3ac9-118">Para iniciar um novo fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c3ac9-118">To start a new workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_StartWorkflow)  
  
-   [<span data-ttu-id="c3ac9-119">Para retomar um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c3ac9-119">To resume a workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_ResumeWorkflow)  
  
-   [<span data-ttu-id="c3ac9-120">Para encerrar um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c3ac9-120">To terminate a workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_TerminateWorkflow)  
  
-   [<span data-ttu-id="c3ac9-121">Para compilar e executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="c3ac9-121">To build and run the application</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_BuildAndRun)  
  
### <a name="BKMK_CreatePersistenceDatabase"></a> <span data-ttu-id="c3ac9-122">Para criar o banco de dados de persistência</span><span class="sxs-lookup"><span data-stu-id="c3ac9-122">To create the persistence database</span></span>  
  
1. <span data-ttu-id="c3ac9-123">Abra o SQL Server Management Studio e conecte-se ao servidor local, por exemplo **. \SQLEXPRESS**.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-123">Open SQL Server Management Studio and connect to the local server, for example **.\SQLEXPRESS**.</span></span> <span data-ttu-id="c3ac9-124">Clique com botão direito do **bancos de dados** nó no servidor local e selecione **novo banco de dados**.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-124">Right-click the **Databases** node on the local server, and select **New Database**.</span></span> <span data-ttu-id="c3ac9-125">Nomeie o novo banco de dados **WF45GettingStartedTutorial**, aceite todos os outros valores e selecione **Okey**.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-125">Name the new database **WF45GettingStartedTutorial**, accept all other values, and select **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c3ac9-126">Certifique-se de que você tenha **criar banco de dados** permissão no servidor local antes de criar o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-126">Ensure that you have **Create Database** permission on the local server before creating the database.</span></span>  
  
2. <span data-ttu-id="c3ac9-127">Escolher **aberto**, **arquivo** do **arquivo** menu.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-127">Choose **Open**, **File** from the **File** menu.</span></span> <span data-ttu-id="c3ac9-128">Navegue até a pasta a seguir: `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`</span><span class="sxs-lookup"><span data-stu-id="c3ac9-128">Browse to the following folder: `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`</span></span>  
  
     <span data-ttu-id="c3ac9-129">Selecione dois arquivos a seguir e clique em **aberto**.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-129">Select the following two files and click **Open**.</span></span>  
  
    -   <span data-ttu-id="c3ac9-130">SqlWorkflowInstanceStoreLogic.sql</span><span class="sxs-lookup"><span data-stu-id="c3ac9-130">SqlWorkflowInstanceStoreLogic.sql</span></span>  
  
    -   <span data-ttu-id="c3ac9-131">SqlWorkflowInstanceStoreSchema.sql</span><span class="sxs-lookup"><span data-stu-id="c3ac9-131">SqlWorkflowInstanceStoreSchema.sql</span></span>  
  
3. <span data-ttu-id="c3ac9-132">Escolher **Sqlworkflowinstancestoreschema** da **janela** menu.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-132">Choose **SqlWorkflowInstanceStoreSchema.sql** from the **Window** menu.</span></span> <span data-ttu-id="c3ac9-133">Certifique-se de que **WF45GettingStartedTutorial** está selecionado na **bancos de dados disponíveis** lista suspensa e escolha **Execute** do **consulta**menu.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-133">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>  
  
4. <span data-ttu-id="c3ac9-134">Escolher **Sqlworkflowinstancestorelogic** da **janela** menu.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-134">Choose **SqlWorkflowInstanceStoreLogic.sql** from the **Window** menu.</span></span> <span data-ttu-id="c3ac9-135">Certifique-se de que **WF45GettingStartedTutorial** está selecionado na **bancos de dados disponíveis** lista suspensa e escolha **Execute** do **consulta**menu.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-135">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="c3ac9-136">É importante executar as duas etapas anteriores na ordem correta.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-136">It is important to perform the previous two steps in the correct order.</span></span> <span data-ttu-id="c3ac9-137">Se as consultas forem executadas fora de ordem, ocorrerão erros e o banco de dados de persistência não estará configurado corretamente.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-137">If the queries are executed out of order, errors occur and the persistence database is not configured correctly.</span></span>  
  
### <a name="BKMK_AddReference"></a> <span data-ttu-id="c3ac9-138">Para adicionar a referência aos assemblies do DurableInstancing</span><span class="sxs-lookup"><span data-stu-id="c3ac9-138">To add the reference to the DurableInstancing assemblies</span></span>  
  
1. <span data-ttu-id="c3ac9-139">Clique com botão direito **NumberGuessWorkflowHost** na **Gerenciador de soluções** e selecione **Add Reference**.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-139">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Add Reference**.</span></span>  
  
2. <span data-ttu-id="c3ac9-140">Selecione **Assemblies** da **adicionar referência** lista e digite `DurableInstancing` no **pesquisar Assemblies** caixa.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-140">Select **Assemblies** from the **Add Reference** list, and type `DurableInstancing` into the **Search Assemblies** box.</span></span> <span data-ttu-id="c3ac9-141">Isso filtra os assemblies e facilita a seleção das referências desejadas.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-141">This filters the assemblies and makes the desired references easier to select.</span></span>  
  
3. <span data-ttu-id="c3ac9-142">Marque a caixa de seleção ao lado **durableinstancing** e **System.Runtime.DurableInstancing** do **resultados da pesquisa** lista e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-142">Check the checkbox beside **System.Activities.DurableInstancing** and **System.Runtime.DurableInstancing** from the **Search Results** list, and click **OK**.</span></span>  
  
### <a name="BKMK_CreateForm"></a> <span data-ttu-id="c3ac9-143">Para criar o formulário de host de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c3ac9-143">To create the workflow host form</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3ac9-144">As etapas neste procedimento descrevem como adicionar e configurar manualmente o formulário.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-144">The steps in this procedure describe how to add and configure the form manually.</span></span> <span data-ttu-id="c3ac9-145">Se for desejar, você poderá baixar os arquivos da solução para o tutorial e adicionar o formulário concluído ao projeto.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-145">If desired, you can download the solution files for the tutorial and add the completed form to the project.</span></span> <span data-ttu-id="c3ac9-146">Para baixar os arquivos do tutorial, consulte [Windows Workflow Foundation (WF45) - Tutorial de Introdução](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="c3ac9-146">To download the tutorial files, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span> <span data-ttu-id="c3ac9-147">Depois que os arquivos são baixados, clique com botão direito **NumberGuessWorkflowHost** e escolha **adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-147">Once the files are downloaded, right-click **NumberGuessWorkflowHost** and choose **Add Reference**.</span></span> <span data-ttu-id="c3ac9-148">Adicione uma referência ao **Forms** e **System. Drawing**.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-148">Add a reference to **System.Windows.Forms** and **System.Drawing**.</span></span> <span data-ttu-id="c3ac9-149">Essas referências são adicionadas automaticamente se você adicionar um novo formulário do **Add**, **Novo Item** menu, mas devem ser adicionadas manualmente ao importar um formulário.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-149">These references are added automatically if you add a new form from the **Add**, **New Item** menu, but must be added manually when importing a form.</span></span> <span data-ttu-id="c3ac9-150">Depois que as referências são adicionadas, clique com botão direito **NumberGuessWorkflowHost** na **Gerenciador de soluções** e escolha **Add**, **Item existente**.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-150">Once the references are added, right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Existing Item**.</span></span> <span data-ttu-id="c3ac9-151">Navegue até a `Form` pasta nos arquivos de projeto, selecionadas **WorkflowHostForm.cs** (ou **Workflowhostform**) e clique em **Add**.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-151">Browse to the `Form` folder in the project files, select **WorkflowHostForm.cs** (or **WorkflowHostForm.vb**), and click **Add**.</span></span> <span data-ttu-id="c3ac9-152">Se você optar por importar o formulário e, em seguida, você poderá pular para a próxima seção, [para adicionar as propriedades e métodos auxiliares do formulário](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods).</span><span class="sxs-lookup"><span data-stu-id="c3ac9-152">If you choose to import the form, then you can skip down to the next section, [To add the properties and helper methods of the form](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods).</span></span>  
  
1. <span data-ttu-id="c3ac9-153">Clique com botão direito **NumberGuessWorkflowHost** na **Gerenciador de soluções** e escolha **Add**, **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-153">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="c3ac9-154">No **instalados** modelos, escolha **formulário do Windows**, tipo `WorkflowHostForm` no **nome** caixa e, em seguida, clique em **adicionar**.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-154">In the **Installed** templates list, choose **Windows Form**, type `WorkflowHostForm` in the **Name** box, and click **Add**.</span></span>  
  
3. <span data-ttu-id="c3ac9-155">Configure as propriedades a seguir no formulário.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-155">Configure the following properties on the form.</span></span>  
  
    |<span data-ttu-id="c3ac9-156">Propriedade</span><span class="sxs-lookup"><span data-stu-id="c3ac9-156">Property</span></span>|<span data-ttu-id="c3ac9-157">Valor</span><span class="sxs-lookup"><span data-stu-id="c3ac9-157">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="c3ac9-158">FormBorderStyle</span><span class="sxs-lookup"><span data-stu-id="c3ac9-158">FormBorderStyle</span></span>|<span data-ttu-id="c3ac9-159">FixedSingle</span><span class="sxs-lookup"><span data-stu-id="c3ac9-159">FixedSingle</span></span>|  
    |<span data-ttu-id="c3ac9-160">MaximizeBox</span><span class="sxs-lookup"><span data-stu-id="c3ac9-160">MaximizeBox</span></span>|<span data-ttu-id="c3ac9-161">False</span><span class="sxs-lookup"><span data-stu-id="c3ac9-161">False</span></span>|  
    |<span data-ttu-id="c3ac9-162">Tamanho</span><span class="sxs-lookup"><span data-stu-id="c3ac9-162">Size</span></span>|<span data-ttu-id="c3ac9-163">400, 420</span><span class="sxs-lookup"><span data-stu-id="c3ac9-163">400, 420</span></span>|  
  
4. <span data-ttu-id="c3ac9-164">Adicione os seguintes controles ao formulário na ordem especificada e configure as propriedades como direcionadas.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-164">Add the following controls to the form in the order specified and configure the properties as directed.</span></span>  
  
    |<span data-ttu-id="c3ac9-165">Controle</span><span class="sxs-lookup"><span data-stu-id="c3ac9-165">Control</span></span>|<span data-ttu-id="c3ac9-166">Propriedade: Valor</span><span class="sxs-lookup"><span data-stu-id="c3ac9-166">Property: Value</span></span>|  
    |-------------|---------------------|  
    |<span data-ttu-id="c3ac9-167">**Button**</span><span class="sxs-lookup"><span data-stu-id="c3ac9-167">**Button**</span></span>|<span data-ttu-id="c3ac9-168">Nome: NewGame</span><span class="sxs-lookup"><span data-stu-id="c3ac9-168">Name: NewGame</span></span><br /><br /> <span data-ttu-id="c3ac9-169">Local: 13, 13</span><span class="sxs-lookup"><span data-stu-id="c3ac9-169">Location: 13, 13</span></span><br /><br /> <span data-ttu-id="c3ac9-170">Tamanho: 75, 23</span><span class="sxs-lookup"><span data-stu-id="c3ac9-170">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="c3ac9-171">Texto: New Game</span><span class="sxs-lookup"><span data-stu-id="c3ac9-171">Text: New Game</span></span>|  
    |<span data-ttu-id="c3ac9-172">**Rótulo**</span><span class="sxs-lookup"><span data-stu-id="c3ac9-172">**Label**</span></span>|<span data-ttu-id="c3ac9-173">Local: 94, 18</span><span class="sxs-lookup"><span data-stu-id="c3ac9-173">Location: 94, 18</span></span><br /><br /> <span data-ttu-id="c3ac9-174">Texto: Dê o palpite de um número de 1 a</span><span class="sxs-lookup"><span data-stu-id="c3ac9-174">Text: Guess a number from 1 to</span></span>|  
    |<span data-ttu-id="c3ac9-175">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="c3ac9-175">**ComboBox**</span></span>|<span data-ttu-id="c3ac9-176">Nome: NumberRange</span><span class="sxs-lookup"><span data-stu-id="c3ac9-176">Name: NumberRange</span></span><br /><br /> <span data-ttu-id="c3ac9-177">DropDownStyle: DropDownList</span><span class="sxs-lookup"><span data-stu-id="c3ac9-177">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="c3ac9-178">Itens: 10, 100, 1000</span><span class="sxs-lookup"><span data-stu-id="c3ac9-178">Items: 10, 100, 1000</span></span><br /><br /> <span data-ttu-id="c3ac9-179">Local: 228, 12</span><span class="sxs-lookup"><span data-stu-id="c3ac9-179">Location: 228, 12</span></span><br /><br /> <span data-ttu-id="c3ac9-180">Tamanho: 143, 21</span><span class="sxs-lookup"><span data-stu-id="c3ac9-180">Size: 143, 21</span></span>|  
    |<span data-ttu-id="c3ac9-181">**Rótulo**</span><span class="sxs-lookup"><span data-stu-id="c3ac9-181">**Label**</span></span>|<span data-ttu-id="c3ac9-182">Local: 13, 43</span><span class="sxs-lookup"><span data-stu-id="c3ac9-182">Location: 13, 43</span></span><br /><br /> <span data-ttu-id="c3ac9-183">Texto: Tipo de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c3ac9-183">Text: Workflow type</span></span>|  
    |<span data-ttu-id="c3ac9-184">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="c3ac9-184">**ComboBox**</span></span>|<span data-ttu-id="c3ac9-185">Nome: WorkflowType</span><span class="sxs-lookup"><span data-stu-id="c3ac9-185">Name: WorkflowType</span></span><br /><br /> <span data-ttu-id="c3ac9-186">DropDownStyle: DropDownList</span><span class="sxs-lookup"><span data-stu-id="c3ac9-186">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="c3ac9-187">Itens: StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="c3ac9-187">Items: StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow</span></span><br /><br /> <span data-ttu-id="c3ac9-188">Local: 94, 40</span><span class="sxs-lookup"><span data-stu-id="c3ac9-188">Location: 94, 40</span></span><br /><br /> <span data-ttu-id="c3ac9-189">Tamanho: 277, 21</span><span class="sxs-lookup"><span data-stu-id="c3ac9-189">Size: 277, 21</span></span>|  
    |<span data-ttu-id="c3ac9-190">**Rótulo**</span><span class="sxs-lookup"><span data-stu-id="c3ac9-190">**Label**</span></span>|<span data-ttu-id="c3ac9-191">Nome: WorkflowVersion</span><span class="sxs-lookup"><span data-stu-id="c3ac9-191">Name: WorkflowVersion</span></span><br /><br /> <span data-ttu-id="c3ac9-192">Local: 13, 362</span><span class="sxs-lookup"><span data-stu-id="c3ac9-192">Location: 13, 362</span></span><br /><br /> <span data-ttu-id="c3ac9-193">Texto: Versão do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c3ac9-193">Text: Workflow version</span></span>|  
    |<span data-ttu-id="c3ac9-194">**GroupBox**</span><span class="sxs-lookup"><span data-stu-id="c3ac9-194">**GroupBox**</span></span>|<span data-ttu-id="c3ac9-195">Local: 13, 67</span><span class="sxs-lookup"><span data-stu-id="c3ac9-195">Location: 13, 67</span></span><br /><br /> <span data-ttu-id="c3ac9-196">Tamanho: 358, 287</span><span class="sxs-lookup"><span data-stu-id="c3ac9-196">Size: 358, 287</span></span><br /><br /> <span data-ttu-id="c3ac9-197">Texto: Jogo</span><span class="sxs-lookup"><span data-stu-id="c3ac9-197">Text: Game</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="c3ac9-198">Ao adicionar os seguintes controles, coloque-os na caixa de grupo.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-198">When adding the following controls, put them into the GroupBox.</span></span>  
  
    |<span data-ttu-id="c3ac9-199">Controle</span><span class="sxs-lookup"><span data-stu-id="c3ac9-199">Control</span></span>|<span data-ttu-id="c3ac9-200">Propriedade: Valor</span><span class="sxs-lookup"><span data-stu-id="c3ac9-200">Property: Value</span></span>|  
    |-------------|---------------------|  
    |<span data-ttu-id="c3ac9-201">**Rótulo**</span><span class="sxs-lookup"><span data-stu-id="c3ac9-201">**Label**</span></span>|<span data-ttu-id="c3ac9-202">Local: 7, 20</span><span class="sxs-lookup"><span data-stu-id="c3ac9-202">Location: 7, 20</span></span><br /><br /> <span data-ttu-id="c3ac9-203">Texto: ID de Instância do Fluxo de Trabalho</span><span class="sxs-lookup"><span data-stu-id="c3ac9-203">Text: Workflow Instance Id</span></span>|  
    |<span data-ttu-id="c3ac9-204">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="c3ac9-204">**ComboBox**</span></span>|<span data-ttu-id="c3ac9-205">Nome: InstanceId</span><span class="sxs-lookup"><span data-stu-id="c3ac9-205">Name: InstanceId</span></span><br /><br /> <span data-ttu-id="c3ac9-206">DropDownStyle: DropDownList</span><span class="sxs-lookup"><span data-stu-id="c3ac9-206">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="c3ac9-207">Local: 121, 17</span><span class="sxs-lookup"><span data-stu-id="c3ac9-207">Location: 121, 17</span></span><br /><br /> <span data-ttu-id="c3ac9-208">Tamanho: 227, 21</span><span class="sxs-lookup"><span data-stu-id="c3ac9-208">Size: 227, 21</span></span>|  
    |<span data-ttu-id="c3ac9-209">**Rótulo**</span><span class="sxs-lookup"><span data-stu-id="c3ac9-209">**Label**</span></span>|<span data-ttu-id="c3ac9-210">Local: 7, 47</span><span class="sxs-lookup"><span data-stu-id="c3ac9-210">Location: 7, 47</span></span><br /><br /> <span data-ttu-id="c3ac9-211">Texto: Palpite</span><span class="sxs-lookup"><span data-stu-id="c3ac9-211">Text: Guess</span></span>|  
    |<span data-ttu-id="c3ac9-212">**TextBox**</span><span class="sxs-lookup"><span data-stu-id="c3ac9-212">**TextBox**</span></span>|<span data-ttu-id="c3ac9-213">Nome: Palpite</span><span class="sxs-lookup"><span data-stu-id="c3ac9-213">Name: Guess</span></span><br /><br /> <span data-ttu-id="c3ac9-214">Local: 50, 44</span><span class="sxs-lookup"><span data-stu-id="c3ac9-214">Location: 50, 44</span></span><br /><br /> <span data-ttu-id="c3ac9-215">Tamanho: 65, 20</span><span class="sxs-lookup"><span data-stu-id="c3ac9-215">Size: 65, 20</span></span>|  
    |<span data-ttu-id="c3ac9-216">**Button**</span><span class="sxs-lookup"><span data-stu-id="c3ac9-216">**Button**</span></span>|<span data-ttu-id="c3ac9-217">Nome: EnterGuess</span><span class="sxs-lookup"><span data-stu-id="c3ac9-217">Name: EnterGuess</span></span><br /><br /> <span data-ttu-id="c3ac9-218">Local: 121, 42</span><span class="sxs-lookup"><span data-stu-id="c3ac9-218">Location: 121, 42</span></span><br /><br /> <span data-ttu-id="c3ac9-219">Tamanho: 75, 23</span><span class="sxs-lookup"><span data-stu-id="c3ac9-219">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="c3ac9-220">Texto: Enter Guess</span><span class="sxs-lookup"><span data-stu-id="c3ac9-220">Text: Enter Guess</span></span>|  
    |<span data-ttu-id="c3ac9-221">**Button**</span><span class="sxs-lookup"><span data-stu-id="c3ac9-221">**Button**</span></span>|<span data-ttu-id="c3ac9-222">Nome: QuitGame</span><span class="sxs-lookup"><span data-stu-id="c3ac9-222">Name: QuitGame</span></span><br /><br /> <span data-ttu-id="c3ac9-223">Local: 274, 42</span><span class="sxs-lookup"><span data-stu-id="c3ac9-223">Location: 274, 42</span></span><br /><br /> <span data-ttu-id="c3ac9-224">Tamanho: 75, 23</span><span class="sxs-lookup"><span data-stu-id="c3ac9-224">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="c3ac9-225">Texto: Encerrar</span><span class="sxs-lookup"><span data-stu-id="c3ac9-225">Text: Quit</span></span>|  
    |<span data-ttu-id="c3ac9-226">**TextBox**</span><span class="sxs-lookup"><span data-stu-id="c3ac9-226">**TextBox**</span></span>|<span data-ttu-id="c3ac9-227">Nome: WorkflowStatus</span><span class="sxs-lookup"><span data-stu-id="c3ac9-227">Name: WorkflowStatus</span></span><br /><br /> <span data-ttu-id="c3ac9-228">Local: 10, 73</span><span class="sxs-lookup"><span data-stu-id="c3ac9-228">Location: 10, 73</span></span><br /><br /> <span data-ttu-id="c3ac9-229">Várias linhas: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="c3ac9-229">Multiline: True</span></span><br /><br /> <span data-ttu-id="c3ac9-230">ReadOnly: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="c3ac9-230">ReadOnly: True</span></span><br /><br /> <span data-ttu-id="c3ac9-231">ScrollBars: Vertical</span><span class="sxs-lookup"><span data-stu-id="c3ac9-231">ScrollBars: Vertical</span></span><br /><br /> <span data-ttu-id="c3ac9-232">Tamanho: 338, 208</span><span class="sxs-lookup"><span data-stu-id="c3ac9-232">Size: 338, 208</span></span>|  
  
5. <span data-ttu-id="c3ac9-233">Defina as **AcceptButton** propriedades do formulário para **EnterGuess**.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-233">Set the **AcceptButton** property of the form to **EnterGuess**.</span></span>  
  
 <span data-ttu-id="c3ac9-234">O exemplo a seguir ilustra o formato concluído.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-234">The following example illustrates the completed form.</span></span>  
  
 <span data-ttu-id="c3ac9-235">![WF45 Introdução ao formulário de Host de fluxo de trabalho Tutorial](./media/wf45gettingstartedtutorialworkflowhostform.png "WF45GettingStartedTutorialWorkflowHostForm")</span><span class="sxs-lookup"><span data-stu-id="c3ac9-235">![WF45 Getting Started Tutorial Workflow Host Form](./media/wf45gettingstartedtutorialworkflowhostform.png "WF45GettingStartedTutorialWorkflowHostForm")</span></span>  
  
### <a name="BKMK_AddHelperMethods"></a> <span data-ttu-id="c3ac9-236">Para adicionar as propriedades e métodos auxiliares do formulário</span><span class="sxs-lookup"><span data-stu-id="c3ac9-236">To add the properties and helper methods of the form</span></span>  
 <span data-ttu-id="c3ac9-237">As etapas nesta seção adicionam propriedades e métodos auxiliares para a classe de formulário que configura a interface de usuário do formulário para dar suporte à execução e à retomada de fluxos de trabalho de palpite de número.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-237">The steps in this section add properties and helper methods to the form class that configure the UI of the form to support running and resuming number guess workflows.</span></span>  
  
1. <span data-ttu-id="c3ac9-238">Clique com botão direito **WorkflowHostForm** na **Gerenciador de soluções** e escolha **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-238">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="c3ac9-239">Adicione as seguintes instruções `using` (ou `Imports`) na parte superior do arquivo com as outras instruções `using` (ou `Imports`).</span><span class="sxs-lookup"><span data-stu-id="c3ac9-239">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Windows.Forms  
    Imports System.Activities.DurableInstancing  
    Imports System.Activities  
    Imports System.Data.SqlClient  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Windows.Forms;  
    using System.Activities.DurableInstancing;  
    using System.Activities;  
    using System.Data.SqlClient;  
    using System.IO;  
    ```  
  
3. <span data-ttu-id="c3ac9-240">Adicione as seguintes declarações de membro para o **WorkflowHostForm** classe.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-240">Add the following member declarations to the **WorkflowHostForm** class.</span></span>  
  
    ```vb  
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"  
    Dim store As SqlWorkflowInstanceStore  
    Dim WorkflowStarting As Boolean  
    ```  
  
    ```csharp  
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";  
    SqlWorkflowInstanceStore store;  
    bool WorkflowStarting;  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="c3ac9-241">Se sua cadeia de conexão for diferente, atualize `connectionString` para se referir a seu banco de dados.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-241">If your connection string is different, update `connectionString` to refer to your database.</span></span>  
  
4. <span data-ttu-id="c3ac9-242">Adicione uma propriedade `WorkflowInstanceId` à classe `WorkflowFormHost`.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-242">Add a `WorkflowInstanceId` property to the `WorkflowFormHost` class.</span></span>  
  
    ```vb  
    Public ReadOnly Property WorkflowInstanceId() As Guid  
        Get  
            If InstanceId.SelectedIndex = -1 Then  
                Return Guid.Empty  
            Else  
                Return New Guid(InstanceId.SelectedItem.ToString())  
            End If  
        End Get  
    End Property  
    ```  
  
    ```csharp  
    public Guid WorkflowInstanceId  
    {  
        get  
        {  
            return InstanceId.SelectedIndex == -1 ? Guid.Empty : (Guid)InstanceId.SelectedItem;  
        }  
    }  
    ```  
  
     <span data-ttu-id="c3ac9-243">O `InstanceId` caixa de combinação exibe uma lista de ids de instância de fluxo de trabalho persistida e o `WorkflowInstanceId` propriedade retorna o fluxo de trabalho selecionado no momento.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-243">The `InstanceId` combo box displays a list of persisted workflow instance ids, and the `WorkflowInstanceId` property returns the currently selected workflow.</span></span>  
  
5. <span data-ttu-id="c3ac9-244">Adicione um manipulador para o evento `Load` do formulário.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-244">Add a handler for the form `Load` event.</span></span> <span data-ttu-id="c3ac9-245">Para adicionar o manipulador, alterne para **modo de exibição de Design** para o formulário, clique no **eventos** ícone na parte superior dos **propriedades** janela e clique duas vezes em **carga**.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-245">To add the handler, switch to **Design View** for the form, click the **Events** icon at the top of the **Properties** window, and double-click **Load**.</span></span>  
  
    ```vb  
    Private Sub WorkflowHostForm_Load(sender As Object, e As EventArgs) Handles Me.Load  
  
    End Sub  
    ```  
  
    ```csharp  
    private void WorkflowHostForm_Load(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
6. <span data-ttu-id="c3ac9-246">Adicione o código a seguir ao `WorkflowHostForm_Load`.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-246">Add the following code to `WorkflowHostForm_Load`.</span></span>  
  
    ```vb  
    'Initialize the store and configure it so that it can be used for  
    'multiple WorkflowApplication instances.  
    store = New SqlWorkflowInstanceStore(connectionString)  
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)  
  
    'Set default ComboBox selections.  
    NumberRange.SelectedIndex = 0  
    WorkflowType.SelectedIndex = 0  
  
    ListPersistedWorkflows()  
    ```  
  
    ```csharp  
    // Initialize the store and configure it so that it can be used for  
    // multiple WorkflowApplication instances.  
    store = new SqlWorkflowInstanceStore(connectionString);  
    WorkflowApplication.CreateDefaultInstanceOwner(store, null, WorkflowIdentityFilter.Any);  
  
    // Set default ComboBox selections.  
    NumberRange.SelectedIndex = 0;  
    WorkflowType.SelectedIndex = 0;  
  
    ListPersistedWorkflows();  
    ```  
  
     <span data-ttu-id="c3ac9-247">Quando o formulário carrega, o `SqlWorkflowInstanceStore` é configurado, as caixas de combinação de intervalo e tipo de fluxo de trabalho são definidas com valores padrão, as instâncias de fluxo de trabalho persistidas são adicionadas à caixa de combinação `InstanceId`.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-247">When the form loads, the `SqlWorkflowInstanceStore` is configured, the range and workflow type combo boxes are set to default values, and the persisted workflow instances are added to the `InstanceId` combo box.</span></span>  
  
7. <span data-ttu-id="c3ac9-248">Adicione um manipulador `SelectedIndexChanged` para `InstanceId`.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-248">Add a `SelectedIndexChanged` handler for `InstanceId`.</span></span> <span data-ttu-id="c3ac9-249">Para adicionar o manipulador, alterne para **modo de exibição de Design** para o formulário, selecione o `InstanceId` caixa de combinação, clique no **eventos** ícone na parte superior do **propriedades** janela, e Clique duas vezes em **SelectedIndexChanged**.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-249">To add the handler, switch to **Design View** for the form, select the `InstanceId` combo box, click the **Events** icon at the top of the **Properties** window, and double-click **SelectedIndexChanged**.</span></span>  
  
    ```vb  
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged  
  
    End Sub  
    ```  
  
    ```csharp  
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
8. <span data-ttu-id="c3ac9-250">Adicione o código a seguir ao `InstanceId_SelectedIndexChanged`.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-250">Add the following code to `InstanceId_SelectedIndexChanged`.</span></span> <span data-ttu-id="c3ac9-251">Sempre que o usuário seleciona um fluxo de trabalho usando a caixa de combinação, esse manipulador atualiza a janela de status.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-251">Whenever the user selects a workflow by using the combo box this handler updates the status window.</span></span>  
  
    ```vb  
    If InstanceId.SelectedIndex = -1 Then  
        Return  
    End If  
  
    'Clear the status window.  
    WorkflowStatus.Clear()  
  
    'Get the workflow version and display it.  
    'If the workflow is just starting then this info will not  
    'be available in the persistence store so do not try and retrieve it.  
    If Not WorkflowStarting Then  
        Dim instance As WorkflowApplicationInstance = _  
            WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
        WorkflowVersion.Text = _  
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity)  
  
        'Unload the instance.  
        instance.Abandon()  
    End If  
    ```  
  
    ```csharp  
    if (InstanceId.SelectedIndex == -1)  
    {  
        return;  
    }  
  
    // Clear the status window.  
    WorkflowStatus.Clear();  
  
    // Get the workflow version and display it.  
    // If the workflow is just starting then this info will not  
    // be available in the persistence store so do not try and retrieve it.  
    if (!WorkflowStarting)  
    {  
        WorkflowApplicationInstance instance =  
            WorkflowApplication.GetInstance(this.WorkflowInstanceId, store);  
  
        WorkflowVersion.Text =  
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity);  
  
        // Unload the instance.  
        instance.Abandon();  
    }  
    ```  
  
9. <span data-ttu-id="c3ac9-252">Adicione o seguinte método `ListPersistedWorkflows` à classe do formulário.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-252">Add the following `ListPersistedWorkflows` method to the form class.</span></span>  
  
    ```vb  
    Private Sub ListPersistedWorkflows()  
        Using localCon As New SqlConnection(connectionString)  
            Dim localCmd As String = _  
                "Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]"  
  
            Dim cmd As SqlCommand = localCon.CreateCommand()  
            cmd.CommandText = localCmd  
            localCon.Open()  
            Using reader As SqlDataReader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
  
                While (reader.Read())  
                    'Get the InstanceId of the persisted Workflow.  
                    Dim id As Guid = Guid.Parse(reader(0).ToString())  
                    InstanceId.Items.Add(id)  
                End While  
            End Using  
        End Using  
    End Sub  
    ```  
  
    ```csharp  
    using (SqlConnection localCon = new SqlConnection(connectionString))  
    {  
        string localCmd =  
            "Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]";  
  
        SqlCommand cmd = localCon.CreateCommand();  
        cmd.CommandText = localCmd;  
        localCon.Open();  
        using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))  
        {  
            while (reader.Read())  
            {  
                // Get the InstanceId of the persisted Workflow  
                Guid id = Guid.Parse(reader[0].ToString());  
                InstanceId.Items.Add(id);  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="c3ac9-253">`ListPersistedWorkflows` consulta o repositório de instâncias em busca de instâncias de fluxo de trabalho persistidas, e adiciona as ids de instância à caixa de combinação `cboInstanceId`.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-253">`ListPersistedWorkflows` queries the instance store for persisted workflow instances, and adds the instance ids to the `cboInstanceId` combo box.</span></span>  
  
10. <span data-ttu-id="c3ac9-254">Adicione o seguinte método `UpdateStatus` e o delegado correspondente à classe de formulário.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-254">Add the following `UpdateStatus` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="c3ac9-255">Este método atualiza a janela de status no formulário com o status do fluxo de trabalho em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-255">This method updates the status window on the form with the status of the currently running workflow.</span></span>  
  
    ```vb  
    Private Delegate Sub UpdateStatusDelegate(msg As String)  
    Public Sub UpdateStatus(msg As String)  
        'We may be on a different thread so we need to  
        'make this call using BeginInvoke.  
        If InvokeRequired Then  
            BeginInvoke(New UpdateStatusDelegate(AddressOf UpdateStatus), msg)  
        Else  
            If Not msg.EndsWith(vbCrLf) Then  
                msg = msg & vbCrLf  
            End If  
  
            WorkflowStatus.AppendText(msg)  
  
            'Ensure that the newly added status is visible.  
            WorkflowStatus.SelectionStart = WorkflowStatus.Text.Length  
            WorkflowStatus.ScrollToCaret()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private delegate void UpdateStatusDelegate(string msg);  
    public void UpdateStatus(string msg)  
    {  
        // We may be on a different thread so we need to  
        // make this call using BeginInvoke.  
        if (InvokeRequired)  
        {  
            BeginInvoke(new UpdateStatusDelegate(UpdateStatus), msg);  
        }  
        else  
        {  
            if (!msg.EndsWith("\r\n"))  
            {  
                msg += "\r\n";  
            }  
            WorkflowStatus.AppendText(msg);  
  
            WorkflowStatus.SelectionStart = WorkflowStatus.Text.Length;  
            WorkflowStatus.ScrollToCaret();  
        }  
    }  
    ```  
  
11. <span data-ttu-id="c3ac9-256">Adicione o seguinte método `GameOver` e o delegado correspondente à classe de formulário.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-256">Add the following `GameOver` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="c3ac9-257">Quando um fluxo de trabalho for concluído, esse método atualiza o formulário da interface do usuário, removendo a id da instância de fluxo de trabalho concluído do **InstanceId** caixa de combinação.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-257">When a workflow completes, this method updates the form UI by removing the instance id of the completed workflow from the **InstanceId** combo box.</span></span>  
  
    ```vb  
    Private Delegate Sub GameOverDelegate()  
    Private Sub GameOver()  
        If InvokeRequired Then  
            BeginInvoke(New GameOverDelegate(AddressOf GameOver))  
        Else  
            'Remove this instance from the InstanceId combo box.  
            InstanceId.Items.Remove(InstanceId.SelectedItem)  
            InstanceId.SelectedIndex = -1  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private delegate void GameOverDelegate();  
    private void GameOver()  
    {  
        if (InvokeRequired)  
        {  
            BeginInvoke(new GameOverDelegate(GameOver));  
        }  
        else  
        {  
            // Remove this instance from the combo box  
            InstanceId.Items.Remove(InstanceId.SelectedItem);  
            InstanceId.SelectedIndex = -1;  
        }  
    }  
    ```  
  
### <a name="BKMK_ConfigureWorkflowApplication"></a> <span data-ttu-id="c3ac9-258">Para configurar o armazenamento de instância, manipuladores de ciclo de vida de fluxo de trabalho e extensões</span><span class="sxs-lookup"><span data-stu-id="c3ac9-258">To configure the instance store, workflow lifecycle handlers, and extensions</span></span>  
  
1. <span data-ttu-id="c3ac9-259">Adicione o método `ConfigureWorkflowApplication` à classe do formulário.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-259">Add a `ConfigureWorkflowApplication` method to the form class.</span></span>  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
  
    End Sub  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {      
    }  
    ```  
  
     <span data-ttu-id="c3ac9-260">Esse método configura o `WorkflowApplication`, adiciona as extensões desejadas e adicionar manipuladores aos eventos de ciclo de vida do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-260">This method configures the `WorkflowApplication`, adds the desired extensions, and adds handlers for the workflow lifecycle events.</span></span>  
  
2. <span data-ttu-id="c3ac9-261">Em `ConfigureWorkflowApplication`, especifique o `SqlWorkflowInstanceStore` para o `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-261">In `ConfigureWorkflowApplication`, specify the `SqlWorkflowInstanceStore` for the `WorkflowApplication`.</span></span>  
  
    ```vb  
    'Configure the persistence store.  
    wfApp.InstanceStore = store  
    ```  
  
    ```csharp  
    // Configure the persistence store.  
    wfApp.InstanceStore = store;  
    ```  
  
3. <span data-ttu-id="c3ac9-262">Em seguida, crie uma instância `StringWriter` e adicione-a à coleção de `Extensions` do `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-262">Next, create a `StringWriter` instance and add it to the `Extensions` collection of the `WorkflowApplication`.</span></span> <span data-ttu-id="c3ac9-263">Quando um `StringWriter` é adicionado às extensões, ele captura todas as `WriteLine` saída da atividade.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-263">When a `StringWriter` is added to the extensions it captures all `WriteLine` activity output.</span></span> <span data-ttu-id="c3ac9-264">Quando o fluxo de trabalho fica ocioso, a saída de `WriteLine` pode ser extraída de `StringWriter` e exibida no formulário.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-264">When the workflow becomes idle, the `WriteLine` output can be extracted from the `StringWriter` and displayed on the form.</span></span>  
  
    ```vb  
    'Add a StringWriter to the extensions. This captures the output  
    'from the WriteLine activities so we can display it in the form.  
    Dim sw As New StringWriter()  
    wfApp.Extensions.Add(sw)  
    ```  
  
    ```csharp  
    // Add a StringWriter to the extensions. This captures the output  
    // from the WriteLine activities so we can display it in the form.  
    StringWriter sw = new StringWriter();  
    wfApp.Extensions.Add(sw);  
    ```  
  
4. <span data-ttu-id="c3ac9-265">Adicione o seguinte manipulador para o evento `Completed`.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-265">Add the following handler for the `Completed` event.</span></span> <span data-ttu-id="c3ac9-266">Quando um fluxo de trabalho for concluído com êxito, o número de sequências realizadas para dar um palpite do número é exibido na janela de status.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-266">When a workflow successfully completes, the number of turns taken to guess the number is displayed to the status window.</span></span> <span data-ttu-id="c3ac9-267">Se o fluxo de trabalho terminar, as informações da exceção que causaram a conclusão serão exibidas.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-267">If the workflow terminates, the exception information that caused the termination is displayed.</span></span> <span data-ttu-id="c3ac9-268">No final do manipulador, o método `GameOver` é chamado, o que remove o fluxo de trabalho concluído da lista de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-268">At the end of the handler the `GameOver` method is called, which removes the completed workflow from the workflow list.</span></span>  
  
    ```vb  
    wfApp.Completed = _  
        Sub(e As WorkflowApplicationCompletedEventArgs)  
            If e.CompletionState = ActivityInstanceState.Faulted Then  
                UpdateStatus(String.Format("Workflow Terminated. Exception: {0}" & vbCrLf & "{1}", _  
                    e.TerminationException.GetType().FullName, _  
                    e.TerminationException.Message))  
            ElseIf e.CompletionState = ActivityInstanceState.Canceled Then  
                UpdateStatus("Workflow Canceled.")  
            Else  
                Dim Turns As Integer = Convert.ToInt32(e.Outputs("Turns"))  
                UpdateStatus(String.Format("Congratulations, you guessed the number in {0} turns.", Turns))  
            End If  
            GameOver()  
        End Sub  
    ```  
  
    ```csharp  
    wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
    {  
        if (e.CompletionState == ActivityInstanceState.Faulted)  
        {  
            UpdateStatus(string.Format("Workflow Terminated. Exception: {0}\r\n{1}",  
                e.TerminationException.GetType().FullName,  
                e.TerminationException.Message));  
        }  
        else if (e.CompletionState == ActivityInstanceState.Canceled)  
        {  
            UpdateStatus("Workflow Canceled.");  
        }  
        else  
        {  
            int Turns = Convert.ToInt32(e.Outputs["Turns"]);  
            UpdateStatus(string.Format("Congratulations, you guessed the number in {0} turns.", Turns));  
        }  
        GameOver();  
    };  
    ```  
  
5. <span data-ttu-id="c3ac9-269">Adicione os seguintes manipuladores `Aborted` e `OnUnhandledException`.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-269">Add the following `Aborted` and `OnUnhandledException` handlers.</span></span> <span data-ttu-id="c3ac9-270">O método `GameOver` não é chamado do manipulador `Aborted` porque, quando uma instância de fluxo de trabalho é cancelada, ela não termina e é possível retomar a instância posteriormente.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-270">The `GameOver` method is not called from the `Aborted` handler because when a workflow instance is aborted, it does not terminate, and it is possible to resume the instance at a later time.</span></span>  
  
    ```vb  
    wfApp.Aborted = _  
        Sub(e As WorkflowApplicationAbortedEventArgs)  
            UpdateStatus(String.Format("Workflow Aborted. Exception: {0}" & vbCrLf & "{1}", _  
                e.Reason.GetType().FullName, _  
                e.Reason.Message))  
        End Sub  
  
    wfApp.OnUnhandledException = _  
        Function(e As WorkflowApplicationUnhandledExceptionEventArgs)  
            UpdateStatus(String.Format("Unhandled Exception: {0}" & vbCrLf & "{1}", _  
                e.UnhandledException.GetType().FullName, _  
                e.UnhandledException.Message))  
            GameOver()  
            Return UnhandledExceptionAction.Terminate  
        End Function  
    ```  
  
    ```csharp  
    wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)  
    {  
        UpdateStatus(string.Format("Workflow Aborted. Exception: {0}\r\n{1}",  
                e.Reason.GetType().FullName,  
                e.Reason.Message));  
    };  
  
    wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)  
    {  
        UpdateStatus(string.Format("Unhandled Exception: {0}\r\n{1}",  
                e.UnhandledException.GetType().FullName,  
                e.UnhandledException.Message));  
        GameOver();  
        return UnhandledExceptionAction.Terminate;  
    };  
    ```  
  
6. <span data-ttu-id="c3ac9-271">Adicione o seguinte manipulador `PersistableIdle`.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-271">Add the following `PersistableIdle` handler.</span></span> <span data-ttu-id="c3ac9-272">Este manipulador recupera a extensão `StringWriter` que foi adicionada, extrai a saída das atividades de `WriteLine` e as exibe na janela de status.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-272">This handler retrieves the `StringWriter` extension that was added, extracts the output from the `WriteLine` activities, and displays it in the status window.</span></span>  
  
    ```vb  
    wfApp.PersistableIdle = _  
        Function(e As WorkflowApplicationIdleEventArgs)  
            'Send the current WriteLine outputs to the status window.  
            Dim writers = e.GetInstanceExtensions(Of StringWriter)()  
            For Each writer In writers  
                UpdateStatus(writer.ToString())  
            Next  
            Return PersistableIdleAction.Unload  
        End Function  
    ```  
  
    ```csharp  
    wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
    {  
        // Send the current WriteLine outputs to the status window.  
        var writers = e.GetInstanceExtensions<StringWriter>();  
        foreach (var writer in writers)  
        {  
            UpdateStatus(writer.ToString());  
        }  
        return PersistableIdleAction.Unload;  
    };  
    ```  
  
     <span data-ttu-id="c3ac9-273">A enumeração <xref:System.Activities.PersistableIdleAction> tem três valores: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist> e <xref:System.Activities.PersistableIdleAction.Unload>.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-273">The <xref:System.Activities.PersistableIdleAction> enumeration has three values: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>, and <xref:System.Activities.PersistableIdleAction.Unload>.</span></span> <span data-ttu-id="c3ac9-274"><xref:System.Activities.PersistableIdleAction.Persist> faz com o fluxo de trabalho persistir, mas não faz o fluxo de trabalho descarregar.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-274"><xref:System.Activities.PersistableIdleAction.Persist> causes the workflow to persist but it does not cause the workflow to unload.</span></span> <span data-ttu-id="c3ac9-275"><xref:System.Activities.PersistableIdleAction.Unload> faz o fluxo de trabalho persistir e ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-275"><xref:System.Activities.PersistableIdleAction.Unload> causes the workflow to persist and be unloaded.</span></span>  
  
     <span data-ttu-id="c3ac9-276">O exemplo a seguir é o método `ConfigureWorkflowApplication` concluído.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-276">The following example is the completed `ConfigureWorkflowApplication` method.</span></span>  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
        'Configure the persistence store.  
        wfApp.InstanceStore = store  
  
        'Add a StringWriter to the extensions. This captures the output  
        'from the WriteLine activities so we can display it in the form.  
        Dim sw As New StringWriter()  
        wfApp.Extensions.Add(sw)  
  
        wfApp.Completed = _  
            Sub(e As WorkflowApplicationCompletedEventArgs)  
                If e.CompletionState = ActivityInstanceState.Faulted Then  
                    UpdateStatus(String.Format("Workflow Terminated. Exception: {0}" & vbCrLf & "{1}", _  
                        e.TerminationException.GetType().FullName, _  
                        e.TerminationException.Message))  
                ElseIf e.CompletionState = ActivityInstanceState.Canceled Then  
                    UpdateStatus("Workflow Canceled.")  
                Else  
                    Dim Turns As Integer = Convert.ToInt32(e.Outputs("Turns"))  
                    UpdateStatus(String.Format("Congratulations, you guessed the number in {0} turns.", Turns))  
                End If  
                GameOver()  
            End Sub  
  
        wfApp.Aborted = _  
            Sub(e As WorkflowApplicationAbortedEventArgs)  
                UpdateStatus(String.Format("Workflow Aborted. Exception: {0}" & vbCrLf & "{1}", _  
                    e.Reason.GetType().FullName, _  
                    e.Reason.Message))  
            End Sub  
  
        wfApp.OnUnhandledException = _  
            Function(e As WorkflowApplicationUnhandledExceptionEventArgs)  
                UpdateStatus(String.Format("Unhandled Exception: {0}" & vbCrLf & "{1}", _  
                    e.UnhandledException.GetType().FullName, _  
                    e.UnhandledException.Message))  
                GameOver()  
                Return UnhandledExceptionAction.Terminate  
            End Function  
  
        wfApp.PersistableIdle = _  
            Function(e As WorkflowApplicationIdleEventArgs)  
                'Send the current WriteLine outputs to the status window.  
                Dim writers = e.GetInstanceExtensions(Of StringWriter)()  
                For Each writer In writers  
                    UpdateStatus(writer.ToString())  
                Next  
                Return PersistableIdleAction.Unload  
            End Function  
    End Sub  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {  
        // Configure the persistence store.  
        wfApp.InstanceStore = store;  
  
        // Add a StringWriter to the extensions. This captures the output  
        // from the WriteLine activities so we can display it in the form.  
        StringWriter sw = new StringWriter();  
        wfApp.Extensions.Add(sw);  
  
        wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
        {  
            if (e.CompletionState == ActivityInstanceState.Faulted)  
            {  
                UpdateStatus(string.Format("Workflow Terminated. Exception: {0}\r\n{1}",  
                    e.TerminationException.GetType().FullName,  
                    e.TerminationException.Message));  
            }  
            else if (e.CompletionState == ActivityInstanceState.Canceled)  
            {  
                UpdateStatus("Workflow Canceled.");  
            }  
            else  
            {  
                int Turns = Convert.ToInt32(e.Outputs["Turns"]);  
                UpdateStatus(string.Format("Congratulations, you guessed the number in {0} turns.", Turns));  
            }  
            GameOver();  
        };  
  
        wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)  
        {  
            UpdateStatus(string.Format("Workflow Aborted. Exception: {0}\r\n{1}",  
                    e.Reason.GetType().FullName,  
                    e.Reason.Message));  
        };  
  
        wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)  
        {  
            UpdateStatus(string.Format("Unhandled Exception: {0}\r\n{1}",  
                    e.UnhandledException.GetType().FullName,  
                    e.UnhandledException.Message));  
            GameOver();  
            return UnhandledExceptionAction.Terminate;  
        };  
  
        wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
        {  
            // Send the current WriteLine outputs to the status window.  
            var writers = e.GetInstanceExtensions<StringWriter>();  
            foreach (var writer in writers)  
            {  
                UpdateStatus(writer.ToString());  
            }  
            return PersistableIdleAction.Unload;  
        };  
    }  
    ```  
  
### <a name="BKMK_WorkflowVersionMap"></a> <span data-ttu-id="c3ac9-277">Para habilitar o início e retomada de vários tipos de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c3ac9-277">To enable starting and resuming multiple workflow types</span></span>  
 <span data-ttu-id="c3ac9-278">Para retomar uma instância de fluxo de trabalho, o host precisa fornecer a definição de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-278">In order to resume a workflow instance, the host has to provide the workflow definition.</span></span> <span data-ttu-id="c3ac9-279">Neste tutorial, há três tipos de fluxo de trabalho e as etapas tutoriais subsequentes trazem várias versões desses tipos.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-279">In this tutorial there are three workflow types, and subsequent tutorial steps introduce multiple versions of these types.</span></span> <span data-ttu-id="c3ac9-280">`WorkflowIdentity` fornece uma maneira de um aplicativo de host associar informações de identificação a uma instância do fluxo de trabalho persistida.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-280">`WorkflowIdentity` provides a way for a host application to associate identifying information with a persisted workflow instance.</span></span> <span data-ttu-id="c3ac9-281">As etapas nesta seção demonstram como criar uma classe de utilitário para ajudar com o mapeamento da identidade de fluxo de trabalho de uma instância do fluxo de trabalho persistida para a definição do fluxo de trabalho correspondente.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-281">The steps in this section demonstrate how to create a utility class to assist with mapping the workflow identity from a persisted workflow instance to the corresponding workflow definition.</span></span> <span data-ttu-id="c3ac9-282">Para obter mais informações sobre `WorkflowIdentity` e o controle de versão, consulte [usando WorkflowIdentity e controle de versão](using-workflowidentity-and-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="c3ac9-282">For more information about `WorkflowIdentity` and versioning, see [Using WorkflowIdentity and Versioning](using-workflowidentity-and-versioning.md).</span></span>  
  
1. <span data-ttu-id="c3ac9-283">Clique com botão direito **NumberGuessWorkflowHost** na **Gerenciador de soluções** e escolha **Add**, **classe**.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-283">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="c3ac9-284">Tipo de `WorkflowVersionMap` para o **nome** caixa e clique em **Add**.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-284">Type `WorkflowVersionMap` into the **Name** box and click **Add**.</span></span>  
  
2. <span data-ttu-id="c3ac9-285">Adicione as seguintes instruções `using` ou `Imports` na parte superior do arquivo com as outras instruções `using` ou `Imports`.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-285">Add the following `using` or `Imports` statements at the top of the file with the other `using` or `Imports` statements.</span></span>  
  
    ```vb  
    Imports NumberGuessWorkflowActivities  
    Imports System.Activities  
    ```  
  
    ```csharp  
    using NumberGuessWorkflowActivities;  
    using System.Activities;  
    ```  
  
3. <span data-ttu-id="c3ac9-286">Substitua a declaração de classe `WorkflowVersionMap` pela seguinte declaração.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-286">Replace the `WorkflowVersionMap` class declaration with the following declaration.</span></span>  
  
    ```vb  
    Public Module WorkflowVersionMap  
        Dim map As Dictionary(Of WorkflowIdentity, Activity)  
  
        'Current version identities.  
        Public StateMachineNumberGuessIdentity As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity As WorkflowIdentity  
        Public SequentialNumberGuessIdentity As WorkflowIdentity  
  
        Sub New()  
            map = New Dictionary(Of WorkflowIdentity, Activity)  
  
            'Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "StateMachineNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            FlowchartNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "FlowchartNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            SequentialNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "SequentialNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())  
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())  
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())  
        End Sub  
  
        Public Function GetWorkflowDefinition(identity As WorkflowIdentity) As Activity  
            Return map(identity)  
        End Function  
  
        Public Function GetIdentityDescription(identity As WorkflowIdentity) As String  
            Return identity.ToString()  
        End Function  
    End Module  
    ```  
  
    ```csharp  
    public static class WorkflowVersionMap  
    {  
        static Dictionary<WorkflowIdentity, Activity> map;  
  
        // Current version identities.  
        static public WorkflowIdentity StateMachineNumberGuessIdentity;  
        static public WorkflowIdentity FlowchartNumberGuessIdentity;  
        static public WorkflowIdentity SequentialNumberGuessIdentity;  
  
        static WorkflowVersionMap()  
        {  
            map = new Dictionary<WorkflowIdentity, Activity>();  
  
            // Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "StateMachineNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            FlowchartNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "FlowchartNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            SequentialNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "SequentialNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());  
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());  
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());  
        }  
  
        public static Activity GetWorkflowDefinition(WorkflowIdentity identity)  
        {  
            return map[identity];  
        }  
  
        public static string GetIdentityDescription(WorkflowIdentity identity)  
        {          
            return identity.ToString();  
       }  
    }  
    ```  
  
     <span data-ttu-id="c3ac9-287">O `WorkflowVersionMap` contém três identidades de fluxo de trabalho que mapeiam para as três definições de fluxo de trabalho deste tutorial e é usado nas seções a seguir quando os fluxos de trabalho são iniciados e retomados.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-287">`WorkflowVersionMap` contains three workflow identities that map to the three workflow definitions from this tutorial and is used in the following sections when workflows are started and resumed.</span></span>  
  
### <a name="BKMK_StartWorkflow"></a> <span data-ttu-id="c3ac9-288">Para iniciar um novo fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c3ac9-288">To start a new workflow</span></span>  
  
1. <span data-ttu-id="c3ac9-289">Adicione um manipulador `Click` para `NewGame`.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-289">Add a `Click` handler for `NewGame`.</span></span> <span data-ttu-id="c3ac9-290">Para adicionar o manipulador, alterne para **modo de exibição de Design** para o formulário e clique duas vezes em `NewGame`.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-290">To add the handler, switch to **Design View** for the form, and double-click `NewGame`.</span></span> <span data-ttu-id="c3ac9-291">Um manipulador `NewGame_Click` é adicionado e a exibição alterna para a exibição do código para o formulário.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-291">A `NewGame_Click` handler is added and the view switches to code view for the form.</span></span> <span data-ttu-id="c3ac9-292">Sempre que o usuário clicar nesse botão, um novo fluxo de trabalho será iniciado.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-292">Whenever the user clicks this button a new workflow is started.</span></span>  
  
    ```vb  
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void NewGame_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2. <span data-ttu-id="c3ac9-293">Adicione o seguinte código ao manipulador de cliques.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-293">Add the following code to the click handler.</span></span> <span data-ttu-id="c3ac9-294">O código cria um dicionário de argumentos de entrada para o fluxo de trabalho, fechados pelo nome do argumento.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-294">This code creates a dictionary of input arguments for the workflow, keyed by argument name.</span></span> <span data-ttu-id="c3ac9-295">Esse dicionário tem uma entrada que contém o intervalo de números gerados aleatoriamente recuperados da caixa de combinação do intervalo.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-295">This dictionary has one entry that contains the range of the randomly generated number retrieved from the range combo box.</span></span>  
  
    ```vb  
    Dim inputs As New Dictionary(Of String, Object)()  
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))  
    ```  
  
    ```csharp  
    var inputs = new Dictionary<string, object>();  
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));  
    ```  
  
3. <span data-ttu-id="c3ac9-296">Em seguida, adicione o código a seguir que inicia o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-296">Next, add the following code that starts the workflow.</span></span> <span data-ttu-id="c3ac9-297">O `WorkflowIdentity` e a definição de fluxo de trabalho que corresponde ao tipo de fluxo de trabalho selecionado são recuperados usando a classe auxiliar `WorkflowVersionMap`.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-297">The `WorkflowIdentity` and workflow definition corresponding to the type of workflow selected are retrieved using the `WorkflowVersionMap` helper class.</span></span> <span data-ttu-id="c3ac9-298">Em seguida, uma nova instância de `WorkflowApplication` é criada usando a definição de fluxo de trabalho, `WorkflowIdentity`, e o dicionário de argumentos de entrada.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-298">Next, a new `WorkflowApplication` instance is created using the workflow definition, `WorkflowIdentity`, and dictionary of input arguments.</span></span>  
  
    ```vb  
    Dim identity As WorkflowIdentity = Nothing  
    Select Case WorkflowType.SelectedItem.ToString()  
        Case "SequentialNumberGuessWorkflow"  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity  
  
        Case "StateMachineNumberGuessWorkflow"  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity  
  
        Case "FlowchartNumberGuessWorkflow"  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity  
    End Select  
  
    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(identity)  
  
    Dim wfApp = New WorkflowApplication(wf, inputs, identity)  
    ```  
  
    ```csharp  
    WorkflowIdentity identity = null;  
    switch (WorkflowType.SelectedItem.ToString())  
    {  
        case "SequentialNumberGuessWorkflow":  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity;  
            break;  
  
        case "StateMachineNumberGuessWorkflow":  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;  
            break;  
  
        case "FlowchartNumberGuessWorkflow":  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;  
            break;  
    };  
  
    Activity wf = WorkflowVersionMap.GetWorkflowDefinition(identity);  
  
    WorkflowApplication wfApp = new WorkflowApplication(wf, inputs, identity);  
    ```  
  
4. <span data-ttu-id="c3ac9-299">Em seguida, adicione o código a seguir, que adiciona o fluxo de trabalho à lista de fluxo de trabalho e exibe as informações de versão do fluxo de trabalho no formulário.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-299">Next, add the following code which adds the workflow to the workflow list and displays the workflow's version information on the form.</span></span>  
  
    ```vb  
    'Add the workflow to the list and display the version information.  
    WorkflowStarting = True  
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)  
    WorkflowVersion.Text = identity.ToString()  
    WorkflowStarting = False  
    ```  
  
    ```csharp  
    // Add the workflow to the list and display the version information.  
    WorkflowStarting = true;  
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);  
    WorkflowVersion.Text = identity.ToString();  
    WorkflowStarting = false;  
    ```  
  
5. <span data-ttu-id="c3ac9-300">Chame `ConfigureWorkflowApplication` para configurar o repositório de instâncias, as extensões e os manipuladores do ciclo de vida de fluxo de trabalho para essa instância `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-300">Call `ConfigureWorkflowApplication` to configure the instance store, extensions, and workflow lifecycle handlers for this `WorkflowApplication` instance.</span></span>  
  
    ```vb  
    'Configure the instance store, extensions, and   
    'workflow lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp)  
    ```  
  
    ```csharp  
    // Configure the instance store, extensions, and   
    // workflow lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp);  
    ```  
  
6. <span data-ttu-id="c3ac9-301">Finalmente, chame `Run`.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-301">Finally, call `Run`.</span></span>  
  
    ```vb  
    'Start the workflow.  
    wfApp.Run()  
    ```  
  
    ```  
    // Start the workflow.  
    wfApp.Run();  
    ```  
  
     <span data-ttu-id="c3ac9-302">O exemplo a seguir é o manipulador `NewGame_Click` concluído.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-302">The following example is the completed `NewGame_Click` handler.</span></span>  
  
    ```vb  
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click  
        'Start a new workflow.  
        Dim inputs As New Dictionary(Of String, Object)()  
        inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))  
  
        Dim identity As WorkflowIdentity = Nothing  
        Select Case WorkflowType.SelectedItem.ToString()  
            Case "SequentialNumberGuessWorkflow"  
                identity = WorkflowVersionMap.SequentialNumberGuessIdentity  
  
            Case "StateMachineNumberGuessWorkflow"  
                identity = WorkflowVersionMap.StateMachineNumberGuessIdentity  
  
            Case "FlowchartNumberGuessWorkflow"  
                identity = WorkflowVersionMap.FlowchartNumberGuessIdentity  
        End Select  
  
        Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(identity)  
  
        Dim wfApp = New WorkflowApplication(wf, inputs, identity)  
  
        'Add the workflow to the list and display the version information.  
        WorkflowStarting = True  
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)  
        WorkflowVersion.Text = identity.ToString()  
        WorkflowStarting = False  
  
        'Configure the instance store, extensions, and   
        'workflow lifecycle handlers.  
        ConfigureWorkflowApplication(wfApp)  
  
        'Start the workflow.  
        wfApp.Run()  
    End Sub  
    ```  
  
    ```csharp  
    private void NewGame_Click(object sender, EventArgs e)  
    {  
        var inputs = new Dictionary<string, object>();  
        inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));  
  
        WorkflowIdentity identity = null;  
        switch (WorkflowType.SelectedItem.ToString())  
        {  
            case "SequentialNumberGuessWorkflow":  
                identity = WorkflowVersionMap.SequentialNumberGuessIdentity;  
                break;  
  
            case "StateMachineNumberGuessWorkflow":  
                identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;  
                break;  
  
            case "FlowchartNumberGuessWorkflow":  
                identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;  
                break;  
        };  
  
        Activity wf = WorkflowVersionMap.GetWorkflowDefinition(identity);  
  
        WorkflowApplication wfApp = new WorkflowApplication(wf, inputs, identity);  
  
        // Add the workflow to the list and display the version information.  
        WorkflowStarting = true;  
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);  
        WorkflowVersion.Text = identity.ToString();  
        WorkflowStarting = false;  
  
        // Configure the instance store, extensions, and   
        // workflow lifecycle handlers.  
        ConfigureWorkflowApplication(wfApp);  
  
        // Start the workflow.  
        wfApp.Run();  
    }  
    ```  
  
### <a name="BKMK_ResumeWorkflow"></a> <span data-ttu-id="c3ac9-303">Para retomar um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c3ac9-303">To resume a workflow</span></span>  
  
1. <span data-ttu-id="c3ac9-304">Adicione um manipulador `Click` para `EnterGuess`.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-304">Add a `Click` handler for `EnterGuess`.</span></span> <span data-ttu-id="c3ac9-305">Para adicionar o manipulador, alterne para **modo de exibição de Design** para o formulário e clique duas vezes em `EnterGuess`.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-305">To add the handler, switch to **Design View** for the form, and double-click `EnterGuess`.</span></span> <span data-ttu-id="c3ac9-306">Sempre que o usuário clicar nesse botão, um fluxo de trabalho é retomado.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-306">Whenever the user clicks this button a workflow is resumed.</span></span>  
  
    ```vb  
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void EnterGuess_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2. <span data-ttu-id="c3ac9-307">Adicione o código a seguir para garantir que um fluxo de trabalho seja selecionado na lista de fluxo de trabalho, e que o palpite do usuário seja válido.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-307">Add the following code to ensure that a workflow is selected in the workflow list, and that the user's guess is valid.</span></span>  
  
    ```vb  
    If WorkflowInstanceId = Guid.Empty Then  
        MessageBox.Show("Please select a workflow.")  
        Return  
    End If  
  
    Dim userGuess As Integer  
    If Not Int32.TryParse(Guess.Text, userGuess) Then  
        MessageBox.Show("Please enter an integer.")  
        Guess.SelectAll()  
        Guess.Focus()  
        Return  
    End If  
    ```  
  
    ```csharp  
    if (WorkflowInstanceId == Guid.Empty)  
    {  
        MessageBox.Show("Please select a workflow.");  
        return;  
    }  
  
    int guess;  
    if (!Int32.TryParse(Guess.Text, out guess))  
    {  
        MessageBox.Show("Please enter an integer.");  
        Guess.SelectAll();  
        Guess.Focus();  
        return;  
    }  
    ```  
  
3. <span data-ttu-id="c3ac9-308">Em seguida, recupere o `WorkflowApplicationInstance` da instância do fluxo de trabalho persistida.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-308">Next, retrieve the `WorkflowApplicationInstance` of the persisted workflow instance.</span></span> <span data-ttu-id="c3ac9-309">Um `WorkflowApplicationInstance` representa uma instância do fluxo de trabalho persistida que ainda não esteja associada a uma definição de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-309">A `WorkflowApplicationInstance` represents a persisted workflow instance that has not yet been associated with a workflow definition.</span></span> <span data-ttu-id="c3ac9-310">O `DefinitionIdentity` do `WorkflowApplicationInstance` contém o `WorkflowIdentity` da instância do fluxo de trabalho persistida.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-310">The `DefinitionIdentity` of the `WorkflowApplicationInstance` contains the `WorkflowIdentity` of the persisted workflow instance.</span></span> <span data-ttu-id="c3ac9-311">Neste tutorial, a classe de utilitário `WorkflowVersionMap` é usada para mapear o `WorkflowIdentity` para a definição correta de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-311">In this tutorial, the `WorkflowVersionMap` utility class is used to map the `WorkflowIdentity` to the correct workflow definition.</span></span> <span data-ttu-id="c3ac9-312">Quando a definição de fluxo de trabalho é recuperada, um `WorkflowApplication` é criado, usando a definição correta de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-312">Once the workflow definition is retrieved, a `WorkflowApplication` is created, using the correct workflow definition.</span></span>  
  
    ```vb  
    Dim instance As WorkflowApplicationInstance = _  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
    'Use the persisted WorkflowIdentity to retrieve the correct workflow  
    'definition from the dictionary.  
    Dim wf As Activity = _  
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
    'Associate the WorkflowApplication with the correct definition  
    Dim wfApp As WorkflowApplication = _  
        New WorkflowApplication(wf, instance.DefinitionIdentity)  
    ```  
  
    ```csharp  
    WorkflowApplicationInstance instance =  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
    // Use the persisted WorkflowIdentity to retrieve the correct workflow  
    // definition from the dictionary.  
    Activity wf =  
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
    // Associate the WorkflowApplication with the correct definition  
    WorkflowApplication wfApp =  
        new WorkflowApplication(wf, instance.DefinitionIdentity);  
    ```  
  
4. <span data-ttu-id="c3ac9-313">Quando a `WorkflowApplication` é criada, configure o repositório de instâncias, os manipuladores do ciclo de vida de fluxo de trabalho e as extensões chamando `ConfigureWorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-313">Once the `WorkflowApplication` is created, configure the instance store, workflow lifecycle handlers, and extensions by calling `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="c3ac9-314">Essas etapas devem ser executadas toda vez que um `WorkflowApplication` novo é criado, e devem ser feitas antes que a instância de fluxo de trabalho seja carregada no `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-314">These steps must be done every time a new `WorkflowApplication` is created, and they must be done before the workflow instance is loaded into the `WorkflowApplication`.</span></span> <span data-ttu-id="c3ac9-315">Depois que o fluxo de trabalho é carregado, ele será retomado com o palpite do usuário.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-315">After the workflow is loaded, it is resumed with the user's guess.</span></span>  
  
    ```vb  
    'Configure the extensions and lifecycle handlers.  
    'Do this before the instance is loaded. Once the instance is  
    'loaded it is too late to add extensions.  
    ConfigureWorkflowApplication(wfApp)  
  
    'Load the workflow.  
    wfApp.Load(instance)  
  
    'Resume the workflow.  
    wfApp.ResumeBookmark("EnterGuess", userGuess)  
    ```  
  
    ```csharp  
    // Configure the extensions and lifecycle handlers.  
    // Do this before the instance is loaded. Once the instance is  
    // loaded it is too late to add extensions.  
    ConfigureWorkflowApplication(wfApp);  
  
    // Load the workflow.  
    wfApp.Load(instance);  
  
    // Resume the workflow.  
    wfApp.ResumeBookmark("EnterGuess", guess);  
    ```  
  
5. <span data-ttu-id="c3ac9-316">Finalmente, desmarque a caixa de texto de palpite e prepare o formulário para aceitar outro palpite.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-316">Finally, clear the guess textbox and prepare the form to accept another guess.</span></span>  
  
    ```vb  
    'Clear the Guess textbox.  
    Guess.Clear()  
    Guess.Focus()  
    ```  
  
    ```csharp  
    // Clear the Guess textbox.  
    Guess.Clear();  
    Guess.Focus();  
    ```  
  
     <span data-ttu-id="c3ac9-317">O exemplo a seguir é o manipulador `EnterGuess_Click` concluído.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-317">The following example is the completed `EnterGuess_Click` handler.</span></span>  
  
    ```vb  
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click  
        If WorkflowInstanceId = Guid.Empty Then  
            MessageBox.Show("Please select a workflow.")  
            Return  
        End If  
  
        Dim userGuess As Integer  
        If Not Int32.TryParse(Guess.Text, userGuess) Then  
            MessageBox.Show("Please enter an integer.")  
            Guess.SelectAll()  
            Guess.Focus()  
            Return  
        End If  
  
        Dim instance As WorkflowApplicationInstance = _  
            WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
        'Use the persisted WorkflowIdentity to retrieve the correct workflow  
        'definition from the dictionary.  
        Dim wf As Activity = _  
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
        'Associate the WorkflowApplication with the correct definition  
        Dim wfApp As WorkflowApplication = _  
            New WorkflowApplication(wf, instance.DefinitionIdentity)  
  
        'Configure the extensions and lifecycle handlers.  
        'Do this before the instance is loaded. Once the instance is  
        'loaded it is too late to add extensions.  
        ConfigureWorkflowApplication(wfApp)  
  
        'Load the workflow.  
        wfApp.Load(instance)  
  
        'Resume the workflow.  
        wfApp.ResumeBookmark("EnterGuess", userGuess)  
  
        'Clear the Guess textbox.  
        Guess.Clear()  
        Guess.Focus()  
    End Sub  
    ```  
  
    ```csharp  
    private void EnterGuess_Click(object sender, EventArgs e)  
    {  
        if (WorkflowInstanceId == Guid.Empty)  
        {  
            MessageBox.Show("Please select a workflow.");  
            return;  
        }  
  
        int guess;  
        if (!Int32.TryParse(Guess.Text, out guess))  
        {  
            MessageBox.Show("Please enter an integer.");  
            Guess.SelectAll();  
            Guess.Focus();  
            return;  
        }  
  
        WorkflowApplicationInstance instance =  
            WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
        // Use the persisted WorkflowIdentity to retrieve the correct workflow  
        // definition from the dictionary.  
        Activity wf =  
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
        // Associate the WorkflowApplication with the correct definition  
        WorkflowApplication wfApp =  
            new WorkflowApplication(wf, instance.DefinitionIdentity);  
  
        // Configure the extensions and lifecycle handlers.  
        // Do this before the instance is loaded. Once the instance is  
        // loaded it is too late to add extensions.  
        ConfigureWorkflowApplication(wfApp);  
  
        // Load the workflow.  
        wfApp.Load(instance);  
  
        // Resume the workflow.  
        wfApp.ResumeBookmark("EnterGuess", guess);  
  
        // Clear the Guess textbox.  
        Guess.Clear();  
        Guess.Focus();  
    }  
    ```  
  
### <a name="BKMK_TerminateWorkflow"></a> <span data-ttu-id="c3ac9-318">Para encerrar um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c3ac9-318">To terminate a workflow</span></span>  
  
1. <span data-ttu-id="c3ac9-319">Adicione um manipulador `Click` para `QuitGame`.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-319">Add a `Click` handler for `QuitGame`.</span></span> <span data-ttu-id="c3ac9-320">Para adicionar o manipulador, alterne para **modo de exibição de Design** para o formulário e clique duas vezes em `QuitGame`.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-320">To add the handler, switch to **Design View** for the form, and double-click `QuitGame`.</span></span> <span data-ttu-id="c3ac9-321">Sempre que o usuário clicar nesse botão, o fluxo de trabalho selecionado atual será encerrado.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-321">Whenever the user clicks this button the currently selected workflow is terminated.</span></span>  
  
    ```vb  
    Private Sub QuitGame_Click(sender As Object, e As EventArgs) Handles QuitGame.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void QuitGame_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2. <span data-ttu-id="c3ac9-322">Adicione o seguinte código ao manipulador `QuitGame_Click`.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-322">Add the following code to the `QuitGame_Click` handler.</span></span> <span data-ttu-id="c3ac9-323">Esse código primeiro verifica para garantir que um fluxo de trabalho esteja selecionado na lista de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-323">This code first checks to ensure that a workflow is selected in the workflow list.</span></span> <span data-ttu-id="c3ac9-324">Em seguida, ele carrega a instância persistida em um `WorkflowApplicationInstance`, use a `DefinitionIdentity` para determinar a definição correta de fluxo de trabalho e depois inicializa o `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-324">Then it loads the persisted instance into a `WorkflowApplicationInstance`, uses the `DefinitionIdentity` to determine the correct workflow definition, and then initializes the `WorkflowApplication`.</span></span> <span data-ttu-id="c3ac9-325">Em seguida, as extensões e os manipuladores de ciclo de vida de fluxo de trabalho são configurados com uma chamada para `ConfigureWorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-325">Next the extensions and workflow lifecycle handlers are configured with a call to `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="c3ac9-326">Quando o `WorkflowApplication` é configurado, ele será carregado e, em seguida, `Terminate` será chamado.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-326">Once the `WorkflowApplication` is configured, it is loaded, and then `Terminate` is called.</span></span>  
  
    ```vb  
    If WorkflowInstanceId = Guid.Empty Then  
        MessageBox.Show("Please select a workflow.")  
        Return  
    End If  
  
    Dim instance As WorkflowApplicationInstance = _  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
    'Use the persisted WorkflowIdentity to retrieve the correct workflow  
    'definition from the dictionary.  
    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
    'Associate the WorkflowApplication with the correct definition.  
    Dim wfApp As WorkflowApplication = _  
        New WorkflowApplication(wf, instance.DefinitionIdentity)  
  
    'Configure the extensions and lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp)  
  
    'Load the workflow.  
    wfApp.Load(instance)  
  
    'Terminate the workflow.  
    wfApp.Terminate("User resigns.")  
    ```  
  
    ```csharp  
    if (WorkflowInstanceId == Guid.Empty)  
    {  
        MessageBox.Show("Please select a workflow.");  
        return;  
    }  
  
    WorkflowApplicationInstance instance =  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
    // Use the persisted WorkflowIdentity to retrieve the correct workflow  
    // definition from the dictionary.  
    Activity wf = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
    // Associate the WorkflowApplication with the correct definition  
    WorkflowApplication wfApp =  
        new WorkflowApplication(wf, instance.DefinitionIdentity);  
  
    // Configure the extensions and lifecycle handlers  
    ConfigureWorkflowApplication(wfApp);  
  
    // Load the workflow.  
    wfApp.Load(instance);  
  
    // Terminate the workflow.  
    wfApp.Terminate("User resigns.");  
    ```  
  
### <a name="BKMK_BuildAndRun"></a> <span data-ttu-id="c3ac9-327">Para compilar e executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="c3ac9-327">To build and run the application</span></span>  
  
1. <span data-ttu-id="c3ac9-328">Clique duas vezes em **Program.cs** (ou **Module1.vb**) na **Gerenciador de soluções** para exibir o código.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-328">Double-click **Program.cs** (or **Module1.vb**) in **Solution Explorer** to display the code.</span></span>  
  
2. <span data-ttu-id="c3ac9-329">Adicione a seguinte instrução `using` (ou `Imports`) na parte superior do arquivo com as outras instruções `using` (ou `Imports`).</span><span class="sxs-lookup"><span data-stu-id="c3ac9-329">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
3. <span data-ttu-id="c3ac9-330">Remova ou comente o fluxo de trabalho existente que hospeda o código de [como: Executar um fluxo de trabalho](how-to-run-a-workflow.md)e substitua-o pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-330">Remove or comment out the existing workflow hosting code from [How to: Run a Workflow](how-to-run-a-workflow.md), and replace it with the following code.</span></span>  
  
    ```vb  
    Sub Main()  
        Application.EnableVisualStyles()  
        Application.Run(New WorkflowHostForm())  
    End Sub  
    ```  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        Application.EnableVisualStyles();  
        Application.Run(new WorkflowHostForm());  
    }  
    ```  
  
4. <span data-ttu-id="c3ac9-331">Clique com botão direito **NumberGuessWorkflowHost** na **Gerenciador de soluções** e escolha **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-331">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Properties**.</span></span> <span data-ttu-id="c3ac9-332">No **Application** , especifique **aplicativo do Windows** para o **tipo de saída**.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-332">In the **Application** tab, specify **Windows Application** for the **Output type**.</span></span> <span data-ttu-id="c3ac9-333">Essa etapa é opcional, mas se não for seguida, a janela do console será exibida além do formulário.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-333">This step is optional, but if it is not followed the console window is displayed in addition to the form.</span></span>  
  
5. <span data-ttu-id="c3ac9-334">Pressione Ctrl+Shift+B para criar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-334">Press Ctrl+Shift+B to build the application.</span></span>  
  
6. <span data-ttu-id="c3ac9-335">Certifique-se de que **NumberGuessWorkflowHost** está definido como o aplicativo de inicialização e pressione Ctrl + F5 para iniciar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-335">Ensure that **NumberGuessWorkflowHost** is set as the startup application, and press Ctrl+F5 to start the application.</span></span>  
  
7. <span data-ttu-id="c3ac9-336">Selecionar um intervalo para o jogo de estimativa e o tipo de fluxo de trabalho para iniciar e, em seguida, clique em **novo jogo**.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-336">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="c3ac9-337">Insira um Palpite na **Palpite** caixa e clique em **vá** para enviar seu palpite.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-337">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="c3ac9-338">Observe que a saída das atividades de `WriteLine` são exibidas no formulário.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-338">Note that the output from the `WriteLine` activities is displayed on the form.</span></span>  
  
8. <span data-ttu-id="c3ac9-339">Iniciar vários fluxos de trabalho usando intervalos de número e os tipos de fluxo de trabalho diferente, insira alguns Palpites e alterne entre os fluxos de trabalho, selecionando a partir de **Id da instância de fluxo de trabalho** lista.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-339">Start several workflows using different workflow types and number ranges, enter some guesses, and switch between the workflows by selecting from the **Workflow Instance Id** list.</span></span>  
  
     <span data-ttu-id="c3ac9-340">Observe que, quando você alterna para um novo fluxo de trabalho, os palpites anteriores e o progresso do fluxo de trabalho não são exibidos na janela de status.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-340">Note that when you switch to a new workflow, the previous guesses and progress of the workflow are not displayed in the status window.</span></span> <span data-ttu-id="c3ac9-341">A razão pela qual o status não está disponível é porque ele não é capturado e salvo em nenhum lugar.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-341">The reason the status is not available is because it is not captured and saved anywhere.</span></span> <span data-ttu-id="c3ac9-342">Na próxima etapa do tutorial, [como: Criar um participante de acompanhamento personalizado](how-to-create-a-custom-tracking-participant.md), criar um participante personalizado que salva essas informações.</span><span class="sxs-lookup"><span data-stu-id="c3ac9-342">In the next step of the tutorial, [How to: Create a Custom Tracking Participant](how-to-create-a-custom-tracking-participant.md), you create a custom tracking participant that saves this information.</span></span>

---
title: Como criar e executar um fluxo de trabalho de execução longa
description: Este artigo mostra como criar um aplicativo de host Windows Forms que dá suporte ao início e à retomada de várias instâncias de fluxo de trabalho e persistência de fluxo de trabalho.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0043c89-2192-43c9-986d-3ecec4dd8c9c
ms.openlocfilehash: 557b3512e534198d47c0c6f6b0a7c5f92bb71739
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419545"
---
# <a name="how-to-create-and-run-a-long-running-workflow"></a><span data-ttu-id="eaad1-103">Como criar e executar um fluxo de trabalho de execução longa</span><span class="sxs-lookup"><span data-stu-id="eaad1-103">How to create and run a long-running workflow</span></span>

<span data-ttu-id="eaad1-104">Um dos recursos centrais do Windows Workflow Foundation (WF) é a capacidade do tempo de execução de persistir e descarregar fluxos de trabalho ociosos em um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="eaad1-104">One of the central features of Windows Workflow Foundation (WF) is the runtime’s ability to persist and unload idle workflows to a database.</span></span> <span data-ttu-id="eaad1-105">As etapas em [como executar um fluxo de trabalho](how-to-run-a-workflow.md) demonstraram os conceitos básicos da hospedagem do fluxo de trabalho usando um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="eaad1-105">The steps in [How to: Run a Workflow](how-to-run-a-workflow.md) demonstrated the basics of workflow hosting using a console application.</span></span> <span data-ttu-id="eaad1-106">Foram mostrados exemplos de iniciação de fluxos de trabalho, manipuladores do ciclo de vida de fluxo de trabalho e retomada de indicadores.</span><span class="sxs-lookup"><span data-stu-id="eaad1-106">Examples were shown of starting workflows, workflow lifecycle handlers, and resuming bookmarks.</span></span> <span data-ttu-id="eaad1-107">Para demonstrar efetivamente a persistência do fluxo de trabalho, um host de fluxo de trabalho mais complexo é necessário que dá suporte a início e retomada de várias instâncias de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="eaad1-107">In order to demonstrate workflow persistence effectively, a more complex workflow host is required that supports starting and resuming multiple workflow instances.</span></span> <span data-ttu-id="eaad1-108">Esta etapa no tutorial demonstra como criar um aplicativo de host do Windows Form que dê suporte ao início e à retomada de várias instâncias de fluxo de trabalho, persistência de fluxo de trabalho e fornece uma base para os recursos avançados como o rastreamento e o controle de versão que são demonstrados em etapas tutoriais subsequentes.</span><span class="sxs-lookup"><span data-stu-id="eaad1-108">This step in the tutorial demonstrates how to create a Windows form host application that supports starting and resuming multiple workflow instances, workflow persistence, and provides a basis for the advanced features such as tracking and versioning that are demonstrated in subsequent tutorial steps.</span></span>

> [!NOTE]
> <span data-ttu-id="eaad1-109">Esta etapa do tutorial e as etapas subsequentes usam todos os três tipos de fluxo de trabalho de [como: criar um fluxo de trabalho](how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="eaad1-109">This tutorial step and the subsequent steps use all three workflow types from [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span> <span data-ttu-id="eaad1-110">Se você não tiver concluído todos os três tipos, poderá baixar uma versão completa das etapas de [Windows Workflow Foundation (WF45) – introdução tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="eaad1-110">If you did not complete all three types you can download a completed version of the steps from [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

> [!NOTE]
> <span data-ttu-id="eaad1-111">Para fazer o download de uma versão completa ou exibir um vídeo com o tutorial, consulte [Windows Workflow Foundation (WF45) – introdução tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="eaad1-111">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="to-create-the-persistence-database"></a><span data-ttu-id="eaad1-112">Para criar o banco de dados de persistência</span><span class="sxs-lookup"><span data-stu-id="eaad1-112">To create the persistence database</span></span>

1. <span data-ttu-id="eaad1-113">Abra SQL Server Management Studio e conecte-se ao servidor local, por exemplo, **.\sqlexpress**.</span><span class="sxs-lookup"><span data-stu-id="eaad1-113">Open SQL Server Management Studio and connect to the local server, for example **.\SQLEXPRESS**.</span></span> <span data-ttu-id="eaad1-114">Clique com o botão direito do mouse no nó **bancos** de dados no servidor local e selecione **novo Database**.</span><span class="sxs-lookup"><span data-stu-id="eaad1-114">Right-click the **Databases** node on the local server, and select **New Database**.</span></span> <span data-ttu-id="eaad1-115">Nomeie o novo banco de dados **WF45GettingStartedTutorial**, aceite todos os outros valores e selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="eaad1-115">Name the new database **WF45GettingStartedTutorial**, accept all other values, and select **OK**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="eaad1-116">Verifique se você tem a permissão **CREATE DATABASE** no servidor local antes de criar o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="eaad1-116">Ensure that you have **Create Database** permission on the local server before creating the database.</span></span>

2. <span data-ttu-id="eaad1-117">Escolha **abrir**, **arquivo** no menu **arquivo** .</span><span class="sxs-lookup"><span data-stu-id="eaad1-117">Choose **Open**, **File** from the **File** menu.</span></span> <span data-ttu-id="eaad1-118">Navegue até a seguinte pasta: *C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en*</span><span class="sxs-lookup"><span data-stu-id="eaad1-118">Browse to the following folder: *C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en*</span></span>

    <span data-ttu-id="eaad1-119">Selecione os dois arquivos a seguir e clique em **abrir**.</span><span class="sxs-lookup"><span data-stu-id="eaad1-119">Select the following two files and click **Open**.</span></span>

    - <span data-ttu-id="eaad1-120">*SqlWorkflowInstanceStoreLogic.sql*</span><span class="sxs-lookup"><span data-stu-id="eaad1-120">*SqlWorkflowInstanceStoreLogic.sql*</span></span>

    - <span data-ttu-id="eaad1-121">*SqlWorkflowInstanceStoreSchema.sql*</span><span class="sxs-lookup"><span data-stu-id="eaad1-121">*SqlWorkflowInstanceStoreSchema.sql*</span></span>

3. <span data-ttu-id="eaad1-122">Escolha **SqlWorkflowInstanceStoreSchema. SQL** no menu **janela** .</span><span class="sxs-lookup"><span data-stu-id="eaad1-122">Choose **SqlWorkflowInstanceStoreSchema.sql** from the **Window** menu.</span></span> <span data-ttu-id="eaad1-123">Verifique se **WF45GettingStartedTutorial** está selecionado na lista suspensa **bancos de dados disponíveis** e escolha **executar** no menu **consulta** .</span><span class="sxs-lookup"><span data-stu-id="eaad1-123">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>

4. <span data-ttu-id="eaad1-124">Escolha **SqlWorkflowInstanceStoreLogic. SQL** no menu **janela** .</span><span class="sxs-lookup"><span data-stu-id="eaad1-124">Choose **SqlWorkflowInstanceStoreLogic.sql** from the **Window** menu.</span></span> <span data-ttu-id="eaad1-125">Verifique se **WF45GettingStartedTutorial** está selecionado na lista suspensa **bancos de dados disponíveis** e escolha **executar** no menu **consulta** .</span><span class="sxs-lookup"><span data-stu-id="eaad1-125">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>

    > [!WARNING]
    > <span data-ttu-id="eaad1-126">É importante executar as duas etapas anteriores na ordem correta.</span><span class="sxs-lookup"><span data-stu-id="eaad1-126">It is important to perform the previous two steps in the correct order.</span></span> <span data-ttu-id="eaad1-127">Se as consultas forem executadas fora de ordem, ocorrerão erros e o banco de dados de persistência não estará configurado corretamente.</span><span class="sxs-lookup"><span data-stu-id="eaad1-127">If the queries are executed out of order, errors occur and the persistence database is not configured correctly.</span></span>

## <a name="to-add-the-reference-to-the-durableinstancing-assemblies"></a><span data-ttu-id="eaad1-128">Para adicionar a referência aos assemblies do DurableInstancing</span><span class="sxs-lookup"><span data-stu-id="eaad1-128">To add the reference to the DurableInstancing assemblies</span></span>

1. <span data-ttu-id="eaad1-129">Clique com o botão direito do mouse em **NumberGuessWorkflowHost** em **Gerenciador de soluções** e selecione **Adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="eaad1-129">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Add Reference**.</span></span>

2. <span data-ttu-id="eaad1-130">Selecione **assemblies** na lista **Adicionar referência** e digite `DurableInstancing` na caixa **Pesquisar assemblies** .</span><span class="sxs-lookup"><span data-stu-id="eaad1-130">Select **Assemblies** from the **Add Reference** list, and type `DurableInstancing` into the **Search Assemblies** box.</span></span> <span data-ttu-id="eaad1-131">Isso filtra os assemblies e facilita a seleção das referências desejadas.</span><span class="sxs-lookup"><span data-stu-id="eaad1-131">This filters the assemblies and makes the desired references easier to select.</span></span>

3. <span data-ttu-id="eaad1-132">Marque a caixa de seleção ao lado de **System. Activities. DurableInstancing** e **System. Runtime. DurableInstancing** na lista de **resultados da pesquisa** e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="eaad1-132">Check the checkbox beside **System.Activities.DurableInstancing** and **System.Runtime.DurableInstancing** from the **Search Results** list, and click **OK**.</span></span>

## <a name="to-create-the-workflow-host-form"></a><span data-ttu-id="eaad1-133">Para criar o formulário de host de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="eaad1-133">To create the workflow host form</span></span>

> [!NOTE]
> <span data-ttu-id="eaad1-134">As etapas neste procedimento descrevem como adicionar e configurar manualmente o formulário.</span><span class="sxs-lookup"><span data-stu-id="eaad1-134">The steps in this procedure describe how to add and configure the form manually.</span></span> <span data-ttu-id="eaad1-135">Se for desejar, você poderá baixar os arquivos da solução para o tutorial e adicionar o formulário concluído ao projeto.</span><span class="sxs-lookup"><span data-stu-id="eaad1-135">If desired, you can download the solution files for the tutorial and add the completed form to the project.</span></span> <span data-ttu-id="eaad1-136">Para baixar os arquivos do tutorial, consulte [Windows Workflow Foundation (WF45) – introdução tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="eaad1-136">To download the tutorial files, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span> <span data-ttu-id="eaad1-137">Depois que os arquivos forem baixados, clique com o botão direito do mouse em **NumberGuessWorkflowHost** e escolha **Adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="eaad1-137">Once the files are downloaded, right-click **NumberGuessWorkflowHost** and choose **Add Reference**.</span></span> <span data-ttu-id="eaad1-138">Adicione uma referência a **System. Windows. Forms** e **System. Drawing**.</span><span class="sxs-lookup"><span data-stu-id="eaad1-138">Add a reference to **System.Windows.Forms** and **System.Drawing**.</span></span> <span data-ttu-id="eaad1-139">Essas referências são adicionadas automaticamente se você adicionar um novo formulário a partir do menu **Adicionar**, **novo item** , mas precisar ser adicionado manualmente ao importar um formulário.</span><span class="sxs-lookup"><span data-stu-id="eaad1-139">These references are added automatically if you add a new form from the **Add**, **New Item** menu, but must be added manually when importing a form.</span></span> <span data-ttu-id="eaad1-140">Depois que as referências forem adicionadas, clique com o botão direito do mouse em **NumberGuessWorkflowHost** em **Gerenciador de soluções** e escolha **Adicionar**, **Item existente**.</span><span class="sxs-lookup"><span data-stu-id="eaad1-140">Once the references are added, right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Existing Item**.</span></span> <span data-ttu-id="eaad1-141">Navegue até a `Form` pasta nos arquivos de projeto, selecione **WorkflowHostForm.cs** (ou **WorkflowHostForm. vb**) e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="eaad1-141">Browse to the `Form` folder in the project files, select **WorkflowHostForm.cs** (or **WorkflowHostForm.vb**), and click **Add**.</span></span> <span data-ttu-id="eaad1-142">Se você optar por importar o formulário, poderá pular para a próxima seção, [para adicionar as propriedades e os métodos auxiliares do formulário](#to-add-the-properties-and-helper-methods-of-the-form).</span><span class="sxs-lookup"><span data-stu-id="eaad1-142">If you choose to import the form, then you can skip down to the next section, [To add the properties and helper methods of the form](#to-add-the-properties-and-helper-methods-of-the-form).</span></span>

1. <span data-ttu-id="eaad1-143">Clique com o botão direito do mouse em **NumberGuessWorkflowHost** em **Gerenciador de soluções** e escolha **Adicionar**, **novo item**.</span><span class="sxs-lookup"><span data-stu-id="eaad1-143">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **New Item**.</span></span>

2. <span data-ttu-id="eaad1-144">Na lista modelos **instalados** , escolha **Windows Form**, digite `WorkflowHostForm` na caixa **nome** e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="eaad1-144">In the **Installed** templates list, choose **Windows Form**, type `WorkflowHostForm` in the **Name** box, and click **Add**.</span></span>

3. <span data-ttu-id="eaad1-145">Configure as propriedades a seguir no formulário.</span><span class="sxs-lookup"><span data-stu-id="eaad1-145">Configure the following properties on the form.</span></span>

    |<span data-ttu-id="eaad1-146">Propriedade</span><span class="sxs-lookup"><span data-stu-id="eaad1-146">Property</span></span>|<span data-ttu-id="eaad1-147">Valor</span><span class="sxs-lookup"><span data-stu-id="eaad1-147">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="eaad1-148">FormBorderStyle</span><span class="sxs-lookup"><span data-stu-id="eaad1-148">FormBorderStyle</span></span>|<span data-ttu-id="eaad1-149">FixedSingle</span><span class="sxs-lookup"><span data-stu-id="eaad1-149">FixedSingle</span></span>|
    |<span data-ttu-id="eaad1-150">MaximizeBox</span><span class="sxs-lookup"><span data-stu-id="eaad1-150">MaximizeBox</span></span>|<span data-ttu-id="eaad1-151">Falso</span><span class="sxs-lookup"><span data-stu-id="eaad1-151">False</span></span>|
    |<span data-ttu-id="eaad1-152">Tamanho</span><span class="sxs-lookup"><span data-stu-id="eaad1-152">Size</span></span>|<span data-ttu-id="eaad1-153">400, 420</span><span class="sxs-lookup"><span data-stu-id="eaad1-153">400, 420</span></span>|

4. <span data-ttu-id="eaad1-154">Adicione os seguintes controles ao formulário na ordem especificada e configure as propriedades como direcionadas.</span><span class="sxs-lookup"><span data-stu-id="eaad1-154">Add the following controls to the form in the order specified and configure the properties as directed.</span></span>

    |<span data-ttu-id="eaad1-155">Control</span><span class="sxs-lookup"><span data-stu-id="eaad1-155">Control</span></span>|<span data-ttu-id="eaad1-156">Propriedade: valor</span><span class="sxs-lookup"><span data-stu-id="eaad1-156">Property: Value</span></span>|
    |-------------|---------------------|
    |<span data-ttu-id="eaad1-157">**Botão**</span><span class="sxs-lookup"><span data-stu-id="eaad1-157">**Button**</span></span>|<span data-ttu-id="eaad1-158">Nome: NewGame</span><span class="sxs-lookup"><span data-stu-id="eaad1-158">Name: NewGame</span></span><br /><br /> <span data-ttu-id="eaad1-159">Local: 13, 13</span><span class="sxs-lookup"><span data-stu-id="eaad1-159">Location: 13, 13</span></span><br /><br /> <span data-ttu-id="eaad1-160">Tamanho: 75, 23</span><span class="sxs-lookup"><span data-stu-id="eaad1-160">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="eaad1-161">Texto: novo jogo</span><span class="sxs-lookup"><span data-stu-id="eaad1-161">Text: New Game</span></span>|
    |<span data-ttu-id="eaad1-162">**Rotular**</span><span class="sxs-lookup"><span data-stu-id="eaad1-162">**Label**</span></span>|<span data-ttu-id="eaad1-163">Local: 94, 18</span><span class="sxs-lookup"><span data-stu-id="eaad1-163">Location: 94, 18</span></span><br /><br /> <span data-ttu-id="eaad1-164">Texto: Adivinhe um número de 1 a</span><span class="sxs-lookup"><span data-stu-id="eaad1-164">Text: Guess a number from 1 to</span></span>|
    |<span data-ttu-id="eaad1-165">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="eaad1-165">**ComboBox**</span></span>|<span data-ttu-id="eaad1-166">Nome: NumberRange</span><span class="sxs-lookup"><span data-stu-id="eaad1-166">Name: NumberRange</span></span><br /><br /> <span data-ttu-id="eaad1-167">DropDownstyle: DropDownList</span><span class="sxs-lookup"><span data-stu-id="eaad1-167">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="eaad1-168">Itens: 10, 100, 1000</span><span class="sxs-lookup"><span data-stu-id="eaad1-168">Items: 10, 100, 1000</span></span><br /><br /> <span data-ttu-id="eaad1-169">Local: 228, 12</span><span class="sxs-lookup"><span data-stu-id="eaad1-169">Location: 228, 12</span></span><br /><br /> <span data-ttu-id="eaad1-170">Tamanho: 143, 21</span><span class="sxs-lookup"><span data-stu-id="eaad1-170">Size: 143, 21</span></span>|
    |<span data-ttu-id="eaad1-171">**Rotular**</span><span class="sxs-lookup"><span data-stu-id="eaad1-171">**Label**</span></span>|<span data-ttu-id="eaad1-172">Local: 13, 43</span><span class="sxs-lookup"><span data-stu-id="eaad1-172">Location: 13, 43</span></span><br /><br /> <span data-ttu-id="eaad1-173">Texto: tipo de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="eaad1-173">Text: Workflow type</span></span>|
    |<span data-ttu-id="eaad1-174">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="eaad1-174">**ComboBox**</span></span>|<span data-ttu-id="eaad1-175">Nome: fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="eaad1-175">Name: WorkflowType</span></span><br /><br /> <span data-ttu-id="eaad1-176">DropDownstyle: DropDownList</span><span class="sxs-lookup"><span data-stu-id="eaad1-176">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="eaad1-177">Itens: StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="eaad1-177">Items: StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow</span></span><br /><br /> <span data-ttu-id="eaad1-178">Local: 94, 40</span><span class="sxs-lookup"><span data-stu-id="eaad1-178">Location: 94, 40</span></span><br /><br /> <span data-ttu-id="eaad1-179">Tamanho: 277, 21</span><span class="sxs-lookup"><span data-stu-id="eaad1-179">Size: 277, 21</span></span>|
    |<span data-ttu-id="eaad1-180">**Rotular**</span><span class="sxs-lookup"><span data-stu-id="eaad1-180">**Label**</span></span>|<span data-ttu-id="eaad1-181">Nome: WorkflowVersion</span><span class="sxs-lookup"><span data-stu-id="eaad1-181">Name: WorkflowVersion</span></span><br /><br /> <span data-ttu-id="eaad1-182">Local: 13, 362</span><span class="sxs-lookup"><span data-stu-id="eaad1-182">Location: 13, 362</span></span><br /><br /> <span data-ttu-id="eaad1-183">Texto: versão do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="eaad1-183">Text: Workflow version</span></span>|
    |<span data-ttu-id="eaad1-184">**GroupBox**</span><span class="sxs-lookup"><span data-stu-id="eaad1-184">**GroupBox**</span></span>|<span data-ttu-id="eaad1-185">Local: 13, 67</span><span class="sxs-lookup"><span data-stu-id="eaad1-185">Location: 13, 67</span></span><br /><br /> <span data-ttu-id="eaad1-186">Tamanho: 358, 287</span><span class="sxs-lookup"><span data-stu-id="eaad1-186">Size: 358, 287</span></span><br /><br /> <span data-ttu-id="eaad1-187">Texto: jogo</span><span class="sxs-lookup"><span data-stu-id="eaad1-187">Text: Game</span></span>|

    > [!NOTE]
    > <span data-ttu-id="eaad1-188">Ao adicionar os seguintes controles, coloque-os na GroupBox.</span><span class="sxs-lookup"><span data-stu-id="eaad1-188">When adding the following controls, put them into the GroupBox.</span></span>

    |<span data-ttu-id="eaad1-189">Control</span><span class="sxs-lookup"><span data-stu-id="eaad1-189">Control</span></span>|<span data-ttu-id="eaad1-190">Propriedade: valor</span><span class="sxs-lookup"><span data-stu-id="eaad1-190">Property: Value</span></span>|
    |-------------|---------------------|
    |<span data-ttu-id="eaad1-191">**Rotular**</span><span class="sxs-lookup"><span data-stu-id="eaad1-191">**Label**</span></span>|<span data-ttu-id="eaad1-192">Local: 7, 20</span><span class="sxs-lookup"><span data-stu-id="eaad1-192">Location: 7, 20</span></span><br /><br /> <span data-ttu-id="eaad1-193">Texto: ID da instância do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="eaad1-193">Text: Workflow Instance Id</span></span>|
    |<span data-ttu-id="eaad1-194">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="eaad1-194">**ComboBox**</span></span>|<span data-ttu-id="eaad1-195">Nome: InstanceId</span><span class="sxs-lookup"><span data-stu-id="eaad1-195">Name: InstanceId</span></span><br /><br /> <span data-ttu-id="eaad1-196">DropDownstyle: DropDownList</span><span class="sxs-lookup"><span data-stu-id="eaad1-196">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="eaad1-197">Local: 121, 17</span><span class="sxs-lookup"><span data-stu-id="eaad1-197">Location: 121, 17</span></span><br /><br /> <span data-ttu-id="eaad1-198">Tamanho: 227, 21</span><span class="sxs-lookup"><span data-stu-id="eaad1-198">Size: 227, 21</span></span>|
    |<span data-ttu-id="eaad1-199">**Rotular**</span><span class="sxs-lookup"><span data-stu-id="eaad1-199">**Label**</span></span>|<span data-ttu-id="eaad1-200">Local: 7, 47</span><span class="sxs-lookup"><span data-stu-id="eaad1-200">Location: 7, 47</span></span><br /><br /> <span data-ttu-id="eaad1-201">Texto: estimativa</span><span class="sxs-lookup"><span data-stu-id="eaad1-201">Text: Guess</span></span>|
    |<span data-ttu-id="eaad1-202">**TextBox**</span><span class="sxs-lookup"><span data-stu-id="eaad1-202">**TextBox**</span></span>|<span data-ttu-id="eaad1-203">Nome: palpite</span><span class="sxs-lookup"><span data-stu-id="eaad1-203">Name: Guess</span></span><br /><br /> <span data-ttu-id="eaad1-204">Local: 50, 44</span><span class="sxs-lookup"><span data-stu-id="eaad1-204">Location: 50, 44</span></span><br /><br /> <span data-ttu-id="eaad1-205">Tamanho: 65, 20</span><span class="sxs-lookup"><span data-stu-id="eaad1-205">Size: 65, 20</span></span>|
    |<span data-ttu-id="eaad1-206">**Botão**</span><span class="sxs-lookup"><span data-stu-id="eaad1-206">**Button**</span></span>|<span data-ttu-id="eaad1-207">Nome: EnterGuess</span><span class="sxs-lookup"><span data-stu-id="eaad1-207">Name: EnterGuess</span></span><br /><br /> <span data-ttu-id="eaad1-208">Local: 121, 42</span><span class="sxs-lookup"><span data-stu-id="eaad1-208">Location: 121, 42</span></span><br /><br /> <span data-ttu-id="eaad1-209">Tamanho: 75, 23</span><span class="sxs-lookup"><span data-stu-id="eaad1-209">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="eaad1-210">Texto: Insira uma estimativa</span><span class="sxs-lookup"><span data-stu-id="eaad1-210">Text: Enter Guess</span></span>|
    |<span data-ttu-id="eaad1-211">**Botão**</span><span class="sxs-lookup"><span data-stu-id="eaad1-211">**Button**</span></span>|<span data-ttu-id="eaad1-212">Nome: QuitGame</span><span class="sxs-lookup"><span data-stu-id="eaad1-212">Name: QuitGame</span></span><br /><br /> <span data-ttu-id="eaad1-213">Local: 274, 42</span><span class="sxs-lookup"><span data-stu-id="eaad1-213">Location: 274, 42</span></span><br /><br /> <span data-ttu-id="eaad1-214">Tamanho: 75, 23</span><span class="sxs-lookup"><span data-stu-id="eaad1-214">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="eaad1-215">Texto: sair</span><span class="sxs-lookup"><span data-stu-id="eaad1-215">Text: Quit</span></span>|
    |<span data-ttu-id="eaad1-216">**TextBox**</span><span class="sxs-lookup"><span data-stu-id="eaad1-216">**TextBox**</span></span>|<span data-ttu-id="eaad1-217">Nome: WorkflowStatus</span><span class="sxs-lookup"><span data-stu-id="eaad1-217">Name: WorkflowStatus</span></span><br /><br /> <span data-ttu-id="eaad1-218">Local: 10, 73</span><span class="sxs-lookup"><span data-stu-id="eaad1-218">Location: 10, 73</span></span><br /><br /> <span data-ttu-id="eaad1-219">Multiline: true</span><span class="sxs-lookup"><span data-stu-id="eaad1-219">Multiline: True</span></span><br /><br /> <span data-ttu-id="eaad1-220">ReadOnly: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="eaad1-220">ReadOnly: True</span></span><br /><br /> <span data-ttu-id="eaad1-221">Barras de rolagem: vertical</span><span class="sxs-lookup"><span data-stu-id="eaad1-221">ScrollBars: Vertical</span></span><br /><br /> <span data-ttu-id="eaad1-222">Tamanho: 338, 208</span><span class="sxs-lookup"><span data-stu-id="eaad1-222">Size: 338, 208</span></span>|

5. <span data-ttu-id="eaad1-223">Defina a propriedade **AcceptButton** do formulário como **EnterGuess**.</span><span class="sxs-lookup"><span data-stu-id="eaad1-223">Set the **AcceptButton** property of the form to **EnterGuess**.</span></span>

 <span data-ttu-id="eaad1-224">O exemplo a seguir ilustra o formato concluído.</span><span class="sxs-lookup"><span data-stu-id="eaad1-224">The following example illustrates the completed form.</span></span>

 ![Captura de tela de um formulário de host Windows Workflow Foundation fluxo de trabalho.](./media/how-to-create-and-run-a-long-running-workflow/windows-workflow-foundation-workflowhostform.png)

## <a name="to-add-the-properties-and-helper-methods-of-the-form"></a><span data-ttu-id="eaad1-226">Para adicionar as propriedades e os métodos auxiliares do formulário</span><span class="sxs-lookup"><span data-stu-id="eaad1-226">To add the properties and helper methods of the form</span></span>

<span data-ttu-id="eaad1-227">As etapas nesta seção adicionam propriedades e métodos auxiliares para a classe de formulário que configura a interface de usuário do formulário para dar suporte à execução e à retomada de fluxos de trabalho de palpite de número.</span><span class="sxs-lookup"><span data-stu-id="eaad1-227">The steps in this section add properties and helper methods to the form class that configure the UI of the form to support running and resuming number guess workflows.</span></span>

1. <span data-ttu-id="eaad1-228">Clique com o botão direito do mouse em **WorkflowHostForm** em **Gerenciador de soluções** e escolha **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="eaad1-228">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>

2. <span data-ttu-id="eaad1-229">Adicione as seguintes instruções `using` (ou `Imports`) na parte superior do arquivo com as outras instruções `using` (ou `Imports`).</span><span class="sxs-lookup"><span data-stu-id="eaad1-229">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Activities
    Imports System.Activities.DurableInstancing
    Imports System.Data.SqlClient
    Imports System.IO
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Activities;
    using System.Activities.DurableInstancing;
    using System.Data.SqlClient;
    using System.IO;
    using System.Windows.Forms;
    ```

3. <span data-ttu-id="eaad1-230">Adicione as seguintes declarações de membro à classe **WorkflowHostForm** .</span><span class="sxs-lookup"><span data-stu-id="eaad1-230">Add the following member declarations to the **WorkflowHostForm** class.</span></span>

    ```vb
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"
    Dim store As SqlWorkflowInstanceStore
    Dim workflowStarting As Boolean
    ```

    ```csharp
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";
    SqlWorkflowInstanceStore store;
    bool workflowStarting;
    ```

    > [!NOTE]
    > <span data-ttu-id="eaad1-231">Se sua cadeia de conexão for diferente, atualize `connectionString` para se referir a seu banco de dados.</span><span class="sxs-lookup"><span data-stu-id="eaad1-231">If your connection string is different, update `connectionString` to refer to your database.</span></span>

4. <span data-ttu-id="eaad1-232">Adicione uma propriedade `WorkflowInstanceId` à classe `WorkflowFormHost`.</span><span class="sxs-lookup"><span data-stu-id="eaad1-232">Add a `WorkflowInstanceId` property to the `WorkflowFormHost` class.</span></span>

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

    <span data-ttu-id="eaad1-233">A `InstanceId` caixa de combinação exibe uma lista de IDs de instância de fluxo de trabalho persistentes e a `WorkflowInstanceId` propriedade retorna o fluxo de trabalho selecionado no momento.</span><span class="sxs-lookup"><span data-stu-id="eaad1-233">The `InstanceId` combo box displays a list of persisted workflow instance ids, and the `WorkflowInstanceId` property returns the currently selected workflow.</span></span>

5. <span data-ttu-id="eaad1-234">Adicione um manipulador para o evento `Load` do formulário.</span><span class="sxs-lookup"><span data-stu-id="eaad1-234">Add a handler for the form `Load` event.</span></span> <span data-ttu-id="eaad1-235">Para adicionar o manipulador, alterne para o **modo de exibição de design** do formulário, clique no ícone **eventos** na parte superior da janela **Propriedades** e clique duas vezes em **carregar**.</span><span class="sxs-lookup"><span data-stu-id="eaad1-235">To add the handler, switch to **Design View** for the form, click the **Events** icon at the top of the **Properties** window, and double-click **Load**.</span></span>

    ```vb
    Private Sub WorkflowHostForm_Load(sender As Object, e As EventArgs) Handles Me.Load

    End Sub
    ```

    ```csharp
    private void WorkflowHostForm_Load(object sender, EventArgs e)
    {

    }
    ```

6. <span data-ttu-id="eaad1-236">Adicione o código a seguir ao `WorkflowHostForm_Load`.</span><span class="sxs-lookup"><span data-stu-id="eaad1-236">Add the following code to `WorkflowHostForm_Load`.</span></span>

    ```vb
    ' Initialize the store and configure it so that it can be used for
    ' multiple WorkflowApplication instances.
    store = New SqlWorkflowInstanceStore(connectionString)
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)

    ' Set default ComboBox selections.
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

    <span data-ttu-id="eaad1-237">Quando o formulário carrega, o `SqlWorkflowInstanceStore` é configurado, as caixas de combinação de intervalo e tipo de fluxo de trabalho são definidas com valores padrão, as instâncias de fluxo de trabalho persistidas são adicionadas à caixa de combinação `InstanceId`.</span><span class="sxs-lookup"><span data-stu-id="eaad1-237">When the form loads, the `SqlWorkflowInstanceStore` is configured, the range and workflow type combo boxes are set to default values, and the persisted workflow instances are added to the `InstanceId` combo box.</span></span>

7. <span data-ttu-id="eaad1-238">Adicione um manipulador `SelectedIndexChanged` para `InstanceId`.</span><span class="sxs-lookup"><span data-stu-id="eaad1-238">Add a `SelectedIndexChanged` handler for `InstanceId`.</span></span> <span data-ttu-id="eaad1-239">Para adicionar o manipulador, alterne para o **modo de exibição de design** do formulário, selecione a caixa de `InstanceId` combinação, clique no ícone **eventos** na parte superior da janela **Propriedades** e clique duas vezes em **SelectedIndexChanged**.</span><span class="sxs-lookup"><span data-stu-id="eaad1-239">To add the handler, switch to **Design View** for the form, select the `InstanceId` combo box, click the **Events** icon at the top of the **Properties** window, and double-click **SelectedIndexChanged**.</span></span>

    ```vb
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged

    End Sub
    ```

    ```csharp
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)
    {

    }
    ```

8. <span data-ttu-id="eaad1-240">Adicione o código a seguir ao `InstanceId_SelectedIndexChanged`.</span><span class="sxs-lookup"><span data-stu-id="eaad1-240">Add the following code to `InstanceId_SelectedIndexChanged`.</span></span> <span data-ttu-id="eaad1-241">Sempre que o usuário seleciona um fluxo de trabalho usando a caixa de combinação, esse manipulador atualiza a janela de status.</span><span class="sxs-lookup"><span data-stu-id="eaad1-241">Whenever the user selects a workflow by using the combo box this handler updates the status window.</span></span>

    ```vb
    If InstanceId.SelectedIndex = -1 Then
        Return
    End If

    ' Clear the status window.
    WorkflowStatus.Clear()

    ' Get the workflow version and display it.
    ' If the workflow is just starting then this info will not
    ' be available in the persistence store so do not try and retrieve it.
    If Not workflowStarting Then
        Dim instance As WorkflowApplicationInstance = _
            WorkflowApplication.GetInstance(WorkflowInstanceId, store)

        WorkflowVersion.Text = _
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity)

        ' Unload the instance.
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
    if (!workflowStarting)
    {
        WorkflowApplicationInstance instance =
            WorkflowApplication.GetInstance(this.WorkflowInstanceId, store);

        WorkflowVersion.Text =
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity);

        // Unload the instance.
        instance.Abandon();
    }
    ```

9. <span data-ttu-id="eaad1-242">Adicione o seguinte método `ListPersistedWorkflows` à classe do formulário.</span><span class="sxs-lookup"><span data-stu-id="eaad1-242">Add the following `ListPersistedWorkflows` method to the form class.</span></span>

    ```vb
    Private Sub ListPersistedWorkflows()
        Using localCon As New SqlConnection(connectionString)
            Dim localCmd As String = _
                "SELECT [InstanceId] FROM [System.Activities.DurableInstancing].[Instances] ORDER BY [CreationTime]"

            Dim cmd As SqlCommand = localCon.CreateCommand()
            cmd.CommandText = localCmd
            localCon.Open()
            Using reader As SqlDataReader = cmd.ExecuteReader(CommandBehavior.CloseConnection)

                While (reader.Read())
                    ' Get the InstanceId of the persisted Workflow.
                    Dim id As Guid = Guid.Parse(reader(0).ToString())
                    InstanceId.Items.Add(id)
                End While
            End Using
        End Using
    End Sub
    ```

    ```csharp
    using (var localCon = new SqlConnection(connectionString))
    {
        string localCmd =
            "SELECT [InstanceId] FROM [System.Activities.DurableInstancing].[Instances] ORDER BY [CreationTime]";

        SqlCommand cmd = localCon.CreateCommand();
        cmd.CommandText = localCmd;
        localCon.Open();
        using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))
        {
            while (reader.Read())
            {
                // Get the InstanceId of the persisted Workflow.
                Guid id = Guid.Parse(reader[0].ToString());
                InstanceId.Items.Add(id);
            }
        }
    }
    ```

    <span data-ttu-id="eaad1-243">`ListPersistedWorkflows` consulta o repositório de instâncias em busca de instâncias de fluxo de trabalho persistidas, e adiciona as ids de instância à caixa de combinação `cboInstanceId`.</span><span class="sxs-lookup"><span data-stu-id="eaad1-243">`ListPersistedWorkflows` queries the instance store for persisted workflow instances, and adds the instance ids to the `cboInstanceId` combo box.</span></span>

10. <span data-ttu-id="eaad1-244">Adicione o seguinte método `UpdateStatus` e o delegado correspondente à classe de formulário.</span><span class="sxs-lookup"><span data-stu-id="eaad1-244">Add the following `UpdateStatus` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="eaad1-245">Este método atualiza a janela de status no formulário com o status do fluxo de trabalho em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="eaad1-245">This method updates the status window on the form with the status of the currently running workflow.</span></span>

    ```vb
    Private Delegate Sub UpdateStatusDelegate(msg As String)
    Public Sub UpdateStatus(msg As String)
        ' We may be on a different thread so we need to
        ' make this call using BeginInvoke.
        If InvokeRequired Then
            BeginInvoke(New UpdateStatusDelegate(AddressOf UpdateStatus), msg)
        Else
            If Not msg.EndsWith(vbCrLf) Then
                msg = msg & vbCrLf
            End If

            WorkflowStatus.AppendText(msg)

            ' Ensure that the newly added status is visible.
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

11. <span data-ttu-id="eaad1-246">Adicione o seguinte método `GameOver` e o delegado correspondente à classe de formulário.</span><span class="sxs-lookup"><span data-stu-id="eaad1-246">Add the following `GameOver` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="eaad1-247">Quando um fluxo de trabalho é concluído, esse método atualiza a interface do usuário do formulário removendo a ID da instância do fluxo de trabalho concluído da caixa de combinação **InstanceId** .</span><span class="sxs-lookup"><span data-stu-id="eaad1-247">When a workflow completes, this method updates the form UI by removing the instance id of the completed workflow from the **InstanceId** combo box.</span></span>

    ```vb
    Private Delegate Sub GameOverDelegate()
    Private Sub GameOver()
        If InvokeRequired Then
            BeginInvoke(New GameOverDelegate(AddressOf GameOver))
        Else
            ' Remove this instance from the InstanceId combo box.
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
            // Remove this instance from the combo box.
            InstanceId.Items.Remove(InstanceId.SelectedItem);
            InstanceId.SelectedIndex = -1;
        }
    }
    ```

## <a name="to-configure-the-instance-store-workflow-lifecycle-handlers-and-extensions"></a><span data-ttu-id="eaad1-248">Para configurar o repositório de instâncias, os manipuladores do ciclo de vida de fluxo de trabalho e as extensões</span><span class="sxs-lookup"><span data-stu-id="eaad1-248">To configure the instance store, workflow lifecycle handlers, and extensions</span></span>

1. <span data-ttu-id="eaad1-249">Adicione o método `ConfigureWorkflowApplication` à classe do formulário.</span><span class="sxs-lookup"><span data-stu-id="eaad1-249">Add a `ConfigureWorkflowApplication` method to the form class.</span></span>

    ```vb
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)

    End Sub
    ```

    ```csharp
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)
    {
    }
    ```

    <span data-ttu-id="eaad1-250">Esse método configura o `WorkflowApplication`, adiciona as extensões desejadas e adicionar manipuladores aos eventos de ciclo de vida do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="eaad1-250">This method configures the `WorkflowApplication`, adds the desired extensions, and adds handlers for the workflow lifecycle events.</span></span>

2. <span data-ttu-id="eaad1-251">Em `ConfigureWorkflowApplication`, especifique o `SqlWorkflowInstanceStore` para o `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="eaad1-251">In `ConfigureWorkflowApplication`, specify the `SqlWorkflowInstanceStore` for the `WorkflowApplication`.</span></span>

    ```vb
    ' Configure the persistence store.
    wfApp.InstanceStore = store
    ```

    ```csharp
    // Configure the persistence store.
    wfApp.InstanceStore = store;
    ```

3. <span data-ttu-id="eaad1-252">Em seguida, crie uma instância `StringWriter` e adicione-a à coleção de `Extensions` do `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="eaad1-252">Next, create a `StringWriter` instance and add it to the `Extensions` collection of the `WorkflowApplication`.</span></span> <span data-ttu-id="eaad1-253">Quando um `StringWriter` é adicionado às extensões, ele captura toda a `WriteLine` saída da atividade.</span><span class="sxs-lookup"><span data-stu-id="eaad1-253">When a `StringWriter` is added to the extensions it captures all `WriteLine` activity output.</span></span> <span data-ttu-id="eaad1-254">Quando o fluxo de trabalho fica ocioso, a saída de `WriteLine` pode ser extraída de `StringWriter` e exibida no formulário.</span><span class="sxs-lookup"><span data-stu-id="eaad1-254">When the workflow becomes idle, the `WriteLine` output can be extracted from the `StringWriter` and displayed on the form.</span></span>

    ```vb
    ' Add a StringWriter to the extensions. This captures the output
    ' from the WriteLine activities so we can display it in the form.
    Dim sw As New StringWriter()
    wfApp.Extensions.Add(sw)
    ```

    ```csharp
    // Add a StringWriter to the extensions. This captures the output
    // from the WriteLine activities so we can display it in the form.
    var sw = new StringWriter();
    wfApp.Extensions.Add(sw);
    ```

4. <span data-ttu-id="eaad1-255">Adicione o seguinte manipulador para o evento `Completed`.</span><span class="sxs-lookup"><span data-stu-id="eaad1-255">Add the following handler for the `Completed` event.</span></span> <span data-ttu-id="eaad1-256">Quando um fluxo de trabalho for concluído com êxito, o número de sequências realizadas para dar um palpite do número é exibido na janela de status.</span><span class="sxs-lookup"><span data-stu-id="eaad1-256">When a workflow successfully completes, the number of turns taken to guess the number is displayed to the status window.</span></span> <span data-ttu-id="eaad1-257">Se o fluxo de trabalho terminar, as informações da exceção que causaram a conclusão serão exibidas.</span><span class="sxs-lookup"><span data-stu-id="eaad1-257">If the workflow terminates, the exception information that caused the termination is displayed.</span></span> <span data-ttu-id="eaad1-258">No final do manipulador, o método `GameOver` é chamado, o que remove o fluxo de trabalho concluído da lista de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="eaad1-258">At the end of the handler the `GameOver` method is called, which removes the completed workflow from the workflow list.</span></span>

    ```vb
    wfApp.Completed = _
        Sub(e As WorkflowApplicationCompletedEventArgs)
            If e.CompletionState = ActivityInstanceState.Faulted Then
                UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}{vbCrLf}{e.TerminationException.Message}")
            ElseIf e.CompletionState = ActivityInstanceState.Canceled Then
                UpdateStatus("Workflow Canceled.")
            Else
                Dim turns As Integer = Convert.ToInt32(e.Outputs("Turns"))
                UpdateStatus($"Congratulations, you guessed the number in {turns} turns.")
            End If
            GameOver()
        End Sub
    ```

    ```csharp
    wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)
    {
        if (e.CompletionState == ActivityInstanceState.Faulted)
        {
            UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}\r\n{e.TerminationException.Message}");
        }
        else if (e.CompletionState == ActivityInstanceState.Canceled)
        {
            UpdateStatus("Workflow Canceled.");
        }
        else
        {
            int turns = Convert.ToInt32(e.Outputs["Turns"]);
            UpdateStatus($"Congratulations, you guessed the number in {turns} turns.");
        }
        GameOver();
    };
    ```

5. <span data-ttu-id="eaad1-259">Adicione os seguintes manipuladores `Aborted` e `OnUnhandledException`.</span><span class="sxs-lookup"><span data-stu-id="eaad1-259">Add the following `Aborted` and `OnUnhandledException` handlers.</span></span> <span data-ttu-id="eaad1-260">O método `GameOver` não é chamado do manipulador `Aborted` porque, quando uma instância de fluxo de trabalho é cancelada, ela não termina e é possível retomar a instância posteriormente.</span><span class="sxs-lookup"><span data-stu-id="eaad1-260">The `GameOver` method is not called from the `Aborted` handler because when a workflow instance is aborted, it does not terminate, and it is possible to resume the instance at a later time.</span></span>

    ```vb
    wfApp.Aborted = _
        Sub(e As WorkflowApplicationAbortedEventArgs)
            UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}{vbCrLf}{e.Reason.Message}")
        End Sub

    wfApp.OnUnhandledException = _
        Function(e As WorkflowApplicationUnhandledExceptionEventArgs)
            UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}{vbCrLf}{e.UnhandledException.Message}")
            GameOver()
            Return UnhandledExceptionAction.Terminate
        End Function
    ```

    ```csharp
    wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)
    {
        UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}\r\n{e.Reason.Message}");
    };

    wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)
    {
        UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}\r\n{e.UnhandledException.Message}");
        GameOver();
        return UnhandledExceptionAction.Terminate;
    };
    ```

6. <span data-ttu-id="eaad1-261">Adicione o seguinte manipulador `PersistableIdle`.</span><span class="sxs-lookup"><span data-stu-id="eaad1-261">Add the following `PersistableIdle` handler.</span></span> <span data-ttu-id="eaad1-262">Este manipulador recupera a extensão `StringWriter` que foi adicionada, extrai a saída das atividades de `WriteLine` e as exibe na janela de status.</span><span class="sxs-lookup"><span data-stu-id="eaad1-262">This handler retrieves the `StringWriter` extension that was added, extracts the output from the `WriteLine` activities, and displays it in the status window.</span></span>

    ```vb
    wfApp.PersistableIdle = _
        Function(e As WorkflowApplicationIdleEventArgs)
            ' Send the current WriteLine outputs to the status window.
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

    <span data-ttu-id="eaad1-263">A enumeração <xref:System.Activities.PersistableIdleAction> tem três valores: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist> e <xref:System.Activities.PersistableIdleAction.Unload>.</span><span class="sxs-lookup"><span data-stu-id="eaad1-263">The <xref:System.Activities.PersistableIdleAction> enumeration has three values: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>, and <xref:System.Activities.PersistableIdleAction.Unload>.</span></span> <span data-ttu-id="eaad1-264"><xref:System.Activities.PersistableIdleAction.Persist> faz com o fluxo de trabalho persistir, mas não faz o fluxo de trabalho descarregar.</span><span class="sxs-lookup"><span data-stu-id="eaad1-264"><xref:System.Activities.PersistableIdleAction.Persist> causes the workflow to persist but it does not cause the workflow to unload.</span></span> <span data-ttu-id="eaad1-265"><xref:System.Activities.PersistableIdleAction.Unload> faz o fluxo de trabalho persistir e ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="eaad1-265"><xref:System.Activities.PersistableIdleAction.Unload> causes the workflow to persist and be unloaded.</span></span>

    <span data-ttu-id="eaad1-266">O exemplo a seguir é o método `ConfigureWorkflowApplication` concluído.</span><span class="sxs-lookup"><span data-stu-id="eaad1-266">The following example is the completed `ConfigureWorkflowApplication` method.</span></span>

    ```vb
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)
        ' Configure the persistence store.
        wfApp.InstanceStore = store

        ' Add a StringWriter to the extensions. This captures the output
        ' from the WriteLine activities so we can display it in the form.
        Dim sw As New StringWriter()
        wfApp.Extensions.Add(sw)

        wfApp.Completed = _
            Sub(e As WorkflowApplicationCompletedEventArgs)
                If e.CompletionState = ActivityInstanceState.Faulted Then
                    UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}{vbCrLf}{e.TerminationException.Message}")
                ElseIf e.CompletionState = ActivityInstanceState.Canceled Then
                    UpdateStatus("Workflow Canceled.")
                Else
                    Dim turns As Integer = Convert.ToInt32(e.Outputs("Turns"))
                    UpdateStatus($"Congratulations, you guessed the number in {turns} turns.")
                End If
                GameOver()
            End Sub

        wfApp.Aborted = _
            Sub(e As WorkflowApplicationAbortedEventArgs)
                UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}{vbCrLf}{e.Reason.Message}")
            End Sub

        wfApp.OnUnhandledException = _
            Function(e As WorkflowApplicationUnhandledExceptionEventArgs)
                UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}{vbCrLf}{e.UnhandledException.Message}")
                GameOver()
                Return UnhandledExceptionAction.Terminate
            End Function

        wfApp.PersistableIdle = _
            Function(e As WorkflowApplicationIdleEventArgs)
                ' Send the current WriteLine outputs to the status window.
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
        var sw = new StringWriter();
        wfApp.Extensions.Add(sw);

        wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)
        {
            if (e.CompletionState == ActivityInstanceState.Faulted)
            {
                UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}\r\n{e.TerminationException.Message}");
            }
            else if (e.CompletionState == ActivityInstanceState.Canceled)
            {
                UpdateStatus("Workflow Canceled.");
            }
            else
            {
                int turns = Convert.ToInt32(e.Outputs["Turns"]);
                UpdateStatus($"Congratulations, you guessed the number in {turns} turns.");
            }
            GameOver();
        };

        wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)
        {
            UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}\r\n{e.Reason.Message}");
        };

        wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)
        {
            UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}\r\n{e.UnhandledException.Message}");
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

## <a name="to-enable-starting-and-resuming-multiple-workflow-types"></a><span data-ttu-id="eaad1-267">Para habilitar o início e a retomada de vários tipos de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="eaad1-267">To enable starting and resuming multiple workflow types</span></span>

<span data-ttu-id="eaad1-268">Para retomar uma instância de fluxo de trabalho, o host precisa fornecer a definição de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="eaad1-268">In order to resume a workflow instance, the host has to provide the workflow definition.</span></span> <span data-ttu-id="eaad1-269">Neste tutorial, há três tipos de fluxo de trabalho e as etapas tutoriais subsequentes trazem várias versões desses tipos.</span><span class="sxs-lookup"><span data-stu-id="eaad1-269">In this tutorial there are three workflow types, and subsequent tutorial steps introduce multiple versions of these types.</span></span> <span data-ttu-id="eaad1-270">`WorkflowIdentity` fornece uma maneira de um aplicativo de host associar informações de identificação a uma instância do fluxo de trabalho persistida.</span><span class="sxs-lookup"><span data-stu-id="eaad1-270">`WorkflowIdentity` provides a way for a host application to associate identifying information with a persisted workflow instance.</span></span> <span data-ttu-id="eaad1-271">As etapas nesta seção demonstram como criar uma classe de utilitário para ajudar com o mapeamento da identidade de fluxo de trabalho de uma instância do fluxo de trabalho persistida para a definição do fluxo de trabalho correspondente.</span><span class="sxs-lookup"><span data-stu-id="eaad1-271">The steps in this section demonstrate how to create a utility class to assist with mapping the workflow identity from a persisted workflow instance to the corresponding workflow definition.</span></span> <span data-ttu-id="eaad1-272">Para obter mais informações sobre o `WorkflowIdentity` e o controle de versão, consulte [usando a WorkflowIdentity e o controle de versão](using-workflowidentity-and-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="eaad1-272">For more information about `WorkflowIdentity` and versioning, see [Using WorkflowIdentity and Versioning](using-workflowidentity-and-versioning.md).</span></span>

1. <span data-ttu-id="eaad1-273">Clique com o botão direito do mouse em **NumberGuessWorkflowHost** em **Gerenciador de soluções** e escolha **Adicionar**, **classe**.</span><span class="sxs-lookup"><span data-stu-id="eaad1-273">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="eaad1-274">Digite `WorkflowVersionMap` na caixa **nome** e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="eaad1-274">Type `WorkflowVersionMap` into the **Name** box and click **Add**.</span></span>

2. <span data-ttu-id="eaad1-275">Adicione as seguintes instruções `using` ou `Imports` na parte superior do arquivo com as outras instruções `using` ou `Imports`.</span><span class="sxs-lookup"><span data-stu-id="eaad1-275">Add the following `using` or `Imports` statements at the top of the file with the other `using` or `Imports` statements.</span></span>

    ```vb
    Imports System.Activities
    Imports NumberGuessWorkflowActivities
    ```

    ```csharp
    using System.Activities;
    using NumberGuessWorkflowActivities;
    ```

3. <span data-ttu-id="eaad1-276">Substitua a declaração de classe `WorkflowVersionMap` pela seguinte declaração.</span><span class="sxs-lookup"><span data-stu-id="eaad1-276">Replace the `WorkflowVersionMap` class declaration with the following declaration.</span></span>

    ```vb
    Public Module WorkflowVersionMap
        Dim map As Dictionary(Of WorkflowIdentity, Activity)

        ' Current version identities.
        Public StateMachineNumberGuessIdentity As WorkflowIdentity
        Public FlowchartNumberGuessIdentity As WorkflowIdentity
        Public SequentialNumberGuessIdentity As WorkflowIdentity

        Sub New()
            map = New Dictionary(Of WorkflowIdentity, Activity)

            ' Add the current workflow version identities.
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

    <span data-ttu-id="eaad1-277">O `WorkflowVersionMap` contém três identidades de fluxo de trabalho que mapeiam para as três definições de fluxo de trabalho deste tutorial e é usado nas seções a seguir quando os fluxos de trabalho são iniciados e retomados.</span><span class="sxs-lookup"><span data-stu-id="eaad1-277">`WorkflowVersionMap` contains three workflow identities that map to the three workflow definitions from this tutorial and is used in the following sections when workflows are started and resumed.</span></span>

## <a name="to-start-a-new-workflow"></a><span data-ttu-id="eaad1-278">Para iniciar um novo fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="eaad1-278">To start a new workflow</span></span>

1. <span data-ttu-id="eaad1-279">Adicione um manipulador `Click` para `NewGame`.</span><span class="sxs-lookup"><span data-stu-id="eaad1-279">Add a `Click` handler for `NewGame`.</span></span> <span data-ttu-id="eaad1-280">Para adicionar o manipulador, alterne para o **modo de exibição de design** do formulário e clique duas vezes em `NewGame` .</span><span class="sxs-lookup"><span data-stu-id="eaad1-280">To add the handler, switch to **Design View** for the form, and double-click `NewGame`.</span></span> <span data-ttu-id="eaad1-281">Um manipulador `NewGame_Click` é adicionado e a exibição alterna para a exibição do código para o formulário.</span><span class="sxs-lookup"><span data-stu-id="eaad1-281">A `NewGame_Click` handler is added and the view switches to code view for the form.</span></span> <span data-ttu-id="eaad1-282">Sempre que o usuário clicar nesse botão, um novo fluxo de trabalho será iniciado.</span><span class="sxs-lookup"><span data-stu-id="eaad1-282">Whenever the user clicks this button a new workflow is started.</span></span>

    ```vb
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click

    End Sub
    ```

    ```csharp
    private void NewGame_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="eaad1-283">Adicione o seguinte código ao manipulador de cliques.</span><span class="sxs-lookup"><span data-stu-id="eaad1-283">Add the following code to the click handler.</span></span> <span data-ttu-id="eaad1-284">O código cria um dicionário de argumentos de entrada para o fluxo de trabalho, fechados pelo nome do argumento.</span><span class="sxs-lookup"><span data-stu-id="eaad1-284">This code creates a dictionary of input arguments for the workflow, keyed by argument name.</span></span> <span data-ttu-id="eaad1-285">Esse dicionário tem uma entrada que contém o intervalo de números gerados aleatoriamente recuperados da caixa de combinação do intervalo.</span><span class="sxs-lookup"><span data-stu-id="eaad1-285">This dictionary has one entry that contains the range of the randomly generated number retrieved from the range combo box.</span></span>

    ```vb
    Dim inputs As New Dictionary(Of String, Object)()
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))
    ```

    ```csharp
    var inputs = new Dictionary<string, object>();
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));
    ```

3. <span data-ttu-id="eaad1-286">Em seguida, adicione o código a seguir que inicia o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="eaad1-286">Next, add the following code that starts the workflow.</span></span> <span data-ttu-id="eaad1-287">O `WorkflowIdentity` e a definição de fluxo de trabalho que corresponde ao tipo de fluxo de trabalho selecionado são recuperados usando a classe auxiliar `WorkflowVersionMap`.</span><span class="sxs-lookup"><span data-stu-id="eaad1-287">The `WorkflowIdentity` and workflow definition corresponding to the type of workflow selected are retrieved using the `WorkflowVersionMap` helper class.</span></span> <span data-ttu-id="eaad1-288">Em seguida, uma nova instância de `WorkflowApplication` é criada usando a definição de fluxo de trabalho, `WorkflowIdentity`, e o dicionário de argumentos de entrada.</span><span class="sxs-lookup"><span data-stu-id="eaad1-288">Next, a new `WorkflowApplication` instance is created using the workflow definition, `WorkflowIdentity`, and dictionary of input arguments.</span></span>

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

4. <span data-ttu-id="eaad1-289">Em seguida, adicione o código a seguir, que adiciona o fluxo de trabalho à lista de fluxo de trabalho e exibe as informações de versão do fluxo de trabalho no formulário.</span><span class="sxs-lookup"><span data-stu-id="eaad1-289">Next, add the following code which adds the workflow to the workflow list and displays the workflow's version information on the form.</span></span>

    ```vb
    ' Add the workflow to the list and display the version information.
    workflowStarting = True
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)
    WorkflowVersion.Text = identity.ToString()
    workflowStarting = False
    ```

    ```csharp
    // Add the workflow to the list and display the version information.
    workflowStarting = true;
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);
    WorkflowVersion.Text = identity.ToString();
    workflowStarting = false;
    ```

5. <span data-ttu-id="eaad1-290">Chame `ConfigureWorkflowApplication` para configurar o repositório de instâncias, as extensões e os manipuladores do ciclo de vida de fluxo de trabalho para essa instância `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="eaad1-290">Call `ConfigureWorkflowApplication` to configure the instance store, extensions, and workflow lifecycle handlers for this `WorkflowApplication` instance.</span></span>

    ```vb
    ' Configure the instance store, extensions, and
    ' workflow lifecycle handlers.
    ConfigureWorkflowApplication(wfApp)
    ```

    ```csharp
    // Configure the instance store, extensions, and
    // workflow lifecycle handlers.
    ConfigureWorkflowApplication(wfApp);
    ```

6. <span data-ttu-id="eaad1-291">Finalmente, chame `Run`.</span><span class="sxs-lookup"><span data-stu-id="eaad1-291">Finally, call `Run`.</span></span>

    ```vb
    ' Start the workflow.
    wfApp.Run()
    ```

    ```csharp
    // Start the workflow.
    wfApp.Run();
    ```

     <span data-ttu-id="eaad1-292">O exemplo a seguir é o manipulador `NewGame_Click` concluído.</span><span class="sxs-lookup"><span data-stu-id="eaad1-292">The following example is the completed `NewGame_Click` handler.</span></span>

    ```vb
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click
        ' Start a new workflow.
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

        ' Add the workflow to the list and display the version information.
        workflowStarting = True
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)
        WorkflowVersion.Text = identity.ToString()
        workflowStarting = False

        ' Configure the instance store, extensions, and
        ' workflow lifecycle handlers.
        ConfigureWorkflowApplication(wfApp)

        ' Start the workflow.
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

        var wfApp = new WorkflowApplication(wf, inputs, identity);

        // Add the workflow to the list and display the version information.
        workflowStarting = true;
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);
        WorkflowVersion.Text = identity.ToString();
        workflowStarting = false;

        // Configure the instance store, extensions, and
        // workflow lifecycle handlers.
        ConfigureWorkflowApplication(wfApp);

        // Start the workflow.
        wfApp.Run();
    }
    ```

## <a name="to-resume-a-workflow"></a><span data-ttu-id="eaad1-293">Para retomar um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="eaad1-293">To resume a workflow</span></span>

1. <span data-ttu-id="eaad1-294">Adicione um manipulador `Click` para `EnterGuess`.</span><span class="sxs-lookup"><span data-stu-id="eaad1-294">Add a `Click` handler for `EnterGuess`.</span></span> <span data-ttu-id="eaad1-295">Para adicionar o manipulador, alterne para o **modo de exibição de design** do formulário e clique duas vezes em `EnterGuess` .</span><span class="sxs-lookup"><span data-stu-id="eaad1-295">To add the handler, switch to **Design View** for the form, and double-click `EnterGuess`.</span></span> <span data-ttu-id="eaad1-296">Sempre que o usuário clicar nesse botão, um fluxo de trabalho é retomado.</span><span class="sxs-lookup"><span data-stu-id="eaad1-296">Whenever the user clicks this button a workflow is resumed.</span></span>

    ```vb
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click

    End Sub
    ```

    ```csharp
    private void EnterGuess_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="eaad1-297">Adicione o código a seguir para garantir que um fluxo de trabalho seja selecionado na lista de fluxo de trabalho, e que o palpite do usuário seja válido.</span><span class="sxs-lookup"><span data-stu-id="eaad1-297">Add the following code to ensure that a workflow is selected in the workflow list, and that the user's guess is valid.</span></span>

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

3. <span data-ttu-id="eaad1-298">Em seguida, recupere o `WorkflowApplicationInstance` da instância do fluxo de trabalho persistida.</span><span class="sxs-lookup"><span data-stu-id="eaad1-298">Next, retrieve the `WorkflowApplicationInstance` of the persisted workflow instance.</span></span> <span data-ttu-id="eaad1-299">Um `WorkflowApplicationInstance` representa uma instância do fluxo de trabalho persistida que ainda não esteja associada a uma definição de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="eaad1-299">A `WorkflowApplicationInstance` represents a persisted workflow instance that has not yet been associated with a workflow definition.</span></span> <span data-ttu-id="eaad1-300">O `DefinitionIdentity` do `WorkflowApplicationInstance` contém o `WorkflowIdentity` da instância do fluxo de trabalho persistida.</span><span class="sxs-lookup"><span data-stu-id="eaad1-300">The `DefinitionIdentity` of the `WorkflowApplicationInstance` contains the `WorkflowIdentity` of the persisted workflow instance.</span></span> <span data-ttu-id="eaad1-301">Neste tutorial, a classe de utilitário `WorkflowVersionMap` é usada para mapear o `WorkflowIdentity` para a definição correta de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="eaad1-301">In this tutorial, the `WorkflowVersionMap` utility class is used to map the `WorkflowIdentity` to the correct workflow definition.</span></span> <span data-ttu-id="eaad1-302">Quando a definição de fluxo de trabalho é recuperada, um `WorkflowApplication` é criado, usando a definição correta de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="eaad1-302">Once the workflow definition is retrieved, a `WorkflowApplication` is created, using the correct workflow definition.</span></span>

    ```vb
    Dim instance As WorkflowApplicationInstance = _
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)

    ' Use the persisted WorkflowIdentity to retrieve the correct workflow
    ' definition from the dictionary.
    Dim wf As Activity = _
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)

    ' Associate the WorkflowApplication with the correct definition
    Dim wfApp As New WorkflowApplication(wf, instance.DefinitionIdentity)
    ```

    ```csharp
    WorkflowApplicationInstance instance =
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);

    // Use the persisted WorkflowIdentity to retrieve the correct workflow
    // definition from the dictionary.
    Activity wf =
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);

    // Associate the WorkflowApplication with the correct definition
    var wfApp = new WorkflowApplication(wf, instance.DefinitionIdentity);
    ```

4. <span data-ttu-id="eaad1-303">Quando a `WorkflowApplication` é criada, configure o repositório de instâncias, os manipuladores do ciclo de vida de fluxo de trabalho e as extensões chamando `ConfigureWorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="eaad1-303">Once the `WorkflowApplication` is created, configure the instance store, workflow lifecycle handlers, and extensions by calling `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="eaad1-304">Essas etapas devem ser executadas toda vez que um `WorkflowApplication` novo é criado, e devem ser feitas antes que a instância de fluxo de trabalho seja carregada no `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="eaad1-304">These steps must be done every time a new `WorkflowApplication` is created, and they must be done before the workflow instance is loaded into the `WorkflowApplication`.</span></span> <span data-ttu-id="eaad1-305">Depois que o fluxo de trabalho é carregado, ele será retomado com o palpite do usuário.</span><span class="sxs-lookup"><span data-stu-id="eaad1-305">After the workflow is loaded, it is resumed with the user's guess.</span></span>

    ```vb
    ' Configure the extensions and lifecycle handlers.
    ' Do this before the instance is loaded. Once the instance is
    ' loaded it is too late to add extensions.
    ConfigureWorkflowApplication(wfApp)

    ' Load the workflow.
    wfApp.Load(instance)

    ' Resume the workflow.
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

5. <span data-ttu-id="eaad1-306">Finalmente, desmarque a caixa de texto de palpite e prepare o formulário para aceitar outro palpite.</span><span class="sxs-lookup"><span data-stu-id="eaad1-306">Finally, clear the guess textbox and prepare the form to accept another guess.</span></span>

    ```vb
    ' Clear the Guess textbox.
    Guess.Clear()
    Guess.Focus()
    ```

    ```csharp
    // Clear the Guess textbox.
    Guess.Clear();
    Guess.Focus();
    ```

    <span data-ttu-id="eaad1-307">O exemplo a seguir é o manipulador `EnterGuess_Click` concluído.</span><span class="sxs-lookup"><span data-stu-id="eaad1-307">The following example is the completed `EnterGuess_Click` handler.</span></span>

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

        ' Use the persisted WorkflowIdentity to retrieve the correct workflow
        ' definition from the dictionary.
        Dim wf As Activity = _
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)

        ' Associate the WorkflowApplication with the correct definition
        Dim wfApp As New WorkflowApplication(wf, instance.DefinitionIdentity)

        ' Configure the extensions and lifecycle handlers.
        ' Do this before the instance is loaded. Once the instance is
        ' loaded it is too late to add extensions.
        ConfigureWorkflowApplication(wfApp)

        ' Load the workflow.
        wfApp.Load(instance)

        ' Resume the workflow.
        wfApp.ResumeBookmark("EnterGuess", userGuess)

        ' Clear the Guess textbox.
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
        var wfApp = new WorkflowApplication(wf, instance.DefinitionIdentity);

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

## <a name="to-terminate-a-workflow"></a><span data-ttu-id="eaad1-308">Para encerrar um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="eaad1-308">To terminate a workflow</span></span>

1. <span data-ttu-id="eaad1-309">Adicione um manipulador `Click` para `QuitGame`.</span><span class="sxs-lookup"><span data-stu-id="eaad1-309">Add a `Click` handler for `QuitGame`.</span></span> <span data-ttu-id="eaad1-310">Para adicionar o manipulador, alterne para o **modo de exibição de design** do formulário e clique duas vezes em `QuitGame` .</span><span class="sxs-lookup"><span data-stu-id="eaad1-310">To add the handler, switch to **Design View** for the form, and double-click `QuitGame`.</span></span> <span data-ttu-id="eaad1-311">Sempre que o usuário clicar nesse botão, o fluxo de trabalho selecionado atual será encerrado.</span><span class="sxs-lookup"><span data-stu-id="eaad1-311">Whenever the user clicks this button the currently selected workflow is terminated.</span></span>

    ```vb
    Private Sub QuitGame_Click(sender As Object, e As EventArgs) Handles QuitGame.Click

    End Sub
    ```

    ```csharp
    private void QuitGame_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="eaad1-312">Adicione o seguinte código ao manipulador `QuitGame_Click`.</span><span class="sxs-lookup"><span data-stu-id="eaad1-312">Add the following code to the `QuitGame_Click` handler.</span></span> <span data-ttu-id="eaad1-313">Esse código primeiro verifica para garantir que um fluxo de trabalho esteja selecionado na lista de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="eaad1-313">This code first checks to ensure that a workflow is selected in the workflow list.</span></span> <span data-ttu-id="eaad1-314">Em seguida, ele carrega a instância persistida em um `WorkflowApplicationInstance`, use a `DefinitionIdentity` para determinar a definição correta de fluxo de trabalho e depois inicializa o `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="eaad1-314">Then it loads the persisted instance into a `WorkflowApplicationInstance`, uses the `DefinitionIdentity` to determine the correct workflow definition, and then initializes the `WorkflowApplication`.</span></span> <span data-ttu-id="eaad1-315">Em seguida, as extensões e os manipuladores de ciclo de vida de fluxo de trabalho são configurados com uma chamada para `ConfigureWorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="eaad1-315">Next the extensions and workflow lifecycle handlers are configured with a call to `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="eaad1-316">Quando o `WorkflowApplication` é configurado, ele será carregado e, em seguida, `Terminate` será chamado.</span><span class="sxs-lookup"><span data-stu-id="eaad1-316">Once the `WorkflowApplication` is configured, it is loaded, and then `Terminate` is called.</span></span>

    ```vb
    If WorkflowInstanceId = Guid.Empty Then
        MessageBox.Show("Please select a workflow.")
        Return
    End If

    Dim instance As WorkflowApplicationInstance = _
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)

    ' Use the persisted WorkflowIdentity to retrieve the correct workflow
    ' definition from the dictionary.
    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)

    ' Associate the WorkflowApplication with the correct definition.
    Dim wfApp As New WorkflowApplication(wf, instance.DefinitionIdentity)

    ' Configure the extensions and lifecycle handlers.
    ConfigureWorkflowApplication(wfApp)

    ' Load the workflow.
    wfApp.Load(instance)

    ' Terminate the workflow.
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
    var wfApp = new WorkflowApplication(wf, instance.DefinitionIdentity);

    // Configure the extensions and lifecycle handlers
    ConfigureWorkflowApplication(wfApp);

    // Load the workflow.
    wfApp.Load(instance);

    // Terminate the workflow.
    wfApp.Terminate("User resigns.");
    ```

## <a name="to-build-and-run-the-application"></a><span data-ttu-id="eaad1-317">Para criar e executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="eaad1-317">To build and run the application</span></span>

1. <span data-ttu-id="eaad1-318">Clique duas vezes em **Program.cs** (ou **Module1. vb**) em **Gerenciador de soluções** para exibir o código.</span><span class="sxs-lookup"><span data-stu-id="eaad1-318">Double-click **Program.cs** (or **Module1.vb**) in **Solution Explorer** to display the code.</span></span>

2. <span data-ttu-id="eaad1-319">Adicione a seguinte instrução `using` (ou `Imports`) na parte superior do arquivo com as outras instruções `using` (ou `Imports`).</span><span class="sxs-lookup"><span data-stu-id="eaad1-319">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Windows.Forms;
    ```

3. <span data-ttu-id="eaad1-320">Remova ou comente o código de hospedagem do fluxo de trabalho existente de [como executar um fluxo de trabalho](how-to-run-a-workflow.md)e substitua-o pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="eaad1-320">Remove or comment out the existing workflow hosting code from [How to: Run a Workflow](how-to-run-a-workflow.md), and replace it with the following code.</span></span>

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

4. <span data-ttu-id="eaad1-321">Clique com o botão direito do mouse em **NumberGuessWorkflowHost** em **Gerenciador de soluções** e escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="eaad1-321">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Properties**.</span></span> <span data-ttu-id="eaad1-322">Na guia **aplicativo** , especifique **aplicativo do Windows** para o **tipo de saída**.</span><span class="sxs-lookup"><span data-stu-id="eaad1-322">In the **Application** tab, specify **Windows Application** for the **Output type**.</span></span> <span data-ttu-id="eaad1-323">Essa etapa é opcional, mas se não for seguida, a janela do console será exibida além do formulário.</span><span class="sxs-lookup"><span data-stu-id="eaad1-323">This step is optional, but if it is not followed the console window is displayed in addition to the form.</span></span>

5. <span data-ttu-id="eaad1-324">Pressione Ctrl+Shift+B para criar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eaad1-324">Press Ctrl+Shift+B to build the application.</span></span>

6. <span data-ttu-id="eaad1-325">Verifique se **NumberGuessWorkflowHost** está definido como o aplicativo de inicialização e pressione CTRL + F5 para iniciar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eaad1-325">Ensure that **NumberGuessWorkflowHost** is set as the startup application, and press Ctrl+F5 to start the application.</span></span>

7. <span data-ttu-id="eaad1-326">Selecione um intervalo para o jogo de adivinhação e o tipo de fluxo de trabalho a ser iniciado e clique em **novo jogo**.</span><span class="sxs-lookup"><span data-stu-id="eaad1-326">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="eaad1-327">Insira uma estimativa na caixa de **estimativa** e clique em **ir** para enviar sua estimativa.</span><span class="sxs-lookup"><span data-stu-id="eaad1-327">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="eaad1-328">Observe que a saída das atividades de `WriteLine` são exibidas no formulário.</span><span class="sxs-lookup"><span data-stu-id="eaad1-328">Note that the output from the `WriteLine` activities is displayed on the form.</span></span>

8. <span data-ttu-id="eaad1-329">Inicie vários fluxos de trabalho usando diferentes tipos de fluxo de trabalho e intervalos de números, insira alguns palpites e alterne entre os fluxos de trabalho selecionando na lista **ID da instância do fluxo de trabalho** .</span><span class="sxs-lookup"><span data-stu-id="eaad1-329">Start several workflows using different workflow types and number ranges, enter some guesses, and switch between the workflows by selecting from the **Workflow Instance Id** list.</span></span>

    <span data-ttu-id="eaad1-330">Observe que, quando você alterna para um novo fluxo de trabalho, os palpites anteriores e o progresso do fluxo de trabalho não são exibidos na janela de status.</span><span class="sxs-lookup"><span data-stu-id="eaad1-330">Note that when you switch to a new workflow, the previous guesses and progress of the workflow are not displayed in the status window.</span></span> <span data-ttu-id="eaad1-331">A razão pela qual o status não está disponível é porque ele não é capturado e salvo em nenhum lugar.</span><span class="sxs-lookup"><span data-stu-id="eaad1-331">The reason the status is not available is because it is not captured and saved anywhere.</span></span> <span data-ttu-id="eaad1-332">Na próxima etapa do tutorial, [como criar um participante de acompanhamento personalizado](how-to-create-a-custom-tracking-participant.md), você cria um participante de acompanhamento personalizado que salva essas informações.</span><span class="sxs-lookup"><span data-stu-id="eaad1-332">In the next step of the tutorial, [How to: Create a Custom Tracking Participant](how-to-create-a-custom-tracking-participant.md), you create a custom tracking participant that saves this information.</span></span>

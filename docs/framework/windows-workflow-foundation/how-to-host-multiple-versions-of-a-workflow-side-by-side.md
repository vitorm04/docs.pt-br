---
title: 'Como: hospedar várias versões de um fluxo de trabalho lado a lado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09c575df-e0a3-4f3b-9e01-a7ac59d65287
ms.openlocfilehash: 4fc4565db58d008f52bc047d26118fc849648770
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59329447"
---
# <a name="how-to-host-multiple-versions-of-a-workflow-side-by-side"></a><span data-ttu-id="0c4fe-102">Como: hospedar várias versões de um fluxo de trabalho lado a lado</span><span class="sxs-lookup"><span data-stu-id="0c4fe-102">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>
<span data-ttu-id="0c4fe-103">O `WorkflowIdentity` fornece uma maneira para que os desenvolvedores de aplicativos de fluxo de trabalho associem um nome e uma versão a uma definição de fluxo de trabalho, e para que essas informações sejam associadas a uma instância de fluxo de trabalho persistida.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-103">`WorkflowIdentity` provides a way for workflow application developers to associate a name and a version with a workflow definition, and for this information to be associated with a persisted workflow instance.</span></span> <span data-ttu-id="0c4fe-104">Essas informações de identidade podem ser usadas por desenvolvedores de aplicativos de fluxo de trabalho para habilitar cenários como execução lado a lado de várias versões de uma definição de fluxo de trabalho, e fornece o pilar para outra funcionalidade como a atualização dinâmica.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-104">This identity information can be used by workflow application developers to enable scenarios such as side-by-side execution of multiple versions of a workflow definition, and provides the cornerstone for other functionality such as dynamic update.</span></span> <span data-ttu-id="0c4fe-105">Esta etapa no tutorial demonstra como usar o `WorkflowIdentity` para hospedar ao mesmo tempo várias versões de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-105">This step in the tutorial demonstrates how to use `WorkflowIdentity` to host multiple versions of a workflow at the same time.</span></span>

> [!NOTE]
>  <span data-ttu-id="0c4fe-106">Para baixar uma versão completa ou exibir uma vídeo passo a passo do tutorial, consulte [Windows Workflow Foundation (WF45) - Tutorial de Introdução](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="0c4fe-106">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="0c4fe-107">Neste tópico</span><span class="sxs-lookup"><span data-stu-id="0c4fe-107">In this topic</span></span>  
 <span data-ttu-id="0c4fe-108">Nesta etapa do tutorial, as atividades `WriteLine` no fluxo de trabalho são modificadas para fornecer informações adicionais e uma nova atividade `WriteLine` é adicionada.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-108">In this step of the tutorial, the `WriteLine` activities in the workflow are modified to provide additional information, and a new `WriteLine` activity is added.</span></span> <span data-ttu-id="0c4fe-109">Uma cópia do assembly original do fluxo de trabalho é armazenada e o aplicativo host é atualizado de forma que possa executar os fluxos de trabalho atualizados e originais ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-109">A copy of the original workflow assembly is stored, and the host application is updated so that it can run both the original and the updated workflows at the same time.</span></span>  
  
-   [<span data-ttu-id="0c4fe-110">Para fazer uma cópia do projeto NumberGuessWorkflowActivities</span><span class="sxs-lookup"><span data-stu-id="0c4fe-110">To make a copy of the NumberGuessWorkflowActivities project</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BackupCopy)  
  
-   [<span data-ttu-id="0c4fe-111">Para atualizar os fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="0c4fe-111">To update the workflows</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflows)  
  
    -   [<span data-ttu-id="0c4fe-112">Para atualizar o fluxo de trabalho StateMachine</span><span class="sxs-lookup"><span data-stu-id="0c4fe-112">To update the StateMachine workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateStateMachine)  
  
    -   [<span data-ttu-id="0c4fe-113">Para atualizar o fluxo de trabalho de fluxograma</span><span class="sxs-lookup"><span data-stu-id="0c4fe-113">To update the Flowchart workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateFlowchart)  
  
    -   [<span data-ttu-id="0c4fe-114">Para atualizar o fluxo de trabalho sequencial</span><span class="sxs-lookup"><span data-stu-id="0c4fe-114">To update the Sequential workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateSequential)  
  
-   [<span data-ttu-id="0c4fe-115">Para atualizar WorkflowVersionMap para incluir as versões anteriores do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="0c4fe-115">To update WorkflowVersionMap to include the previous workflow versions</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflowVersionMap)  
  
-   [<span data-ttu-id="0c4fe-116">Para compilar e executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="0c4fe-116">To build and run the application</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BuildAndRun)  
  
> [!NOTE]
>  <span data-ttu-id="0c4fe-117">Antes de seguir as etapas deste tópico, execute o aplicativo, inicie vários fluxos de trabalho de cada tipo e dê um ou dois palpites para cada um.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-117">Before following the steps in this topic, run the application, start several workflows of each type, and making one or two guesses for each one.</span></span> <span data-ttu-id="0c4fe-118">Esses fluxos de trabalho persistidos são usados nesta etapa e a etapa a seguir, [como: Atualizar a definição de uma instância de fluxo de trabalho em execução](how-to-update-the-definition-of-a-running-workflow-instance.md).</span><span class="sxs-lookup"><span data-stu-id="0c4fe-118">These persisted workflows are used in this step and the following step, [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="0c4fe-119">Cada etapa do tutorial de Introdução depende das etapas anteriores.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-119">Each step in the Getting Started tutorial depends on the previous steps.</span></span> <span data-ttu-id="0c4fe-120">Se você não tiver concluído as etapas anteriores, você pode baixar uma versão completa do tutorial do [Windows Workflow Foundation (WF45) - Tutorial de Introdução](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="0c4fe-120">If you did not complete the previous steps you can download a completed version of the tutorial from [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="BKMK_BackupCopy"></a> <span data-ttu-id="0c4fe-121">Para fazer uma cópia do projeto NumberGuessWorkflowActivities</span><span class="sxs-lookup"><span data-stu-id="0c4fe-121">To make a copy of the NumberGuessWorkflowActivities project</span></span>  
  
1. <span data-ttu-id="0c4fe-122">Abra o **WF45GettingStartedTutorial** solução no Visual Studio 2012 se não estiver aberto.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-122">Open the **WF45GettingStartedTutorial** solution in Visual Studio 2012 if it is not open.</span></span>  
  
2. <span data-ttu-id="0c4fe-123">Pressione CTRL+SHIFT+B para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-123">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3. <span data-ttu-id="0c4fe-124">Fechar o **WF45GettingStartedTutorial** solução.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-124">Close the **WF45GettingStartedTutorial** solution.</span></span>  
  
4. <span data-ttu-id="0c4fe-125">Abra o Windows Explorer e navegue até a pasta onde o arquivo da solução do tutorial e as pastas do projeto estão localizados.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-125">Open Windows Explorer and navigate to the folder where the tutorial solution file and the project folders are located.</span></span>  
  
5. <span data-ttu-id="0c4fe-126">Criar uma nova pasta chamada **PreviousVersions** na mesma pasta que **NumberGuessWorkflowHost** e **NumberGuessWorkflowActivities**.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-126">Create a new folder named **PreviousVersions** in the same folder as **NumberGuessWorkflowHost** and **NumberGuessWorkflowActivities**.</span></span> <span data-ttu-id="0c4fe-127">Essa pasta é usada para conter os assemblies que contêm as versões diferentes dos fluxos de trabalho usados nas etapas subsequentes do tutorial.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-127">This folder is used to contain the assemblies that contain the different versions of the workflows used in the subsequent tutorial steps.</span></span>  
  
6. <span data-ttu-id="0c4fe-128">Navegue até a **NumberGuessWorkflowActivities\bin\debug** pasta (ou **bin\release** dependendo de suas configurações de projeto).</span><span class="sxs-lookup"><span data-stu-id="0c4fe-128">Navigate to the **NumberGuessWorkflowActivities\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="0c4fe-129">Cópia **Numberguessworkflowactivities** e cole-o **PreviousVersions** pasta.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-129">Copy **NumberGuessWorkflowActivities.dll** and paste it into the **PreviousVersions** folder.</span></span>  
  
7. <span data-ttu-id="0c4fe-130">Renomeie **Numberguessworkflowactivities** na **PreviousVersions** pasta a ser **NumberGuessWorkflowActivities_v1.dll**.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-130">Rename **NumberGuessWorkflowActivities.dll** in the **PreviousVersions** folder to **NumberGuessWorkflowActivities_v1.dll**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0c4fe-131">As etapas deste tópico demonstram uma maneira de gerenciar os assemblies usados para conter várias versões dos fluxos de trabalho.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-131">The steps in this topic demonstrate one way to manage the assemblies used to contain multiple versions of the workflows.</span></span> <span data-ttu-id="0c4fe-132">Outros métodos como nomeação forte dos assemblies e registrando deles no cache de assembly global também podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-132">Other methods such as strong naming the assemblies and registering them in the global assembly cache could also be used.</span></span>

8. <span data-ttu-id="0c4fe-133">Criar uma nova pasta chamada **NumberGuessWorkflowActivities_du** na mesma pasta que **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**e o recentemente adicionado **PreviousVersions** pasta e copie todos os arquivos e subpastas do **NumberGuessWorkflowActivities** pasta para a nova  **NumberGuessWorkflowActivities_du** pasta.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-133">Create a new folder named **NumberGuessWorkflowActivities_du** in the same folder as **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**, and the newly added **PreviousVersions** folder, and copy all of the files and subfolders from the **NumberGuessWorkflowActivities** folder into the new **NumberGuessWorkflowActivities_du** folder.</span></span> <span data-ttu-id="0c4fe-134">Essa cópia de backup do projeto para a versão inicial das atividades é usada em [como: Atualizar a definição de uma instância de fluxo de trabalho em execução](how-to-update-the-definition-of-a-running-workflow-instance.md).</span><span class="sxs-lookup"><span data-stu-id="0c4fe-134">This backup copy of the project for the initial version of the activities is used in [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>

9. <span data-ttu-id="0c4fe-135">Abra novamente o **WF45GettingStartedTutorial** solução no Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-135">Re-open the **WF45GettingStartedTutorial** solution in Visual Studio 2012.</span></span>

### <a name="BKMK_UpdateWorkflows"></a> <span data-ttu-id="0c4fe-136">Para atualizar os fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="0c4fe-136">To update the workflows</span></span>
 <span data-ttu-id="0c4fe-137">Nesta seção, as definições de fluxo de trabalho são atualizadas.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-137">In this section, the workflow definitions are updated.</span></span> <span data-ttu-id="0c4fe-138">As duas atividades `WriteLine` que fornecem comentários sobre o palpite do usuário são atualizadas, e uma nova atividade `WriteLine` é adicionada, que fornece informações adicionais sobre o jogo quando o número é acertado.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-138">The two `WriteLine` activities that give feedback on the user's guess are updated, and a new `WriteLine` activity is added that provides additional information about the game once the number is guessed.</span></span>

#### <a name="BKMK_UpdateStateMachine"></a> <span data-ttu-id="0c4fe-139">Para atualizar o fluxo de trabalho StateMachine</span><span class="sxs-lookup"><span data-stu-id="0c4fe-139">To update the StateMachine workflow</span></span>

1. <span data-ttu-id="0c4fe-140">Na **Gerenciador de soluções**, sob o **NumberGuessWorkflowActivities** do projeto, clique duas vezes em **Statemachinenumberguessworkflow**.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-140">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **StateMachineNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="0c4fe-141">Clique duas vezes o **Palpite incorreto** transição na máquina de estado.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-141">Double-click the **Guess Incorrect** transition on the state machine.</span></span>

3. <span data-ttu-id="0c4fe-142">Atualize o `Text` do `WriteLine` mais à esquerda na atividade `If`.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-142">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

4. <span data-ttu-id="0c4fe-143">Atualize o `Text` do `WriteLine` mais à direita na atividade `If`.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-143">Update the `Text` of the right-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

5. <span data-ttu-id="0c4fe-144">Retorne ao geral exibição no designer de fluxo de trabalho de máquina de estado clicando **StateMachine** na trilha exibir na parte superior do designer de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-144">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>

6. <span data-ttu-id="0c4fe-145">Clique duas vezes o **Palpite correto** transição na máquina de estado.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-145">Double-click the **Guess Correct** transition on the state machine.</span></span>

7. <span data-ttu-id="0c4fe-146">Arraste uma **WriteLine** a atividade do **primitivos** seção do **caixa de ferramentas** e solte-a no **atividade de ação de soltar aqui** rótulo da transição.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-146">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the **Drop Action activity here** label of the transition.</span></span>

8. <span data-ttu-id="0c4fe-147">Digite a seguinte expressão na caixa de propriedades de `Text`.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-147">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="BKMK_UpdateFlowchart"></a> <span data-ttu-id="0c4fe-148">Para atualizar o fluxo de trabalho de fluxograma</span><span class="sxs-lookup"><span data-stu-id="0c4fe-148">To update the Flowchart workflow</span></span>

1. <span data-ttu-id="0c4fe-149">Na **Gerenciador de soluções**, sob o **NumberGuessWorkflowActivities** do projeto, clique duas vezes em **Flowchartnumberguessworkflow**.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-149">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **FlowchartNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="0c4fe-150">Atualize o `Text` do `WriteLine` mais à esquerda.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-150">Update the `Text` of the left-most `WriteLine` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. <span data-ttu-id="0c4fe-151">Atualize o `Text` do `WriteLine` mais à direita.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-151">Update the `Text` of the right-most `WriteLine` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. <span data-ttu-id="0c4fe-152">Arraste um **WriteLine** a atividade do **primitivos** seção o **caixa de ferramentas** e solte-no ponto certo do `True` ação de nível superior `FlowDecision` .</span><span class="sxs-lookup"><span data-stu-id="0c4fe-152">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the drop point of the `True` action of the topmost `FlowDecision`.</span></span> <span data-ttu-id="0c4fe-153">A atividade `WriteLine` é adicionada ao fluxograma e vinculada à ação `True` do `FlowDecision`.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-153">The `WriteLine` activity is added to the flowchart and linked to the `True` action of the `FlowDecision`.</span></span>

5. <span data-ttu-id="0c4fe-154">Digite a seguinte expressão na caixa de propriedades de `Text`.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-154">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="BKMK_UpdateSequential"></a> <span data-ttu-id="0c4fe-155">Para atualizar o fluxo de trabalho sequencial</span><span class="sxs-lookup"><span data-stu-id="0c4fe-155">To update the Sequential workflow</span></span>

1. <span data-ttu-id="0c4fe-156">Na **Gerenciador de soluções**, sob o **NumberGuessWorkflowActivities** do projeto, clique duas vezes em **Sequentialnumberguessworkflow**.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-156">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **SequentialNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="0c4fe-157">Atualize o `Text` do `WriteLine` mais à esquerda na atividade `If`.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-157">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. <span data-ttu-id="0c4fe-158">Atualize o `Text` da atividade `WriteLine` mais à direita na atividade `If`.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-158">Update the `Text` of the right-most `WriteLine` activity in the `If` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. <span data-ttu-id="0c4fe-159">Arrastar um **WriteLine** a atividade do **primitivos** seção o **caixa de ferramentas** e solte-a depois o **DoWhile** atividade para que o  **WriteLine** é a atividade final na raiz `Sequence` atividade.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-159">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it after the **DoWhile** activity so that the **WriteLine** is the final activity in the root `Sequence` activity.</span></span>

5. <span data-ttu-id="0c4fe-160">Digite a seguinte expressão na caixa de propriedades de `Text`.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-160">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

### <a name="BKMK_UpdateWorkflowVersionMap"></a> <span data-ttu-id="0c4fe-161">Para atualizar WorkflowVersionMap para incluir as versões anteriores do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="0c4fe-161">To update WorkflowVersionMap to include the previous workflow versions</span></span>

1. <span data-ttu-id="0c4fe-162">Clique duas vezes em **WorkflowVersionMap.cs** (ou **Workflowversionmap**) sob o **NumberGuessWorkflowHost** para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-162">Double-click **WorkflowVersionMap.cs** (or **WorkflowVersionMap.vb**) under the **NumberGuessWorkflowHost** project to open it.</span></span>

2. <span data-ttu-id="0c4fe-163">Adicione as seguintes instruções `using` (ou `Imports`) na parte superior do arquivo com as outras instruções `using` (ou `Imports`).</span><span class="sxs-lookup"><span data-stu-id="0c4fe-163">Add the following `using` (or `Imports`) statements to the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Reflection
    Imports System.IO
    ```

    ```csharp
    using System.Reflection;
    using System.IO;
    ```

3. <span data-ttu-id="0c4fe-164">Adicione três novas identidades de fluxo de trabalho abaixo das três declarações de identidade de fluxo de trabalho existentes.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-164">Add three new workflow identities just below the three existing workflow identity declarations.</span></span> <span data-ttu-id="0c4fe-165">Essas novas identidades de fluxo de trabalho `v1` serão usadas para fornecer a definição correta para fluxos de trabalho iniciados antes que as atualizações foram feitas.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-165">These new `v1` workflow identities will be used provide the correct workflow definition to workflows started before the updates were made.</span></span>

    ```vb
    'Current version identities.
    Public StateMachineNumberGuessIdentity As WorkflowIdentity
    Public FlowchartNumberGuessIdentity As WorkflowIdentity
    Public SequentialNumberGuessIdentity As WorkflowIdentity

    'v1 Identities.
    Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
    Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
    Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity
    ```

    ```csharp
    // Current version identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity;
    static public WorkflowIdentity FlowchartNumberGuessIdentity;
    static public WorkflowIdentity SequentialNumberGuessIdentity;

    // v1 identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;
    static public WorkflowIdentity SequentialNumberGuessIdentity_v1;
    ```

4. <span data-ttu-id="0c4fe-166">No construtor `WorkflowVersionMap`, atualize a propriedade `Version` das três identidades atuais de fluxo de trabalho para `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-166">In the `WorkflowVersionMap` constructor, update the `Version` property of the three current workflow identities to `2.0.0.0`.</span></span>

    ```vb
    'Add the current workflow version identities.
    StateMachineNumberGuessIdentity = New WorkflowIdentity With
    {
        .Name = "StateMachineNumberGuessWorkflow",
        .Version = New Version(2, 0, 0, 0)
    }

    FlowchartNumberGuessIdentity = New WorkflowIdentity With
    {
        .Name = "FlowchartNumberGuessWorkflow",
        .Version = New Version(2, 0, 0, 0)
    }

    SequentialNumberGuessIdentity = New WorkflowIdentity With
    {
        .Name = "SequentialNumberGuessWorkflow",
        .Version = New Version(2, 0, 0, 0)
    }

    map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())
    map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())
    map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())
    ```

    ```csharp
    // Add the current workflow version identities.
    StateMachineNumberGuessIdentity = new WorkflowIdentity
    {
        Name = "StateMachineNumberGuessWorkflow",
        // Version = new Version(1, 0, 0, 0),
        Version = new Version(2, 0, 0, 0)
    };

    FlowchartNumberGuessIdentity = new WorkflowIdentity
    {
        Name = "FlowchartNumberGuessWorkflow",
        // Version = new Version(1, 0, 0, 0),
        Version = new Version(2, 0, 0, 0)
    };

    SequentialNumberGuessIdentity = new WorkflowIdentity
    {
        Name = "SequentialNumberGuessWorkflow",
        // Version = new Version(1, 0, 0, 0),
        Version = new Version(2, 0, 0, 0)
    };

    map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());
    map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());
    map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());
    ```

     <span data-ttu-id="0c4fe-167">Esse código adiciona as versões atuais dos fluxos de trabalho para o dicionário que usa as versões atuais que são referenciadas no projeto, de modo que o código que inicializa as definições de fluxo de trabalho não precise ser atualizado.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-167">The code in that adds the current versions of the workflows to the dictionary uses the current versions that are referenced in the project, so the code that initializes the workflow definitions does not need to be updated.</span></span>

5. <span data-ttu-id="0c4fe-168">Adicione o seguinte código no construtor imediatamente depois do código que adiciona as versões atuais ao dicionário.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-168">Add the following code in the constructor just after the code that adds the current versions to the dictionary.</span></span>

    ```vb
    'Initialize the previous workflow version identities.
    StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With
    {
        .Name = "StateMachineNumberGuessWorkflow",
        .Version = New Version(1, 0, 0, 0)
    }

    FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With
    {
        .Name = "FlowchartNumberGuessWorkflow",
        .Version = New Version(1, 0, 0, 0)
    }

    SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With
    {
        .Name = "SequentialNumberGuessWorkflow",
        .Version = New Version(1, 0, 0, 0)
    }
    ```

    ```csharp
    // Initialize the previous workflow version identities.
    StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity
    {
        Name = "StateMachineNumberGuessWorkflow",
        Version = new Version(1, 0, 0, 0)
    };

    FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity
    {
        Name = "FlowchartNumberGuessWorkflow",
        Version = new Version(1, 0, 0, 0)
    };

    SequentialNumberGuessIdentity_v1 = new WorkflowIdentity
    {
        Name = "SequentialNumberGuessWorkflow",
        Version = new Version(1, 0, 0, 0)
    };
    ```

     <span data-ttu-id="0c4fe-169">Essas identidades de fluxo de trabalho são associadas às versões iniciais das definições de fluxo de trabalho correspondentes.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-169">These workflow identities are associated with the initial versions of the corresponding workflow definitions.</span></span>

6. <span data-ttu-id="0c4fe-170">Em seguida, carregue o assembly que contém a versão inicial das definições de fluxo de trabalho, e crie e adicione as definições correspondentes do fluxo de trabalho ao dicionário.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-170">Next, load the assembly that contains the initial version of the workflow definitions, and create and add the corresponding workflow definitions to the dictionary.</span></span>

    ```vb
    'Add the previous version workflow identities to the dictionary along with
    'the corresponding workflow definitions loaded from the v1 assembly.
    'Assembly.LoadFile requires an absolute path so convert this relative path
    'to an absolute path.
    Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"
    v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)
    Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)

    map.Add(StateMachineNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

    map.Add(SequentialNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

    map.Add(FlowchartNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
    ```

    ```csharp
    // Add the previous version workflow identities to the dictionary along with
    // the corresponding workflow definitions loaded from the v1 assembly.
    // Assembly.LoadFile requires an absolute path so convert this relative path
    // to an absolute path.
    string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";
    v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);
    Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);

    map.Add(StateMachineNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

    map.Add(SequentialNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

    map.Add(FlowchartNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
    ```

     <span data-ttu-id="0c4fe-171">O exemplo a seguir é a listagem completa para a classe `WorkflowVersionMap` atualizada.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-171">The following example is the complete listing for the updated `WorkflowVersionMap` class.</span></span>

    ```vb
    Public Module WorkflowVersionMap
        Dim map As Dictionary(Of WorkflowIdentity, Activity)

        'Current version identities.
        Public StateMachineNumberGuessIdentity As WorkflowIdentity
        Public FlowchartNumberGuessIdentity As WorkflowIdentity
        Public SequentialNumberGuessIdentity As WorkflowIdentity

        'v1 Identities.
        Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
        Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
        Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity

        Sub New()
            map = New Dictionary(Of WorkflowIdentity, Activity)

            'Add the current workflow version identities.
            StateMachineNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            SequentialNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())

            'Initialize the previous workflow version identities.
            StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            'Add the previous version workflow identities to the dictionary along with
            'the corresponding workflow definitions loaded from the v1 assembly.
            'Assembly.LoadFile requires an absolute path so convert this relative path
            'to an absolute path.
            Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)
            Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)

            map.Add(StateMachineNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

            map.Add(SequentialNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

            map.Add(FlowchartNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
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

        // v1 identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;
        static public WorkflowIdentity SequentialNumberGuessIdentity_v1;

        static WorkflowVersionMap()
        {
            map = new Dictionary<WorkflowIdentity, Activity>();

            // Add the current workflow version identities.
            StateMachineNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            SequentialNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());

            // Initialize the previous workflow version identities.
            StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            SequentialNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            // Add the previous version workflow identities to the dictionary along with
            // the corresponding workflow definitions loaded from the v1 assembly.
            // Assembly.LoadFile requires an absolute path so convert this relative path
            // to an absolute path.
            string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);
            Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);

            map.Add(StateMachineNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

            map.Add(SequentialNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

            map.Add(FlowchartNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
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

### <a name="BKMK_BuildAndRun"></a> <span data-ttu-id="0c4fe-172">Para compilar e executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="0c4fe-172">To build and run the application</span></span>

1. <span data-ttu-id="0c4fe-173">Pressione CTRL+SHIFT+B para criar o aplicativo, e CTRL+F5 para iniciar.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-173">Press CTRL+SHIFT+B to build the application, and then CTRL+F5 to start.</span></span>

2. <span data-ttu-id="0c4fe-174">Inicie um novo fluxo de trabalho clicando **novo jogo**.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-174">Start a new workflow by clicking **New Game**.</span></span> <span data-ttu-id="0c4fe-175">A versão do fluxo de trabalho é exibida abaixo da janela de status e reflete a versão atualizada do `WorkflowIdentity` associado.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-175">The version of the workflow is displayed under the status window and reflects the updated version from the associated `WorkflowIdentity`.</span></span> <span data-ttu-id="0c4fe-176">Faça uma anotação do `InstanceId` para que você possa exibir o arquivo de rastreamento para o fluxo de trabalho quando ele for concluído, e insira os palpites até que o jogo seja concluído.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-176">Make a note of the `InstanceId` so you can view the tracking file for the workflow when it completes, and then enter guesses until the game is complete.</span></span> <span data-ttu-id="0c4fe-177">Observe como o palpite do usuário é exibido nas informações exibidas na janela de status com base nas atualizações das atividades `WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-177">Note how the user's guess is displayed in the information displayed in the status window based on the updates to the `WriteLine` activities.</span></span>

 <span data-ttu-id="0c4fe-178">**Insira um número entre 1 e 10**</span><span class="sxs-lookup"><span data-stu-id="0c4fe-178">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="0c4fe-179">**5 é muito alta.**</span><span class="sxs-lookup"><span data-stu-id="0c4fe-179">**5 is too high.**</span></span>  
<span data-ttu-id="0c4fe-180">**Insira um número entre 1 e 10**</span><span class="sxs-lookup"><span data-stu-id="0c4fe-180">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="0c4fe-181">**3 é muito alta.**</span><span class="sxs-lookup"><span data-stu-id="0c4fe-181">**3 is too high.**</span></span>  
<span data-ttu-id="0c4fe-182">**Insira um número entre 1 e 10**</span><span class="sxs-lookup"><span data-stu-id="0c4fe-182">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="0c4fe-183">**1 é muito baixo.**</span><span class="sxs-lookup"><span data-stu-id="0c4fe-183">**1 is too low.**</span></span>  
<span data-ttu-id="0c4fe-184">**Insira um número entre 1 e 10**</span><span class="sxs-lookup"><span data-stu-id="0c4fe-184">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="0c4fe-185">**Parabéns, você já entendeu o número em 4 sequências.**</span><span class="sxs-lookup"><span data-stu-id="0c4fe-185">**Congratulations, you guessed the number in 4 turns.**</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="0c4fe-186">O texto atualizado das atividades `WriteLine` é exibido, mas não a saída final da atividade `WriteLine` final que foi adicionada neste tópico.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-186">The updated text from the `WriteLine` activities is displayed, but the output of the final `WriteLine` activity that was added in this topic is not.</span></span> <span data-ttu-id="0c4fe-187">Isso ocorre porque a janela de status é atualizada pelo manipulador `PersistableIdle`.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-187">That is because the status window is updated by the `PersistableIdle` handler.</span></span> <span data-ttu-id="0c4fe-188">Como o fluxo de trabalho é concluído e não fica ocioso após a atividade final, o manipulador `PersistableIdle` não é chamado.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-188">Because the workflow completes and does not go idle after the final activity, the `PersistableIdle` handler is not called.</span></span> <span data-ttu-id="0c4fe-189">No entanto, uma mensagem semelhante é exibida na janela de status pelo manipulador `Completed`.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-189">However, a similar message is displayed in the status window by the `Completed` handler.</span></span> <span data-ttu-id="0c4fe-190">Se desejar, um código pode ser adicionado ao manipulador `Completed` para extrair o texto de `StringWriter` e exibi-lo na janela de status.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-190">If desired, code could be added to the `Completed` handler to extract the text from the `StringWriter` and display it to the status window.</span></span>

3. <span data-ttu-id="0c4fe-191">Abra o Windows Explorer e navegue até a **NumberGuessWorkflowHost\bin\debug** pasta (ou **bin\release** dependendo de suas configurações de projeto) e abra o arquivo de rastreamento usando o bloco de notas que corresponde o fluxo de trabalho concluído.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-191">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings) and open the tracking file using Notepad that corresponds to the completed workflow.</span></span> <span data-ttu-id="0c4fe-192">Se você não fez uma anotação do `InstanceId`, você pode identificar o arquivo de controle correto usando a **data modificada** informações no Windows Explorer.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-192">If you did not make a note of the `InstanceId`, you can identify the correct tracking file by using the **Date modified** information in Windows Explorer.</span></span>

 <span data-ttu-id="0c4fe-193">**Insira um número entre 1 e 10**
**5 é muito alta.** 
 **Insira um número entre 1 e 10**
**3 é muito alta.** 
 **Insira um número entre 1 e 10**
**1 é muito baixa.** 
 **Insira um número entre 1 e 10**
**2 está correto. Você acertou o Palpite em 4 sequências.**</span><span class="sxs-lookup"><span data-stu-id="0c4fe-193">**Please enter a number between 1 and 10**
**5 is too high.**
**Please enter a number between 1 and 10**
**3 is too high.**
**Please enter a number between 1 and 10**
**1 is too low.**
**Please enter a number between 1 and 10**
**2 is correct. You guessed it in 4 turns.**</span></span>      <span data-ttu-id="0c4fe-194">A saída `WriteLine` atualizada está contida no arquivo de rastreamento, incluindo a saída de `WriteLine` que foi adicionada neste tópico.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-194">The updated `WriteLine` output is contained within the tracking file, including the output of the `WriteLine` that was added in this topic.</span></span>

4. <span data-ttu-id="0c4fe-195">Alterne novamente para o aplicativo de palpite de número e selecione um dos fluxos de trabalho que foi iniciado antes que as atualizações foram feitas.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-195">Switch back to the number guessing application and select one of the workflows that was started before the updates were made.</span></span> <span data-ttu-id="0c4fe-196">Você pode identificar a versão do fluxo de trabalho selecionado no momento examinando as informações de versão que são exibidas embaixo da janela de status.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-196">You can identify the version of the currently selected workflow by looking at the version information that is displayed below the status window.</span></span> <span data-ttu-id="0c4fe-197">Insira alguns palpites e observe que as atualizações de status correspondem à saída da atividade `WriteLine` da versão anterior, e não incluem o palpite do usuário.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-197">Enter some guesses and note that the status updates match the `WriteLine` activity output from the previous version, and do not include the user's guess.</span></span> <span data-ttu-id="0c4fe-198">Isso ocorre porque esses fluxos de trabalho estão usando a definição do fluxo de trabalho anterior que não tem as atualizações `WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-198">That is because these workflows are using the previous workflow definition that does not have the `WriteLine` updates.</span></span>

     <span data-ttu-id="0c4fe-199">Na próxima etapa, [como: Atualizar a definição de uma instância de fluxo de trabalho em execução](how-to-update-the-definition-of-a-running-workflow-instance.md), a execução `v1` instâncias de fluxo de trabalho são atualizadas para conter a nova funcionalidade como a `v2` instâncias.</span><span class="sxs-lookup"><span data-stu-id="0c4fe-199">In the next step, [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md), the running `v1` workflow instances are updated so they contain the new functionality as the `v2` instances.</span></span>

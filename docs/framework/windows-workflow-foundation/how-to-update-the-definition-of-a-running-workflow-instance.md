---
title: Como atualizar a definição de uma instância de fluxo de trabalho em execução
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26dfac36-ae23-4909-9867-62495b55fb5e
ms.openlocfilehash: da8b6adeede1fddf39c818568cfd884c3add317f
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123833"
---
# <a name="how-to-update-the-definition-of-a-running-workflow-instance"></a><span data-ttu-id="65087-102">Como atualizar a definição de uma instância de fluxo de trabalho em execução</span><span class="sxs-lookup"><span data-stu-id="65087-102">How to: Update the Definition of a Running Workflow Instance</span></span>
<span data-ttu-id="65087-103">A atualização dinâmica fornece um mecanismo para que os desenvolvedores de aplicativos de fluxo de trabalho atualizem a definição de fluxo de trabalho de uma instância do fluxo de trabalho persistida.</span><span class="sxs-lookup"><span data-stu-id="65087-103">Dynamic update provides a mechanism for workflow application developers to update the workflow definition of a persisted workflow instance.</span></span> <span data-ttu-id="65087-104">A alteração necessária pode ser implementar uma correção de bug, novos requisitos ou acomodar alterações inesperadas.</span><span class="sxs-lookup"><span data-stu-id="65087-104">The required change can be to implement a bug fix, new requirements, or to accommodate unexpected changes.</span></span> <span data-ttu-id="65087-105">Esta etapa no tutorial demonstra como usar a atualização dinâmica para modificar instâncias persistidas do `v1` número de fluxo de trabalho de adivinhação para coincidir com a nova funcionalidade introduzida na [como: Host de várias versões de uma fluxo de trabalho lado a lado ](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="65087-105">This step in the tutorial demonstrates how to use dynamic update to modify  persisted instances of the `v1` number guessing workflow to match the new functionality introduced in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="65087-106">Para baixar uma versão completa ou exibir uma vídeo passo a passo do tutorial, consulte [Windows Workflow Foundation (WF45) - Tutorial de Introdução](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="65087-106">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="65087-107">Neste tópico</span><span class="sxs-lookup"><span data-stu-id="65087-107">In this topic</span></span>  
  
-   [<span data-ttu-id="65087-108">Para criar o projeto CreateUpdateMaps</span><span class="sxs-lookup"><span data-stu-id="65087-108">To create the CreateUpdateMaps project</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateProject)  
  
-   [<span data-ttu-id="65087-109">Para atualizar StateMachineNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="65087-109">To update StateMachineNumberGuessWorkflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StateMachine)  
  
-   [<span data-ttu-id="65087-110">Para atualizar FlowchartNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="65087-110">To update FlowchartNumberGuessWorkflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Flowchart)  
  
-   [<span data-ttu-id="65087-111">Para atualizar SequentialNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="65087-111">To update SequentialNumberGuessWorkflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Sequential)  
  
-   [<span data-ttu-id="65087-112">Para compilar e executar o aplicativo CreateUpdateMaps</span><span class="sxs-lookup"><span data-stu-id="65087-112">To build and run the CreateUpdateMaps application</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateUpdateMaps)  
  
-   [<span data-ttu-id="65087-113">Para compilar o assembly de fluxo de trabalho atualizado</span><span class="sxs-lookup"><span data-stu-id="65087-113">To build the updated workflow assembly</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAssembly)  
  
-   [<span data-ttu-id="65087-114">Para atualizar WorkflowVersionMap com as novas versões</span><span class="sxs-lookup"><span data-stu-id="65087-114">To update WorkflowVersionMap with the new versions</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_UpdateWorkflowVersionMap)  
  
-   [<span data-ttu-id="65087-115">Para aplicar as atualizações dinâmicas</span><span class="sxs-lookup"><span data-stu-id="65087-115">To apply the dynamic updates</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_ApplyUpdate)  
  
-   [<span data-ttu-id="65087-116">Para executar o aplicativo com os fluxos de trabalho atualizados</span><span class="sxs-lookup"><span data-stu-id="65087-116">To run the application with the updated workflows</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAndRun)  
  
-   [<span data-ttu-id="65087-117">Para habilitar o início de versões anteriores dos fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="65087-117">To enable starting previous versions of the workflows</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StartPreviousVersions)  
  
###  <a name="BKMK_CreateProject"></a> <span data-ttu-id="65087-118">Para criar o projeto CreateUpdateMaps</span><span class="sxs-lookup"><span data-stu-id="65087-118">To create the CreateUpdateMaps project</span></span>  
  
1.  <span data-ttu-id="65087-119">Clique com botão direito **WF45GettingStartedTutorial** na **Gerenciador de soluções** e escolha **Add**, **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="65087-119">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>  
  
2.  <span data-ttu-id="65087-120">No **Installed** nó, selecione **Visual c#**, **Windows** (ou **Visual Basic**, **Windows**).</span><span class="sxs-lookup"><span data-stu-id="65087-120">In the **Installed** node, select **Visual C#**, **Windows** (or **Visual Basic**, **Windows**).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="65087-121">Dependendo da linguagem de programação configurada como linguagem primária no Visual Studio, o **Visual c#** ou **Visual Basic** nó pode estar abaixo de **outros idiomas** nó de **instalado** nó.</span><span class="sxs-lookup"><span data-stu-id="65087-121">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>

     <span data-ttu-id="65087-122">Certifique-se de que **.NET Framework 4.5** está selecionado na lista suspensa de versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="65087-122">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="65087-123">Selecione **aplicativo de Console** da **Windows** lista.</span><span class="sxs-lookup"><span data-stu-id="65087-123">Select **Console Application** from the **Windows** list.</span></span> <span data-ttu-id="65087-124">Tipo de **CreateUpdateMaps** para o **nome** caixa e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="65087-124">Type **CreateUpdateMaps** into the **Name** box and click **OK**.</span></span>

3.  <span data-ttu-id="65087-125">Clique com botão direito **CreateUpdateMaps** na **Gerenciador de soluções** e escolha **Add Reference**.</span><span class="sxs-lookup"><span data-stu-id="65087-125">Right-click **CreateUpdateMaps** in **Solution Explorer** and choose **Add Reference**.</span></span>

4.  <span data-ttu-id="65087-126">Selecione **Framework** da **Assemblies** nó no **Add Reference** lista.</span><span class="sxs-lookup"><span data-stu-id="65087-126">Select **Framework** from the **Assemblies** node in the **Add Reference** list.</span></span> <span data-ttu-id="65087-127">Tipo **System. Activities** para o **pesquisar Assemblies** caixa para filtrar os assemblies e facilitar selecionar o das referências desejadas.</span><span class="sxs-lookup"><span data-stu-id="65087-127">Type **System.Activities** into the **Search Assemblies** box to filter the assemblies and make the desired references easier to select.</span></span>

5.  <span data-ttu-id="65087-128">Marque a caixa de seleção ao lado **System. Activities** da **os resultados da pesquisa** lista.</span><span class="sxs-lookup"><span data-stu-id="65087-128">Check the checkbox beside **System.Activities** from the **Search Results** list.</span></span>

6.  <span data-ttu-id="65087-129">Tipo **serialização** para o **Assemblies de pesquisa** caixa e marque a caixa de seleção ao lado **Serialization** do **os resultados da pesquisa**  lista.</span><span class="sxs-lookup"><span data-stu-id="65087-129">Type **Serialization** into the **Search Assemblies** box, and check the checkbox beside **System.Runtime.Serialization** from the **Search Results** list.</span></span>

7.  <span data-ttu-id="65087-130">Tipo **System. XAML** para o **Assemblies de pesquisa** caixa e marque a caixa de seleção ao lado **System. XAML** do **os resultados da pesquisa** lista.</span><span class="sxs-lookup"><span data-stu-id="65087-130">Type **System.Xaml** into the **Search Assemblies** box, and check the checkbox beside **System.Xaml** from the **Search Results** list.</span></span>

8.  <span data-ttu-id="65087-131">Clique em **Okey** para fechar **Gerenciador de referências** e adicionar as referências.</span><span class="sxs-lookup"><span data-stu-id="65087-131">Click **OK** to close **Reference Manager** and add the references.</span></span>

9. <span data-ttu-id="65087-132">Adicione as seguintes instruções `using` (ou `Imports`) na parte superior do arquivo com as outras instruções `using` (ou `Imports`).</span><span class="sxs-lookup"><span data-stu-id="65087-132">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Activities
    Imports System.Activities.Statements
    Imports System.Xaml
    Imports System.Reflection
    Imports System.IO
    Imports System.Activities.XamlIntegration
    Imports System.Activities.DynamicUpdate
    Imports System.Runtime.Serialization
    Imports Microsoft.VisualBasic.Activities
    ```

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    using System.IO;
    using System.Xaml;
    using System.Reflection;
    using System.Activities.XamlIntegration;
    using System.Activities.DynamicUpdate;
    using System.Runtime.Serialization;
    using Microsoft.CSharp.Activities;
    ```

10. <span data-ttu-id="65087-133">Adicionar os dois membros de cadeia de caracteres a seguir à classe `Program` (ou `Module1`).</span><span class="sxs-lookup"><span data-stu-id="65087-133">Add the following two string members to the `Program` class (or `Module1`).</span></span>

    ```vb
    Const mapPath = "..\..\..\PreviousVersions"
    Const definitionPath = "..\..\..\NumberGuessWorkflowActivities_du"
    ```

    ```csharp
    const string mapPath = @"..\..\..\PreviousVersions";
    const string definitionPath = @"..\..\..\NumberGuessWorkflowActivities_du";
    ```

11. <span data-ttu-id="65087-134">Adicione o método `StartUpdate` a seguir à classe `Program` (ou `Module1`).</span><span class="sxs-lookup"><span data-stu-id="65087-134">Add the following `StartUpdate` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="65087-135">Esse método carrega acima uma definição do fluxo de trabalho do xaml especificado em um `ActivityBuilder` e chama `DynamicUpdate.PrepareForUpdate`.</span><span class="sxs-lookup"><span data-stu-id="65087-135">This method loads up the specified xaml workflow definition into an `ActivityBuilder`, and then calls `DynamicUpdate.PrepareForUpdate`.</span></span> <span data-ttu-id="65087-136">O `PrepareForUpdate` faz uma cópia da definição de fluxo de trabalho dentro do `ActivityBuilder`.</span><span class="sxs-lookup"><span data-stu-id="65087-136">`PrepareForUpdate` makes a copy of the workflow definition inside the `ActivityBuilder`.</span></span> <span data-ttu-id="65087-137">Depois que a definição de fluxo de trabalho tiver sido alterada, essa cópia será usada junto com a definição de fluxo de trabalho alterada para criar o mapa de atualização.</span><span class="sxs-lookup"><span data-stu-id="65087-137">After the workflow definition is modified, this copy is used along with the modified workflow definition to create the update map.</span></span>

    ```vb
    Private Function StartUpdate(name As String) As ActivityBuilder
        'Create the XamlXmlReaderSettings.
        Dim readerSettings As XamlReaderSettings = New XamlXmlReaderSettings()
        'In the XAML the "local" namespace referes to artifacts that come from
        'the same project as the XAML. When loading XAML if the currently executing
        'assembly is not the same assembly that was referred to as "local" in the XAML
        'LocalAssembly must be set to the assembly containing the artifacts.
        'Assembly.LoadFile requires an absolute path so convert this relative path
        'to an absolute path.
        readerSettings.LocalAssembly = Assembly.LoadFile(
            Path.GetFullPath(Path.Combine(mapPath, "NumberGuessWorkflowActivities_v1.dll")))

        Dim fullPath As String = Path.Combine(definitionPath, name)
        Dim xamlReader As XamlXmlReader = New XamlXmlReader(fullPath, readerSettings)

        'Load the workflow definition into an ActivityBuilder.
        Dim wf As ActivityBuilder = XamlServices.Load(
            ActivityXamlServices.CreateBuilderReader(xamlReader))

        'PrepareForUpdate makes a copy of the workflow definition in the
        'ActivityBuilder that is used for comparison when the update
        'map is created.
        DynamicUpdateServices.PrepareForUpdate(wf)

        Return wf
    End Function
    ```

    ```csharp
    private static ActivityBuilder StartUpdate(string name)
    {
        // Create the XamlXmlReaderSettings.
        XamlXmlReaderSettings readerSettings = new XamlXmlReaderSettings()
        {
            // In the XAML the "local" namespace referes to artifacts that come from
            // the same project as the XAML. When loading XAML if the currently executing
            // assembly is not the same assembly that was referred to as "local" in the XAML
            // LocalAssembly must be set to the assembly containing the artifacts.
            // Assembly.LoadFile requires an absolute path so convert this relative path
            // to an absolute path.
            LocalAssembly = Assembly.LoadFile(
                Path.GetFullPath(Path.Combine(mapPath, "NumberGuessWorkflowActivities_v1.dll")))
        };

        string path = Path.Combine(definitionPath, name);
        XamlXmlReader xamlReader = new XamlXmlReader(path, readerSettings);

        // Load the workflow definition into an ActivityBuilder.
        ActivityBuilder wf = XamlServices.Load(
            ActivityXamlServices.CreateBuilderReader(xamlReader))
            as ActivityBuilder;

        // PrepareForUpdate makes a copy of the workflow definition in the
        // ActivityBuilder that is used for comparison when the update
        // map is created.
        DynamicUpdateServices.PrepareForUpdate(wf);

        return wf;
    }
    ```

12. <span data-ttu-id="65087-138">Em seguida, adicione o `CreateUpdateMethod` a seguir à classe `Program` (ou `Module1`).</span><span class="sxs-lookup"><span data-stu-id="65087-138">Next, add the following `CreateUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="65087-139">Isso cria um mapa dinâmico de atualização chamando DynamicUpdateServices.CreateUpdateMap e, em seguida, salva o mapa de atualização usando o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="65087-139">This creates a dynamic update map by calling DynamicUpdateServices.CreateUpdateMap, and then saves the update map using the specified name.</span></span> <span data-ttu-id="65087-140">Esse mapa de atualização contém as informações necessárias pelo tempo de execução do fluxo de trabalho para atualizar uma instância do fluxo de trabalho persistida, que foi iniciada usando a definição original de fluxo de trabalho contida no `ActivityBuilder`, de forma que ela fosse concluída usando a definição atualizada do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="65087-140">This update map contains the information needed by the workflow runtime to update a persisted workflow instance that was started using the original workflow definition contained in the `ActivityBuilder` so that it completes using the updated workflow definition.</span></span>

    ```vb
    Private Sub CreateUpdateMaps(wf As ActivityBuilder, name As String)
        'Create the UpdateMap.
        Dim map As DynamicUpdateMap =
            DynamicUpdateServices.CreateUpdateMap(wf)

        'Serialize it to a file.
        Dim mapFullPath As String = Path.Combine(mapPath, name)
        Dim sz As DataContractSerializer = New DataContractSerializer(GetType(DynamicUpdateMap))
        Using fs As FileStream = File.Open(mapFullPath, FileMode.Create)
            sz.WriteObject(fs, map)
        End Using
    End Sub
    ```

    ```csharp
    private static void CreateUpdateMaps(ActivityBuilder wf, string name)
    {
        // Create the UpdateMap.
        DynamicUpdateMap map =
            DynamicUpdateServices.CreateUpdateMap(wf);

        // Serialize it to a file.
        string path = Path.Combine(mapPath, name);
        DataContractSerializer sz = new DataContractSerializer(typeof(DynamicUpdateMap));
        using (FileStream fs = System.IO.File.Open(path, FileMode.Create))
        {
            sz.WriteObject(fs, map);
        }
    }
    ```

13. <span data-ttu-id="65087-141">Adicione o método `SaveUpdatedDefinition` a seguir à classe `Program` (ou `Module1`).</span><span class="sxs-lookup"><span data-stu-id="65087-141">Add the following `SaveUpdatedDefinition` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="65087-142">Esse método salva a definição atualizada de fluxo de trabalho quando o mapa de atualização é criado.</span><span class="sxs-lookup"><span data-stu-id="65087-142">This method saves the updated workflow definition once the update map is created.</span></span>

    ```vb
    Private Sub SaveUpdatedDefinition(wf As ActivityBuilder, name As String)
        Dim xamlPath As String = Path.Combine(definitionPath, name)
        Dim sw As StreamWriter = File.CreateText(xamlPath)
        Dim xw As XamlWriter = ActivityXamlServices.CreateBuilderWriter(
            New XamlXmlWriter(sw, New XamlSchemaContext()))
        XamlServices.Save(xw, wf)
        sw.Close()
    End Sub
    ```

    ```csharp
    private static void SaveUpdatedDefinition(ActivityBuilder wf, string name)
    {
        string xamlPath = Path.Combine(definitionPath, name);
        StreamWriter sw = File.CreateText(xamlPath);
        XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(
            new XamlXmlWriter(sw, new XamlSchemaContext()));
        XamlServices.Save(xw, wf);
        sw.Close();
    }
    ```

###  <a name="BKMK_StateMachine"></a> <span data-ttu-id="65087-143">Para atualizar StateMachineNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="65087-143">To update StateMachineNumberGuessWorkflow</span></span>

1.  <span data-ttu-id="65087-144">Adicione um `CreateStateMachineUpdateMap` à classe `Program` (ou `Module1`).</span><span class="sxs-lookup"><span data-stu-id="65087-144">Add a `CreateStateMachineUpdateMap` to the `Program` class (or `Module1`).</span></span>

    ```vb
    Private Sub CreateStateMachineUpdateMap()

    End Sub
    ```

    ```csharp
    private static void CreateStateMachineUpdateMap()
    {
    }
    ```

2.  <span data-ttu-id="65087-145">Faz uma chamada para `StartUpdate` e obtém uma referência à atividade raiz `StateMachine` do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="65087-145">Make a call to `StartUpdate` and then get a reference to the root `StateMachine` activity of the workflow.</span></span>

    ```vb
    Dim wf As ActivityBuilder = StartUpdate("StateMachineNumberGuessWorkflow.xaml")

    'Get a reference to the root StateMachine activity.
    Dim sm As StateMachine = wf.Implementation
    ```

    ```csharp
    ActivityBuilder wf = StartUpdate("StateMachineNumberGuessWorkflow.xaml");

    // Get a reference to the root StateMachine activity.
    StateMachine sm = wf.Implementation as StateMachine;
    ```

3.  <span data-ttu-id="65087-146">Em seguida, atualize as expressões das duas `WriteLine` atividades que são exibidas se o palpite do usuário é muito alto ou muito baixo, para que elas coincidam com as atualizações feitas no [como: Host de várias versões de uma fluxo de trabalho lado a lado](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="65087-146">Next, update the expressions of the two `WriteLine` activities that display whether the user's guess is too high or too low so that they match the updates made in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

    ```vb
    'Update the Text of the two WriteLine activities that write the
    'results of the user's guess. They are contained in the workflow as the
    'Then and Else action of the If activity in sm.States[1].Transitions[1].Action.
    Dim guessLow As Statements.If = sm.States(1).Transitions(1).Action

    'Update the "too low" message.
    Dim tooLow As WriteLine = guessLow.Then
    tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")

    'Update the "too high" message.
    Dim tooHigh As WriteLine = guessLow.Else
    tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")
    ```

    ```csharp
    // Update the Text of the two WriteLine activities that write the
    // results of the user's guess. They are contained in the workflow as the
    // Then and Else action of the If activity in sm.States[1].Transitions[1].Action.
    If guessLow = sm.States[1].Transitions[1].Action as If;

    // Update the "too low" message.
    WriteLine tooLow = guessLow.Then as WriteLine;
    tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");

    // Update the "too high" message.
    WriteLine tooHigh = guessLow.Else as WriteLine;
    tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");
    ```

4.  <span data-ttu-id="65087-147">Em seguida, adicione a nova atividade `WriteLine` que exibe a mensagem de fechamento.</span><span class="sxs-lookup"><span data-stu-id="65087-147">Next, add the new `WriteLine` activity that displays the closing message.</span></span>

    ```vb
    'Create the new WriteLine that displays the closing message.
    Dim wl As New WriteLine() With
    {
        .Text = New VisualBasicValue(Of String) _
            ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")
    }

    'Add it as the Action for the Guess Correct transition. The Guess Correct
    'transition is the first transition of States[1]. The transitions are listed
    'at the bottom of the State activity designer.
    sm.States(1).Transitions(0).Action = wl
    ```

    ```csharp
    // Create the new WriteLine that displays the closing message.
    WriteLine wl = new WriteLine
    {
        Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")
    };

    // Add it as the Action for the Guess Correct transition. The Guess Correct
    // transition is the first transition of States[1]. The transitions are listed
    // at the bottom of the State activity designer.
    sm.States[1].Transitions[0].Action = wl;
    ```

5.  <span data-ttu-id="65087-148">Depois que o fluxo de trabalho é atualizado, chame `CreateUpdateMaps` e `SaveUpdatedDefinition`.</span><span class="sxs-lookup"><span data-stu-id="65087-148">After the workflow is updated, call `CreateUpdateMaps` and `SaveUpdatedDefinition`.</span></span> <span data-ttu-id="65087-149">`CreateUpdateMaps` cria e salva o `DynamicUpdateMap` e o `SaveUpdatedDefinition` salva a definição atualizada do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="65087-149">`CreateUpdateMaps` creates and saves the `DynamicUpdateMap`, and `SaveUpdatedDefinition` saves the updated workflow definition.</span></span>

    ```vb
    'Create the update map.
    CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map")

    'Save the updated workflow definition.
    SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml")
    ```

    ```csharp
    // Create the update map.
    CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map");

    // Save the updated workflow definition.
    SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml");
    ```

     <span data-ttu-id="65087-150">O exemplo a seguir é o método `CreateStateMachineUpdateMap` concluído.</span><span class="sxs-lookup"><span data-stu-id="65087-150">The following example is the completed `CreateStateMachineUpdateMap` method.</span></span>

    ```vb
    Private Sub CreateStateMachineUpdateMap()
        Dim wf As ActivityBuilder = StartUpdate("StateMachineNumberGuessWorkflow.xaml")

        'Get a reference to the root StateMachine activity.
        Dim sm As StateMachine = wf.Implementation

        'Update the Text of the two WriteLine activities that write the
        'results of the user's guess. They are contained in the workflow as the
        'Then and Else action of the If activity in sm.States[1].Transitions[1].Action.
        Dim guessLow As Statements.If = sm.States(1).Transitions(1).Action

        'Update the "too low" message.
        Dim tooLow As WriteLine = guessLow.Then
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")

        'Update the "too high" message.
        Dim tooHigh As WriteLine = guessLow.Else
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")

        'Create the new WriteLine that displays the closing message.
        Dim wl As New WriteLine() With
        {
            .Text = New VisualBasicValue(Of String) _
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")
        }

        'Add it as the Action for the Guess Correct transition. The Guess Correct
        'transition is the first transition of States[1]. The transitions are listed
        'at the bottom of the State activity designer.
        sm.States(1).Transitions(0).Action = wl

        'Create the update map.
        CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map")

        'Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml")
    End Sub
    ```

    ```csharp
    private static void CreateStateMachineUpdateMap()
    {
        ActivityBuilder wf = StartUpdate("StateMachineNumberGuessWorkflow.xaml");

        // Get a reference to the root StateMachine activity.
        StateMachine sm = wf.Implementation as StateMachine;

        // Update the Text of the two WriteLine activities that write the
        // results of the user's guess. They are contained in the workflow as the
        // Then and Else action of the If activity in sm.States[1].Transitions[1].Action.
        If guessLow = sm.States[1].Transitions[1].Action as If;

        // Update the "too low" message.
        WriteLine tooLow = guessLow.Then as WriteLine;
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");

        // Update the "too high" message.
        WriteLine tooHigh = guessLow.Else as WriteLine;
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");

        // Create the new WriteLine that displays the closing message.
        WriteLine wl = new WriteLine
        {
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")
        };

        // Add it as the Action for the Guess Correct transition. The Guess Correct
        // transition is the first transition of States[1]. The transitions are listed
        // at the bottom of the State activity designer.
        sm.States[1].Transitions[0].Action = wl;

        // Create the update map.
        CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map");

        // Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml");
    }
    ```

###  <a name="BKMK_Flowchart"></a> <span data-ttu-id="65087-151">Para atualizar FlowchartNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="65087-151">To update FlowchartNumberGuessWorkflow</span></span>

1.  <span data-ttu-id="65087-152">Adicione o `CreateFlowchartUpdateMethod` a seguir à classe `Program` (ou `Module1`).</span><span class="sxs-lookup"><span data-stu-id="65087-152">Add the following `CreateFlowchartUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="65087-153">Esse método é semelhante a `CreateStateMachineUpdateMap`.</span><span class="sxs-lookup"><span data-stu-id="65087-153">This method is similar to `CreateStateMachineUpdateMap`.</span></span> <span data-ttu-id="65087-154">Começa com uma chamada para `StartUpdate`, atualiza a definição do fluxo de trabalho do fluxograma e conclui salvando o mapa de atualização e a definição atualizada do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="65087-154">It starts with a call to `StartUpdate`, updates the flowchart workflow definition, and finishes by saving the update map and the updated workflow definition.</span></span>

    ```vb
    Private Sub CreateFlowchartUpdateMap()
        Dim wf As ActivityBuilder = StartUpdate("FlowchartNumberGuessWorkflow.xaml")

        'Get a reference to the root Flowchart activity.
        Dim fc As Flowchart = wf.Implementation

        'Update the Text of the two WriteLine activities that write the
        'results of the user's guess. They are contained in the workflow as the
        'True and False action of the "Guess < Target" FlowDecision, which is
        'Nodes[4].
        Dim guessLow As FlowDecision = fc.Nodes(4)

        'Update the "too low" message.
        Dim trueStep As FlowStep = guessLow.True
        Dim tooLow As WriteLine = trueStep.Action
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")

        'Update the "too high" message.
        Dim falseStep As FlowStep = guessLow.False
        Dim tooHigh As WriteLine = falseStep.Action
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")

        'Create the new WriteLine that displays the closing message.
        Dim wl As New WriteLine() With
        {
            .Text = New VisualBasicValue(Of String) _
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")
        }

        'Create a FlowStep to hold the WriteLine.
        Dim closingStep As New FlowStep() With
        {
            .Action = wl
        }

        'Add this new FlowStep to the True action of the
        '"Guess = Guess" FlowDecision
        Dim guessCorrect As FlowDecision = fc.Nodes(3)
        guessCorrect.True = closingStep

        'Add the new FlowStep to the Nodes collection.
        'If closingStep was replacing an existing node then
        'we would need to remove that Step from the collection.
        'In this example there was no existing True step to remove.
        fc.Nodes.Add(closingStep)

        'Create the update map.
        CreateUpdateMaps(wf, "FlowchartNumberGuessWorkflow.map")

        'Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "FlowchartNumberGuessWorkflow_du.xaml")
    End Sub
    ```

    ```csharp
    private static void CreateFlowchartUpdateMap()
    {
        ActivityBuilder wf = StartUpdate("FlowchartNumberGuessWorkflow.xaml");

        // Get a reference to the root Flowchart activity.
        Flowchart fc = wf.Implementation as Flowchart;

        // Update the Text of the two WriteLine activities that write the
        // results of the user's guess. They are contained in the workflow as the
        // True and False action of the "Guess < Target" FlowDecision, which is
        // Nodes[4].
        FlowDecision guessLow = fc.Nodes[4] as FlowDecision;

        // Update the "too low" message.
        FlowStep trueStep = guessLow.True as FlowStep;
        WriteLine tooLow = trueStep.Action as WriteLine;
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");

        // Update the "too high" message.
        FlowStep falseStep = guessLow.False as FlowStep;
        WriteLine tooHigh = falseStep.Action as WriteLine;
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");

        // Add the new WriteLine that displays the closing message.
        WriteLine wl = new WriteLine
        {
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")
        };

        // Create a FlowStep to hold the WriteLine.
        FlowStep closingStep = new FlowStep
        {
            Action = wl
        };

        // Add this new FlowStep to the True action of the
        // "Guess == Guess" FlowDecision
        FlowDecision guessCorrect = fc.Nodes[3] as FlowDecision;
        guessCorrect.True = closingStep;

        // Add the new FlowStep to the Nodes collection.
        // If closingStep was replacing an existing node then
        // we would need to remove that Step from the collection.
        // In this example there was no existing True step to remove.
        fc.Nodes.Add(closingStep);

        // Create the update map.
        CreateUpdateMaps(wf, "FlowchartNumberGuessWorkflow.map");

        //  Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "FlowchartNumberGuessWorkflow_du.xaml");
    }
    ```

###  <a name="BKMK_Sequential"></a> <span data-ttu-id="65087-155">Para atualizar SequentialNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="65087-155">To update SequentialNumberGuessWorkflow</span></span>

1.  <span data-ttu-id="65087-156">Adicione o `CreateSequentialUpdateMethod` a seguir à classe `Program` (ou `Module1`).</span><span class="sxs-lookup"><span data-stu-id="65087-156">Add the following `CreateSequentialUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="65087-157">Esse método é semelhante aos outros dois métodos.</span><span class="sxs-lookup"><span data-stu-id="65087-157">This method is similar to the other two methods.</span></span> <span data-ttu-id="65087-158">Começa com uma chamada para `StartUpdate`, atualiza a definição do fluxo de trabalho sequencial e conclui salvando o mapa de atualização e a definição atualizada do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="65087-158">It starts with a call to `StartUpdate`, updates the sequential workflow definition, and finishes by saving the update map and the updated workflow definition.</span></span>

    ```vb
    Private Sub CreateSequentialUpdateMap()
        Dim wf As ActivityBuilder = StartUpdate("SequentialNumberGuessWorkflow.xaml")

        'Get a reference to the root activity in the workflow.
        Dim rootSequence As Sequence = wf.Implementation

        'Update the Text of the two WriteLine activities that write the
        'results of the user's guess. They are contained in the workflow as the
        'Then and Else action of the "Guess < Target" If activity.
        'Sequence[1]->DoWhile->Body->Sequence[2]->If->Then->If
        Dim gameLoop As Statements.DoWhile = rootSequence.Activities(1)
        Dim gameBody As Sequence = gameLoop.Body
        Dim guessCorrect As Statements.If = gameBody.Activities(2)
        Dim guessLow As Statements.If = guessCorrect.Then
        Dim tooLow As WriteLine = guessLow.Then
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")
        Dim tooHigh As WriteLine = guessLow.Else
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")

        'Create the new WriteLine that displays the closing message.
        Dim wl As New WriteLine() With
        {
            .Text = New VisualBasicValue(Of String) _
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")
        }

        'Insert it as the third activity in the root sequence
        rootSequence.Activities.Insert(2, wl)

        'Create the update map.
        CreateUpdateMaps(wf, "SequentialNumberGuessWorkflow.map")

        'Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "SequentialNumberGuessWorkflow_du.xaml")
    End Sub
    ```

    ```csharp
    private static void CreateSequentialUpdateMap()
    {
        ActivityBuilder wf = StartUpdate("SequentialNumberGuessWorkflow.xaml");

        // Get a reference to the root activity in the workflow.
        Sequence rootSequence = wf.Implementation as Sequence;

        // Update the Text of the two WriteLine activities that write the
        // results of the user's guess. They are contained in the workflow as the
        // Then and Else action of the "Guess < Target" If activity.
        // Sequence[1]->DoWhile->Body->Sequence[2]->If->Then->If
        DoWhile gameLoop = rootSequence.Activities[1] as DoWhile;
        Sequence gameBody = gameLoop.Body as Sequence;
        If guessCorrect = gameBody.Activities[2] as If;
        If guessLow = guessCorrect.Then as If;
        WriteLine tooLow = guessLow.Then as WriteLine;
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");
        WriteLine tooHigh = guessLow.Else as WriteLine;
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");

        // Add the new WriteLine that displays the closing message.
        WriteLine wl = new WriteLine
        {
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")
        };

        // Insert it as the third activity in the root sequence
        rootSequence.Activities.Insert(2, wl);

        // Create the update map.
        CreateUpdateMaps(wf, "SequentialNumberGuessWorkflow.map");

        // Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "SequentialNumberGuessWorkflow_du.xaml");
    }
    ```

###  <a name="BKMK_CreateUpdateMaps"></a> <span data-ttu-id="65087-159">Para compilar e executar o aplicativo CreateUpdateMaps</span><span class="sxs-lookup"><span data-stu-id="65087-159">To build and run the CreateUpdateMaps application</span></span>

1.  <span data-ttu-id="65087-160">Atualize o método `Main` e adicione as três chamadas de método a seguir.</span><span class="sxs-lookup"><span data-stu-id="65087-160">Update the `Main` method and add the following three method calls.</span></span> <span data-ttu-id="65087-161">Esses métodos são adicionados nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="65087-161">These methods are added in the following sections.</span></span> <span data-ttu-id="65087-162">Cada método atualiza o fluxo de trabalho de palpite de número correspondente e cria um `DynamicUpdateMap` que descreve as atualizações.</span><span class="sxs-lookup"><span data-stu-id="65087-162">Each method updates the corresponding number guess workflow and creates a `DynamicUpdateMap` that describes the updates.</span></span>

    ```vb
    Sub Main()
        'Create the update maps for the changes needed to the v1 activities
        'so they match the v2 activities.
        CreateSequentialUpdateMap()
        CreateFlowchartUpdateMap()
        CreateStateMachineUpdateMap()
    End Sub
    ```

    ```csharp
    static void Main(string[] args)
    {
        // Create the update maps for the changes needed to the v1 activities
        // so they match the v2 activities.
        CreateSequentialUpdateMap();
        CreateFlowchartUpdateMap();
        CreateStateMachineUpdateMap();
    }
    ```

2.  <span data-ttu-id="65087-163">Clique com botão direito **CreateUpdateMaps** na **Gerenciador de soluções** e escolha **Set as StartUp Project**.</span><span class="sxs-lookup"><span data-stu-id="65087-163">Right-click **CreateUpdateMaps** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>

3.  <span data-ttu-id="65087-164">Pressione CTRL+SHIFT+B para criar a solução, e CTRL+F5 para executar o aplicativo `CreateUpdateMaps`.</span><span class="sxs-lookup"><span data-stu-id="65087-164">Press CTRL+SHIFT+B to build the solution, and then CTRL+F5 to run the `CreateUpdateMaps` application.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="65087-165">O `CreateUpdateMaps` aplicativo não exibe informações de status ao ser executado, mas se você examina o **NumberGuessWorkflowActivities_du** pasta e o **PreviousVersions** pasta, você verá os arquivos de definição de fluxo de trabalho atualizados e os mapas de atualização.</span><span class="sxs-lookup"><span data-stu-id="65087-165">The `CreateUpdateMaps` application does not display any status information while running, but if you look in the **NumberGuessWorkflowActivities_du** folder and the **PreviousVersions** folder you will see the updated workflow definition files and the update maps.</span></span>

     <span data-ttu-id="65087-166">Assim que os mapas de atualização são criados e as definições de fluxo de trabalho são atualizadas, a próxima etapa é criar um assembly atualizado do fluxo de trabalho que contém as definições atualizadas.</span><span class="sxs-lookup"><span data-stu-id="65087-166">Once the update maps are created and the workflow definitions updated, the next step is to build an updated workflow assembly containing the updated definitions.</span></span>

###  <a name="BKMK_BuildAssembly"></a> <span data-ttu-id="65087-167">Para compilar o assembly de fluxo de trabalho atualizado</span><span class="sxs-lookup"><span data-stu-id="65087-167">To build the updated workflow assembly</span></span>

1.  <span data-ttu-id="65087-168">Abra uma segunda instância do Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="65087-168">Open a second instance of Visual Studio 2012.</span></span>

2.  <span data-ttu-id="65087-169">Escolher **aberto**, **projeto/solução** do **arquivo** menu.</span><span class="sxs-lookup"><span data-stu-id="65087-169">Choose **Open**, **Project/Solution** from the **File** menu.</span></span>

3.  <span data-ttu-id="65087-170">Navegue até a **NumberGuessWorkflowActivities_du** pasta criada na [como: Host de várias versões de uma fluxo de trabalho lado a lado](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md), selecione **Numberguessworkflowactivities**  (ou **vbproj**) e clique em **abrir**.</span><span class="sxs-lookup"><span data-stu-id="65087-170">Navigate to the **NumberGuessWorkflowActivities_du** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md), select **NumberGuessWorkflowActivities.csproj** (or **vbproj**), and click **Open**.</span></span>

4.  <span data-ttu-id="65087-171">Na **Gerenciador de soluções**, clique com botão direito **Sequentialnumberguessworkflow** e escolha **excluir do projeto**.</span><span class="sxs-lookup"><span data-stu-id="65087-171">In **Solution Explorer**, right click **SequentialNumberGuessWorkflow.xaml** and choose **Exclude From Project**.</span></span> <span data-ttu-id="65087-172">Fazer a mesma coisa **Flowchartnumberguessworkflow** e **Statemachinenumberguessworkflow**.</span><span class="sxs-lookup"><span data-stu-id="65087-172">Do the same thing for **FlowchartNumberGuessWorkflow.xaml** and **StateMachineNumberGuessWorkflow.xaml**.</span></span> <span data-ttu-id="65087-173">Esta etapa remove as versões anteriores das definições de fluxo de trabalho do projeto.</span><span class="sxs-lookup"><span data-stu-id="65087-173">This step removes the previous versions of the workflow definitions from the project.</span></span>

5.  <span data-ttu-id="65087-174">Escolher **Adicionar Item existente** da **projeto** menu.</span><span class="sxs-lookup"><span data-stu-id="65087-174">Choose **Add Existing Item** from the **Project** menu.</span></span>

6.  <span data-ttu-id="65087-175">Navegue até a **NumberGuessWorkflowActivities_du** pasta criada na [como: Host de várias versões de uma fluxo de trabalho lado a lado](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="65087-175">Navigate to the **NumberGuessWorkflowActivities_du** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

7.  <span data-ttu-id="65087-176">Escolher **arquivos XAML (\*. XAML;\*. xoml)** do **arquivos de tipo** lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="65087-176">Choose **XAML Files (\*.xaml;\*.xoml)** from the **Files of type** drop-down list.</span></span>

8.  <span data-ttu-id="65087-177">Selecione **sequentialnumberguessworkflow_du. XAML**, **flowchartnumberguessworkflow_du. XAML**, e **statemachinenumberguessworkflow_du. XAML** e clique em  **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="65087-177">Select **SequentialNumberGuessWorkflow_du.xaml**, **FlowchartNumberGuessWorkflow_du.xaml**, and **StateMachineNumberGuessWorkflow_du.xaml** and click **Add**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="65087-178">CTRL+Click para selecionar vários itens de cada vez.</span><span class="sxs-lookup"><span data-stu-id="65087-178">CTRL+Click to select multiple items at a time.</span></span>

     <span data-ttu-id="65087-179">Esta etapa adiciona as versões atualizadas das definições de fluxo de trabalho para o projeto.</span><span class="sxs-lookup"><span data-stu-id="65087-179">This step adds the updated versions of the workflow definitions to the project.</span></span>

9. <span data-ttu-id="65087-180">Pressione CTRL+SHIFT+B para criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="65087-180">Press CTRL+SHIFT+B to build the project.</span></span>

10. <span data-ttu-id="65087-181">Escolher **fechar solução** da **arquivo** menu.</span><span class="sxs-lookup"><span data-stu-id="65087-181">Choose **Close Solution** from the **File** menu.</span></span> <span data-ttu-id="65087-182">Um arquivo de solução para o projeto não é necessário, portanto, clique em **não** para fechar o Visual Studio sem salvar um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="65087-182">A solution file for the project is not required, so click **No** to close Visual Studio without saving a solution file.</span></span> <span data-ttu-id="65087-183">Escolher **Exit** da **arquivo** menu para fechar o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="65087-183">Choose **Exit** from the **File** menu to close Visual Studio.</span></span>

11. <span data-ttu-id="65087-184">Abra o Windows Explorer e navegue até a **NumberGuessWorkflowActivities_du\bin\Debug** pasta (ou **bin\Release** dependendo de suas configurações de projeto).</span><span class="sxs-lookup"><span data-stu-id="65087-184">Open Windows Explorer and navigate to the **NumberGuessWorkflowActivities_du\bin\Debug** folder (or **bin\Release** depending on your project settings).</span></span>

12. <span data-ttu-id="65087-185">Renomeie **Numberguessworkflowactivities** à **NumberGuessWorkflowActivities_v15.dll**e copie-o para o **PreviousVersions** pasta que você criou no [Como: hospedar várias versões de uma fluxo de trabalho lado a lado](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="65087-185">Rename **NumberGuessWorkflowActivities.dll** to **NumberGuessWorkflowActivities_v15.dll**, and copy it to the **PreviousVersions** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

###  <a name="BKMK_UpdateWorkflowVersionMap"></a> <span data-ttu-id="65087-186">Para atualizar WorkflowVersionMap com as novas versões</span><span class="sxs-lookup"><span data-stu-id="65087-186">To update WorkflowVersionMap with the new versions</span></span>

1.  <span data-ttu-id="65087-187">Alterne para a instância inicial do Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="65087-187">Switch back to the initial instance of Visual Studio 2012.</span></span>

2.  <span data-ttu-id="65087-188">Clique duas vezes em **WorkflowVersionMap.cs** (ou **Workflowversionmap**) sob o **NumberGuessWorkflowHost** para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="65087-188">Double-click **WorkflowVersionMap.cs** (or **WorkflowVersionMap.vb**) under the **NumberGuessWorkflowHost** project to open it.</span></span>

3.  <span data-ttu-id="65087-189">Adicione três novas identidades de fluxo de trabalho abaixo das seis declarações de identidade de fluxo de trabalho existentes.</span><span class="sxs-lookup"><span data-stu-id="65087-189">Add three new workflow identities just below the six existing workflow identity declarations.</span></span> <span data-ttu-id="65087-190">Neste tutorial, `1.5.0.0` é usado como o `WorkflowIdentity.Version` para as identidades dinâmicas de atualização.</span><span class="sxs-lookup"><span data-stu-id="65087-190">In this tutorial, `1.5.0.0` is used as the `WorkflowIdentity.Version` for the dynamic update identities.</span></span> <span data-ttu-id="65087-191">Essas novas identidades de fluxo de trabalho `v15` serão usadas para fornecer a definição correta do fluxo de trabalho para as instâncias de fluxo de trabalho persistidas atualizadas dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="65087-191">These new `v15` workflow identities will be used provide the correct workflow definition for the dynamically updated persisted workflow instances.</span></span>

    ```vb
    'Current version identities.
    Public StateMachineNumberGuessIdentity As WorkflowIdentity
    Public FlowchartNumberGuessIdentity As WorkflowIdentity
    Public SequentialNumberGuessIdentity As WorkflowIdentity

    'v1 identities.
    Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
    Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
    Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity

    'v1.5 (Dynamimc Update) identities.
    Public StateMachineNumberGuessIdentity_v15 As WorkflowIdentity
    Public FlowchartNumberGuessIdentity_v15 As WorkflowIdentity
    Public SequentialNumberGuessIdentity_v15 As WorkflowIdentity
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

    // v1.5 (Dynamic Update) identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v15;
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v15;
    static public WorkflowIdentity SequentialNumberGuessIdentity_v15;
    ```

4.  <span data-ttu-id="65087-192">Adicione o código a seguir no final do construtor.</span><span class="sxs-lookup"><span data-stu-id="65087-192">Add the following code at the end of the constructor.</span></span> <span data-ttu-id="65087-193">Esse código inicializa as identidades dinâmicos do fluxo de trabalho de atualização, carrega as definições de fluxo de trabalho correspondentes e adiciona-as ao dicionário de versão do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="65087-193">This code initializes the dynamic update workflow identities, loads the corresponding workflow definitions, and adds them to the workflow version dictionary.</span></span>

    ```vb
    'Initialize the dynamic update workflow identities.
    StateMachineNumberGuessIdentity_v15 = New WorkflowIdentity With
    {
        .Name = "StateMachineNumberGuessWorkflow",
        .Version = New Version(1, 5, 0, 0)
    }

    FlowchartNumberGuessIdentity_v15 = New WorkflowIdentity With
    {
        .Name = "FlowchartNumberGuessWorkflow",
        .Version = New Version(1, 5, 0, 0)
    }

    SequentialNumberGuessIdentity_v15 = New WorkflowIdentity With
    {
        .Name = "SequentialNumberGuessWorkflow",
        .Version = New Version(1, 5, 0, 0)
    }

    'Add the dynamic update workflow identities to the dictionary along with
    'the corresponding workflow definitions loaded from the v15 assembly.
    'Assembly.LoadFile requires an absolute path so convert this relative path
    'to an absolute path.
    Dim v15AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll"
    v15AssemblyPath = Path.GetFullPath(v15AssemblyPath)
    Dim v15Assembly As Assembly = Assembly.LoadFile(v15AssemblyPath)

    map.Add(StateMachineNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

    map.Add(SequentialNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

    map.Add(FlowchartNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
    ```

    ```csharp
    // Initialize the dynamic update workflow identities.
    StateMachineNumberGuessIdentity_v15 = new WorkflowIdentity
    {
        Name = "StateMachineNumberGuessWorkflow",
        Version = new Version(1, 5, 0, 0)
    };

    FlowchartNumberGuessIdentity_v15 = new WorkflowIdentity
    {
        Name = "FlowchartNumberGuessWorkflow",
        Version = new Version(1, 5, 0, 0)
    };

    SequentialNumberGuessIdentity_v15 = new WorkflowIdentity
    {
        Name = "SequentialNumberGuessWorkflow",
        Version = new Version(1, 5, 0, 0)
    };

    // Add the dynamic update workflow identities to the dictionary along with
    // the corresponding workflow definitions loaded from the v15 assembly.
    // Assembly.LoadFile requires an absolute path so convert this relative path
    // to an absolute path.
    string v15AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll";
    v15AssemblyPath = Path.GetFullPath(v15AssemblyPath);
    Assembly v15Assembly = Assembly.LoadFile(v15AssemblyPath);

    map.Add(StateMachineNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

    map.Add(SequentialNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

    map.Add(FlowchartNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
    ```

     <span data-ttu-id="65087-194">O exemplo a seguir é a classe `WorkflowVersionMap` concluída.</span><span class="sxs-lookup"><span data-stu-id="65087-194">The following example is the completed `WorkflowVersionMap` class.</span></span>

    ```vb
    Public Module WorkflowVersionMap
        Dim map As Dictionary(Of WorkflowIdentity, Activity)

        'Current version identities.
        Public StateMachineNumberGuessIdentity As WorkflowIdentity
        Public FlowchartNumberGuessIdentity As WorkflowIdentity
        Public SequentialNumberGuessIdentity As WorkflowIdentity

        'v1 identities.
        Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
        Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
        Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity

        'v1.5 (Dynamimc Update) identities.
        Public StateMachineNumberGuessIdentity_v15 As WorkflowIdentity
        Public FlowchartNumberGuessIdentity_v15 As WorkflowIdentity
        Public SequentialNumberGuessIdentity_v15 As WorkflowIdentity

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

            'Initialize the dynamic update workflow identities.
            StateMachineNumberGuessIdentity_v15 = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(1, 5, 0, 0)
            }

            FlowchartNumberGuessIdentity_v15 = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(1, 5, 0, 0)
            }

            SequentialNumberGuessIdentity_v15 = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(1, 5, 0, 0)
            }

            'Add the dynamic update workflow identities to the dictionary along with
            'the corresponding workflow definitions loaded from the v15 assembly.
            'Assembly.LoadFile requires an absolute path so convert this relative path
            'to an absolute path.
            Dim v15AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll"
            v15AssemblyPath = Path.GetFullPath(v15AssemblyPath)
            Dim v15Assembly As Assembly = Assembly.LoadFile(v15AssemblyPath)

            map.Add(StateMachineNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

            map.Add(SequentialNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

            map.Add(FlowchartNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
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

        // v1.5 (Dynamic Update) identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v15;
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v15;
        static public WorkflowIdentity SequentialNumberGuessIdentity_v15;

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

            // Initialize the dynamic update workflow identities.
            StateMachineNumberGuessIdentity_v15 = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                Version = new Version(1, 5, 0, 0)
            };

            FlowchartNumberGuessIdentity_v15 = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                Version = new Version(1, 5, 0, 0)
            };

            SequentialNumberGuessIdentity_v15 = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                Version = new Version(1, 5, 0, 0)
            };

            // Add the dynamic update workflow identities to the dictionary along with
            // the corresponding workflow definitions loaded from the v15 assembly.
            // Assembly.LoadFile requires an absolute path so convert this relative path
            // to an absolute path.
            string v15AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll";
            v15AssemblyPath = Path.GetFullPath(v15AssemblyPath);
            Assembly v15Assembly = Assembly.LoadFile(v15AssemblyPath);

            map.Add(StateMachineNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

            map.Add(SequentialNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

            map.Add(FlowchartNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
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

5.  <span data-ttu-id="65087-195">Pressione CTRL+SHIFT+B para criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="65087-195">Press CTRL+SHIFT+B to build the project.</span></span>

###  <a name="BKMK_ApplyUpdate"></a> <span data-ttu-id="65087-196">Para aplicar as atualizações dinâmicas</span><span class="sxs-lookup"><span data-stu-id="65087-196">To apply the dynamic updates</span></span>

1.  <span data-ttu-id="65087-197">Clique com botão direito **WF45GettingStartedTutorial** na **Gerenciador de soluções** e escolha **Add**, **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="65087-197">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>

2.  <span data-ttu-id="65087-198">No **Installed** nó, selecione **Visual c#**, **Windows** (ou **Visual Basic**, **Windows**).</span><span class="sxs-lookup"><span data-stu-id="65087-198">In the **Installed** node, select **Visual C#**, **Windows** (or **Visual Basic**, **Windows**).</span></span>

    > [!NOTE]
    >  <span data-ttu-id="65087-199">Dependendo da linguagem de programação configurada como linguagem primária no Visual Studio, o **Visual c#** ou **Visual Basic** nó pode estar abaixo de **outros idiomas** nó de **instalado** nó.</span><span class="sxs-lookup"><span data-stu-id="65087-199">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>

     <span data-ttu-id="65087-200">Certifique-se de que **.NET Framework 4.5** está selecionado na lista suspensa de versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="65087-200">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="65087-201">Selecione **aplicativo de Console** da **Windows** lista.</span><span class="sxs-lookup"><span data-stu-id="65087-201">Select **Console Application** from the **Windows** list.</span></span> <span data-ttu-id="65087-202">Tipo de **ApplyDynamicUpdate** para o **nome** caixa e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="65087-202">Type **ApplyDynamicUpdate** into the **Name** box and click **OK**.</span></span>

3.  <span data-ttu-id="65087-203">Clique com botão direito **ApplyDynamicUpdate** na **Gerenciador de soluções** e escolha **Add Reference**.</span><span class="sxs-lookup"><span data-stu-id="65087-203">Right-click **ApplyDynamicUpdate** in **Solution Explorer** and choose **Add Reference**.</span></span>

4.  <span data-ttu-id="65087-204">Clique em **Solution** e marque a caixa ao lado de **NumberGuessWorkflowHost**.</span><span class="sxs-lookup"><span data-stu-id="65087-204">Click **Solution** and check the box next to **NumberGuessWorkflowHost**.</span></span> <span data-ttu-id="65087-205">Essa referência é necessária para que `ApplyDynamicUpdate` pode usar a classe `NumberGuessWorkflowHost.WorkflowVersionMap`.</span><span class="sxs-lookup"><span data-stu-id="65087-205">This reference is needed so that `ApplyDynamicUpdate` can use the `NumberGuessWorkflowHost.WorkflowVersionMap` class.</span></span>

5.  <span data-ttu-id="65087-206">Selecione **Framework** da **Assemblies** nó no **Add Reference** lista.</span><span class="sxs-lookup"><span data-stu-id="65087-206">Select **Framework** from the **Assemblies** node in the **Add Reference** list.</span></span> <span data-ttu-id="65087-207">Tipo de **System. Activities** para o **pesquisar Assemblies** caixa.</span><span class="sxs-lookup"><span data-stu-id="65087-207">Type **System.Activities** into the **Search Assemblies** box.</span></span> <span data-ttu-id="65087-208">Isso filtrará os assemblies e facilitará a seleção das referências desejadas.</span><span class="sxs-lookup"><span data-stu-id="65087-208">This will filter the assemblies and make the desired references easier to select.</span></span>

6.  <span data-ttu-id="65087-209">Marque a caixa de seleção ao lado **System. Activities** da **os resultados da pesquisa** lista.</span><span class="sxs-lookup"><span data-stu-id="65087-209">Check the checkbox beside **System.Activities** from the **Search Results** list.</span></span>

7.  <span data-ttu-id="65087-210">Tipo **serialização** para o **Assemblies de pesquisa** caixa e marque a caixa de seleção ao lado **Serialization** do **os resultados da pesquisa**  lista.</span><span class="sxs-lookup"><span data-stu-id="65087-210">Type **Serialization** into the **Search Assemblies** box, and check the checkbox beside **System.Runtime.Serialization** from the **Search Results** list.</span></span>

8.  <span data-ttu-id="65087-211">Tipo de **DurableInstancing** para o **Assemblies de pesquisa** caixa e marque a caixa de seleção ao lado de **durableinstancing** e  **System.Runtime.DurableInstancing** do **os resultados da pesquisa** lista.</span><span class="sxs-lookup"><span data-stu-id="65087-211">Type **DurableInstancing** into the **Search Assemblies** box, and check the checkbox beside **System.Activities.DurableInstancing** and **System.Runtime.DurableInstancing** from the **Search Results** list.</span></span>

9. <span data-ttu-id="65087-212">Clique em **Okey** para fechar **Gerenciador de referências** e adicionar as referências.</span><span class="sxs-lookup"><span data-stu-id="65087-212">Click **OK** to close **Reference Manager** and add the references.</span></span>

10. <span data-ttu-id="65087-213">Clique com botão direito **ApplyDynamicUpdate** no Gerenciador de soluções e escolha **Add**, **classe**.</span><span class="sxs-lookup"><span data-stu-id="65087-213">Right-click **ApplyDynamicUpdate** in Solution Explorer and choose **Add**, **Class**.</span></span> <span data-ttu-id="65087-214">Tipo de `DynamicUpdateInfo` para o **nome** caixa e clique em **Add**.</span><span class="sxs-lookup"><span data-stu-id="65087-214">Type `DynamicUpdateInfo` into the **Name** box and click **Add**.</span></span>

11. <span data-ttu-id="65087-215">Adicionar os dois membros a seguir à classe `DynamicUpdateInfo`.</span><span class="sxs-lookup"><span data-stu-id="65087-215">Add the following two members to the `DynamicUpdateInfo` class.</span></span> <span data-ttu-id="65087-216">O exemplo a seguir é a classe `DynamicUpdateInfo` concluída.</span><span class="sxs-lookup"><span data-stu-id="65087-216">The following example is the completed `DynamicUpdateInfo` class.</span></span> <span data-ttu-id="65087-217">Esta classe contém informações sobre o mapa de atualização e a nova identidade de fluxo de trabalho usada quando uma instância de fluxo de trabalho é atualizada.</span><span class="sxs-lookup"><span data-stu-id="65087-217">This class contains information on the update map and new workflow identity used when a workflow instance is updated.</span></span>

    ```vb
    Public Class DynamicUpdateInfo
        Public updateMap As DynamicUpdateMap
        Public newIdentity As WorkflowIdentity
    End Class
    ```

    ```csharp
    class DynamicUpdateInfo
    {
        public DynamicUpdateMap updateMap;
        public WorkflowIdentity newIdentity;
    }
    ```

12. <span data-ttu-id="65087-218">Adicione as seguintes instruções `using` (ou `Imports`) na parte superior do arquivo com as outras instruções `using` (ou `Imports`).</span><span class="sxs-lookup"><span data-stu-id="65087-218">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Activities
    Imports System.Activities.DynamicUpdate
    ```

    ```csharp
    using System.Activities;
    using System.Activities.DynamicUpdate;
    ```

13. <span data-ttu-id="65087-219">Clique duas vezes em **Program.cs** (ou **Module1.vb**) no Gerenciador de soluções.</span><span class="sxs-lookup"><span data-stu-id="65087-219">Double-click **Program.cs** (or **Module1.vb**) in Solution Explorer.</span></span>

14. <span data-ttu-id="65087-220">Adicione as seguintes instruções `using` (ou `Imports`) na parte superior do arquivo com as outras instruções `using` (ou `Imports`).</span><span class="sxs-lookup"><span data-stu-id="65087-220">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports NumberGuessWorkflowHost
    Imports System.Data.SqlClient
    Imports System.Activities.DynamicUpdate
    Imports System.IO
    Imports System.Runtime.Serialization
    Imports System.Activities
    Imports System.Activities.DurableInstancing
    ```

    ```csharp
    using NumberGuessWorkflowHost;
    using System.Data;
    using System.Data.SqlClient;
    using System.Activities;
    using System.Activities.DynamicUpdate;
    using System.IO;
    using System.Runtime.Serialization;
    using System.Activities.DurableInstancing;
    ```

15. <span data-ttu-id="65087-221">Adicionar o membro de cadeia de conexão a seguir à classe `Program` (ou `Module1`).</span><span class="sxs-lookup"><span data-stu-id="65087-221">Add the following connection string member to the `Program` class (or `Module1`).</span></span>

    ```vb
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"
    ```

    ```csharp
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";
    ```

    > [!NOTE]
    >  <span data-ttu-id="65087-222">Dependendo de sua edição do SQL Server, o nome do servidor da cadeia de conexão pode ser diferente.</span><span class="sxs-lookup"><span data-stu-id="65087-222">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>

16. <span data-ttu-id="65087-223">Adicione o método `GetIDs` a seguir à classe `Program` (ou `Module1`).</span><span class="sxs-lookup"><span data-stu-id="65087-223">Add the following `GetIDs` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="65087-224">Esse método retorna uma lista de ids de instância de fluxo de trabalho persistidas.</span><span class="sxs-lookup"><span data-stu-id="65087-224">This method returns a list of persisted workflow instance ids.</span></span>

    ```vb
    Function GetIds() As IList(Of Guid)
        Dim Ids As New List(Of Guid)
        Dim localCmd = _
            String.Format("Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]")
        Using localCon = New SqlConnection(connectionString)
            Dim cmd As SqlCommand = localCon.CreateCommand()
            cmd.CommandText = localCmd
            localCon.Open()
            Using reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)
                While reader.Read()
                    'Get the InstanceId of the persisted Workflow
                    Dim id As Guid = Guid.Parse(reader(0).ToString())

                    'Add it to the list.
                    Ids.Add(id)
                End While
            End Using
        End Using

        Return Ids
    End Function
    ```

    ```csharp
    static IList<Guid> GetIds()
    {
        List<Guid> Ids = new List<Guid>();
        string localCmd = string.Format("Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]");
        using (SqlConnection localCon = new SqlConnection(connectionString))
        {
            SqlCommand cmd = localCon.CreateCommand();
            cmd.CommandText = localCmd;
            localCon.Open();
            using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))
            {
                while (reader.Read())
                {
                    // Get the InstanceId of the persisted Workflow
                    Guid id = Guid.Parse(reader[0].ToString());

                    // Add it to the list.
                    Ids.Add(id);
                }
            }
        }

        return Ids;
    }
    ```

17. <span data-ttu-id="65087-225">Adicione o método `LoadMap` a seguir à classe `Program` (ou `Module1`).</span><span class="sxs-lookup"><span data-stu-id="65087-225">Add the following `LoadMap` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="65087-226">Este método cria um dicionário que mapeia identidades de fluxo de trabalho `v1` para os mapas de atualização e as novas identidades de fluxo de trabalho usadas para atualizar as instâncias de fluxo de trabalho correspondentes persistidas.</span><span class="sxs-lookup"><span data-stu-id="65087-226">This method creates a dictionary that maps `v1` workflow identities to the update maps and new workflow identities used to update the corresponding persisted workflow instances.</span></span>

    ```vb
    Function LoadMap(mapName As String) As DynamicUpdateMap
        Dim mapPath As String = Path.Combine("..\..\..\PreviousVersions", mapName)

        Dim map As DynamicUpdateMap
        Using fs As FileStream = File.Open(mapPath, FileMode.Open)
            Dim serializer As DataContractSerializer = New DataContractSerializer(GetType(DynamicUpdateMap))
            Dim updateMap = serializer.ReadObject(fs)
            If updateMap Is Nothing Then
                Throw New ApplicationException("DynamicUpdateMap is null.")
            End If

            map = updateMap
        End Using

        Return map
    End Function
    ```

    ```csharp
    static DynamicUpdateMap LoadMap(string mapName)
    {
        string path = Path.Combine(@"..\..\..\PreviousVersions", mapName);

        DynamicUpdateMap map;
        using (FileStream fs = File.Open(path, FileMode.Open))
        {
            DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));
            object updateMap = serializer.ReadObject(fs);
            if (updateMap == null)
            {
                throw new ApplicationException("DynamicUpdateMap is null.");
            }

            map = updateMap as DynamicUpdateMap;
        }

        return map;
    }
    ```

18. <span data-ttu-id="65087-227">Adicione o método `LoadMaps` a seguir à classe `Program` (ou `Module1`).</span><span class="sxs-lookup"><span data-stu-id="65087-227">Add the following `LoadMaps` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="65087-228">Esse método carrega os três mapas de atualização e cria um dicionário que mapeia identidades de fluxo de trabalho `v1` para os mapas de atualização.</span><span class="sxs-lookup"><span data-stu-id="65087-228">This method loads the three update maps and creates a dictionary that maps `v1` workflow identities to the update maps.</span></span>

    ```vb
    Function LoadMaps() As IDictionary(Of WorkflowIdentity, DynamicUpdateInfo)
        'There are 3 update maps to describe the changes to update v1 workflows,
        'one for reach of the 3 workflow types in the tutorial.
        Dim maps = New Dictionary(Of WorkflowIdentity, DynamicUpdateInfo)()

        Dim sequentialMap As DynamicUpdateMap = LoadMap("SequentialNumberGuessWorkflow.map")
        Dim sequentialInfo = New DynamicUpdateInfo With
        {
            .updateMap = sequentialMap,
            .newIdentity = WorkflowVersionMap.SequentialNumberGuessIdentity_v15
        }
        maps.Add(WorkflowVersionMap.SequentialNumberGuessIdentity_v1, sequentialInfo)

        Dim stateMap As DynamicUpdateMap = LoadMap("StateMachineNumberGuessWorkflow.map")
        Dim stateInfo = New DynamicUpdateInfo With
        {
            .updateMap = stateMap,
            .newIdentity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v15
        }
        maps.Add(WorkflowVersionMap.StateMachineNumberGuessIdentity_v1, stateInfo)

        Dim flowchartMap As DynamicUpdateMap = LoadMap("FlowchartNumberGuessWorkflow.map")
        Dim flowchartInfo = New DynamicUpdateInfo With
        {
            .updateMap = flowchartMap,
            .newIdentity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v15
        }
        maps.Add(WorkflowVersionMap.FlowchartNumberGuessIdentity_v1, flowchartInfo)

        Return maps
    End Function
    ```

    ```csharp
    static IDictionary<WorkflowIdentity, DynamicUpdateInfo> LoadMaps()
    {
        // There are 3 update maps to describe the changes to update v1 workflows,
        // one for reach of the 3 workflow types in the tutorial.
        Dictionary<WorkflowIdentity, DynamicUpdateInfo> maps =
            new Dictionary<WorkflowIdentity, DynamicUpdateInfo>();

        DynamicUpdateMap sequentialMap = LoadMap("SequentialNumberGuessWorkflow.map");
        DynamicUpdateInfo sequentialInfo = new DynamicUpdateInfo
        {
            updateMap = sequentialMap,
            newIdentity = WorkflowVersionMap.SequentialNumberGuessIdentity_v15
        };
        maps.Add(WorkflowVersionMap.SequentialNumberGuessIdentity_v1, sequentialInfo);

        DynamicUpdateMap stateMap = LoadMap("StateMachineNumberGuessWorkflow.map");
        DynamicUpdateInfo stateInfo = new DynamicUpdateInfo
        {
            updateMap = stateMap,
            newIdentity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v15
        };
        maps.Add(WorkflowVersionMap.StateMachineNumberGuessIdentity_v1, stateInfo);

        DynamicUpdateMap flowchartMap = LoadMap("FlowchartNumberGuessWorkflow.map");
        DynamicUpdateInfo flowchartInfo = new DynamicUpdateInfo
        {
            updateMap = flowchartMap,
            newIdentity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v15
        };
        maps.Add(WorkflowVersionMap.FlowchartNumberGuessIdentity_v1, flowchartInfo);

        return maps;
    }
    ```

19. <span data-ttu-id="65087-229">Adicione o código a seguir ao `Main`.</span><span class="sxs-lookup"><span data-stu-id="65087-229">Add the following code to `Main`.</span></span> <span data-ttu-id="65087-230">Este código itera as instâncias de fluxo de trabalho persistidas e examina cada `WorkflowIdentity`.</span><span class="sxs-lookup"><span data-stu-id="65087-230">This code iterates the persisted workflow instances and examines each `WorkflowIdentity`.</span></span> <span data-ttu-id="65087-231">Se o `WorkflowIdentity` mapeia para uma instância de fluxo de trabalho `v1`, um `WorkflowApplication` é configurado com a definição atualizada de fluxo de trabalho e uma identidade atualizada do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="65087-231">If the `WorkflowIdentity` maps to a `v1` workflow instance, a `WorkflowApplication` is configured with the updated workflow definition and an updated workflow identity.</span></span> <span data-ttu-id="65087-232">Em seguida, `WorkflowApplication.Load` é chamado com a instância e o mapa de atualização, que aplica o mapa de atualização dinâmica.</span><span class="sxs-lookup"><span data-stu-id="65087-232">Next, `WorkflowApplication.Load` is called with the instance and the update map, which applies the dynamic update map.</span></span> <span data-ttu-id="65087-233">Assim que a atualização é aplicada, a instância atualizada é persistida com uma chamada para `Unload`.</span><span class="sxs-lookup"><span data-stu-id="65087-233">Once the update is applied, the updated instance is persisted with a call to `Unload`.</span></span>

    ```vb
    Dim store = New SqlWorkflowInstanceStore(connectionString)
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)

    Dim updateMaps As IDictionary(Of WorkflowIdentity, DynamicUpdateInfo) = LoadMaps()

    For Each id As Guid In GetIds()
        'Get a proxy to the instance.
        Dim instance As WorkflowApplicationInstance = WorkflowApplication.GetInstance(id, store)

        Console.WriteLine("Inspecting: {0}", instance.DefinitionIdentity)

        'Only update v1 workflows.
        If Not instance.DefinitionIdentity Is Nothing AndAlso _
            instance.DefinitionIdentity.Version.Equals(New Version(1, 0, 0, 0)) Then

            Dim info As DynamicUpdateInfo = updateMaps(instance.DefinitionIdentity)

            'Associate the persisted WorkflowApplicationInstance with
            'a WorkflowApplication that is configured with the updated
            'definition and updated WorkflowIdentity.
            Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(info.newIdentity)
            Dim wfApp = New WorkflowApplication(wf, info.newIdentity)

            'Apply the Dynamic Update.
            wfApp.Load(instance, info.updateMap)

            'Persist the updated instance.
            wfApp.Unload()

            Console.WriteLine("Updated to: {0}", info.newIdentity)
        Else
            'Not updating this instance, so unload it.
            instance.Abandon()
        End If
    Next
    ```

    ```csharp
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);
    WorkflowApplication.CreateDefaultInstanceOwner(store, null, WorkflowIdentityFilter.Any);

    IDictionary<WorkflowIdentity, DynamicUpdateInfo> updateMaps = LoadMaps();

    foreach (Guid id in GetIds())
    {
        // Get a proxy to the instance.
        WorkflowApplicationInstance instance =
            WorkflowApplication.GetInstance(id, store);

        Console.WriteLine("Inspecting: {0}", instance.DefinitionIdentity);

        // Only update v1 workflows.
        if (instance.DefinitionIdentity != null &&
            instance.DefinitionIdentity.Version.Equals(new Version(1, 0, 0, 0)))
        {
            DynamicUpdateInfo info = updateMaps[instance.DefinitionIdentity];

            // Associate the persisted WorkflowApplicationInstance with
            // a WorkflowApplication that is configured with the updated
            // definition and updated WorkflowIdentity.
            Activity wf = WorkflowVersionMap.GetWorkflowDefinition(info.newIdentity);
            WorkflowApplication wfApp =
                new WorkflowApplication(wf, info.newIdentity);

            // Apply the Dynamic Update.
            wfApp.Load(instance, info.updateMap);

            // Persist the updated instance.
            wfApp.Unload();

            Console.WriteLine("Updated to: {0}", info.newIdentity);
        }
        else
        {
            // Not updating this instance, so unload it.
            instance.Abandon();
        }
    }
    ```

20. <span data-ttu-id="65087-234">Clique com botão direito **ApplyDynamicUpdate** na **Gerenciador de soluções** e escolha **Set as StartUp Project**.</span><span class="sxs-lookup"><span data-stu-id="65087-234">Right-click **ApplyDynamicUpdate** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>

21. <span data-ttu-id="65087-235">Pressione CTRL+SHIFT+B para criar a solução e pressione CTRL+F5 para executar o aplicativo `ApplyDynamicUpdate` e atualizar as instâncias de fluxo de trabalho persistidas.</span><span class="sxs-lookup"><span data-stu-id="65087-235">Press CTRL+SHIFT+B to build the solution, and then press CTRL+F5 to run the `ApplyDynamicUpdate` application and update the persisted workflow instances.</span></span> <span data-ttu-id="65087-236">Você deve ver a saída semelhante ao seguinte.</span><span class="sxs-lookup"><span data-stu-id="65087-236">You should see output similar to the following.</span></span> <span data-ttu-id="65087-237">Os fluxos de trabalho da versão 1.0.0.0 são atualizados para a versão 1.5.0.0, enquanto que os fluxos de trabalho da versão 2.0.0.0 não são atualizados.</span><span class="sxs-lookup"><span data-stu-id="65087-237">The version 1.0.0.0 workflows are updated to version 1.5.0.0, while the version 2.0.0.0 workflows are not updated.</span></span>

 <span data-ttu-id="65087-238">**Inspecionando: StateMachineNumberGuessWorkflow; Versão = 1.0.0.0**
**atualizado para: StateMachineNumberGuessWorkflow; Versão = 1.5.0.0**
**inspecionando: StateMachineNumberGuessWorkflow; Versão = 1.0.0.0**
**atualizado para: StateMachineNumberGuessWorkflow; Versão = 1.5.0.0**
**inspecionando: FlowchartNumberGuessWorkflow; Versão = 1.0.0.0**
**atualizado para: FlowchartNumberGuessWorkflow; Versão = 1.5.0.0**
**inspecionando: FlowchartNumberGuessWorkflow; Versão = 1.0.0.0**
**atualizado para: FlowchartNumberGuessWorkflow; Versão = 1.5.0.0**
**inspecionando: SequentialNumberGuessWorkflow; Versão = 1.0.0.0**
**atualizado para: SequentialNumberGuessWorkflow; Versão = 1.5.0.0**
**inspecionando: SequentialNumberGuessWorkflow; Versão = 1.0.0.0**
**atualizado para: SequentialNumberGuessWorkflow; Versão = 1.5.0.0**
**inspecionando: SequentialNumberGuessWorkflow; Versão = 1.0.0.0**
**atualizado para: SequentialNumberGuessWorkflow; Versão = 1.5.0.0**
**inspecionando: StateMachineNumberGuessWorkflow; Versão = 1.0.0.0**
**atualizado para: StateMachineNumberGuessWorkflow; Versão = 1.5.0.0**
**inspecionando: FlowchartNumberGuessWorkflow; Versão = 1.0.0.0**
**atualizado para: FlowchartNumberGuessWorkflow; Versão = 1.5.0.0**
**inspecionando: StateMachineNumberGuessWorkflow; Versão = 2.0.0.0**
**inspecionando: StateMachineNumberGuessWorkflow; Versão = 2.0.0.0**
**inspecionando: FlowchartNumberGuessWorkflow; Versão = 2.0.0.0**
**inspecionando: FlowchartNumberGuessWorkflow; Versão = 2.0.0.0**
**inspecionando: SequentialNumberGuessWorkflow; Versão = 2.0.0.0**
**inspecionando: SequentialNumberGuessWorkflow; Versão = 2.0.0.0**
**pressione qualquer tecla para continuar...**</span><span class="sxs-lookup"><span data-stu-id="65087-238">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0**
**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0**
**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0**
**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0**
**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0**
**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0**
**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0**
**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0**
**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0**
**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0**
**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0**
**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0**
**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0**
**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0**
**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0**
**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0**
**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0**
**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0**
**Inspecting: StateMachineNumberGuessWorkflow; Version=2.0.0.0**
**Inspecting: StateMachineNumberGuessWorkflow; Version=2.0.0.0**
**Inspecting: FlowchartNumberGuessWorkflow; Version=2.0.0.0**
**Inspecting: FlowchartNumberGuessWorkflow; Version=2.0.0.0**
**Inspecting: SequentialNumberGuessWorkflow; Version=2.0.0.0**
**Inspecting: SequentialNumberGuessWorkflow; Version=2.0.0.0**
**Press any key to continue . . .**</span></span>

###  <a name="BKMK_BuildAndRun"></a> <span data-ttu-id="65087-239">Para executar o aplicativo com os fluxos de trabalho atualizados</span><span class="sxs-lookup"><span data-stu-id="65087-239">To run the application with the updated workflows</span></span>

1.  <span data-ttu-id="65087-240">Clique com botão direito **NumberGuessWorkflowHost** na **Gerenciador de soluções** e escolha **Set as StartUp Project**.</span><span class="sxs-lookup"><span data-stu-id="65087-240">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>

2.  <span data-ttu-id="65087-241">Pressione CTRL+F5 para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="65087-241">Press CTRL+F5 to run the application.</span></span>

3.  <span data-ttu-id="65087-242">Clique em **novo jogo** para iniciar um novo fluxo de trabalho e observe as informações de versão abaixo a janela de status que indica o fluxo de trabalho é um `v2` fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="65087-242">Click **New Game** to start a new workflow and note the version information below the status window that indicates the workflow is a `v2` workflow.</span></span>

4.  <span data-ttu-id="65087-243">Selecione uma da `v1` fluxos de trabalho iniciados no início do [como: Host de várias versões de uma fluxo de trabalho lado a lado](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="65087-243">Select one of the `v1` workflows you started at the beginning of the [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) topic.</span></span> <span data-ttu-id="65087-244">Observe que as informações de versão na janela de status indicam que o fluxo de trabalho é uma versão **1.5.0.0** fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="65087-244">Note that the version information under the status window indicates that the workflow is a version **1.5.0.0** workflow.</span></span> <span data-ttu-id="65087-245">Observe que não há informações indicada sobre os palpites anteriores além de se eram muito altos ou muito baixos.</span><span class="sxs-lookup"><span data-stu-id="65087-245">Note that there is no information indicated about previous guesses other than whether they were too high or too low.</span></span>

 <span data-ttu-id="65087-246">**Insira um número entre 1 e 10**
**sua estimativa é muito baixo.**</span><span class="sxs-lookup"><span data-stu-id="65087-246">**Please enter a number between 1 and 10**
**Your guess is too low.**</span></span>

5.  <span data-ttu-id="65087-247">Faça uma anotação da `InstanceId` e insira palpites até que o fluxo de trabalho seja concluído.</span><span class="sxs-lookup"><span data-stu-id="65087-247">Make a note of the `InstanceId` and then enter guesses until the workflow completes.</span></span> <span data-ttu-id="65087-248">A janela de status exibe informações sobre o conteúdo do palpite porque as atividades `WriteLine` foram atualizadas pela atualização dinâmica.</span><span class="sxs-lookup"><span data-stu-id="65087-248">The status window displays information about the content of the guess because the `WriteLine` activities were updated by the dynamic update.</span></span>

 <span data-ttu-id="65087-249">**Insira um número entre 1 e 10**
**sua estimativa é muito baixo.** 
 **Insira um número entre 1 e 10**
**5 é muito baixo.** 
 **Insira um número entre 1 e 10**
**7 é muito alta.** 
 **Insira um número entre 1 e 10**
**Parabéns, você já entendeu o número em 4 sequências.**</span><span class="sxs-lookup"><span data-stu-id="65087-249">**Please enter a number between 1 and 10**
**Your guess is too low.**
**Please enter a number between 1 and 10**
**5 is too low.**
**Please enter a number between 1 and 10**
**7 is too high.**
**Please enter a number between 1 and 10**
**Congratulations, you guessed the number in 4 turns.**</span></span>

6.  <span data-ttu-id="65087-250">Abra o Windows Explorer e navegue até a **NumberGuessWorkflowHost\bin\debug** pasta (ou **bin\release** dependendo de suas configurações de projeto) e abra o arquivo de rastreamento usando o bloco de notas que corresponde o fluxo de trabalho concluído.</span><span class="sxs-lookup"><span data-stu-id="65087-250">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings) and open the tracking file using Notepad that corresponds to the completed workflow.</span></span> <span data-ttu-id="65087-251">Se você não fez uma anotação do `InstanceId` talvez você possa identificar o arquivo de controle correto usando a **data modificada** informações no Windows Explorer.</span><span class="sxs-lookup"><span data-stu-id="65087-251">If you did not make a note of the `InstanceId` you may be able to identify the correct tracking file by using the **Date modified** information in Windows Explorer.</span></span> <span data-ttu-id="65087-252">A última linha das informações de rastreamento contém a saída de atividade recém-adicionada `WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="65087-252">The last line of the tracking information contains the output of the newly added `WriteLine` activity.</span></span>

 <span data-ttu-id="65087-253">**Insira um número entre 1 e 10**
**sua estimativa é muito baixo.** 
 **Insira um número entre 1 e 10**
**5 é muito baixo.** 
 **Insira um número entre 1 e 10**
**7 é muito alta.** 
 **Insira um número entre 1 e 10**
**6 está correta. Você acertou o Palpite em 4 sequências.**</span><span class="sxs-lookup"><span data-stu-id="65087-253">**Please enter a number between 1 and 10**
**Your guess is too low.**
**Please enter a number between 1 and 10**
**5 is too low.**
**Please enter a number between 1 and 10**
**7 is too high.**
**Please enter a number between 1 and 10**
**6 is correct. You guessed it in 4 turns.**</span></span>

###  <a name="BKMK_StartPreviousVersions"></a> <span data-ttu-id="65087-254">Para habilitar o início de versões anteriores dos fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="65087-254">To enable starting previous versions of the workflows</span></span>
 <span data-ttu-id="65087-255">Se você não tiver mais fluxos de trabalho para atualizar, poderá modificar o aplicativo `NumberGuessWorkflowHost` para habilitar o início das versões anteriores dos fluxos de trabalho.</span><span class="sxs-lookup"><span data-stu-id="65087-255">If you run out of workflows to update, you can modify the `NumberGuessWorkflowHost` application to enable starting previous versions of the workflows.</span></span>

1.  <span data-ttu-id="65087-256">Clique duas vezes em **WorkflowHostForm** na **Gerenciador de soluções**e selecione o **WorkflowType** caixa de combinação.</span><span class="sxs-lookup"><span data-stu-id="65087-256">Double-click **WorkflowHostForm** in **Solution Explorer**, and select the **WorkflowType** combo box.</span></span>

2.  <span data-ttu-id="65087-257">No **propriedades** janela, selecione a **itens** propriedade e clique no botão de reticências para editar o **itens** coleção.</span><span class="sxs-lookup"><span data-stu-id="65087-257">In the **Properties** window, select the **Items** property and click the ellipsis button to edit the **Items** collection.</span></span>

3.  <span data-ttu-id="65087-258">Adicione os três itens a seguir à coleção.</span><span class="sxs-lookup"><span data-stu-id="65087-258">Add the following three items to the collection.</span></span>

    ```
    StateMachineNumberGuessWorkflow v1
    FlowchartNumberGuessWorkflow v1
    SequentialNumberGuessWorkflow v1
    ```

     <span data-ttu-id="65087-259">A coleção de `Items` concluída terá seis itens.</span><span class="sxs-lookup"><span data-stu-id="65087-259">The completed `Items` collection will have six items.</span></span>

    ```
    StateMachineNumberGuessWorkflow
    FlowchartNumberGuessWorkflow
    SequentialNumberGuessWorkflow
    StateMachineNumberGuessWorkflow v1
    FlowchartNumberGuessWorkflow v1
    SequentialNumberGuessWorkflow v1
    ```

4.  <span data-ttu-id="65087-260">Clique duas vezes em **WorkflowHostForm** na **Gerenciador de soluções**e selecione **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="65087-260">Double-click **WorkflowHostForm** in **Solution Explorer**, and select **View Code**.</span></span>

5.  <span data-ttu-id="65087-261">Adicione três novos casos para o `switch` (ou `Select Case`) instrução na `NewGame_Click` manipulador para mapear os novos itens no **WorkflowType** caixa de combinação para as identidades de fluxo de trabalho correspondente.</span><span class="sxs-lookup"><span data-stu-id="65087-261">Add three new cases to the `switch` (or `Select Case`) statement in the `NewGame_Click` handler to map the new items in the **WorkflowType** combo box to the matching workflow identities.</span></span>

    ```vb
    Case "SequentialNumberGuessWorkflow v1"
        identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1

    Case "StateMachineNumberGuessWorkflow v1"
        identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1

    Case "FlowchartNumberGuessWorkflow v1"
        identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1
    ```

    ```csharp
    case "SequentialNumberGuessWorkflow v1":
        identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1;
        break;

    case "StateMachineNumberGuessWorkflow v1":
        identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1;
        break;

    case "FlowchartNumberGuessWorkflow v1":
        identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1;
        break;
    ```

     <span data-ttu-id="65087-262">O exemplo a seguir contém a instrução completa de `switch` (ou `Select Case`).</span><span class="sxs-lookup"><span data-stu-id="65087-262">The following example contains the complete `switch` (or `Select Case`) statement.</span></span>

    ```vb
    Select Case WorkflowType.SelectedItem.ToString()
        Case "SequentialNumberGuessWorkflow"
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity

        Case "StateMachineNumberGuessWorkflow"
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity

        Case "FlowchartNumberGuessWorkflow"
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity

        Case "SequentialNumberGuessWorkflow v1"
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1

        Case "StateMachineNumberGuessWorkflow v1"
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1

        Case "FlowchartNumberGuessWorkflow v1"
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1
    End Select
    ```

    ```csharp
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

        case "SequentialNumberGuessWorkflow v1":
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1;
            break;

        case "StateMachineNumberGuessWorkflow v1":
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1;
            break;

        case "FlowchartNumberGuessWorkflow v1":
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1;
            break;
    };
    ```

6.  <span data-ttu-id="65087-263">Pressione CTRL+F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="65087-263">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="65087-264">Agora você pode iniciar as versões `v1` do fluxo de trabalho assim como as versões atuais.</span><span class="sxs-lookup"><span data-stu-id="65087-264">You can now start the `v1` versions of the workflow as well as the current versions.</span></span> <span data-ttu-id="65087-265">Para atualizar dinamicamente essas novas instâncias, execute as **ApplyDynamicUpdate** aplicativo.</span><span class="sxs-lookup"><span data-stu-id="65087-265">To dynamically update these new instances, run the **ApplyDynamicUpdate** application.</span></span>

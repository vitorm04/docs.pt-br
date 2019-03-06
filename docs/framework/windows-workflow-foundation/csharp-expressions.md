---
title: Expressões C#
ms.date: 03/30/2017
ms.assetid: 29110be7-f4e3-407e-8dbe-78102eb21115
ms.openlocfilehash: ac123a396bd43bc7b91aff6ce928b18ef4fbe6bd
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354720"
---
# <a name="c-expressions"></a><span data-ttu-id="de9ae-102">Expressões C#</span><span class="sxs-lookup"><span data-stu-id="de9ae-102">C# Expressions</span></span>
<span data-ttu-id="de9ae-103">Começando com [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], as expressões c# têm suporte no Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="de9ae-103">Starting with [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# expressions are supported in Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="de9ae-104">Novos projetos de fluxo de trabalho c# criados no Visual Studio 2012 que direcionam [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] usam expressões c# e projetos de fluxo de trabalho do Visual Basic usam expressões do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="de9ae-104">New C# workflow projects created in Visual Studio 2012 that target [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] use C# expressions, and Visual Basic workflow projects use Visual Basic expressions.</span></span> <span data-ttu-id="de9ae-105">Os projetos de fluxo de trabalho existentes do [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] que usam as expressões do Visual Basic podem ser migrados para o [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] independentemente da linguagem do projeto e têm suporte.</span><span class="sxs-lookup"><span data-stu-id="de9ae-105">Existing [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] workflow projects that use Visual Basic expressions can be migrated to [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] regardless of the project language and are supported.</span></span> <span data-ttu-id="de9ae-106">Este tópico fornece uma visão geral de expressões C# no [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="de9ae-106">This topic provides an overview of C# expressions in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span>

## <a name="using-c-expressions-in-workflows"></a><span data-ttu-id="de9ae-107">Usando expressões C# em fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="de9ae-107">Using C# expressions in workflows</span></span>

-   [<span data-ttu-id="de9ae-108">Usando expressões c# no Designer de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="de9ae-108">Using C# expressions in the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFDesigner)

    -   [<span data-ttu-id="de9ae-109">Com versões anteriores compatibilidade</span><span class="sxs-lookup"><span data-stu-id="de9ae-109">Backwards compatibility</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#BackwardCompat)

-   [<span data-ttu-id="de9ae-110">Usando expressões c# em fluxos de trabalho de código</span><span class="sxs-lookup"><span data-stu-id="de9ae-110">Using C# expressions in code workflows</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows)

-   [<span data-ttu-id="de9ae-111">Usando expressões c# em fluxos de trabalho XAML</span><span class="sxs-lookup"><span data-stu-id="de9ae-111">Using C# expressions in XAML workflows</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#XamlWorkflows)

    -   [<span data-ttu-id="de9ae-112">Xaml compilado</span><span class="sxs-lookup"><span data-stu-id="de9ae-112">Compiled Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)

    -   [<span data-ttu-id="de9ae-113">Xaml livre</span><span class="sxs-lookup"><span data-stu-id="de9ae-113">Loose Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)

-   [<span data-ttu-id="de9ae-114">Usando expressões c# em serviços de fluxo de trabalho do XAMLX</span><span class="sxs-lookup"><span data-stu-id="de9ae-114">Using C# expressions in XAMLX workflow services</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFServices)

### <a name="WFDesigner"></a> <span data-ttu-id="de9ae-115">Usando expressões c# no Designer de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="de9ae-115">Using C# expressions in the Workflow Designer</span></span>
 <span data-ttu-id="de9ae-116">Começando com [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], as expressões c# têm suporte no Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="de9ae-116">Starting with [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# expressions are supported in Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="de9ae-117">Projetos de fluxo de trabalho c# criados no Visual Studio 2012 que direcionam [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] usar expressões c#, enquanto os projetos de fluxo de trabalho do Visual Basic usam expressões do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="de9ae-117">C# workflow projects created in Visual Studio 2012 that target [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] use C# expressions, while Visual Basic workflow projects use Visual Basic expressions.</span></span> <span data-ttu-id="de9ae-118">Para especificar a expressão desejada c#, digite-o na caixa rotulada **insira uma expressão c#**.</span><span class="sxs-lookup"><span data-stu-id="de9ae-118">To specify the desired C# expression, type it into the box labeled **Enter a C# expression**.</span></span> <span data-ttu-id="de9ae-119">Esse rótulo é exibido na janela de propriedades quando a atividade é selecionada no designer ou na atividade no designer de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="de9ae-119">This label is displayed in the properties window when the activity is selected in the designer, or on the activity in the workflow designer.</span></span> <span data-ttu-id="de9ae-120">No exemplo a seguir, duas atividades `WriteLine` estão contidas no `Sequence` dentro de `NoPersistScope`.</span><span class="sxs-lookup"><span data-stu-id="de9ae-120">In the following example, two `WriteLine` activities are contained within a `Sequence` inside a `NoPersistScope`.</span></span>

 <span data-ttu-id="de9ae-121">![Atividade de sequência criada automaticamente](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")</span><span class="sxs-lookup"><span data-stu-id="de9ae-121">![Automatically created sequence activity](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")</span></span>

> [!NOTE]
>  <span data-ttu-id="de9ae-122">Expressões c# têm suporte apenas no Visual Studio e não têm suporte no designer de fluxo de trabalho hospedado novamente.</span><span class="sxs-lookup"><span data-stu-id="de9ae-122">C# expressions are supported only in Visual Studio, and are not supported in the re-hosted workflow designer.</span></span> <span data-ttu-id="de9ae-123">Para obter mais informações sobre os novos recursos WF45 com suporte no designer hospedado novamente, consulte [suporte para recursos do novo fluxo de trabalho Foundation 4.5 no Designer de fluxo de trabalho Rehosted](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md).</span><span class="sxs-lookup"><span data-stu-id="de9ae-123">For more information about new WF45 features supported in the re-hosted designer, see [Support for New Workflow Foundation 4.5 Features in the Rehosted Workflow Designer](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md).</span></span>

#### <a name="BackwardCompat"></a> <span data-ttu-id="de9ae-124">Com versões anteriores compatibilidade</span><span class="sxs-lookup"><span data-stu-id="de9ae-124">Backwards compatibility</span></span>
 <span data-ttu-id="de9ae-125">As expressões do Visual Basic em projetos existentes de fluxo de trabalho do [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] C# que foram migrados para [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] têm suporte.</span><span class="sxs-lookup"><span data-stu-id="de9ae-125">Visual Basic expressions in existing [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] C# workflow projects that have been migrated to [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are supported.</span></span> <span data-ttu-id="de9ae-126">Quando as expressões do Visual Basic são exibidas no designer de fluxo de trabalho, o texto da expressão existente do Visual Basic é substituído por **valor foi definido em XAML**, a menos que a expressão do Visual Basic é uma sintaxe c# válida.</span><span class="sxs-lookup"><span data-stu-id="de9ae-126">When the Visual Basic expressions are viewed in the workflow designer, the text of the existing Visual Basic expression is replaced with **Value was set in XAML**, unless the Visual Basic expression is valid C# syntax.</span></span> <span data-ttu-id="de9ae-127">Se a expressão do Visual Basic for uma sintaxe C# válida, a expressão será exibida.</span><span class="sxs-lookup"><span data-stu-id="de9ae-127">If the Visual Basic expression is valid C# syntax, then the expression is displayed.</span></span> <span data-ttu-id="de9ae-128">Para atualizar as expressões do Visual Basic para C#, você poderá editá-las no designer de fluxo de trabalho e especificar a expressão C# equivalente.</span><span class="sxs-lookup"><span data-stu-id="de9ae-128">To update the Visual Basic expressions to C#, you can edit them in the workflow designer and specify the equivalent C# expression.</span></span> <span data-ttu-id="de9ae-129">Não é necessário atualizar as expressões do Visual Basic para C#, mas, assim que as expressões forem atualizadas no designer de fluxo de trabalho, serão convertidas em C# e não poderão ser revertidas para o Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="de9ae-129">It is not required to update the Visual Basic expressions to C#, but once the expressions are updated in the workflow designer they are converted to C# and may not be reverted to Visual Basic.</span></span>

### <a name="CodeWorkflows"></a> <span data-ttu-id="de9ae-130">Usando expressões c# em fluxos de trabalho de código</span><span class="sxs-lookup"><span data-stu-id="de9ae-130">Using C# expressions in code workflows</span></span>
 <span data-ttu-id="de9ae-131">As expressões C# têm suporte em fluxos de trabalho com base no código do [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], mas antes que o fluxo de trabalho possa ser chamado, as expressões C# devem ser criadas usando <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="de9ae-131">C# expressions are supported in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] code based workflows, but before the workflow can be invoked the C# expressions must be compiled using <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="de9ae-132">Os autores de fluxo de trabalho podem usar `CSharpValue` para representar o valor r de uma expressão e `CSharpReference` para representar o valor l de uma expressão.</span><span class="sxs-lookup"><span data-stu-id="de9ae-132">Workflow authors can use `CSharpValue` to represent the r-value of an expression, and `CSharpReference` to represent the l-value of an expression.</span></span> <span data-ttu-id="de9ae-133">No exemplo a seguir, um fluxo de trabalho é criado com uma atividade `Assign` e uma atividade `WriteLine` contidas em uma atividade `Sequence`.</span><span class="sxs-lookup"><span data-stu-id="de9ae-133">In the following example, a workflow is created with an `Assign` activity and a `WriteLine` activity contained in a `Sequence` activity.</span></span> <span data-ttu-id="de9ae-134">Um `CSharpReference` é especificado para o argumento `To` do `Assign`, e representa o valor l da expressão.</span><span class="sxs-lookup"><span data-stu-id="de9ae-134">A `CSharpReference` is specified for the `To` argument of the `Assign`, and represents the l-value of the expression.</span></span> <span data-ttu-id="de9ae-135">Um `CSharpValue` é especificado para o argumento `Value` do `Assign` e para o argumento `Text` do `WriteLine` e representa o valor r para essas duas expressões.</span><span class="sxs-lookup"><span data-stu-id="de9ae-135">A `CSharpValue` is specified for the `Value` argument of the `Assign`, and for the `Text` argument of the `WriteLine`, and represents the r-value for those two expressions.</span></span>

```csharp
Variable<int> n = new Variable<int>
{
    Name = "n"
};

Activity wf = new Sequence
{
    Variables = { n },
    Activities =
    {
        new Assign<int>
        {
            To = new CSharpReference<int>("n"),
            Value = new CSharpValue<int>("new Random().Next(1, 101)")
        },
        new WriteLine
        {
            Text = new CSharpValue<string>("\"The number is \" + n")
        }
    }
};

CompileExpressions(wf);

WorkflowInvoker.Invoke(wf);
```

 <span data-ttu-id="de9ae-136">Depois que o fluxo de trabalho for criado, as expressões C# serão compiladas chamando o método auxiliar do `CompileExpressions` e, em seguida, o fluxo de trabalho será chamado.</span><span class="sxs-lookup"><span data-stu-id="de9ae-136">After the workflow is constructed, the C# expressions are compiled by calling the `CompileExpressions` helper method and then the workflow is invoked.</span></span> <span data-ttu-id="de9ae-137">O exemplo a seguir é o método `CompileExpressions`.</span><span class="sxs-lookup"><span data-stu-id="de9ae-137">The following example is the `CompileExpressions` method.</span></span>

```csharp
static void CompileExpressions(Activity activity)
{
    // activityName is the Namespace.Type of the activity that contains the
    // C# expressions.
    string activityName = activity.GetType().ToString();

    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name
    // to represent the new type that represents the compiled expressions.
    // Take everything after the last . for the type name.
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";
    // Take everything before the last . for the namespace.
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());

    // Create a TextExpressionCompilerSettings.
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings
    {
        Activity = activity,
        Language = "C#",
        ActivityName = activityType,
        ActivityNamespace = activityNamespace,
        RootNamespace = null,
        GenerateAsPartialClass = false,
        AlwaysGenerateSource = true,
        ForImplementation = false
    };

    // Compile the C# expression.
    TextExpressionCompilerResults results =
        new TextExpressionCompiler(settings).Compile();

    // Any compilation errors are contained in the CompilerMessages.
    if (results.HasErrors)
    {
        throw new Exception("Compilation failed.");
    }

    // Create an instance of the new compiled expression type.
    ICompiledExpressionRoot compiledExpressionRoot =
        Activator.CreateInstance(results.ResultType,
            new object[] { activity }) as ICompiledExpressionRoot;

    // Attach it to the activity.
    CompiledExpressionInvoker.SetCompiledExpressionRoot(
        activity, compiledExpressionRoot);
}
```

> [!NOTE]
>  <span data-ttu-id="de9ae-138">Se o C# expressões não forem compiladas, um <xref:System.NotSupportedException> é gerada quando o fluxo de trabalho é invocado com uma mensagem semelhante à seguinte: `Expression Activity type 'CSharpValue`1' exige compilação para ser executado.</span><span class="sxs-lookup"><span data-stu-id="de9ae-138">If the C# expressions are not compiled, a <xref:System.NotSupportedException> is thrown when the workflow is invoked with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="de9ae-139">Certifique-se de que o fluxo de trabalho tiver sido compilado.'</span><span class="sxs-lookup"><span data-stu-id="de9ae-139">Please ensure that the workflow has been compiled.\`</span></span>

 <span data-ttu-id="de9ae-140">Se seu fluxo de trabalho baseado em código personalizado usar `DynamicActivity`, algumas alterações ao método `CompileExpressions` serão necessárias, como mostrado no seguinte exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="de9ae-140">If your custom code based workflow uses `DynamicActivity`, then some changes to the `CompileExpressions` method are required, as demonstrated in the following code example.</span></span>

```csharp
static void CompileExpressions(DynamicActivity dynamicActivity)
{
    // activityName is the Namespace.Type of the activity that contains the
    // C# expressions. For Dynamic Activities this can be retrieved using the
    // name property , which must be in the form Namespace.Type.
    string activityName = dynamicActivity.Name;

    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name
    // to represent the new type that represents the compiled expressions.
    // Take everything after the last . for the type name.
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";
    // Take everything before the last . for the namespace.
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());

    // Create a TextExpressionCompilerSettings.
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings
    {
        Activity = dynamicActivity,
        Language = "C#",
        ActivityName = activityType,
        ActivityNamespace = activityNamespace,
        RootNamespace = null,
        GenerateAsPartialClass = false,
        AlwaysGenerateSource = true,
        ForImplementation = true
    };

    // Compile the C# expression.
    TextExpressionCompilerResults results =
        new TextExpressionCompiler(settings).Compile();

    // Any compilation errors are contained in the CompilerMessages.
    if (results.HasErrors)
    {
        throw new Exception("Compilation failed.");
    }

    // Create an instance of the new compiled expression type.
    ICompiledExpressionRoot compiledExpressionRoot =
        Activator.CreateInstance(results.ResultType,
            new object[] { dynamicActivity }) as ICompiledExpressionRoot;

    // Attach it to the activity.
    CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation(
        dynamicActivity, compiledExpressionRoot);
}
```

 <span data-ttu-id="de9ae-141">Há várias diferenças na sobrecarga do `CompileExpressions` que cria as expressões C# em uma atividade dinâmica.</span><span class="sxs-lookup"><span data-stu-id="de9ae-141">There are several differences in the `CompileExpressions` overload that compiles the C# expressions in a dynamic activity.</span></span>

-   <span data-ttu-id="de9ae-142">O parâmetro para `CompileExpressions` é um `DynamicActivity`.</span><span class="sxs-lookup"><span data-stu-id="de9ae-142">The parameter to `CompileExpressions` is a `DynamicActivity`.</span></span>

-   <span data-ttu-id="de9ae-143">O nome e o namespace do tipo são recuperados usando a propriedade `DynamicActivity.Name`.</span><span class="sxs-lookup"><span data-stu-id="de9ae-143">The type name and namespace are retrieved using the `DynamicActivity.Name` property.</span></span>

-   <span data-ttu-id="de9ae-144">`TextExpressionCompilerSettings.ForImplementation` é definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="de9ae-144">`TextExpressionCompilerSettings.ForImplementation` is set to `true`.</span></span>

-   <span data-ttu-id="de9ae-145">`CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` é chamado em vez de `CompiledExpressionInvoker.SetCompiledExpressionRoot`.</span><span class="sxs-lookup"><span data-stu-id="de9ae-145">`CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` is called instead of `CompiledExpressionInvoker.SetCompiledExpressionRoot`.</span></span>

 <span data-ttu-id="de9ae-146">Para obter mais informações sobre como trabalhar com expressões no código, consulte [criação de fluxos de trabalho, atividades e expressões usando / código](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="de9ae-146">For more information about working with expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>

### <a name="XamlWorkflows"></a> <span data-ttu-id="de9ae-147">Usando expressões c# em fluxos de trabalho XAML</span><span class="sxs-lookup"><span data-stu-id="de9ae-147">Using C# expressions in XAML workflows</span></span>
 <span data-ttu-id="de9ae-148">As expressões C# têm suporte em fluxos de trabalho XAML.</span><span class="sxs-lookup"><span data-stu-id="de9ae-148">C# expressions are supported in XAML workflows.</span></span> <span data-ttu-id="de9ae-149">Os fluxos de trabalho XAML compilados são criados em um tipo e os fluxos de trabalho XAML flexíveis são carregados pelo tempo de execução e compilados em uma árvore de atividade quando o fluxo de trabalho é executado.</span><span class="sxs-lookup"><span data-stu-id="de9ae-149">Compiled XAML workflows are compiled into a type, and loose XAML workflows are loaded by the runtime and compiled into an activity tree when the workflow is executed.</span></span>

-   [<span data-ttu-id="de9ae-150">Xaml compilado</span><span class="sxs-lookup"><span data-stu-id="de9ae-150">Compiled Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)

-   [<span data-ttu-id="de9ae-151">Xaml livre</span><span class="sxs-lookup"><span data-stu-id="de9ae-151">Loose Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)

#### <a name="CompiledXaml"></a> <span data-ttu-id="de9ae-152">Xaml compilado</span><span class="sxs-lookup"><span data-stu-id="de9ae-152">Compiled Xaml</span></span>
 <span data-ttu-id="de9ae-153">As expressões C# têm suporte nos fluxos de trabalho XAML compilados criados em um tipo como parte de um projeto de fluxo de trabalho de C# destinado para [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="de9ae-153">C# expressions are supported in compiled XAML workflows that are compiled to a type as part of a C# workflow project that targets [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].</span></span> <span data-ttu-id="de9ae-154">XAML compilado é o tipo de padrão de criação de fluxo de trabalho no Visual Studio e projetos de fluxo de trabalho c# criados no Visual Studio que direcionam [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] usam expressões c#.</span><span class="sxs-lookup"><span data-stu-id="de9ae-154">Compiled XAML is the default type of workflow authoring in Visual Studio, and C# workflow projects created in Visual Studio that target [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] use C# expressions.</span></span>

#### <a name="LooseXaml"></a> <span data-ttu-id="de9ae-155">Xaml livre</span><span class="sxs-lookup"><span data-stu-id="de9ae-155">Loose Xaml</span></span>
 <span data-ttu-id="de9ae-156">As expressões C# têm suporte em fluxos de trabalho XAML flexíveis.</span><span class="sxs-lookup"><span data-stu-id="de9ae-156">C# expressions are supported in loose XAML workflows.</span></span> <span data-ttu-id="de9ae-157">O programa do host de fluxo de trabalho que carrega e chama o fluxo de trabalho XAML flexível deve ser destinado para [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] e <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> devem ser definidos como `true` (o padrão é `false`).</span><span class="sxs-lookup"><span data-stu-id="de9ae-157">The workflow host program that loads and invokes the loose XAML workflow must target [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], and <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> must be set to `true` (the default is `false`).</span></span> <span data-ttu-id="de9ae-158">Para definir <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> como `true`, crie uma instância <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> com o conjunto de propriedades <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> definido como `true` e passá-lo como um parâmetro para <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="de9ae-158">To set <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> to `true`, create an <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance with its <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> property set to `true`, and pass it as a parameter to <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="de9ae-159">Se `CompileExpressions` não está definido como `true`, um <xref:System.NotSupportedException> será lançada com uma mensagem semelhante à seguinte: `Expression Activity type 'CSharpValue`1' exige compilação para ser executado.</span><span class="sxs-lookup"><span data-stu-id="de9ae-159">If `CompileExpressions` Is not set to `true`, a <xref:System.NotSupportedException> will be thrown with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="de9ae-160">Certifique-se de que o fluxo de trabalho tiver sido compilado.'</span><span class="sxs-lookup"><span data-stu-id="de9ae-160">Please ensure that the workflow has been compiled.\`</span></span>

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

 <span data-ttu-id="de9ae-161">Para obter mais informações sobre como trabalhar com fluxos de trabalho XAML, consulte [serializar fluxos de trabalho e atividades de XAML e](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="de9ae-161">For more information about working with XAML workflows, see [Serializing Workflows and Activities to and from XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).</span></span>

### <a name="WFServices"></a> <span data-ttu-id="de9ae-162">Usando expressões c# em serviços de fluxo de trabalho do XAMLX</span><span class="sxs-lookup"><span data-stu-id="de9ae-162">Using C# expressions in XAMLX workflow services</span></span>
 <span data-ttu-id="de9ae-163">Expressões C# têm suporte em serviços de fluxo de trabalho do XAMLX.</span><span class="sxs-lookup"><span data-stu-id="de9ae-163">C# expressions are supported in XAMLX workflow services.</span></span> <span data-ttu-id="de9ae-164">Quando um serviço de fluxo de trabalho é hospedado no IIS ou WAS, nenhuma etapa adicional é necessária. Porém, se o serviço de fluxo de trabalho XAML for auto-hospedado, as expressões C# deverão ser compiladas.</span><span class="sxs-lookup"><span data-stu-id="de9ae-164">When a workflow service is hosted in IIS or WAS then no additional steps are required, but if the XAML workflow service is self-hosted, then the C# expressions must be compiled.</span></span> <span data-ttu-id="de9ae-165">Para compilar as expressões c# em um serviço de fluxo de trabalho XAMLX auto-hospedado, primeiro carregue o arquivo XAMLX em um `WorkflowService`e, em seguida, passar a `Body` da `WorkflowService` para o `CompileExpressions` método descrito anteriormente na [usando c# expressões em fluxos de trabalho de código](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) seção.</span><span class="sxs-lookup"><span data-stu-id="de9ae-165">To compile the C# expressions in a self-hosted XAMLX workflow service, first load the XAMLX file into a `WorkflowService`, and then pass the `Body` of the `WorkflowService` to the `CompileExpressions` method described in the previous [Using C# expressions in code workflows](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) section.</span></span> <span data-ttu-id="de9ae-166">No exemplo a seguir, um serviço de fluxo de trabalho XAMLX é carregado, as expressões C# são criadas e o serviço do fluxo de trabalho é aberto e aguarda solicitações.</span><span class="sxs-lookup"><span data-stu-id="de9ae-166">In the following example, a XAMLX workflow service is loaded, the C# expressions are compiled, and then the workflow service is opened and waits for requests.</span></span>

```csharp
// Load the XAMLX workflow service.
WorkflowService workflow1 =
    (WorkflowService)XamlServices.Load(xamlxPath);

// Compile the C# expressions in the workflow by passing the Body to CompileExpressions.
CompileExpressions(workflow1.Body);

// Initialize the WorkflowServiceHost.
var host = new WorkflowServiceHost(workflow1, new Uri("http://localhost:8293/Service1.xamlx"));

// Enable Metadata publishing/
ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
smb.HttpGetEnabled = true;
smb.MetadataExporter.PolicyVersion = PolicyVersion.Policy15;
host.Description.Behaviors.Add(smb);

// Open the WorkflowServiceHost and wait for requests.
host.Open();
Console.WriteLine("Press enter to quit");
Console.ReadLine();
```

 <span data-ttu-id="de9ae-167">Se as expressões C# não forem compiladas, a operação `Open` terá êxito, mas o fluxo de trabalho falhará quando for chamado.</span><span class="sxs-lookup"><span data-stu-id="de9ae-167">If the C# expressions are not compiled, the `Open` operation succeeds but the workflow will fail when it is invoked.</span></span> <span data-ttu-id="de9ae-168">O seguinte `CompileExpressions` método é o mesmo que o método do anterior [usando expressões c# em fluxos de trabalho de código](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) seção.</span><span class="sxs-lookup"><span data-stu-id="de9ae-168">The following `CompileExpressions` method is the same as the method from the previous [Using C# expressions in code workflows](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) section.</span></span>

```csharp
static void CompileExpressions(Activity activity)
{
    // activityName is the Namespace.Type of the activity that contains the
    // C# expressions.
    string activityName = activity.GetType().ToString();

    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name
    // to represent the new type that represents the compiled expressions.
    // Take everything after the last . for the type name.
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";
    // Take everything before the last . for the namespace.
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());

    // Create a TextExpressionCompilerSettings.
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings
    {
        Activity = activity,
        Language = "C#",
        ActivityName = activityType,
        ActivityNamespace = activityNamespace,
        RootNamespace = null,
        GenerateAsPartialClass = false,
        AlwaysGenerateSource = true,
        ForImplementation = false
    };

    // Compile the C# expression.
    TextExpressionCompilerResults results =
        new TextExpressionCompiler(settings).Compile();

    // Any compilation errors are contained in the CompilerMessages.
    if (results.HasErrors)
    {
        throw new Exception("Compilation failed.");
    }

    // Create an instance of the new compiled expression type.
    ICompiledExpressionRoot compiledExpressionRoot =
        Activator.CreateInstance(results.ResultType,
            new object[] { activity }) as ICompiledExpressionRoot;

    // Attach it to the activity.
    CompiledExpressionInvoker.SetCompiledExpressionRoot(
        activity, compiledExpressionRoot);
}
```

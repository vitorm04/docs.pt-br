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
# <a name="c-expressions"></a>Expressões C#
Começando com [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], as expressões c# têm suporte no Windows Workflow Foundation (WF). Novos projetos de fluxo de trabalho c# criados no Visual Studio 2012 que direcionam [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] usam expressões c# e projetos de fluxo de trabalho do Visual Basic usam expressões do Visual Basic. Os projetos de fluxo de trabalho existentes do [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] que usam as expressões do Visual Basic podem ser migrados para o [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] independentemente da linguagem do projeto e têm suporte. Este tópico fornece uma visão geral de expressões C# no [!INCLUDE[wf1](../../../includes/wf1-md.md)].

## <a name="using-c-expressions-in-workflows"></a>Usando expressões C# em fluxos de trabalho

-   [Usando expressões c# no Designer de fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFDesigner)

    -   [Com versões anteriores compatibilidade](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#BackwardCompat)

-   [Usando expressões c# em fluxos de trabalho de código](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows)

-   [Usando expressões c# em fluxos de trabalho XAML](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#XamlWorkflows)

    -   [Xaml compilado](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)

    -   [Xaml livre](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)

-   [Usando expressões c# em serviços de fluxo de trabalho do XAMLX](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFServices)

### <a name="WFDesigner"></a> Usando expressões c# no Designer de fluxo de trabalho
 Começando com [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], as expressões c# têm suporte no Windows Workflow Foundation (WF). Projetos de fluxo de trabalho c# criados no Visual Studio 2012 que direcionam [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] usar expressões c#, enquanto os projetos de fluxo de trabalho do Visual Basic usam expressões do Visual Basic. Para especificar a expressão desejada c#, digite-o na caixa rotulada **insira uma expressão c#**. Esse rótulo é exibido na janela de propriedades quando a atividade é selecionada no designer ou na atividade no designer de fluxo de trabalho. No exemplo a seguir, duas atividades `WriteLine` estão contidas no `Sequence` dentro de `NoPersistScope`.

 ![Atividade de sequência criada automaticamente](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")

> [!NOTE]
>  Expressões c# têm suporte apenas no Visual Studio e não têm suporte no designer de fluxo de trabalho hospedado novamente. Para obter mais informações sobre os novos recursos WF45 com suporte no designer hospedado novamente, consulte [suporte para recursos do novo fluxo de trabalho Foundation 4.5 no Designer de fluxo de trabalho Rehosted](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md).

#### <a name="BackwardCompat"></a> Com versões anteriores compatibilidade
 As expressões do Visual Basic em projetos existentes de fluxo de trabalho do [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] C# que foram migrados para [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] têm suporte. Quando as expressões do Visual Basic são exibidas no designer de fluxo de trabalho, o texto da expressão existente do Visual Basic é substituído por **valor foi definido em XAML**, a menos que a expressão do Visual Basic é uma sintaxe c# válida. Se a expressão do Visual Basic for uma sintaxe C# válida, a expressão será exibida. Para atualizar as expressões do Visual Basic para C#, você poderá editá-las no designer de fluxo de trabalho e especificar a expressão C# equivalente. Não é necessário atualizar as expressões do Visual Basic para C#, mas, assim que as expressões forem atualizadas no designer de fluxo de trabalho, serão convertidas em C# e não poderão ser revertidas para o Visual Basic.

### <a name="CodeWorkflows"></a> Usando expressões c# em fluxos de trabalho de código
 As expressões C# têm suporte em fluxos de trabalho com base no código do [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], mas antes que o fluxo de trabalho possa ser chamado, as expressões C# devem ser criadas usando <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>. Os autores de fluxo de trabalho podem usar `CSharpValue` para representar o valor r de uma expressão e `CSharpReference` para representar o valor l de uma expressão. No exemplo a seguir, um fluxo de trabalho é criado com uma atividade `Assign` e uma atividade `WriteLine` contidas em uma atividade `Sequence`. Um `CSharpReference` é especificado para o argumento `To` do `Assign`, e representa o valor l da expressão. Um `CSharpValue` é especificado para o argumento `Value` do `Assign` e para o argumento `Text` do `WriteLine` e representa o valor r para essas duas expressões.

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

 Depois que o fluxo de trabalho for criado, as expressões C# serão compiladas chamando o método auxiliar do `CompileExpressions` e, em seguida, o fluxo de trabalho será chamado. O exemplo a seguir é o método `CompileExpressions`.

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
>  Se o C# expressões não forem compiladas, um <xref:System.NotSupportedException> é gerada quando o fluxo de trabalho é invocado com uma mensagem semelhante à seguinte: `Expression Activity type 'CSharpValue`1' exige compilação para ser executado.  Certifique-se de que o fluxo de trabalho tiver sido compilado.'

 Se seu fluxo de trabalho baseado em código personalizado usar `DynamicActivity`, algumas alterações ao método `CompileExpressions` serão necessárias, como mostrado no seguinte exemplo de código.

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

 Há várias diferenças na sobrecarga do `CompileExpressions` que cria as expressões C# em uma atividade dinâmica.

-   O parâmetro para `CompileExpressions` é um `DynamicActivity`.

-   O nome e o namespace do tipo são recuperados usando a propriedade `DynamicActivity.Name`.

-   `TextExpressionCompilerSettings.ForImplementation` é definido como `true`.

-   `CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` é chamado em vez de `CompiledExpressionInvoker.SetCompiledExpressionRoot`.

 Para obter mais informações sobre como trabalhar com expressões no código, consulte [criação de fluxos de trabalho, atividades e expressões usando / código](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).

### <a name="XamlWorkflows"></a> Usando expressões c# em fluxos de trabalho XAML
 As expressões C# têm suporte em fluxos de trabalho XAML. Os fluxos de trabalho XAML compilados são criados em um tipo e os fluxos de trabalho XAML flexíveis são carregados pelo tempo de execução e compilados em uma árvore de atividade quando o fluxo de trabalho é executado.

-   [Xaml compilado](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)

-   [Xaml livre](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)

#### <a name="CompiledXaml"></a> Xaml compilado
 As expressões C# têm suporte nos fluxos de trabalho XAML compilados criados em um tipo como parte de um projeto de fluxo de trabalho de C# destinado para [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]. XAML compilado é o tipo de padrão de criação de fluxo de trabalho no Visual Studio e projetos de fluxo de trabalho c# criados no Visual Studio que direcionam [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] usam expressões c#.

#### <a name="LooseXaml"></a> Xaml livre
 As expressões C# têm suporte em fluxos de trabalho XAML flexíveis. O programa do host de fluxo de trabalho que carrega e chama o fluxo de trabalho XAML flexível deve ser destinado para [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] e <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> devem ser definidos como `true` (o padrão é `false`). Para definir <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> como `true`, crie uma instância <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> com o conjunto de propriedades <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> definido como `true` e passá-lo como um parâmetro para <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>. Se `CompileExpressions` não está definido como `true`, um <xref:System.NotSupportedException> será lançada com uma mensagem semelhante à seguinte: `Expression Activity type 'CSharpValue`1' exige compilação para ser executado.  Certifique-se de que o fluxo de trabalho tiver sido compilado.'

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

 Para obter mais informações sobre como trabalhar com fluxos de trabalho XAML, consulte [serializar fluxos de trabalho e atividades de XAML e](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).

### <a name="WFServices"></a> Usando expressões c# em serviços de fluxo de trabalho do XAMLX
 Expressões C# têm suporte em serviços de fluxo de trabalho do XAMLX. Quando um serviço de fluxo de trabalho é hospedado no IIS ou WAS, nenhuma etapa adicional é necessária. Porém, se o serviço de fluxo de trabalho XAML for auto-hospedado, as expressões C# deverão ser compiladas. Para compilar as expressões c# em um serviço de fluxo de trabalho XAMLX auto-hospedado, primeiro carregue o arquivo XAMLX em um `WorkflowService`e, em seguida, passar a `Body` da `WorkflowService` para o `CompileExpressions` método descrito anteriormente na [usando c# expressões em fluxos de trabalho de código](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) seção. No exemplo a seguir, um serviço de fluxo de trabalho XAMLX é carregado, as expressões C# são criadas e o serviço do fluxo de trabalho é aberto e aguarda solicitações.

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

 Se as expressões C# não forem compiladas, a operação `Open` terá êxito, mas o fluxo de trabalho falhará quando for chamado. O seguinte `CompileExpressions` método é o mesmo que o método do anterior [usando expressões c# em fluxos de trabalho de código](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) seção.

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

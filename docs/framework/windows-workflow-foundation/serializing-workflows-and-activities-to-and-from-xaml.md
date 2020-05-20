---
title: Serializando fluxos de trabalho e atividades para e do XAML
description: Este artigo é uma visão geral de como serializar definições de fluxo de trabalho e trabalhar com definições de fluxo de trabalhos XAML no Workflow Foundation.
ms.date: 03/30/2017
ms.assetid: 37685b32-24e3-4d72-88d8-45d5fcc49ec2
ms.openlocfilehash: 168dbc9a36cfa80c15fddc7481e986d1ce383adb
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421339"
---
# <a name="serialize-workflows-and-activities-to-and-from-xaml"></a><span data-ttu-id="ad632-103">Serializar fluxos de trabalho e atividades de e para XAML</span><span class="sxs-lookup"><span data-stu-id="ad632-103">Serialize Workflows and Activities to and from XAML</span></span>

<span data-ttu-id="ad632-104">Além de serem construídas em tipos contidos nos assemblies, as definições de fluxo de trabalho também podem ser serializadas para XAML.</span><span class="sxs-lookup"><span data-stu-id="ad632-104">In addition to being compiled into types that are contained in assemblies, workflow definitions can also be serialized to XAML.</span></span> <span data-ttu-id="ad632-105">Essas definições serializadas possam ser recarregadas para edição ou inspeção, podem ser passadas para um sistema de compilação ou carregadas e chamadas.</span><span class="sxs-lookup"><span data-stu-id="ad632-105">These serialized definitions can be reloaded for editing or inspection, passed to a build system for compilation, or loaded and invoked.</span></span> <span data-ttu-id="ad632-106">Este tópico fornece uma visão geral de como serializar definições de fluxo de trabalho e trabalhar com definições de fluxo de trabalho XAML.</span><span class="sxs-lookup"><span data-stu-id="ad632-106">This topic provides an overview of serializing workflow definitions and working with XAML workflow definitions.</span></span>

## <a name="work-with-xaml-workflow-definitions"></a><span data-ttu-id="ad632-107">Trabalhar com definições de fluxo de trabalho XAML</span><span class="sxs-lookup"><span data-stu-id="ad632-107">Work with XAML Workflow definitions</span></span>

<span data-ttu-id="ad632-108">Para criar uma definição de fluxo de trabalho para serialização, a classe <xref:System.Activities.ActivityBuilder> é usada.</span><span class="sxs-lookup"><span data-stu-id="ad632-108">To create a workflow definition for serialization, the <xref:System.Activities.ActivityBuilder> class is used.</span></span> <span data-ttu-id="ad632-109">Criar um <xref:System.Activities.ActivityBuilder> é bem semelhante a criar um <xref:System.Activities.DynamicActivity>.</span><span class="sxs-lookup"><span data-stu-id="ad632-109">Creating an <xref:System.Activities.ActivityBuilder> is very similar to creating a <xref:System.Activities.DynamicActivity>.</span></span> <span data-ttu-id="ad632-110">Todos os argumentos desejados são especificados, e as atividades que constituem o comportamento são configuradas.</span><span class="sxs-lookup"><span data-stu-id="ad632-110">Any desired arguments are specified, and the activities that constitute the behavior are configured.</span></span> <span data-ttu-id="ad632-111">No exemplo a seguir, uma atividade `Add` é criada e usa dois argumentos de entrada, adiciona-os juntos e retorna o resultado.</span><span class="sxs-lookup"><span data-stu-id="ad632-111">In the following example, an `Add` activity is created that takes two input arguments, adds them together, and returns the result.</span></span> <span data-ttu-id="ad632-112">Como essa atividade retorna um resultado, a classe genérica <xref:System.Activities.ActivityBuilder%601> é usada.</span><span class="sxs-lookup"><span data-stu-id="ad632-112">Because this activity returns a result, the generic <xref:System.Activities.ActivityBuilder%601> class is used.</span></span>

[!code-csharp[CFX_WorkflowApplicationExample#41](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#41)]

<span data-ttu-id="ad632-113">Cada uma das instâncias <xref:System.Activities.DynamicActivityProperty> representa um dos argumentos de entrada para o fluxo de trabalho, e <xref:System.Activities.ActivityBuilder.Implementation%2A> contém as atividades que compõem a lógica do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ad632-113">Each of the <xref:System.Activities.DynamicActivityProperty> instances represents one of the input arguments to the workflow, and the <xref:System.Activities.ActivityBuilder.Implementation%2A> contains the activities that make up the logic of the workflow.</span></span> <span data-ttu-id="ad632-114">Observe que as expressões de valor r neste exemplo são expressões do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ad632-114">Note that the r-value expressions in this example are Visual Basic expressions.</span></span> <span data-ttu-id="ad632-115">As expressões lambda não são serializáveis para XAML a menos que <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> seja usado.</span><span class="sxs-lookup"><span data-stu-id="ad632-115">Lambda expressions are not serializable to XAML unless <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> is used.</span></span> <span data-ttu-id="ad632-116">Se os fluxos de trabalho serializados devem ser abertos ou editados no designer de fluxo de trabalho, Visual Basic expressões devem ser usadas.</span><span class="sxs-lookup"><span data-stu-id="ad632-116">If the serialized workflows are intended to be opened or edited in the workflow designer, then Visual Basic expressions should be used.</span></span> <span data-ttu-id="ad632-117">Para obter mais informações, consulte [criando fluxos de trabalho, atividades e expressões usando código imperativo](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="ad632-117">For more information, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>

<span data-ttu-id="ad632-118">Para serializar a definição de fluxo de trabalho representada pela instância <xref:System.Activities.ActivityBuilder> para XAML, use <xref:System.Activities.XamlIntegration.ActivityXamlServices> para criar um <xref:System.Xaml.XamlWriter> e, em seguida, use <xref:System.Xaml.XamlServices> para serializar a definição de fluxo de trabalho usando o <xref:System.Xaml.XamlWriter>.</span><span class="sxs-lookup"><span data-stu-id="ad632-118">To serialize the workflow definition represented by the <xref:System.Activities.ActivityBuilder> instance to XAML, use <xref:System.Activities.XamlIntegration.ActivityXamlServices> to create a <xref:System.Xaml.XamlWriter>, and then use <xref:System.Xaml.XamlServices> to serialize the workflow definition by using the <xref:System.Xaml.XamlWriter>.</span></span> <span data-ttu-id="ad632-119"><xref:System.Activities.XamlIntegration.ActivityXamlServices>tem métodos para mapear <xref:System.Activities.ActivityBuilder> instâncias de e para XAML e para carregar fluxos de trabalho XAML e retornar um <xref:System.Activities.DynamicActivity> que pode ser invocado.</span><span class="sxs-lookup"><span data-stu-id="ad632-119"><xref:System.Activities.XamlIntegration.ActivityXamlServices> has methods to map <xref:System.Activities.ActivityBuilder> instances to and from XAML and to load XAML workflows and return a <xref:System.Activities.DynamicActivity> that can be invoked.</span></span> <span data-ttu-id="ad632-120">No exemplo a seguir, a <xref:System.Activities.ActivityBuilder> instância do exemplo anterior é serializada para uma cadeia de caracteres e salva em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="ad632-120">In the following example, the <xref:System.Activities.ActivityBuilder> instance from the previous example is serialized to a string and saved to a file.</span></span>

```csharp
// Serialize the workflow to XAML and store it in a string.
StringBuilder sb = new StringBuilder();
StringWriter tw = new StringWriter(sb);
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(tw, new XamlSchemaContext()));
XamlServices.Save(xw, ab);
string serializedAB = sb.ToString();

// Display the XAML to the console.
Console.WriteLine(serializedAB);

// Serialize the workflow to XAML and save it to a file.
StreamWriter sw = File.CreateText(@"C:\Workflows\add.xaml");
XamlWriter xw2 = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));
XamlServices.Save(xw2, ab);
sw.Close();
```

<span data-ttu-id="ad632-121">O exemplo a seguir representa o fluxo de trabalho serializado.</span><span class="sxs-lookup"><span data-stu-id="ad632-121">The following example represents the serialized workflow.</span></span>

```xaml
<Activity
  x:TypeArguments="x:Int32"
  x:Class="Add"
  xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
  <x:Members>
    <x:Property Name="Operand1" Type="InArgument(x:Int32)" />
    <x:Property Name="Operand2" Type="InArgument(x:Int32)" />
  </x:Members>
  <Sequence>
    <WriteLine Text="[Operand1.ToString() + " + " + Operand2.ToString()]" />
    <Assign x:TypeArguments="x:Int32" Value="[Operand1 + Operand2]">
      <Assign.To>
        <OutArgument x:TypeArguments="x:Int32">
          <ArgumentReference x:TypeArguments="x:Int32" ArgumentName="Result" />
          </OutArgument>
      </Assign.To>
    </Assign>
  </Sequence>
</Activity>
```

<span data-ttu-id="ad632-122">Para carregar um fluxo de trabalho serializado, use o <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> método.</span><span class="sxs-lookup"><span data-stu-id="ad632-122">To load a serialized workflow, use the <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method.</span></span> <span data-ttu-id="ad632-123">Isso utiliza a definição de fluxo de trabalho serializado e retorna um <xref:System.Activities.DynamicActivity> que representa a definição de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ad632-123">This takes the serialized workflow definition and returns a <xref:System.Activities.DynamicActivity> that represents the workflow definition.</span></span> <span data-ttu-id="ad632-124">Observe que o XAML não é desserializado até que <xref:System.Activities.Activity.CacheMetadata%2A> seja chamado no corpo do <xref:System.Activities.DynamicActivity> durante o processo de validação.</span><span class="sxs-lookup"><span data-stu-id="ad632-124">Note that the XAML is not deserialized until <xref:System.Activities.Activity.CacheMetadata%2A> is called on the body of the <xref:System.Activities.DynamicActivity> during the validation process.</span></span> <span data-ttu-id="ad632-125">Se a validação não for chamada explicitamente, ela será executada quando o fluxo de trabalho for invocado.</span><span class="sxs-lookup"><span data-stu-id="ad632-125">If validation is not explicitly called, then it is performed when the workflow is invoked.</span></span> <span data-ttu-id="ad632-126">Se a definição de fluxo de trabalho XAML for inválida, uma exceção <xref:System.ArgumentException> será gerada.</span><span class="sxs-lookup"><span data-stu-id="ad632-126">If the XAML workflow definition is invalid, then an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="ad632-127">Todas as exceções geradas de <xref:System.Activities.Activity.CacheMetadata%2A> escapam da chamada para <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> e devem ser tratadas pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="ad632-127">Any exceptions thrown from <xref:System.Activities.Activity.CacheMetadata%2A> escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span> <span data-ttu-id="ad632-128">No exemplo a seguir, o fluxo de trabalho serializado do exemplo anterior é carregado e é chamado usando <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="ad632-128">In the following example, the serialized workflow from the previous example is loaded and invoked by using <xref:System.Activities.WorkflowInvoker>.</span></span>

[!code-csharp[CFX_WorkflowApplicationExample#43](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#43)]

<span data-ttu-id="ad632-129">Quando esse fluxo de trabalho é chamado, a seguinte saída é exibida no console.</span><span class="sxs-lookup"><span data-stu-id="ad632-129">When this workflow is invoked, the following output is displayed to the console.</span></span>

<span data-ttu-id="ad632-130">**25 + 15**</span><span class="sxs-lookup"><span data-stu-id="ad632-130">**25 + 15**</span></span>\
<span data-ttu-id="ad632-131">**40**</span><span class="sxs-lookup"><span data-stu-id="ad632-131">**40**</span></span>

> [!NOTE]
> <span data-ttu-id="ad632-132">Para obter mais informações sobre como invocar fluxos de trabalho com argumentos de entrada e saída, consulte [usando WorkflowInvoker e WorkflowApplication](using-workflowinvoker-and-workflowapplication.md) e <xref:System.Activities.WorkflowInvoker.Invoke%2A> .</span><span class="sxs-lookup"><span data-stu-id="ad632-132">For more information about invoking workflows with input and output arguments, see [Using WorkflowInvoker and WorkflowApplication](using-workflowinvoker-and-workflowapplication.md) and <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span>

<span data-ttu-id="ad632-133">Se o fluxo de trabalho serializado contiver expressões C#, uma <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instância com sua <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> propriedade definida como `true` deve ser passada como um parâmetro para <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType> , caso contrário, uma <xref:System.NotSupportedException> será lançada com uma mensagem semelhante à seguinte: o **tipo de atividade de expressão ' csharpvalue ' 1 ' requer compilação para ser executado.  Verifique se o fluxo de trabalho foi compilado.**</span><span class="sxs-lookup"><span data-stu-id="ad632-133">If the serialized workflow contains C# expressions, then an <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance with its <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> property set to `true` must be passed as a parameter to <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>, otherwise a <xref:System.NotSupportedException> will be thrown with a message similar to the following: **Expression Activity type 'CSharpValue\`1' requires compilation in order to run.  Please ensure that the workflow has been compiled.**</span></span>

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

<span data-ttu-id="ad632-134">Para obter mais informações, consulte [expressões C#](csharp-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="ad632-134">For more information, see [C# Expressions](csharp-expressions.md).</span></span>

<span data-ttu-id="ad632-135">Uma definição de fluxo de trabalho serializada também pode ser carregada em uma <xref:System.Activities.ActivityBuilder> instância usando o <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> método.</span><span class="sxs-lookup"><span data-stu-id="ad632-135">A serialized workflow definition can also be loaded into an <xref:System.Activities.ActivityBuilder> instance by using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> method.</span></span> <span data-ttu-id="ad632-136">Depois que um fluxo de trabalho serializado é carregado em uma <xref:System.Activities.ActivityBuilder> instância, ele pode ser inspecionado e modificado.</span><span class="sxs-lookup"><span data-stu-id="ad632-136">After a serialized workflow is loaded into an <xref:System.Activities.ActivityBuilder> instance, it can be inspected and modified.</span></span> <span data-ttu-id="ad632-137">Isso é útil para autores do designer do fluxo de trabalho personalizado e fornece um mecanismo para salvar e recarregar definições de fluxo de trabalho durante o processo de design.</span><span class="sxs-lookup"><span data-stu-id="ad632-137">This is useful for custom workflow designer authors and provides a mechanism for saving and reloading workflow definitions during the design process.</span></span> <span data-ttu-id="ad632-138">No exemplo a seguir, a definição do fluxo de trabalho serializado do exemplo anterior é carregada e suas propriedades são inspecionadas.</span><span class="sxs-lookup"><span data-stu-id="ad632-138">In the following example, the serialized workflow definition from the previous example is loaded and its properties are inspected.</span></span>

[!code-csharp[CFX_WorkflowApplicationExample#44](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#44)]

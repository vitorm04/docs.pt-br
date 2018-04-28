---
title: Serializando fluxos de trabalho e atividades para e do XAML
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37685b32-24e3-4d72-88d8-45d5fcc49ec2
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9a215be76002b9e8fca8ac4a9073885b3b30a97b
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="serializing-workflows-and-activities-to-and-from-xaml"></a><span data-ttu-id="ad293-102">Serializando fluxos de trabalho e atividades para e do XAML</span><span class="sxs-lookup"><span data-stu-id="ad293-102">Serializing Workflows and Activities to and from XAML</span></span>
<span data-ttu-id="ad293-103">Além de serem construídas em tipos contidos nos assemblies, as definições de fluxo de trabalho também podem ser serializadas para XAML.</span><span class="sxs-lookup"><span data-stu-id="ad293-103">In addition to being compiled into types that are contained in assemblies, workflow definitions can also be serialized to XAML.</span></span> <span data-ttu-id="ad293-104">Essas definições serializadas possam ser recarregadas para edição ou inspeção, podem ser passadas para um sistema de compilação ou carregadas e chamadas.</span><span class="sxs-lookup"><span data-stu-id="ad293-104">These serialized definitions can be reloaded for editing or inspection, passed to a build system for compilation, or loaded and invoked.</span></span> <span data-ttu-id="ad293-105">Este tópico fornece uma visão geral de como serializar definições de fluxo de trabalho e trabalhar com definições de fluxo de trabalho XAML.</span><span class="sxs-lookup"><span data-stu-id="ad293-105">This topic provides an overview of serializing workflow definitions and working with XAML workflow definitions.</span></span>  
  
## <a name="working-with-xaml-workflow-definitions"></a><span data-ttu-id="ad293-106">Trabalhando com definições de fluxo de trabalho XAML</span><span class="sxs-lookup"><span data-stu-id="ad293-106">Working with XAML Workflow Definitions</span></span>  
 <span data-ttu-id="ad293-107">Para criar uma definição de fluxo de trabalho para serialização, a classe <xref:System.Activities.ActivityBuilder> é usada.</span><span class="sxs-lookup"><span data-stu-id="ad293-107">To create a workflow definition for serialization, the <xref:System.Activities.ActivityBuilder> class is used.</span></span> <span data-ttu-id="ad293-108">Criar um <xref:System.Activities.ActivityBuilder> é bem semelhante a criar um <xref:System.Activities.DynamicActivity>.</span><span class="sxs-lookup"><span data-stu-id="ad293-108">Creating an <xref:System.Activities.ActivityBuilder> is very similar to creating a <xref:System.Activities.DynamicActivity>.</span></span> <span data-ttu-id="ad293-109">Todos os argumentos desejados são especificados, e as atividades que constituem o comportamento são configuradas.</span><span class="sxs-lookup"><span data-stu-id="ad293-109">Any desired arguments are specified, and the activities that constitute the behavior are configured.</span></span> <span data-ttu-id="ad293-110">No exemplo a seguir, uma atividade `Add` é criada e usa dois argumentos de entrada, adiciona-os juntos e retorna o resultado.</span><span class="sxs-lookup"><span data-stu-id="ad293-110">In the following example, an `Add` activity is created that takes two input arguments, adds them together, and returns the result.</span></span> <span data-ttu-id="ad293-111">Como essa atividade retorna um resultado, a classe genérica <xref:System.Activities.ActivityBuilder%601> é usada.</span><span class="sxs-lookup"><span data-stu-id="ad293-111">Because this activity returns a result, the generic <xref:System.Activities.ActivityBuilder%601> class is used.</span></span>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#41](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#41)]  
  
 <span data-ttu-id="ad293-112">Cada uma das instâncias <xref:System.Activities.DynamicActivityProperty> representa um dos argumentos de entrada para o fluxo de trabalho, e <xref:System.Activities.ActivityBuilder.Implementation%2A> contém as atividades que compõem a lógica do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ad293-112">Each of the <xref:System.Activities.DynamicActivityProperty> instances represents one of the input arguments to the workflow, and the <xref:System.Activities.ActivityBuilder.Implementation%2A> contains the activities that make up the logic of the workflow.</span></span> <span data-ttu-id="ad293-113">Observe que as expressões de valor r neste exemplo são expressões do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ad293-113">Note that the r-value expressions in this example are Visual Basic expressions.</span></span> <span data-ttu-id="ad293-114">As expressões lambda não são serializáveis para XAML a menos que <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> seja usado.</span><span class="sxs-lookup"><span data-stu-id="ad293-114">Lambda expressions are not serializable to XAML unless <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> is used.</span></span> <span data-ttu-id="ad293-115">Se os fluxos de trabalho serializados forem destinados para serem abertos ou editados no designer de fluxo de trabalho, as expressões do Visual Basic deverão ser usadas.</span><span class="sxs-lookup"><span data-stu-id="ad293-115">If the serialized workflows are intended to be opened or edited in the workflow designer then Visual Basic expressions should be used.</span></span> <span data-ttu-id="ad293-116">Para obter mais informações, consulte [criação de fluxos de trabalho, atividades e expressões usando imperativo código](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="ad293-116">For more information, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>  
  
 <span data-ttu-id="ad293-117">Para serializar a definição de fluxo de trabalho representada pela instância <xref:System.Activities.ActivityBuilder> para XAML, use <xref:System.Activities.XamlIntegration.ActivityXamlServices> para criar um <xref:System.Xaml.XamlWriter> e, em seguida, use <xref:System.Xaml.XamlServices> para serializar a definição de fluxo de trabalho usando o <xref:System.Xaml.XamlWriter>.</span><span class="sxs-lookup"><span data-stu-id="ad293-117">To serialize the workflow definition represented by the <xref:System.Activities.ActivityBuilder> instance to XAML, use <xref:System.Activities.XamlIntegration.ActivityXamlServices> to create a <xref:System.Xaml.XamlWriter>, and then use <xref:System.Xaml.XamlServices> to serialize the workflow definition by using the <xref:System.Xaml.XamlWriter>.</span></span> <span data-ttu-id="ad293-118">O <xref:System.Activities.XamlIntegration.ActivityXamlServices> tem métodos para mapear instâncias <xref:System.Activities.ActivityBuilder> para e de XAML, e para carregar fluxos de trabalho XAML e retornar um <xref:System.Activities.DynamicActivity> que pode ser chamado.</span><span class="sxs-lookup"><span data-stu-id="ad293-118"><xref:System.Activities.XamlIntegration.ActivityXamlServices> has methods to map <xref:System.Activities.ActivityBuilder> instances to and from XAML, and to load XAML workflows and return a <xref:System.Activities.DynamicActivity> that can be invoked.</span></span> <span data-ttu-id="ad293-119">No exemplo a seguir, a instância <xref:System.Activities.ActivityBuilder> do exemplo anterior é serializada para uma cadeia de caracteres, e também salva em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="ad293-119">In the following example, the <xref:System.Activities.ActivityBuilder> instance from the previous example is serialized to a string, and also saved to a file.</span></span>  
  
```csharp  
// Serialize the workflow to XAML and store it in a string.  
StringBuilder sb = new StringBuilder();  
StringWriter tw = new StringWriter(sb);  
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(tw, new XamlSchemaContext()));  
XamlServices.Save(xw , ab);  
string serializedAB = sb.ToString();  
  
// Display the XAML to the console.  
Console.WriteLine(serializedAB);  
  
// Serialize the workflow to XAML and save it to a file.  
StreamWriter sw = File.CreateText(@"C:\Workflows\add.xaml");  
XamlWriter xw2 = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));  
XamlServices.Save(xw2, ab);  
sw.Close();  
```  
  
 <span data-ttu-id="ad293-120">O exemplo a seguir representa o fluxo de trabalho serializado.</span><span class="sxs-lookup"><span data-stu-id="ad293-120">The following example represents the serialized workflow.</span></span>  
  
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
  
 <span data-ttu-id="ad293-121">Para carregar um fluxo de trabalho serializado, o <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> método é usado.</span><span class="sxs-lookup"><span data-stu-id="ad293-121">To load a serialized workflow, the <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method is used.</span></span> <span data-ttu-id="ad293-122">Isso utiliza a definição de fluxo de trabalho serializado e retorna um <xref:System.Activities.DynamicActivity> que representa a definição de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ad293-122">This takes the serialized workflow definition and returns a <xref:System.Activities.DynamicActivity> that represents the workflow definition.</span></span> <span data-ttu-id="ad293-123">Observe que o XAML não é desserializado até que <xref:System.Activities.Activity.CacheMetadata%2A> seja chamado no corpo do <xref:System.Activities.DynamicActivity> durante o processo de validação.</span><span class="sxs-lookup"><span data-stu-id="ad293-123">Note that the XAML is not deserialized until <xref:System.Activities.Activity.CacheMetadata%2A> is called on the body of the <xref:System.Activities.DynamicActivity> during the validation process.</span></span> <span data-ttu-id="ad293-124">Se a validação não for chamada explicitamente, ela será executada quando o fluxo de trabalho for chamado.</span><span class="sxs-lookup"><span data-stu-id="ad293-124">If validation is not explicitly called then it is performed when the workflow is invoked.</span></span> <span data-ttu-id="ad293-125">Se a definição de fluxo de trabalho XAML for inválida, uma exceção <xref:System.ArgumentException> será gerada.</span><span class="sxs-lookup"><span data-stu-id="ad293-125">If the XAML workflow definition is invalid, then an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="ad293-126">Todas as exceções geradas de <xref:System.Activities.Activity.CacheMetadata%2A> escapam da chamada para <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> e devem ser tratadas pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="ad293-126">Any exceptions thrown from <xref:System.Activities.Activity.CacheMetadata%2A> escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span> <span data-ttu-id="ad293-127">No exemplo a seguir, o fluxo de trabalho serializado do exemplo anterior é carregado e é chamado usando <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="ad293-127">In the following example, the serialized workflow from the previous example is loaded and invoked by using <xref:System.Activities.WorkflowInvoker>.</span></span>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#43](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#43)]  
  
 <span data-ttu-id="ad293-128">Quando esse fluxo de trabalho é chamado, a seguinte saída é exibida no console.</span><span class="sxs-lookup"><span data-stu-id="ad293-128">When this workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="ad293-129">**25 + 15**</span><span class="sxs-lookup"><span data-stu-id="ad293-129">**25 + 15**</span></span>  
<span data-ttu-id="ad293-130">**40**</span><span class="sxs-lookup"><span data-stu-id="ad293-130">**40**</span></span>    
> [!NOTE]
>  [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="ad293-131"> chamar fluxos de trabalho com argumentos de entrada e saídos, consulte [usando WorkflowInvoker e WorkflowApplication](../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md) e <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="ad293-131"> invoking workflows with input and output arguments, see [Using WorkflowInvoker and WorkflowApplication](../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md) and <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span>  
  
 <span data-ttu-id="ad293-132">Se o fluxo de trabalho serializado contiver expressões c#, então um <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instância com seu <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> propriedade definida como `true` deve ser passado como um parâmetro para <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>, caso contrário, um <xref:System.NotSupportedException> será gerada uma mensagem semelhante do a seguir: `Expression Activity type 'CSharpValue`1' requer compilação para executar.</span><span class="sxs-lookup"><span data-stu-id="ad293-132">If the serialized workflow contains C# expressions, then an <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance with its <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> property set to `true` must be passed as a parameter to <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>, otherwise a <xref:System.NotSupportedException> will be thrown with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="ad293-133">Certifique-se de que o fluxo de trabalho foi compilado.'</span><span class="sxs-lookup"><span data-stu-id="ad293-133">Please ensure that the workflow has been compiled.\`</span></span>  
  
```csharp  
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings  
{  
    CompileExpressions = true  
};  
  
DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;  
```  
  
 <span data-ttu-id="ad293-134">Para obter mais informações, consulte [c# expressões](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="ad293-134">For more information, see [C# Expressions](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).</span></span>  
  
 <span data-ttu-id="ad293-135">Uma definição de fluxo de trabalho serializada também pode ser carregada em um <xref:System.Activities.ActivityBuilder> instância usando o <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> método.</span><span class="sxs-lookup"><span data-stu-id="ad293-135">A serialized workflow definition can also be loaded into an <xref:System.Activities.ActivityBuilder> instance by using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> method.</span></span> <span data-ttu-id="ad293-136">Depois de um fluxo de trabalho serializado ser carregado em uma instância <xref:System.Activities.ActivityBuilder>, ele pode ser inspecionado e modificado.</span><span class="sxs-lookup"><span data-stu-id="ad293-136">After a serialized workflow is loaded into an <xref:System.Activities.ActivityBuilder> instance it can be inspected and modified.</span></span> <span data-ttu-id="ad293-137">Isso é útil para autores do designer do fluxo de trabalho personalizado e fornece um mecanismo para salvar e recarregar definições de fluxo de trabalho durante o processo de design.</span><span class="sxs-lookup"><span data-stu-id="ad293-137">This is useful for custom workflow designer authors and provides a mechanism for saving and reloading workflow definitions during the design process.</span></span> <span data-ttu-id="ad293-138">No exemplo a seguir, a definição do fluxo de trabalho serializado do exemplo anterior é carregada e suas propriedades são inspecionadas.</span><span class="sxs-lookup"><span data-stu-id="ad293-138">In the following example, the serialized workflow definition from the previous example is loaded and its properties are inspected.</span></span>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#44](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#44)]

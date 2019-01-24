---
title: Criando uma atividade em tempo de execução com o DynamicActivity
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: 17dda5643f86690c25067e70680a6b797dd172d3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54733201"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a><span data-ttu-id="f402a-102">Criando uma atividade em tempo de execução com o DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="f402a-102">Creating an Activity at Runtime with DynamicActivity</span></span>
<span data-ttu-id="f402a-103"><xref:System.Activities.DynamicActivity> é um concreto, classe lacradas com um construtor público.</span><span class="sxs-lookup"><span data-stu-id="f402a-103"><xref:System.Activities.DynamicActivity> is a concrete, sealed class with a public constructor.</span></span> <span data-ttu-id="f402a-104"><xref:System.Activities.DynamicActivity> pode ser usado para reunir a funcionalidade de atividade em tempo de execução usando os DOM de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="f402a-104"><xref:System.Activities.DynamicActivity> can be used to assemble activity functionality at runtime using an activity DOM.</span></span>  
  
## <a name="dynamicactivity-features"></a><span data-ttu-id="f402a-105">Recursos de DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="f402a-105">DynamicActivity Features</span></span>  
 <span data-ttu-id="f402a-106"><xref:System.Activities.DynamicActivity> tem acesso às propriedades de execução, os argumentos e variáveis, mas nenhum o acesso aos serviços de tempo de execução como atividades filhos de programação ou o rastreamento.</span><span class="sxs-lookup"><span data-stu-id="f402a-106"><xref:System.Activities.DynamicActivity> has access to execution properties, arguments and variables, but no access to run-time services such as scheduling child activities or tracking.</span></span>  
  
 <span data-ttu-id="f402a-107">As propriedades de nível superior podem ser definidas usando objetos de <xref:System.Activities.Argument> de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="f402a-107">Top-level properties can be set using workflow <xref:System.Activities.Argument> objects.</span></span> <span data-ttu-id="f402a-108">No código obrigatório, esses argumentos são criados usando propriedades de CLR em um novo tipo.</span><span class="sxs-lookup"><span data-stu-id="f402a-108">In imperative code, these arguments are created using CLR properties on a new type.</span></span> <span data-ttu-id="f402a-109">Em XAML, são declarados usando `x:Class` e marcas de `x:Member` .</span><span class="sxs-lookup"><span data-stu-id="f402a-109">In XAML, they are declared using `x:Class` and `x:Member` tags.</span></span>  
  
 <span data-ttu-id="f402a-110">Atividades construídas usando a interface de <xref:System.Activities.DynamicActivity> com o designer que usa <xref:System.ComponentModel.ICustomTypeDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="f402a-110">Activities constructed using <xref:System.Activities.DynamicActivity> interface with the designer using <xref:System.ComponentModel.ICustomTypeDescriptor>.</span></span> <span data-ttu-id="f402a-111">As atividades criadas no designer podem ser carregadas dinamicamente usando <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, como demonstrado no procedimento a seguir.</span><span class="sxs-lookup"><span data-stu-id="f402a-111">Activities created in the designer can be loaded dynamically using <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, as demonstrated in the following procedure.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a><span data-ttu-id="f402a-112">Para criar uma atividade em tempo de execução usando o código obrigatório</span><span class="sxs-lookup"><span data-stu-id="f402a-112">To create an activity at runtime using imperative code</span></span>  
  
1.  <span data-ttu-id="f402a-113">Abra o Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="f402a-113">OpenVisual Studio 2010.</span></span>  
  
2.  <span data-ttu-id="f402a-114">Selecione **arquivo**, **novos**, **projeto**.</span><span class="sxs-lookup"><span data-stu-id="f402a-114">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="f402a-115">Selecione **Workflow 4.0** sob **Visual c#** no **tipos de projeto** janela e selecione o **v2010** nó.</span><span class="sxs-lookup"><span data-stu-id="f402a-115">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="f402a-116">Selecione **Sequential Workflow Console Application** na **modelos** janela.</span><span class="sxs-lookup"><span data-stu-id="f402a-116">Select **Sequential Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="f402a-117">Nomeie o novo projeto DynamicActivitySample.</span><span class="sxs-lookup"><span data-stu-id="f402a-117">Name the new project DynamicActivitySample.</span></span>  
  
3.  <span data-ttu-id="f402a-118">Botão direito do mouse Workflow1.xaml no projeto de HelloActivity e selecione **excluir**.</span><span class="sxs-lookup"><span data-stu-id="f402a-118">Right-click Workflow1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4.  <span data-ttu-id="f402a-119">Abra Module.vb.</span><span class="sxs-lookup"><span data-stu-id="f402a-119">Open Program.cs.</span></span> <span data-ttu-id="f402a-120">Adicione a seguinte diretiva para a parte superior do arquivo.</span><span class="sxs-lookup"><span data-stu-id="f402a-120">Add the following directive to the top of the file.</span></span>  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
5.  <span data-ttu-id="f402a-121">Substitua o conteúdo do método de `Main` com o código a seguir, que cria uma atividade de <xref:System.Activities.Statements.Sequence> que contém uma única atividade de <xref:System.Activities.Statements.WriteLine> e a atribui à propriedade de <xref:System.Activities.DynamicActivity.Implementation%2A> de uma nova atividade dinâmico.</span><span class="sxs-lookup"><span data-stu-id="f402a-121">Replace the contents of the `Main` method with the following code, which creates a <xref:System.Activities.Statements.Sequence> activity that contains a single <xref:System.Activities.Statements.WriteLine> activity and assigns it to the <xref:System.Activities.DynamicActivity.Implementation%2A> property of a new dynamic activity.</span></span>  
  
    ```csharp  
    //Define the input argument for the activity  
    var textOut = new InArgument<string>();  
    //Create the activity, property, and implementation  
                Activity dynamicWorkflow = new DynamicActivity()  
                {  
                    Properties =   
                    {  
                        new DynamicActivityProperty  
                        {  
                            Name = "Text",  
                            Type = typeof(InArgument<String>),  
                            Value = textOut  
                        }  
                    },  
                    Implementation = () => new Sequence()  
                    {  
                        Activities =   
                        {  
                            new WriteLine()  
                            {  
                                Text = new InArgument<string>(env => textOut.Get(env))  
                            }  
                        }  
                    }  
                };  
    //Execute the activity with a parameter dictionary  
                WorkflowInvoker.Invoke(dynamicWorkflow, new Dictionary<string, object> { { "Text", "Hello World!" } });  
                Console.ReadLine();  
    ```  
  
6.  <span data-ttu-id="f402a-122">Executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f402a-122">Execute the application.</span></span> <span data-ttu-id="f402a-123">Uma janela de console com o texto "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="f402a-123">A console window with the text "Hello World!"</span></span> <span data-ttu-id="f402a-124">Exibe.</span><span class="sxs-lookup"><span data-stu-id="f402a-124">displays.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a><span data-ttu-id="f402a-125">Para criar uma atividade em tempo de execução usando XAML</span><span class="sxs-lookup"><span data-stu-id="f402a-125">To create an activity at runtime using XAML</span></span>  
  
1.  <span data-ttu-id="f402a-126">Abra o Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="f402a-126">Open Visual Studio 2010.</span></span>  
  
2.  <span data-ttu-id="f402a-127">Selecione **arquivo**, **novos**, **projeto**.</span><span class="sxs-lookup"><span data-stu-id="f402a-127">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="f402a-128">Selecione **Workflow 4.0** sob **Visual c#** no **tipos de projeto** janela e selecione o **v2010** nó.</span><span class="sxs-lookup"><span data-stu-id="f402a-128">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="f402a-129">Selecione **aplicativo de Console do fluxo de trabalho** na **modelos** janela.</span><span class="sxs-lookup"><span data-stu-id="f402a-129">Select  **Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="f402a-130">Nomeie o novo projeto DynamicActivitySample.</span><span class="sxs-lookup"><span data-stu-id="f402a-130">Name the new project DynamicActivitySample.</span></span>  
  
3.  <span data-ttu-id="f402a-131">Workflow1.xaml aberto no projeto de HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="f402a-131">Open Workflow1.xaml in the HelloActivity project.</span></span> <span data-ttu-id="f402a-132">Clique o **argumentos** opção na parte inferior do designer.</span><span class="sxs-lookup"><span data-stu-id="f402a-132">Click the **Arguments** option at the bottom of the designer.</span></span> <span data-ttu-id="f402a-133">Crie um novo argumento de `In` chamado `TextToWrite` de tipo `String`.</span><span class="sxs-lookup"><span data-stu-id="f402a-133">Create a new `In` argument called `TextToWrite` of type `String`.</span></span>  
  
4.  <span data-ttu-id="f402a-134">Arraste uma **WriteLine** atividade da **primitivos** seção da caixa de ferramentas na superfície do designer.</span><span class="sxs-lookup"><span data-stu-id="f402a-134">Drag a **WriteLine** activity from the **Primitives** section of the toolbox onto the designer surface.</span></span> <span data-ttu-id="f402a-135">Atribua o valor `TextToWrite` para o **texto** propriedade da atividade.</span><span class="sxs-lookup"><span data-stu-id="f402a-135">Assign the value `TextToWrite` to the **Text** property of the activity.</span></span>  
  
5.  <span data-ttu-id="f402a-136">Abra Module.vb.</span><span class="sxs-lookup"><span data-stu-id="f402a-136">Open Program.cs.</span></span> <span data-ttu-id="f402a-137">Adicione a seguinte diretiva para a parte superior do arquivo.</span><span class="sxs-lookup"><span data-stu-id="f402a-137">Add the following directive to the top of the file.</span></span>  
  
    ```  
    using System.Activities.XamlIntegration;  
    ```  
  
6.  <span data-ttu-id="f402a-138">Substitua o conteúdo do método de `Main` com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="f402a-138">Replace the contents of the `Main` method with the following code.</span></span>  
  
    ```  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7.  <span data-ttu-id="f402a-139">Executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f402a-139">Execute the application.</span></span> <span data-ttu-id="f402a-140">Uma janela de console com o texto "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="f402a-140">A console window with the text "Hello World!"</span></span> <span data-ttu-id="f402a-141">é exibida.</span><span class="sxs-lookup"><span data-stu-id="f402a-141">appears.</span></span>  
  
8.  <span data-ttu-id="f402a-142">Clique no arquivo de Workflow1.xaml na **Gerenciador de soluções** e selecione **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="f402a-142">Right-click the Workflow1.xaml file in the **Solution Explorer** and select **View Code**.</span></span> <span data-ttu-id="f402a-143">Observe que a classe da atividade é criada com `x:Class` e a propriedade é criada com `x:Property`.</span><span class="sxs-lookup"><span data-stu-id="f402a-143">Note that the activity class is created with `x:Class` and the property is created with `x:Property`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f402a-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f402a-144">See also</span></span>

- [<span data-ttu-id="f402a-145">Criando fluxos de trabalho, atividades e expressões de design usando o código obrigatório</span><span class="sxs-lookup"><span data-stu-id="f402a-145">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)

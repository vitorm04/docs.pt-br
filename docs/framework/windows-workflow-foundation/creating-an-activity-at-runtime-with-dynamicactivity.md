---
title: Criando uma atividade em runtime com o DynamicActivity
description: DynamicActivity é uma classe concreta e selada com um construtor público. Use a classe para montar a funcionalidade de atividade em tempo de execução usando um DOM de atividade.
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: 17ee14be7df4801018c7afd2e91f1fb07c34e8e1
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421534"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a><span data-ttu-id="c52a5-104">Criando uma atividade em runtime com o DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="c52a5-104">Creating an Activity at Runtime with DynamicActivity</span></span>
<span data-ttu-id="c52a5-105"><xref:System.Activities.DynamicActivity> é um concreto, classe lacradas com um construtor público.</span><span class="sxs-lookup"><span data-stu-id="c52a5-105"><xref:System.Activities.DynamicActivity> is a concrete, sealed class with a public constructor.</span></span> <span data-ttu-id="c52a5-106"><xref:System.Activities.DynamicActivity> pode ser usado para reunir a funcionalidade de atividade em runtime usando os DOM de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="c52a5-106"><xref:System.Activities.DynamicActivity> can be used to assemble activity functionality at runtime using an activity DOM.</span></span>  
  
## <a name="dynamicactivity-features"></a><span data-ttu-id="c52a5-107">Recursos de DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="c52a5-107">DynamicActivity Features</span></span>  
 <span data-ttu-id="c52a5-108"><xref:System.Activities.DynamicActivity> tem acesso às propriedades de execução, os argumentos e variáveis, mas nenhum o acesso aos serviços de tempo de execução como atividades filhos de programação ou o rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c52a5-108"><xref:System.Activities.DynamicActivity> has access to execution properties, arguments and variables, but no access to run-time services such as scheduling child activities or tracking.</span></span>  
  
 <span data-ttu-id="c52a5-109">As propriedades de nível superior podem ser definidas usando objetos de <xref:System.Activities.Argument> de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c52a5-109">Top-level properties can be set using workflow <xref:System.Activities.Argument> objects.</span></span> <span data-ttu-id="c52a5-110">No código obrigatório, esses argumentos são criados usando propriedades de CLR em um novo tipo.</span><span class="sxs-lookup"><span data-stu-id="c52a5-110">In imperative code, these arguments are created using CLR properties on a new type.</span></span> <span data-ttu-id="c52a5-111">Em XAML, são declarados usando `x:Class` e marcas de `x:Member` .</span><span class="sxs-lookup"><span data-stu-id="c52a5-111">In XAML, they are declared using `x:Class` and `x:Member` tags.</span></span>  
  
 <span data-ttu-id="c52a5-112">Atividades construídas usando a interface de <xref:System.Activities.DynamicActivity> com o designer que usa <xref:System.ComponentModel.ICustomTypeDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="c52a5-112">Activities constructed using <xref:System.Activities.DynamicActivity> interface with the designer using <xref:System.ComponentModel.ICustomTypeDescriptor>.</span></span> <span data-ttu-id="c52a5-113">As atividades criadas no designer podem ser carregadas dinamicamente usando <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, como demonstrado no procedimento a seguir.</span><span class="sxs-lookup"><span data-stu-id="c52a5-113">Activities created in the designer can be loaded dynamically using <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, as demonstrated in the following procedure.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a><span data-ttu-id="c52a5-114">Para criar uma atividade em runtime usando o código obrigatório</span><span class="sxs-lookup"><span data-stu-id="c52a5-114">To create an activity at runtime using imperative code</span></span>  
  
1. <span data-ttu-id="c52a5-115">OpenVisual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="c52a5-115">OpenVisual Studio 2010.</span></span>  
  
2. <span data-ttu-id="c52a5-116">Selecione **arquivo**, **novo**, **projeto**.</span><span class="sxs-lookup"><span data-stu-id="c52a5-116">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="c52a5-117">Selecione **fluxo de trabalho 4,0** em **Visual C#** na janela **tipos de projeto** e selecione o nó **v2010** .</span><span class="sxs-lookup"><span data-stu-id="c52a5-117">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="c52a5-118">Selecione **aplicativo de console de fluxo de trabalho Sequencial** na janela **modelos** .</span><span class="sxs-lookup"><span data-stu-id="c52a5-118">Select **Sequential Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="c52a5-119">Nomeie o novo projeto DynamicActivitySample.</span><span class="sxs-lookup"><span data-stu-id="c52a5-119">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="c52a5-120">Clique com o botão direito do mouse em Workflow1. XAML no projeto HelloActivity e selecione **excluir**.</span><span class="sxs-lookup"><span data-stu-id="c52a5-120">Right-click Workflow1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4. <span data-ttu-id="c52a5-121">Abra Program.cs.</span><span class="sxs-lookup"><span data-stu-id="c52a5-121">Open Program.cs.</span></span> <span data-ttu-id="c52a5-122">Adicione a seguinte diretiva para a parte superior do arquivo.</span><span class="sxs-lookup"><span data-stu-id="c52a5-122">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
5. <span data-ttu-id="c52a5-123">Substitua o conteúdo do método de `Main` com o código a seguir, que cria uma atividade de <xref:System.Activities.Statements.Sequence> que contém uma única atividade de <xref:System.Activities.Statements.WriteLine> e a atribui à propriedade de <xref:System.Activities.DynamicActivity.Implementation%2A> de uma nova atividade dinâmico.</span><span class="sxs-lookup"><span data-stu-id="c52a5-123">Replace the contents of the `Main` method with the following code, which creates a <xref:System.Activities.Statements.Sequence> activity that contains a single <xref:System.Activities.Statements.WriteLine> activity and assigns it to the <xref:System.Activities.DynamicActivity.Implementation%2A> property of a new dynamic activity.</span></span>  
  
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
  
6. <span data-ttu-id="c52a5-124">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c52a5-124">Execute the application.</span></span> <span data-ttu-id="c52a5-125">Uma janela de console com o texto "Olá, Mundo!"</span><span class="sxs-lookup"><span data-stu-id="c52a5-125">A console window with the text "Hello World!"</span></span> <span data-ttu-id="c52a5-126">mostra.</span><span class="sxs-lookup"><span data-stu-id="c52a5-126">displays.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a><span data-ttu-id="c52a5-127">Para criar uma atividade em runtime usando XAML</span><span class="sxs-lookup"><span data-stu-id="c52a5-127">To create an activity at runtime using XAML</span></span>  
  
1. <span data-ttu-id="c52a5-128">Abra o Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="c52a5-128">Open Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="c52a5-129">Selecione **arquivo**, **novo**, **projeto**.</span><span class="sxs-lookup"><span data-stu-id="c52a5-129">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="c52a5-130">Selecione **fluxo de trabalho 4,0** em **Visual C#** na janela **tipos de projeto** e selecione o nó **v2010** .</span><span class="sxs-lookup"><span data-stu-id="c52a5-130">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="c52a5-131">Selecione **aplicativo de console de fluxo de trabalho** na janela **modelos** .</span><span class="sxs-lookup"><span data-stu-id="c52a5-131">Select  **Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="c52a5-132">Nomeie o novo projeto DynamicActivitySample.</span><span class="sxs-lookup"><span data-stu-id="c52a5-132">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="c52a5-133">Workflow1.xaml aberto no projeto de HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="c52a5-133">Open Workflow1.xaml in the HelloActivity project.</span></span> <span data-ttu-id="c52a5-134">Clique na opção **argumentos** na parte inferior do designer.</span><span class="sxs-lookup"><span data-stu-id="c52a5-134">Click the **Arguments** option at the bottom of the designer.</span></span> <span data-ttu-id="c52a5-135">Crie um novo argumento de `In` chamado `TextToWrite` de tipo `String`.</span><span class="sxs-lookup"><span data-stu-id="c52a5-135">Create a new `In` argument called `TextToWrite` of type `String`.</span></span>  
  
4. <span data-ttu-id="c52a5-136">Arraste uma atividade **WriteLine** da seção **primitivas** da caixa de ferramentas para a superfície do designer.</span><span class="sxs-lookup"><span data-stu-id="c52a5-136">Drag a **WriteLine** activity from the **Primitives** section of the toolbox onto the designer surface.</span></span> <span data-ttu-id="c52a5-137">Atribua o valor `TextToWrite` à propriedade **Text** da atividade.</span><span class="sxs-lookup"><span data-stu-id="c52a5-137">Assign the value `TextToWrite` to the **Text** property of the activity.</span></span>  
  
5. <span data-ttu-id="c52a5-138">Abra Program.cs.</span><span class="sxs-lookup"><span data-stu-id="c52a5-138">Open Program.cs.</span></span> <span data-ttu-id="c52a5-139">Adicione a seguinte diretiva para a parte superior do arquivo.</span><span class="sxs-lookup"><span data-stu-id="c52a5-139">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Activities.XamlIntegration;  
    ```  
  
6. <span data-ttu-id="c52a5-140">Substitua o conteúdo do método de `Main` com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="c52a5-140">Replace the contents of the `Main` method with the following code.</span></span>  
  
    ```csharp  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. <span data-ttu-id="c52a5-141">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c52a5-141">Execute the application.</span></span> <span data-ttu-id="c52a5-142">Uma janela de console com o texto "Olá, Mundo!"</span><span class="sxs-lookup"><span data-stu-id="c52a5-142">A console window with the text "Hello World!"</span></span> <span data-ttu-id="c52a5-143"> é exibido.</span><span class="sxs-lookup"><span data-stu-id="c52a5-143">appears.</span></span>  
  
8. <span data-ttu-id="c52a5-144">Clique com o botão direito do mouse no arquivo workflow1. XAML na **Gerenciador de soluções** e selecione **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="c52a5-144">Right-click the Workflow1.xaml file in the **Solution Explorer** and select **View Code**.</span></span> <span data-ttu-id="c52a5-145">Observe que a classe da atividade é criada com `x:Class` e a propriedade é criada com `x:Property`.</span><span class="sxs-lookup"><span data-stu-id="c52a5-145">Note that the activity class is created with `x:Class` and the property is created with `x:Property`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c52a5-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="c52a5-146">See also</span></span>

- [<span data-ttu-id="c52a5-147">Criando fluxos de trabalho, atividades e expressões de design usando o código obrigatório</span><span class="sxs-lookup"><span data-stu-id="c52a5-147">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](authoring-workflows-activities-and-expressions-using-imperative-code.md)

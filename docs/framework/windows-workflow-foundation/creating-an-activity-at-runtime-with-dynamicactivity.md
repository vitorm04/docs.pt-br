---
title: Criando uma atividade em runtime com o DynamicActivity
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: 871108fd09e9127b3f9e06174f05a47c7fd7682c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182985"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a><span data-ttu-id="e0924-102">Criando uma atividade em runtime com o DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="e0924-102">Creating an Activity at Runtime with DynamicActivity</span></span>
<span data-ttu-id="e0924-103"><xref:System.Activities.DynamicActivity> é um concreto, classe lacradas com um construtor público.</span><span class="sxs-lookup"><span data-stu-id="e0924-103"><xref:System.Activities.DynamicActivity> is a concrete, sealed class with a public constructor.</span></span> <span data-ttu-id="e0924-104"><xref:System.Activities.DynamicActivity> pode ser usado para reunir a funcionalidade de atividade em runtime usando os DOM de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="e0924-104"><xref:System.Activities.DynamicActivity> can be used to assemble activity functionality at runtime using an activity DOM.</span></span>  
  
## <a name="dynamicactivity-features"></a><span data-ttu-id="e0924-105">Recursos de DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="e0924-105">DynamicActivity Features</span></span>  
 <span data-ttu-id="e0924-106"><xref:System.Activities.DynamicActivity> tem acesso às propriedades de execução, os argumentos e variáveis, mas nenhum o acesso aos serviços de tempo de execução como atividades filhos de programação ou o rastreamento.</span><span class="sxs-lookup"><span data-stu-id="e0924-106"><xref:System.Activities.DynamicActivity> has access to execution properties, arguments and variables, but no access to run-time services such as scheduling child activities or tracking.</span></span>  
  
 <span data-ttu-id="e0924-107">As propriedades de nível superior podem ser definidas usando objetos de <xref:System.Activities.Argument> de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e0924-107">Top-level properties can be set using workflow <xref:System.Activities.Argument> objects.</span></span> <span data-ttu-id="e0924-108">No código obrigatório, esses argumentos são criados usando propriedades de CLR em um novo tipo.</span><span class="sxs-lookup"><span data-stu-id="e0924-108">In imperative code, these arguments are created using CLR properties on a new type.</span></span> <span data-ttu-id="e0924-109">Em XAML, são declarados usando `x:Class` e marcas de `x:Member` .</span><span class="sxs-lookup"><span data-stu-id="e0924-109">In XAML, they are declared using `x:Class` and `x:Member` tags.</span></span>  
  
 <span data-ttu-id="e0924-110">Atividades construídas usando a interface de <xref:System.Activities.DynamicActivity> com o designer que usa <xref:System.ComponentModel.ICustomTypeDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="e0924-110">Activities constructed using <xref:System.Activities.DynamicActivity> interface with the designer using <xref:System.ComponentModel.ICustomTypeDescriptor>.</span></span> <span data-ttu-id="e0924-111">As atividades criadas no designer podem ser carregadas dinamicamente usando <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, como demonstrado no procedimento a seguir.</span><span class="sxs-lookup"><span data-stu-id="e0924-111">Activities created in the designer can be loaded dynamically using <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, as demonstrated in the following procedure.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a><span data-ttu-id="e0924-112">Para criar uma atividade em runtime usando o código obrigatório</span><span class="sxs-lookup"><span data-stu-id="e0924-112">To create an activity at runtime using imperative code</span></span>  
  
1. <span data-ttu-id="e0924-113">OpenVisual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="e0924-113">OpenVisual Studio 2010.</span></span>  
  
2. <span data-ttu-id="e0924-114">Selecione **Arquivo,** **Novo,** **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="e0924-114">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="e0924-115">Selecione **Workflow 4.0** em **Visual C#** na janela **Tipos de projeto** e selecione o nó **v2010.**</span><span class="sxs-lookup"><span data-stu-id="e0924-115">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="e0924-116">Selecione **aplicativo de console de fluxo de trabalho seqüencial** na janela **Modelos.**</span><span class="sxs-lookup"><span data-stu-id="e0924-116">Select **Sequential Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="e0924-117">Nomeie o novo projeto DynamicActivitySample.</span><span class="sxs-lookup"><span data-stu-id="e0924-117">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="e0924-118">Clique com o botão direito do mouse Workflow1.xaml no projeto HelloActivity e **selecione Excluir**.</span><span class="sxs-lookup"><span data-stu-id="e0924-118">Right-click Workflow1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4. <span data-ttu-id="e0924-119">Abra Program.cs.</span><span class="sxs-lookup"><span data-stu-id="e0924-119">Open Program.cs.</span></span> <span data-ttu-id="e0924-120">Adicione a seguinte diretiva para a parte superior do arquivo.</span><span class="sxs-lookup"><span data-stu-id="e0924-120">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
5. <span data-ttu-id="e0924-121">Substitua o conteúdo do método de `Main` com o código a seguir, que cria uma atividade de <xref:System.Activities.Statements.Sequence> que contém uma única atividade de <xref:System.Activities.Statements.WriteLine> e a atribui à propriedade de <xref:System.Activities.DynamicActivity.Implementation%2A> de uma nova atividade dinâmico.</span><span class="sxs-lookup"><span data-stu-id="e0924-121">Replace the contents of the `Main` method with the following code, which creates a <xref:System.Activities.Statements.Sequence> activity that contains a single <xref:System.Activities.Statements.WriteLine> activity and assigns it to the <xref:System.Activities.DynamicActivity.Implementation%2A> property of a new dynamic activity.</span></span>  
  
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
  
6. <span data-ttu-id="e0924-122">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e0924-122">Execute the application.</span></span> <span data-ttu-id="e0924-123">Uma janela de console com o texto "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="e0924-123">A console window with the text "Hello World!"</span></span> <span data-ttu-id="e0924-124">Exibe.</span><span class="sxs-lookup"><span data-stu-id="e0924-124">displays.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a><span data-ttu-id="e0924-125">Para criar uma atividade em runtime usando XAML</span><span class="sxs-lookup"><span data-stu-id="e0924-125">To create an activity at runtime using XAML</span></span>  
  
1. <span data-ttu-id="e0924-126">Open Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="e0924-126">Open Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="e0924-127">Selecione **Arquivo,** **Novo,** **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="e0924-127">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="e0924-128">Selecione **Workflow 4.0** em **Visual C#** na janela **Tipos de projeto** e selecione o nó **v2010.**</span><span class="sxs-lookup"><span data-stu-id="e0924-128">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="e0924-129">Selecione **O aplicativo do console de fluxo de trabalho** na janela **Modelos.**</span><span class="sxs-lookup"><span data-stu-id="e0924-129">Select  **Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="e0924-130">Nomeie o novo projeto DynamicActivitySample.</span><span class="sxs-lookup"><span data-stu-id="e0924-130">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="e0924-131">Workflow1.xaml aberto no projeto de HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="e0924-131">Open Workflow1.xaml in the HelloActivity project.</span></span> <span data-ttu-id="e0924-132">Clique na opção **Argumentos** na parte inferior do designer.</span><span class="sxs-lookup"><span data-stu-id="e0924-132">Click the **Arguments** option at the bottom of the designer.</span></span> <span data-ttu-id="e0924-133">Crie um novo argumento de `In` chamado `TextToWrite` de tipo `String`.</span><span class="sxs-lookup"><span data-stu-id="e0924-133">Create a new `In` argument called `TextToWrite` of type `String`.</span></span>  
  
4. <span data-ttu-id="e0924-134">Arraste uma atividade **WriteLine** da seção **Primitivos** da caixa de ferramentas para a superfície do designer.</span><span class="sxs-lookup"><span data-stu-id="e0924-134">Drag a **WriteLine** activity from the **Primitives** section of the toolbox onto the designer surface.</span></span> <span data-ttu-id="e0924-135">Atribuir o `TextToWrite` valor à propriedade **Texto** da atividade.</span><span class="sxs-lookup"><span data-stu-id="e0924-135">Assign the value `TextToWrite` to the **Text** property of the activity.</span></span>  
  
5. <span data-ttu-id="e0924-136">Abra Program.cs.</span><span class="sxs-lookup"><span data-stu-id="e0924-136">Open Program.cs.</span></span> <span data-ttu-id="e0924-137">Adicione a seguinte diretiva para a parte superior do arquivo.</span><span class="sxs-lookup"><span data-stu-id="e0924-137">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Activities.XamlIntegration;  
    ```  
  
6. <span data-ttu-id="e0924-138">Substitua o conteúdo do método de `Main` com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e0924-138">Replace the contents of the `Main` method with the following code.</span></span>  
  
    ```csharp  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. <span data-ttu-id="e0924-139">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e0924-139">Execute the application.</span></span> <span data-ttu-id="e0924-140">Uma janela de console com o texto "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="e0924-140">A console window with the text "Hello World!"</span></span> <span data-ttu-id="e0924-141"> é exibido.</span><span class="sxs-lookup"><span data-stu-id="e0924-141">appears.</span></span>  
  
8. <span data-ttu-id="e0924-142">Clique com o botão direito do mouse no arquivo Workflow1.xaml no **Solution Explorer** e selecione **'Exibir código '**.</span><span class="sxs-lookup"><span data-stu-id="e0924-142">Right-click the Workflow1.xaml file in the **Solution Explorer** and select **View Code**.</span></span> <span data-ttu-id="e0924-143">Observe que a classe da atividade é criada com `x:Class` e a propriedade é criada com `x:Property`.</span><span class="sxs-lookup"><span data-stu-id="e0924-143">Note that the activity class is created with `x:Class` and the property is created with `x:Property`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0924-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="e0924-144">See also</span></span>

- [<span data-ttu-id="e0924-145">Criando fluxos de trabalho, atividades e expressões de design usando o código obrigatório</span><span class="sxs-lookup"><span data-stu-id="e0924-145">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](authoring-workflows-activities-and-expressions-using-imperative-code.md)

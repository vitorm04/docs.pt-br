---
title: "Criação de DynamicActivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8ebe82f-98c8-4452-aed7-2c60a512b097
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 43f39d5c78e59925ad73fe7277300848877f83f2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="dynamicactivity-creation"></a><span data-ttu-id="c48b7-102">Criação de DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="c48b7-102">DynamicActivity Creation</span></span>
<span data-ttu-id="c48b7-103">Este exemplo demonstra duas maneiras diferentes para criar uma atividade em tempo de execução usando a atividade de <xref:System.Activities.DynamicActivity> .</span><span class="sxs-lookup"><span data-stu-id="c48b7-103">This sample demonstrates two different ways to create an activity at runtime using the <xref:System.Activities.DynamicActivity> activity.</span></span>  
  
 <span data-ttu-id="c48b7-104">Nesse exemplo, uma atividade é criada em tempo de execução com um corpo que contém uma atividade de <xref:System.Activities.Statements.Sequence> que contém <xref:System.Activities.Statements.ForEach%601> e atividades de <xref:System.Activities.Statements.Assign%601> .</span><span class="sxs-lookup"><span data-stu-id="c48b7-104">In this sample, an activity is created at runtime with a body that contains a <xref:System.Activities.Statements.Sequence> activity that contains <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.Assign%601> activities.</span></span> <span data-ttu-id="c48b7-105">Uma lista de entrada de inteiros é passada para a atividade e o conjunto como uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="c48b7-105">An input list of integers is passed into the activity and set as a property.</span></span> <span data-ttu-id="c48b7-106">A atividade de <xref:System.Activities.Statements.ForEach%601> em itera através da lista de valores e acumula-a.</span><span class="sxs-lookup"><span data-stu-id="c48b7-106">The <xref:System.Activities.Statements.ForEach%601> activity then iterates over the list of values and accumulates it.</span></span> <span data-ttu-id="c48b7-107">Na atividade de <xref:System.Activities.Statements.Assign%601> , o valor médio é calculado dividindo o acumulador pelo número de elementos na lista e atribuí-la a média.</span><span class="sxs-lookup"><span data-stu-id="c48b7-107">In the <xref:System.Activities.Statements.Assign%601> activity, the average value is calculated by dividing the accumulator by the number of elements in the list and assign it to the average.</span></span>  
  
 <span data-ttu-id="c48b7-108">O exemplo demonstra o uso de uma atividade de <xref:System.Activities.DynamicActivity> que flui em variáveis como argumentos de entrada e retornar valores como argumentos de saída.</span><span class="sxs-lookup"><span data-stu-id="c48b7-108">The sample demonstrates the usage of a <xref:System.Activities.DynamicActivity> activity that flows in variables as input arguments and returning values as output arguments.</span></span> <span data-ttu-id="c48b7-109">A atividade tem um `Numbers` chamado argumento conectado que é uma lista de inteiros.</span><span class="sxs-lookup"><span data-stu-id="c48b7-109">The activity has one input argument named `Numbers` that is a list of integers.</span></span> <span data-ttu-id="c48b7-110">A atividade de <xref:System.Activities.Statements.ForEach%601> itera através da lista de valores e acumula-a.</span><span class="sxs-lookup"><span data-stu-id="c48b7-110">The <xref:System.Activities.Statements.ForEach%601> activity iterates over the list of values and accumulates it.</span></span> <span data-ttu-id="c48b7-111">Na atividade de <xref:System.Activities.Statements.Assign%601> , o valor médio é calculado dividindo o acumulador pelo número de elementos na lista e atribuindo a média.</span><span class="sxs-lookup"><span data-stu-id="c48b7-111">In the <xref:System.Activities.Statements.Assign%601> activity, the average value is calculated by dividing the accumulator by the number of elements in the list and assigning it to the average.</span></span> <span data-ttu-id="c48b7-112">A média é retornada como um argumento de saída chamado `Average`.</span><span class="sxs-lookup"><span data-stu-id="c48b7-112">The average is returned as an output argument named `Average`.</span></span>  
  
 <span data-ttu-id="c48b7-113">Quando a atividade dinâmico é criada por meio de programação, entrada e saída são declaradas como mostrado no exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="c48b7-113">When the dynamic activity is created programmatically, the input and output are declared as shown in the following code example.</span></span>  
  
```csharp  
DynamicActivity act = new DynamicActivity()  
{  
    DisplayName = "Find average",  
    Properties =   
    {  
        // Input argument  
        new DynamicActivityProperty  
        {  
            Name = "Numbers",  
            Type = typeof(InArgument<List<int>>),  
            Value = numbers  
        },  
        // Output argument  
        new DynamicActivityProperty  
        {  
            Name = "Average",  
            Type = typeof(OutArgument<double>),  
            Value = average  
        }  
    },  
};  
```  
  
 <span data-ttu-id="c48b7-114">O exemplo de código a seguir mostra a definição completa de `DynamicActivity` que calcula a média dos valores em uma lista.</span><span class="sxs-lookup"><span data-stu-id="c48b7-114">The following code example shows the complete definition of the `DynamicActivity` that computes the average of the values in a list.</span></span>  
  
```  
DynamicActivity act = new DynamicActivity()  
{  
    DisplayName = "Find average",  
    Properties =   
    {  
        // Input argument  
        new DynamicActivityProperty  
        {  
            Name = "Numbers",  
            Type = typeof(InArgument<List<int>>),  
            Value = numbers  
        },  
        // Output argument  
        new DynamicActivityProperty  
        {  
            Name = "Average",  
            Type = typeof(OutArgument<double>),  
            Value = average  
        }  
    },  
    Implementation = () =>  
        new Sequence  
        {  
            Variables = { result, accumulator },  
            Activities =  
            {  
                new ForEach<int>  
                {  
                    Values =  new ArgumentValue<IEnumerable<int>> { ArgumentName = "Numbers" },                                  
                    Body = new ActivityAction<int>  
                    {  
                        Argument = iterationVariable,  
                        Handler = new Assign<int>  
                        {  
                            To = accumulator,  
                            Value = new InArgument<int>(env => iterationVariable.Get(env) +  accumulator.Get(env))  
                        }  
                    }  
                },  
  
                // Calculate the average and assign to the output argument.  
                new Assign<double>  
                {  
                    To = new ArgumentReference<double> { ArgumentName = "Average" },  
                    Value = new InArgument<double>(env => accumulator.Get(env) / numbers.Get(env).Count<int>())  
                },  
            }  
        }  
};  
```  
  
 <span data-ttu-id="c48b7-115">Quando criada em XAML, entrada e saída são declaradas como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c48b7-115">When created in XAML, the input and output are declared as shown in the following example.</span></span>  
  
```xml  
<Activity x:Class="Microsoft.Samples.DynamicActivityCreation.FindAverage"  
          xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
          xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <x:Members>  
    <x:Property Name="Numbers" Type="InArgument(scg:List(x:Int32))" />  
    <x:Property Name="Average" Type="OutArgument(x:Double)" />  
  </x:Members>  
    ...  
    ...  
</Activity>  
```  
  
 <span data-ttu-id="c48b7-116">O XAML pode ser criado usando [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)]visualmente.</span><span class="sxs-lookup"><span data-stu-id="c48b7-116">The XAML can be created visually using the [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)].</span></span> <span data-ttu-id="c48b7-117">Se estiver incluído em um projeto do Visual Studio, certifique-se de definir seu "Build Action" para "None" para impedir que está sendo compilada.</span><span class="sxs-lookup"><span data-stu-id="c48b7-117">If it is included in a Visual Studio project, be sure to set its "Build Action" to "None" to prevent it from being compiled.</span></span> <span data-ttu-id="c48b7-118">O XAML pode então ser carregado dinamicamente usando a chamada a seguir.</span><span class="sxs-lookup"><span data-stu-id="c48b7-118">The XAML can then be loaded dynamically using the following call.</span></span>  
  
```  
Activity act2 = ActivityXamlServices.Load(@"FindAverage.xaml");  
```  
  
 <span data-ttu-id="c48b7-119">A instância de <xref:System.Activities.DynamicActivity> criada ou carregar programaticamente com um fluxo de trabalho XAML pode ser usada como mostrado no exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="c48b7-119">The <xref:System.Activities.DynamicActivity> instance created programmatically or through loading a XAML workflow can be used as shown in the following code example.</span></span> <span data-ttu-id="c48b7-120">Observe que "atuar" passado para o `WorkflowInvoker.Invoke` é o ato de"" <xref:System.Activities.Activity> definido no primeiro exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="c48b7-120">Please note that "act" passed to the `WorkflowInvoker.Invoke` is the "act" <xref:System.Activities.Activity> defined in the first code example.</span></span>  
  
```  
IDictionary<string, object> results = WorkflowInvoker.Invoke(act, new Dictionary<string, object> { { "Numbers", numbers } });  
  
Console.WriteLine("The average calculated using the code activity is = " + results["Average"]);  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="c48b7-121">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="c48b7-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="c48b7-122">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de DynamicActivityCreation.sln.</span><span class="sxs-lookup"><span data-stu-id="c48b7-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the DynamicActivityCreation.sln solution file.</span></span>  
  
2.  <span data-ttu-id="c48b7-123">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="c48b7-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="c48b7-124">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="c48b7-124">To run the solution, press CTRL+F5.</span></span>  
  
## <a name="command-line-arguments"></a><span data-ttu-id="c48b7-125">Argumentos de linha de comando</span><span class="sxs-lookup"><span data-stu-id="c48b7-125">Command line arguments</span></span>  
 <span data-ttu-id="c48b7-126">Este exemplo aceita argumentos de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="c48b7-126">This sample accepts command line arguments.</span></span> <span data-ttu-id="c48b7-127">Os usuários podem fornecer uma lista de números para que a atividade calcula a média.</span><span class="sxs-lookup"><span data-stu-id="c48b7-127">Users can provide a list of numbers for the activity to calculate their average.</span></span> <span data-ttu-id="c48b7-128">A lista de números a ser usado é passada como uma lista de números se ter separado por um espaço.</span><span class="sxs-lookup"><span data-stu-id="c48b7-128">The list of numbers to be used is passed as a list of numbers separated by a space.</span></span> <span data-ttu-id="c48b7-129">Por exemplo, para calcular a média de 5, 10 e 32, chamam o exemplo usando a seguinte linha de comando.</span><span class="sxs-lookup"><span data-stu-id="c48b7-129">For example, to calculate the average of 5, 10, and 32 invoke the sample using the following command line.</span></span>  
  
 <span data-ttu-id="c48b7-130">**DynamicActivityCreation 5 10 32**</span><span class="sxs-lookup"><span data-stu-id="c48b7-130">**DynamicActivityCreation 5 10 32**</span></span>  
> [!IMPORTANT]
>  <span data-ttu-id="c48b7-131">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="c48b7-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c48b7-132">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="c48b7-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c48b7-133">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="c48b7-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c48b7-134">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="c48b7-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\DynamicActivityCreation`
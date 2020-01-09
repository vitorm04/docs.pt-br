---
title: ParallelForEach não genérico
ms.date: 03/30/2017
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
ms.openlocfilehash: ea7f57b8812dca3dfcb4908730dd788182d50c5c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347611"
---
# <a name="non-generic-parallelforeach"></a><span data-ttu-id="1f8b5-102">ParallelForEach não genérico</span><span class="sxs-lookup"><span data-stu-id="1f8b5-102">Non-generic ParallelForEach</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="1f8b5-103">envia na caixa de ferramentas um conjunto de atividades de fluxo de controle, incluindo <xref:System.Activities.Statements.ParallelForEach%601>, que permita iterar através das coleções de <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="1f8b5-103">ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ParallelForEach%601>, which allows iterating through <xref:System.Collections.Generic.IEnumerable%601> collections.</span></span>

<span data-ttu-id="1f8b5-104"><xref:System.Activities.Statements.ParallelForEach%601> requer que sua propriedade <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> seja do tipo <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-104"><xref:System.Activities.Statements.ParallelForEach%601> requires its <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> property to be of type  <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="1f8b5-105">Isso evita que usuários de iterar sobre as estruturas de dados que implementam a interface de <xref:System.Collections.Generic.IEnumerable%601> (por exemplo, <xref:System.Collections.ArrayList>).</span><span class="sxs-lookup"><span data-stu-id="1f8b5-105">This precludes users from iterating over data structures that implement <xref:System.Collections.Generic.IEnumerable%601> interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="1f8b5-106">A versão não genérico de <xref:System.Activities.Statements.ParallelForEach%601> supera esse requisito, custas de mais complexidade de tempo de execução para garantir a compatibilidade dos tipos de valores na coleção.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-106">The non-generic version of <xref:System.Activities.Statements.ParallelForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>

<span data-ttu-id="1f8b5-107">Este exemplo mostra como implementar uma atividade não genérico de <xref:System.Activities.Statements.ParallelForEach%601> e seu designer.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ParallelForEach%601> activity and its designer.</span></span> <span data-ttu-id="1f8b5-108">Esta atividade pode ser usada para percorrer <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>

## <a name="parallelforeach-activity"></a><span data-ttu-id="1f8b5-109">Atividade ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="1f8b5-109">ParallelForEach activity</span></span>

<span data-ttu-id="1f8b5-110">A C#instrução `foreach` do/Visual Basic enumera os elementos de uma coleção, executando uma instrução incorporada para cada elemento da coleção.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-110">The C#/Visual Basic `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="1f8b5-111">As atividades equivalentes de [!INCLUDE[wf1](../../../../includes/wf1-md.md)] são <xref:System.Activities.Statements.ForEach%601> e <xref:System.Activities.Statements.ParallelForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="1f8b5-112">A atividade de <xref:System.Activities.Statements.ForEach%601> contém uma lista de valores e um corpo.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="1f8b5-113">Em runtime, a lista é iterada e o corpo é executado para cada valor na lista.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>

<span data-ttu-id="1f8b5-114"><xref:System.Activities.Statements.ParallelForEach%601> tem <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, de modo que a atividade de <xref:System.Activities.Statements.ParallelForEach%601> pode concluir no início se a avaliação de <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> retorna `true`.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-114"><xref:System.Activities.Statements.ParallelForEach%601> has a <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, so that the <xref:System.Activities.Statements.ParallelForEach%601> activity could complete early if the evaluation of the <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> returns `true`.</span></span> <span data-ttu-id="1f8b5-115"><xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> é avaliado após cada iteração é concluída.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-115">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> is evaluated after each iteration is completed.</span></span>

<span data-ttu-id="1f8b5-116">Para a maioria dos casos, a versão genérica de atividade deve ser a solução preferencial, porque ele aborda a maioria das situações em que é usada e fornece verificação de tipo em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-116">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it is used and provides type checking at compile time.</span></span> <span data-ttu-id="1f8b5-117">A versão não genérico pode ser usada iterando por tipos que implementam a interface não genérica de <xref:System.Collections.IEnumerable> .</span><span class="sxs-lookup"><span data-stu-id="1f8b5-117">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>

## <a name="class-definition"></a><span data-ttu-id="1f8b5-118">Definição de classe</span><span class="sxs-lookup"><span data-stu-id="1f8b5-118">Class definition</span></span>

<span data-ttu-id="1f8b5-119">O exemplo de código a seguir mostra a definição de uma atividade não genérico de `ParallelForEach` é.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-119">The following code example shows the definition of a non-generic `ParallelForEach` activity is.</span></span>

```csharp
[ContentProperty("Body")]
public class ParallelForEach : NativeActivity
{
    [RequiredArgument]
    [DefaultValue(null)]
    InArgument<IEnumerable> Values { get; set; }

    [DefaultValue(null)]
    [DependsOn("Values")]
    public Activity<bool> CompletionCondition
    [DefaultValue(null)]
    [DependsOn("CompletionCondition")]
    ActivityAction<object> Body { get; set; }
}
```

<span data-ttu-id="1f8b5-120">Corpo (opcional) </span><span class="sxs-lookup"><span data-stu-id="1f8b5-120">Body (optional)</span></span>\
<span data-ttu-id="1f8b5-121"><xref:System.Activities.ActivityAction> de tipo <xref:System.Object>, que é executado para cada elemento na coleção.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-121">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="1f8b5-122">Cada elemento individual é passado no corpo através da propriedade do argumento.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-122">Each individual element is passed into the Body through its Argument property.</span></span>

<span data-ttu-id="1f8b5-123">Valores (opcional) </span><span class="sxs-lookup"><span data-stu-id="1f8b5-123">Values (optional)</span></span>\
<span data-ttu-id="1f8b5-124">A coleção de elementos que são iterados sobre.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-124">The collection of elements that are iterated over.</span></span> <span data-ttu-id="1f8b5-125">Garantir que todos os elementos da coleção são de tipos compatíveis é feito em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-125">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>

<span data-ttu-id="1f8b5-126">CompletionCondition (opcional) </span><span class="sxs-lookup"><span data-stu-id="1f8b5-126">CompletionCondition (optional)</span></span>\
<span data-ttu-id="1f8b5-127">A propriedade de <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> é avaliada após qualquer iteração completa.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-127">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> property is evaluated after any iteration completes.</span></span> <span data-ttu-id="1f8b5-128">Se for avaliada como `true`, então o agendada durante iterações é cancelado.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-128">If it evaluates to `true`, then the scheduled pending iterations are canceled.</span></span> <span data-ttu-id="1f8b5-129">Se esta propriedade não for definida, todas as atividades na coleção de ramificações executam até a conclusão.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-129">If this property is not set, all activities in the Branches collection execute until completion.</span></span>

## <a name="example-of-using-parallelforeach"></a><span data-ttu-id="1f8b5-130">Exemplo de uso de ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="1f8b5-130">Example of using ParallelForEach</span></span>

<span data-ttu-id="1f8b5-131">O código a seguir demonstra como usar a atividade de ParallelForEach em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-131">The following code demonstrates how to use the ParallelForEach activity in an application.</span></span>

```csharp
string[] names = { "bill", "steve", "ray" };

DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };

Activity sampleUsage =
    new ParallelForEach
    {
       Values = new InArgument<IEnumerable>(c=> names),
       Body = new ActivityAction<object>
       {
           Argument = iterationVariable,
           Handler = new WriteLine
           {
               Text = new InArgument<string>(env => string.Format("Hello {0}",                                                               iterationVariable.Get(env)))
           }
       }
   };
```

## <a name="parallelforeach-designer"></a><span data-ttu-id="1f8b5-132">Designer de ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="1f8b5-132">ParallelForEach designer</span></span>

<span data-ttu-id="1f8b5-133">O designer de atividade para o exemplo é semelhante a aparência ao designer fornecido para atividades interno de <xref:System.Activities.Statements.ParallelForEach%601> .</span><span class="sxs-lookup"><span data-stu-id="1f8b5-133">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span> <span data-ttu-id="1f8b5-134">O designer aparece na caixa de ferramentas na categoria **exemplos**, **atividades não genéricas** .</span><span class="sxs-lookup"><span data-stu-id="1f8b5-134">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="1f8b5-135">O designer é denominado **ParallelForEachWithBodyFactory** na caixa de ferramentas, porque a atividade expõe uma <xref:System.Activities.Presentation.IActivityTemplateFactory> na caixa de ferramentas que cria a atividade com um <xref:System.Activities.ActivityAction>configurado corretamente.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-135">The designer is named **ParallelForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox that creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>

```csharp
public sealed class ParallelForEachWithBodyFactory : IActivityTemplateFactory
{
    public Activity Create(DependencyObject target)
    {
        return new Microsoft.Samples.Activities.Statements.ParallelForEach()
        {
            Body = new ActivityAction<object>()
            {
                Argument = new DelegateInArgument<object>()
                {
                    Name = "item"
                }
            }
        };
    }
}
```

## <a name="to-run-the-sample"></a><span data-ttu-id="1f8b5-136">Para executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="1f8b5-136">To run the sample</span></span>

1. <span data-ttu-id="1f8b5-137">Defina o projeto de sua escolha como o projeto de inicialização de solução.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-137">Set the project of your choice as the startup project of the solution.</span></span>

    1. <span data-ttu-id="1f8b5-138">**CodeTestClient** mostra como usar a atividade usando código.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-138">**CodeTestClient** shows how to use the activity using code.</span></span>

    2. <span data-ttu-id="1f8b5-139">**DesignerTestClient** mostra como usar a atividade dentro do designer.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-139">**DesignerTestClient** shows how to use the activity within the designer.</span></span>

2. <span data-ttu-id="1f8b5-140">Compile e execute o projeto.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-140">Build and run the project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1f8b5-141">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-141">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1f8b5-142">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-142">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="1f8b5-143">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-143">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1f8b5-144">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="1f8b5-144">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`

---
title: Atividade personalizado para iniciar um intervalo de valores
ms.date: 03/30/2017
ms.assetid: 441e0a17-421f-430c-ba97-59e4cc6c88e3
ms.openlocfilehash: cfaf4318b1557a9fc217de8254e164243ea54569
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44066994"
---
# <a name="custom-activity-to-switch-on-a-range-of-values"></a><span data-ttu-id="a07a6-102">Atividade personalizado para iniciar um intervalo de valores</span><span class="sxs-lookup"><span data-stu-id="a07a6-102">Custom Activity to Switch on a Range of Values</span></span>
<span data-ttu-id="a07a6-103">Este exemplo demonstra como criar uma atividade personalizado que estende o uso de <xref:System.Activities.Statements.Switch%601>.</span><span class="sxs-lookup"><span data-stu-id="a07a6-103">This sample demonstrates how to create a custom activity that extends the use of a <xref:System.Activities.Statements.Switch%601>.</span></span> <span data-ttu-id="a07a6-104">Uma declaração convencional de <xref:System.Activities.Statements.Switch%601> permite alternar baseado em um único valor.</span><span class="sxs-lookup"><span data-stu-id="a07a6-104">A conventional <xref:System.Activities.Statements.Switch%601> statement allows switching based upon a single value.</span></span> <span data-ttu-id="a07a6-105">Mas, há situações onde comerciais uma atividade deve alternar baseado em um intervalo de valores.</span><span class="sxs-lookup"><span data-stu-id="a07a6-105">But, there are business scenarios where an activity must switch based upon a range of values.</span></span> <span data-ttu-id="a07a6-106">Por exemplo, uma atividade pode executar uma ação quando o valor que está sendo alternado na está entre 1 e 5, outra ação quando o valor está entre 6 e 10, e uma ação padrão para todos os outros valores.</span><span class="sxs-lookup"><span data-stu-id="a07a6-106">For example, an activity might execute one action when the value being switched upon is between 1 and 5, another action when the value is between 6 and 10, and a default action for all other values.</span></span> <span data-ttu-id="a07a6-107">Esta atividade personalizado permite exatamente esse cenário.</span><span class="sxs-lookup"><span data-stu-id="a07a6-107">This custom activity enables exactly that scenario.</span></span>  
  
## <a name="the-switchrange-activity"></a><span data-ttu-id="a07a6-108">A atividade de SwitchRange</span><span class="sxs-lookup"><span data-stu-id="a07a6-108">The SwitchRange Activity</span></span>  
 <span data-ttu-id="a07a6-109">As agendas de atividade de `SwitchRange` uma atividade filho quando o valor do resultado da expressão é incluído dentro do intervalo de um do seu `Cases`.</span><span class="sxs-lookup"><span data-stu-id="a07a6-109">The `SwitchRange` activity schedules a child activity when the result value of its expression is included within the range of one of its `Cases`.</span></span>  
  
 <span data-ttu-id="a07a6-110">O exemplo de código é uma atividade personalizado que alterne baseado em um intervalo de valores.</span><span class="sxs-lookup"><span data-stu-id="a07a6-110">The following code example is a custom activity that switches based upon a range of values.</span></span>  
  
```csharp  
public sealed class SwitchRange<T> : NativeActivity where T : IComparable  
{  
   [RequiredArgument]  
   [DefaultValue(null)]  
   public InArgument<T> Expression { get; set; }  
  
   public IList<CaseRange<T>> Cases  
  
   [DefaultValue(null)]  
   public Activity Default { get; set; }}  
}  
```  
  
|<span data-ttu-id="a07a6-111">Propriedade</span><span class="sxs-lookup"><span data-stu-id="a07a6-111">Property</span></span>|<span data-ttu-id="a07a6-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="a07a6-112">Description</span></span>|  
|-|-|  
|<span data-ttu-id="a07a6-113">Expressão</span><span class="sxs-lookup"><span data-stu-id="a07a6-113">Expression</span></span>|<span data-ttu-id="a07a6-114">Esta é a expressão a ser avaliada e comparado com os intervalos na lista select case.</span><span class="sxs-lookup"><span data-stu-id="a07a6-114">This is the expression to be evaluated and compared against the ranges in the Cases list.</span></span> <span data-ttu-id="a07a6-115">O resultado da expressão é do tipo T.</span><span class="sxs-lookup"><span data-stu-id="a07a6-115">The result of the expression is of type T.</span></span>|  
|<span data-ttu-id="a07a6-116">Casos</span><span class="sxs-lookup"><span data-stu-id="a07a6-116">Cases</span></span>|<span data-ttu-id="a07a6-117">Cada caso consistem em um intervalo (e) e uma atividade (corpo).</span><span class="sxs-lookup"><span data-stu-id="a07a6-117">Each case consists of a range (From and To) and an activity (Body).</span></span> <span data-ttu-id="a07a6-118">A expressão é avaliada e comparada com os intervalos.</span><span class="sxs-lookup"><span data-stu-id="a07a6-118">The expression is evaluated and compared against the ranges.</span></span> <span data-ttu-id="a07a6-119">Se o resultado da expressão está dentro do intervalo de uma dos casos, a atividade correspondente é executada.</span><span class="sxs-lookup"><span data-stu-id="a07a6-119">If the result of the expression is within the range of one of the cases, the corresponding activity is executed.</span></span>|  
|<span data-ttu-id="a07a6-120">Padrão</span><span class="sxs-lookup"><span data-stu-id="a07a6-120">Default</span></span>|<span data-ttu-id="a07a6-121">A atividade que é executado quando nenhum caso for correspondente.</span><span class="sxs-lookup"><span data-stu-id="a07a6-121">The activity that is executed when no case is matched.</span></span> <span data-ttu-id="a07a6-122">Quando definida como `null`, nenhuma ação é executada.</span><span class="sxs-lookup"><span data-stu-id="a07a6-122">When set to `null`, no action is taken.</span></span>|  
  
## <a name="caserange-class"></a><span data-ttu-id="a07a6-123">Classe de CaseRange</span><span class="sxs-lookup"><span data-stu-id="a07a6-123">CaseRange Class</span></span>  
 <span data-ttu-id="a07a6-124">A classe de `CaseRange` representa um intervalo dentro de uma atividade de `SwitchRange` .</span><span class="sxs-lookup"><span data-stu-id="a07a6-124">The `CaseRange` class represents a range within a `SwitchRange` activity.</span></span> <span data-ttu-id="a07a6-125">Cada instância de `CaseRange` contém um intervalo (composta de `From` e de `To`) e uma atividade de `Body` que está agendada se a expressão é avaliada em `SwitchRange` dentro do intervalo.</span><span class="sxs-lookup"><span data-stu-id="a07a6-125">Every instance of `CaseRange` contains a range (composed of a `From` and a `To`) and a `Body` activity that is scheduled if the expression in the `SwitchRange` is evaluated within the range.</span></span>  
  
 <span data-ttu-id="a07a6-126">O exemplo de código é a definição da classe de `CaseRange` .</span><span class="sxs-lookup"><span data-stu-id="a07a6-126">The following code example is the definition for the `CaseRange` class.</span></span>  
  
```  
public class CaseRange<T> where T : IComparable  
{  
    public T From { get; set; }  
  
    public T To { get; set; }  
  
    public Activity Action { get; set; }  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="a07a6-127">As classes de `SwitchRange` e de `CaseRange` , que são definidas no exemplo são as classes genéricas que podem trabalhar com qualquer tipo que implementa `IComparable`, como a classe de <xref:System.Activities.Statements.Switch%601> .</span><span class="sxs-lookup"><span data-stu-id="a07a6-127">Both the `SwitchRange` and `CaseRange` classes, which are defined in the sample are generic classes that can work with any type that implements `IComparable`, like the <xref:System.Activities.Statements.Switch%601> class.</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="a07a6-128">Uso de exemplo</span><span class="sxs-lookup"><span data-stu-id="a07a6-128">Sample Usage</span></span>  
 <span data-ttu-id="a07a6-129">O exemplo de código demonstra como usar a atividade de `SwitchRange` .</span><span class="sxs-lookup"><span data-stu-id="a07a6-129">The following code example demonstrates how to use the `SwitchRange` activity.</span></span>  
  
```csharp  
Activity SwitchRange = new SwitchRange<int>  
{  
    Expression = new InArgument<int>(value),  
    Cases =   
    {  
        new CaseRange<int>                      
        {  
            From = 1,  
            To = 5,  
            Action = new WriteLine  
            {  
                Text = "Case 1-5 selected",  
            }  
        },  
        new CaseRange<int>  
        {  
            From = 6,  
            To = 10,  
            Action = new WriteLine  
            {  
                Text = "Case 6-10 selected",  
            }  
        }  
    },  
    Default = new WriteLine { Text = "Default Case selected" }  
};  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="a07a6-130">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="a07a6-130">To use this sample</span></span>  
  
1.  <span data-ttu-id="a07a6-131">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de SwitchRange.sln.</span><span class="sxs-lookup"><span data-stu-id="a07a6-131">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the SwitchRange.sln solution file.</span></span>  
  
2.  <span data-ttu-id="a07a6-132">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="a07a6-132">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="a07a6-133">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="a07a6-133">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a07a6-134">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="a07a6-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a07a6-135">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="a07a6-135">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a07a6-136">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="a07a6-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a07a6-137">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="a07a6-137">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SwitchRange`
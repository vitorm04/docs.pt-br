---
title: ForEach não genéricos
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: 0274cd5b87e6039ff40afa3108986ffd113fc4fb
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46478312"
---
# <a name="non-generic-foreach"></a><span data-ttu-id="04107-102">ForEach não genéricos</span><span class="sxs-lookup"><span data-stu-id="04107-102">Non-Generic ForEach</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="04107-103"> envia na caixa de ferramentas um conjunto de atividades de fluxo de controle, incluindo <xref:System.Activities.Statements.ForEach%601>, que permita iterar através das coleções de <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="04107-103"> ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ForEach%601>, which allows iterating through <xref:System.Collections.Generic.IEnumerable%601> collections.</span></span>  
  
 <span data-ttu-id="04107-104"><xref:System.Activities.Statements.ForEach%601> requer sua propriedade de <xref:System.Activities.Statements.ForEach%601.Values%2A> ser do tipo <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="04107-104"><xref:System.Activities.Statements.ForEach%601> requires its <xref:System.Activities.Statements.ForEach%601.Values%2A> property to be of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="04107-105">Isso evita que usuários de iterar sobre as estruturas de dados que implementam a interface de <xref:System.Collections.Generic.IEnumerable%601> (por exemplo, <xref:System.Collections.ArrayList>).</span><span class="sxs-lookup"><span data-stu-id="04107-105">This precludes users from iterating over data structures that implement <xref:System.Collections.Generic.IEnumerable%601> interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="04107-106">A versão não genérico de <xref:System.Activities.Statements.ForEach%601> supera esse requisito, custas de mais complexidade de tempo de execução para garantir a compatibilidade dos tipos de valores na coleção.</span><span class="sxs-lookup"><span data-stu-id="04107-106">The non-generic version of <xref:System.Activities.Statements.ForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>  
  
 <span data-ttu-id="04107-107">Este exemplo mostra como implementar uma atividade não genérico de <xref:System.Activities.Statements.ForEach%601> e seu designer.</span><span class="sxs-lookup"><span data-stu-id="04107-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ForEach%601> activity and its designer.</span></span> <span data-ttu-id="04107-108">Esta atividade pode ser usada para percorrer <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="04107-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>  
  
## <a name="foreach-activity"></a><span data-ttu-id="04107-109">Atividade ForEach</span><span class="sxs-lookup"><span data-stu-id="04107-109">ForEach Activity</span></span>  
 <span data-ttu-id="04107-110">A declaração de C#/VB `foreach` enumera os elementos de uma coleção, executando uma instrução inserido para cada elemento da coleção.</span><span class="sxs-lookup"><span data-stu-id="04107-110">The C#/VB `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="04107-111">As atividades equivalentes de [!INCLUDE[wf1](../../../../includes/wf1-md.md)] de `foreach` são <xref:System.Activities.Statements.ForEach%601> e <xref:System.Activities.Statements.ParallelForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="04107-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities of `foreach` are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="04107-112">A atividade de <xref:System.Activities.Statements.ForEach%601> contém uma lista de valores e um corpo.</span><span class="sxs-lookup"><span data-stu-id="04107-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="04107-113">Em tempo de execução, a lista é iterada e o corpo é executado para cada valor na lista.</span><span class="sxs-lookup"><span data-stu-id="04107-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>  
  
 <span data-ttu-id="04107-114">Para a maioria dos casos, a versão genérica de atividade deve ser a solução preferencial, porque ele aborda a maioria das situações em que ele deve ser usado, e fornece verificação de tipo em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="04107-114">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it would be used, and provides type checking at compile time.</span></span> <span data-ttu-id="04107-115">A versão não genérico pode ser usada iterando por tipos que implementam a interface não genérica de <xref:System.Collections.IEnumerable> .</span><span class="sxs-lookup"><span data-stu-id="04107-115">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>  
  
## <a name="class-definition"></a><span data-ttu-id="04107-116">Definição de classe</span><span class="sxs-lookup"><span data-stu-id="04107-116">Class Definition</span></span>  
 <span data-ttu-id="04107-117">O exemplo de código a seguir mostra a definição de uma atividade não genérico de `ForEach` .</span><span class="sxs-lookup"><span data-stu-id="04107-117">The following code example shows the definition of a non-generic `ForEach` activity.</span></span>  
  
```  
[ContentProperty("Body")]  
public class ForEach : NativeActivity  
{  
    [RequiredArgument]  
    [DefaultValue(null)]  
    InArgument<IEnumerable> Values { get; set; }  
  
    [DefaultValue(null)]  
    [DependsOn("Values")]  
    ActivityAction<object> Body { get; set; }   
}  
```  
  
 <span data-ttu-id="04107-118">Corpo (opcional)</span><span class="sxs-lookup"><span data-stu-id="04107-118">Body (optional)</span></span>  
 <span data-ttu-id="04107-119"><xref:System.Activities.ActivityAction> de tipo <xref:System.Object>, que é executado para cada elemento na coleção.</span><span class="sxs-lookup"><span data-stu-id="04107-119">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="04107-120">Cada elemento individual é passado no corpo através da propriedade de `Argument` .</span><span class="sxs-lookup"><span data-stu-id="04107-120">Each individual element is passed into the Body through its `Argument` property.</span></span>  
  
 <span data-ttu-id="04107-121">Valores (opcional)</span><span class="sxs-lookup"><span data-stu-id="04107-121">Values (optional)</span></span>  
 <span data-ttu-id="04107-122">A coleção de elementos que são iterados sobre.</span><span class="sxs-lookup"><span data-stu-id="04107-122">The collection of elements that are iterated over.</span></span> <span data-ttu-id="04107-123">Garantir que todos os elementos da coleção são de tipos compatíveis é feito em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="04107-123">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>  
  
## <a name="example-of-using-foreach"></a><span data-ttu-id="04107-124">Exemplo de usar ForEach</span><span class="sxs-lookup"><span data-stu-id="04107-124">Example of Using ForEach</span></span>  
 <span data-ttu-id="04107-125">O código a seguir demonstra como usar a atividade ForEach em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04107-125">The following code demonstrates how to use the ForEach activity in an application.</span></span>  
  
```  
string[] names = { "bill", "steve", "ray" };  
  
DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };  
  
Activity sampleUsage =  
    new ForEach  
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
  
|<span data-ttu-id="04107-126">Condição</span><span class="sxs-lookup"><span data-stu-id="04107-126">Condition</span></span>|<span data-ttu-id="04107-127">Mensagem</span><span class="sxs-lookup"><span data-stu-id="04107-127">Message</span></span>|<span data-ttu-id="04107-128">Severidade</span><span class="sxs-lookup"><span data-stu-id="04107-128">Severity</span></span>|<span data-ttu-id="04107-129">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="04107-129">Exception Type</span></span>|  
|---------------|-------------|--------------|--------------------|  
|<span data-ttu-id="04107-130">Os valores são `null`</span><span class="sxs-lookup"><span data-stu-id="04107-130">Values is `null`</span></span>|<span data-ttu-id="04107-131">O valor para valores de um argumento necessário de atividade “não foi fornecido.</span><span class="sxs-lookup"><span data-stu-id="04107-131">Value for a required activity argument 'Values' was not supplied.</span></span>|<span data-ttu-id="04107-132">Erro</span><span class="sxs-lookup"><span data-stu-id="04107-132">Error</span></span>|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a><span data-ttu-id="04107-133">Designer ForEach</span><span class="sxs-lookup"><span data-stu-id="04107-133">ForEach Designer</span></span>  
 <span data-ttu-id="04107-134">O designer de atividade para o exemplo é semelhante a aparência ao designer fornecido para atividades interno de <xref:System.Activities.Statements.ForEach%601> .</span><span class="sxs-lookup"><span data-stu-id="04107-134">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ForEach%601> activity.</span></span> <span data-ttu-id="04107-135">O designer aparece na caixa de ferramentas do **amostras**, **atividades não genéricas** categoria.</span><span class="sxs-lookup"><span data-stu-id="04107-135">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="04107-136">O designer é chamado **ForEachWithBodyFactory** na caixa de ferramentas, porque a atividade expõe uma <xref:System.Activities.Presentation.IActivityTemplateFactory> na caixa de ferramentas, que cria a atividade com configurada adequadamente <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="04107-136">The designer is named **ForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox, which creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>  
  
```  
public sealed class ForEachWithBodyFactory : IActivityTemplateFactory  
{  
    public Activity Create(DependencyObject target)  
    {  
        return new Microsoft.Samples.Activities.Statements.ForEach()  
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
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="04107-137">Para executar este exemplo</span><span class="sxs-lookup"><span data-stu-id="04107-137">To run this sample</span></span>  
  
1.  <span data-ttu-id="04107-138">Defina o projeto de sua escolha como o projeto inicialização de solução:</span><span class="sxs-lookup"><span data-stu-id="04107-138">Set the project of your choice as the start-up project of the solution:</span></span>  
  
    1.  <span data-ttu-id="04107-139">**CodeTestClient** mostra como usar a atividade usando código.</span><span class="sxs-lookup"><span data-stu-id="04107-139">**CodeTestClient** shows how to use the activity using code.</span></span>  
  
    2.  <span data-ttu-id="04107-140">**DesignerTestClient** mostra como usar a atividade dentro do designer.</span><span class="sxs-lookup"><span data-stu-id="04107-140">**DesignerTestClient** shows how to use the activity within the designer.</span></span>  
  
2.  <span data-ttu-id="04107-141">Compile e execute o projeto.</span><span class="sxs-lookup"><span data-stu-id="04107-141">Build and run the project.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="04107-142">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="04107-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="04107-143">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="04107-143">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="04107-144">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="04107-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="04107-145">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="04107-145">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`

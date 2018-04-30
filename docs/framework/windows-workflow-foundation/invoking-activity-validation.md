---
title: Invocando a validação de atividades
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 22bef766-c505-4fd4-ac0f-7b363b238969
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c334c13457b3e89e451f75e1ca9ea9e00aae1e21
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="invoking-activity-validation"></a><span data-ttu-id="63aab-102">Invocando a validação de atividades</span><span class="sxs-lookup"><span data-stu-id="63aab-102">Invoking Activity Validation</span></span>
<span data-ttu-id="63aab-103">Validação de atividade fornece um método para identificar e relatar erros na configuração de quaisquer atividades antes da execução.</span><span class="sxs-lookup"><span data-stu-id="63aab-103">Activity validation provides a method to identify and report errors in any activity’s configuration prior to its execution.</span></span> <span data-ttu-id="63aab-104">A validação ocorre quando um trabalho são alterados no designer de trabalho e todos os erros ou avisos de validação são exibidos no designer de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="63aab-104">Validation occurs when a workflow is modified in the workflow designer and any validation errors or warnings are displayed in the workflow designer.</span></span> <span data-ttu-id="63aab-105">Validação também ocorre em tempo de execução quando um fluxo de trabalho é chamado e se qualquer erro de validação ocorre, <xref:System.Activities.InvalidWorkflowException> é acionada pela lógica padrão de validação.</span><span class="sxs-lookup"><span data-stu-id="63aab-105">Validation also occurs at run time when a workflow is invoked and if any validation errors occur, an <xref:System.Activities.InvalidWorkflowException> is thrown by the default validation logic.</span></span> <span data-ttu-id="63aab-106">Windows Workflow Foundation (WF) fornece o <xref:System.Activities.Validation.ActivityValidationServices> classe que pode ser usada pelo aplicativo de fluxo de trabalho e os desenvolvedores de ferramentas para validar explicitamente uma atividade.</span><span class="sxs-lookup"><span data-stu-id="63aab-106">Windows Workflow Foundation (WF) provides the <xref:System.Activities.Validation.ActivityValidationServices> class that can be used by workflow application and tooling developers to explicitly validate an activity.</span></span> <span data-ttu-id="63aab-107">Este tópico descreve como usar <xref:System.Activities.Validation.ActivityValidationServices> para executar a validação de atividade.</span><span class="sxs-lookup"><span data-stu-id="63aab-107">This topic describes how to use <xref:System.Activities.Validation.ActivityValidationServices> to perform activity validation.</span></span>  
  
## <a name="using-activityvalidationservices"></a><span data-ttu-id="63aab-108">Usando ActivityValidationServices</span><span class="sxs-lookup"><span data-stu-id="63aab-108">Using ActivityValidationServices</span></span>  
 <span data-ttu-id="63aab-109"><xref:System.Activities.Validation.ActivityValidationServices> tem duas sobrecargas de <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> que são usadas para chamar a lógica de validação de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="63aab-109"><xref:System.Activities.Validation.ActivityValidationServices> has two <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> overloads that are used to invoke an activity’s validation logic.</span></span> <span data-ttu-id="63aab-110">A primeira sobrecarga toma a atividade raiz para ser validadas e retorna uma coleção de erros e avisos de validação.</span><span class="sxs-lookup"><span data-stu-id="63aab-110">The first overload takes the root activity to be validated and returns a collection of validation errors and warnings.</span></span> <span data-ttu-id="63aab-111">No exemplo a seguir, uma atividade de `Add` personalizado é usada que tem dois argumentos necessários.</span><span class="sxs-lookup"><span data-stu-id="63aab-111">In the following example, a custom `Add` activity is used that has two required arguments.</span></span>  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 <span data-ttu-id="63aab-112">A atividade de `Add` é usada dentro de <xref:System.Activities.Statements.Sequence>, mas os dois argumentos necessárias não são associados, conforme mostrado no exemplo o seguir.</span><span class="sxs-lookup"><span data-stu-id="63aab-112">The `Add` activity is used inside a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound, as shown in the following example.</span></span>  
  
```csharp  
Variable<int> Operand1 = new Variable<int>{ Default = 10 };  
Variable<int> Operand2 = new Variable<int>{ Default = 15 };  
Variable<int> Result = new Variable<int>();  
  
Activity wf = new Sequence  
{  
    Variables = { Operand1, Operand2, Result },  
    Activities =   
    {  
        new Add(),  
        new WriteLine  
        {  
            Text = new InArgument<string>(env => "The result is " + Result.Get(env))  
        }  
    }  
};  
```  
  
 <span data-ttu-id="63aab-113">Este fluxo de trabalho pode ser validado chamando <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="63aab-113">This workflow can be validated by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="63aab-114"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> retorna uma coleção de todos os erros ou avisos de validação contidos pela atividade e por quaisquer filhos, conforme mostrado no exemplo o seguir.</span><span class="sxs-lookup"><span data-stu-id="63aab-114"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> returns a collection of any validation errors or warnings contained by the activity and any children, as shown in the following example.</span></span>  
  
```csharp  
ValidationResults results = ActivityValidationServices.Validate(wf);  
  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error: {0}", error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning: {0}", warning.Message);  
    }  
}  
```  
  
 <span data-ttu-id="63aab-115">Quando <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> é chamado esse fluxo de trabalho de exemplo, dois erros de validação são retornados.</span><span class="sxs-lookup"><span data-stu-id="63aab-115">When <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> is called on this sample workflow, two validation errors are returned.</span></span>  
  
 <span data-ttu-id="63aab-116">**Erro: O valor de um argumento de atividade obrigatório 'Operando2' não foi fornecido.**</span><span class="sxs-lookup"><span data-stu-id="63aab-116">**Error: Value for a required activity argument 'Operand2' was not supplied.**</span></span>  
<span data-ttu-id="63aab-117">**Erro: O valor de um argumento de atividade obrigatório 'Operando1' não foi fornecido.**</span><span class="sxs-lookup"><span data-stu-id="63aab-117">**Error: Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="63aab-118">Se esse fluxo de trabalho foi chamado, <xref:System.Activities.InvalidWorkflowException> seria acionada, conforme mostrado no exemplo o seguir.</span><span class="sxs-lookup"><span data-stu-id="63aab-118">If this workflow was invoked, an <xref:System.Activities.InvalidWorkflowException> would be thrown, as shown in the following example.</span></span>  
  
```csharp  
try  
{  
    WorkflowInvoker.Invoke(wf);  
}  
catch (Exception ex)  
{  
    Console.WriteLine(ex);  
}  
```  
  
 <span data-ttu-id="63aab-119">**System.Activities.InvalidWorkflowException:**</span><span class="sxs-lookup"><span data-stu-id="63aab-119">**System.Activities.InvalidWorkflowException:**</span></span>  
<span data-ttu-id="63aab-120">**Os seguintes erros foram encontrados ao processar a árvore de fluxo de trabalho:** </span><span class="sxs-lookup"><span data-stu-id="63aab-120">**The following errors were encountered while processing the workflow tree:** </span></span>  
<span data-ttu-id="63aab-121">**'Add': valor de um argumento de atividade obrigatório 'Operando2' não foi fornecido.** </span><span class="sxs-lookup"><span data-stu-id="63aab-121">**'Add': Value for a required activity argument 'Operand2' was not supplied.** </span></span>  
<span data-ttu-id="63aab-122">**'Add': valor de um argumento de atividade obrigatório 'Operando1' não foi fornecido.**</span><span class="sxs-lookup"><span data-stu-id="63aab-122">**'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="63aab-123">Para que este fluxo de trabalho de exemplo é válida, os dois argumentos pré-requisito de atividade de `Add` devem ser associados.</span><span class="sxs-lookup"><span data-stu-id="63aab-123">For this example workflow to be valid, the two required arguments of the `Add` activity must be bound.</span></span> <span data-ttu-id="63aab-124">No exemplo a seguir, os dois argumentos são necessárias associados a variáveis de fluxo de trabalho juntamente com o valor de resultado.</span><span class="sxs-lookup"><span data-stu-id="63aab-124">In the following example, the two required arguments are bound to workflow variables along with the result value.</span></span> <span data-ttu-id="63aab-125">Nesse exemplo o argumento de <xref:System.Activities.Activity%601.Result%2A> está associado juntamente com os dois argumentos necessários.</span><span class="sxs-lookup"><span data-stu-id="63aab-125">In this example the <xref:System.Activities.Activity%601.Result%2A> argument is bound along with the two required arguments.</span></span> <span data-ttu-id="63aab-126">O argumento de <xref:System.Activities.Activity%601.Result%2A> não é necessário para ser associado e não causa um erro de validação se não é.</span><span class="sxs-lookup"><span data-stu-id="63aab-126">The <xref:System.Activities.Activity%601.Result%2A> argument is not required to be bound and does not cause a validation error if it is not.</span></span> <span data-ttu-id="63aab-127">É responsabilidade do autor de fluxo de trabalho associar <xref:System.Activities.Activity%601.Result%2A> se seu valor é usado em outro lugar no fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="63aab-127">It is the responsibility of the workflow author to bind <xref:System.Activities.Activity%601.Result%2A> if its value is used elsewhere in the workflow.</span></span>  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a><span data-ttu-id="63aab-128">Validando argumentos necessários na atividade raiz</span><span class="sxs-lookup"><span data-stu-id="63aab-128">Validating Required Arguments on the Root Activity</span></span>  
 <span data-ttu-id="63aab-129">Se a atividade raiz de um fluxo de trabalho tem argumentos, eles não estão associados até que o fluxo de trabalho é chamado e os parâmetros são passados para o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="63aab-129">If the root activity of a workflow has arguments, these are not bound until the workflow is invoked and parameters are passed to the workflow.</span></span> <span data-ttu-id="63aab-130">O seguinte fluxo de trabalho passa a validação, mas uma exceção é lançada se o fluxo de trabalho é chamado sem passar os argumentos necessários, conforme mostrado no exemplo o seguir.</span><span class="sxs-lookup"><span data-stu-id="63aab-130">The following workflow passes validation, but an exception is thrown if the workflow is invoked without passing in the required arguments, as shown in the following example.</span></span>  
  
```csharp  
Activity wf = new Add();  
  
ValidationResults results = ActivityValidationServices.Validate(wf);  
// results has no errors or warnings, but when the workflow  
// is invoked, an InvalidWorkflowException is thrown.  
try  
{  
    WorkflowInvoker.Invoke(wf);  
}  
catch (Exception ex)  
{  
    Console.WriteLine(ex);  
}  
```  
  
 <span data-ttu-id="63aab-131">**System. ArgumentException: Configurações do argumento da atividade raiz estão incorretas.**</span><span class="sxs-lookup"><span data-stu-id="63aab-131">**System.ArgumentException: The root activity's argument settings are incorrect.**</span></span>  
<span data-ttu-id="63aab-132">**Corrija a definição de fluxo de trabalho ou fornecer valores de entrada para corrigir estes erros:** </span><span class="sxs-lookup"><span data-stu-id="63aab-132">**Either fix the workflow definition or supply input values to fix these errors:** </span></span>  
<span data-ttu-id="63aab-133">**'Add': valor de um argumento de atividade obrigatório 'Operando2' não foi fornecido.** </span><span class="sxs-lookup"><span data-stu-id="63aab-133">**'Add': Value for a required activity argument 'Operand2' was not supplied.** </span></span>  
<span data-ttu-id="63aab-134">**'Add': valor de um argumento de atividade obrigatório 'Operando1' não foi fornecido.**</span><span class="sxs-lookup"><span data-stu-id="63aab-134">**'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="63aab-135">Após os argumentos corretos são passados, o fluxo de trabalho concluída com sucesso, conforme mostrado no exemplo o seguir.</span><span class="sxs-lookup"><span data-stu-id="63aab-135">After the correct arguments are passed, the workflow completes successfully, as shown in the following example.</span></span>  
  
```csharp  
Add wf = new Add();  
  
ValidationResults results = ActivityValidationServices.Validate(wf);  
// results has no errors or warnings, and the workflow completes  
// successfully because the required arguments were passed.  
try  
{  
    Dictionary<string, object> wfparams = new Dictionary<string, object>  
    {  
        { "Operand1", 10 },  
        { "Operand2", 15 }  
    };  
  
    int result = WorkflowInvoker.Invoke(wf, wfparams);  
    Console.WriteLine("Result: {0}", result);  
}  
catch (Exception ex)  
{  
    Console.WriteLine(ex);  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="63aab-136">Nesse exemplo, a atividade de raiz ter sido declarada como `Add` em vez de `Activity` como no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="63aab-136">In this example, the root activity was declared as `Add` instead of `Activity` as in the previous example.</span></span> <span data-ttu-id="63aab-137">Isso permite que o método de `WorkflowInvoker.Invoke` retorna um único número inteiro que representa os resultados de atividade de `Add` em vez de um dicionário de argumentos de `out` .</span><span class="sxs-lookup"><span data-stu-id="63aab-137">This allows the `WorkflowInvoker.Invoke` method to return a single integer that represents the results of the `Add` activity instead of a dictionary of `out` arguments.</span></span> <span data-ttu-id="63aab-138">`wf` variável pode também ter sido declarado como `Activity<int>`.</span><span class="sxs-lookup"><span data-stu-id="63aab-138">The variable `wf` could also have been declared as `Activity<int>`.</span></span>  
  
 <span data-ttu-id="63aab-139">Para validar argumentos de raiz, é responsabilidade do aplicativo host garantir que todos os argumentos necessários são passados quando o fluxo de trabalho é chamado.</span><span class="sxs-lookup"><span data-stu-id="63aab-139">When validating root arguments, it is the responsibility of the host application to ensure that all required arguments are passed when the workflow is invoked.</span></span>  
  
### <a name="invoking-imperative-code-based-validation"></a><span data-ttu-id="63aab-140">Invocando a validação classe base imperativa</span><span class="sxs-lookup"><span data-stu-id="63aab-140">Invoking Imperative Code-Based Validation</span></span>  
 <span data-ttu-id="63aab-141">A validação classe base imperativa fornece uma maneira simples para uma atividade fornece validação sobre se, e está disponível para as atividades que derivam de <xref:System.Activities.CodeActivity>, de <xref:System.Activities.AsyncCodeActivity>, e de <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="63aab-141">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and is available for activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="63aab-142">O código de validação que determina os erros ou avisos de validação é adicionado à atividade.</span><span class="sxs-lookup"><span data-stu-id="63aab-142">Validation code that determines any validation errors or warnings is added to the activity.</span></span> <span data-ttu-id="63aab-143">Quando a validação é chamada na atividade, esses erros ou avisos estão contidos na coleção retornada pela chamada a <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="63aab-143">When validation is invoked on the activity, these warnings or errors are contained in the collection returned by the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="63aab-144">No exemplo a seguir, retirado de [validação básica](../../../docs/framework/windows-workflow-foundation/samples/basic-validation.md) exemplo, um `CreateProduct` atividade está definida.</span><span class="sxs-lookup"><span data-stu-id="63aab-144">In the following example, taken from the [Basic Validation](../../../docs/framework/windows-workflow-foundation/samples/basic-validation.md) sample, a `CreateProduct` activity is defined.</span></span> <span data-ttu-id="63aab-145">Se `Cost` é maior do que `Price`, um erro de validação é adicionado aos metadados em uma substituição de <xref:System.Activities.CodeActivity.CacheMetadata%2A> .</span><span class="sxs-lookup"><span data-stu-id="63aab-145">If the `Cost` is greater than the `Price`, a validation error is added to the metadata in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span>  
  
```csharp  
public sealed class CreateProduct : CodeActivity  
{  
    public double Price { get; set; }  
    public double Cost { get; set; }  
  
    // [RequiredArgument] attribute will generate a validation error   
    // if the Description argument is not set.  
    [RequiredArgument]  
    public InArgument<string> Description { get; set; }  
  
    protected override void CacheMetadata(CodeActivityMetadata metadata)  
    {  
        base.CacheMetadata(metadata);  
        // Determine when the activity has been configured in an invalid way.  
        if (this.Cost > this.Price)  
        {  
            // Add a validation error with a custom message.  
            metadata.AddValidationError("The Cost must be less than or equal to the Price.");  
        }  
    }  
  
    protected override void Execute(CodeActivityContext context)  
    {  
        // Not needed for the sample.  
    }  
}  
```  
  
 <span data-ttu-id="63aab-146">Nesse exemplo, um fluxo de trabalho é configurado usando a atividade de `CreateProduct` .</span><span class="sxs-lookup"><span data-stu-id="63aab-146">In this example, a workflow is configured using the `CreateProduct` activity.</span></span> <span data-ttu-id="63aab-147">Nesse fluxo de trabalho, `Cost` é maior do que `Price`, e o argumento necessário de `Description` não está definido.</span><span class="sxs-lookup"><span data-stu-id="63aab-147">In this workflow, the `Cost` is greater than the `Price`, and the required `Description` argument is not set.</span></span> <span data-ttu-id="63aab-148">Quando a validação é chamada, os seguintes erros são retornados.</span><span class="sxs-lookup"><span data-stu-id="63aab-148">When validation is invoked, the following errors are returned.</span></span>  
  
```csharp  
Activity wf = new Sequence  
{  
    Activities =   
    {  
        new CreateProduct  
        {  
            Cost = 75.00,  
            Price = 55.00  
            // Cost > Price and required Description argument not set.  
        },  
        new WriteLine  
        {  
            Text = "Product added."  
        }  
    }  
};  
  
ValidationResults results = ActivityValidationServices.Validate(wf);  
  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error: {0}", error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning: {0}", warning.Message);  
    }  
}  
```  
  
 <span data-ttu-id="63aab-149">**Erro: O custo deve ser menor ou igual ao preço.**</span><span class="sxs-lookup"><span data-stu-id="63aab-149">**Error: The Cost must be less than or equal to the Price.**</span></span>  
<span data-ttu-id="63aab-150">**Erro: O valor de um argumento de atividade obrigatório 'Description' não foi fornecido.**</span><span class="sxs-lookup"><span data-stu-id="63aab-150">**Error: Value for a required activity argument 'Description' was not supplied.**</span></span>    
> [!NOTE]
>  <span data-ttu-id="63aab-151">Os autores de atividade personalizados podem fornecer a lógica de validação em uma substituição de <xref:System.Activities.CodeActivity.CacheMetadata%2A> de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="63aab-151">Custom activity authors can provide validation logic in an activity's <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span> <span data-ttu-id="63aab-152">Nenhuma exceções que são geradas de <xref:System.Activities.CodeActivity.CacheMetadata%2A> não são tratados como erros de validação.</span><span class="sxs-lookup"><span data-stu-id="63aab-152">Any exceptions that are thrown from <xref:System.Activities.CodeActivity.CacheMetadata%2A> are not treated as validation errors.</span></span> <span data-ttu-id="63aab-153">Essas exceções escaparão de chamada para <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> e devem ser tratadas pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="63aab-153">These exceptions will escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span>  
  
## <a name="using-validationsettings"></a><span data-ttu-id="63aab-154">Usando ValidationSettings</span><span class="sxs-lookup"><span data-stu-id="63aab-154">Using ValidationSettings</span></span>  
 <span data-ttu-id="63aab-155">Por padrão, todas as atividades na árvore de atividade são avaliadas quando a validação é chamada por <xref:System.Activities.Validation.ActivityValidationServices>.</span><span class="sxs-lookup"><span data-stu-id="63aab-155">By default, all activities in the activity tree are evaluated when validation is invoked by <xref:System.Activities.Validation.ActivityValidationServices>.</span></span> <span data-ttu-id="63aab-156"><xref:System.Activities.Validation.ValidationSettings> permite que a validação seja adequada em várias maneiras diferentes configurando as três propriedades.</span><span class="sxs-lookup"><span data-stu-id="63aab-156"><xref:System.Activities.Validation.ValidationSettings> allows the validation to be customized in several different ways by configuring its three properties.</span></span> <span data-ttu-id="63aab-157"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> especifica se o validador deve percorrer a árvore de atividade inteiro ou apenas aplicar lógica de validação à atividade fornecida.</span><span class="sxs-lookup"><span data-stu-id="63aab-157"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> specifies whether the validator should walk the entire activity tree or only apply validation logic to the supplied activity.</span></span> <span data-ttu-id="63aab-158">O padrão para este valor é `false`.</span><span class="sxs-lookup"><span data-stu-id="63aab-158">The default for this value is `false`.</span></span> <span data-ttu-id="63aab-159"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> especifica a restrição adicional que mapeia de um tipo em uma lista de restrições.</span><span class="sxs-lookup"><span data-stu-id="63aab-159"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> specifies additional constraint mapping from a type to a list of constraints.</span></span> <span data-ttu-id="63aab-160">Para o tipo de base de cada atividade na árvore de atividade que está sendo validada há uma pesquisa em <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span><span class="sxs-lookup"><span data-stu-id="63aab-160">For the base type of each activity in the activity tree being validated there is a lookup into <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="63aab-161">Se uma lista de restrição correspondente for encontrada, todas as restrições na lista são avaliadas para atividades.</span><span class="sxs-lookup"><span data-stu-id="63aab-161">If a matching constraint list is found, all constraints in the list are evaluated for the activity.</span></span> <span data-ttu-id="63aab-162"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> especifica se o validador deve avaliar todas as restrições ou somente aquelas especificadas em <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span><span class="sxs-lookup"><span data-stu-id="63aab-162"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> specifies whether the validator should evaluate all constraints or only those specified in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="63aab-163">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="63aab-163">The default value is `false`.</span></span> <span data-ttu-id="63aab-164"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> e <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> são úteis para que os autores de host de fluxo de trabalho adicionar validação adicional para fluxos de trabalho, como restrições de política para ferramentas como o FxCop.</span><span class="sxs-lookup"><span data-stu-id="63aab-164"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> and <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> are useful for workflow host authors to add additional validation for workflows, such as policy constraints for tools such as FxCop.</span></span> <span data-ttu-id="63aab-165">Para obter mais informações sobre restrições, consulte [restrições declarativas](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="63aab-165">For more information about constraints, see [Declarative Constraints](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md).</span></span>  
  
 <span data-ttu-id="63aab-166">Para usar <xref:System.Activities.Validation.ValidationSettings>, configurar as propriedades desejadas, e passá-las na chamada ao <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="63aab-166">To use <xref:System.Activities.Validation.ValidationSettings>, configure the desired properties, and then pass it in the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="63aab-167">Nesse exemplo, um fluxo de trabalho que consiste <xref:System.Activities.Statements.Sequence> com uma atividade de `Add` personalizado é validado.</span><span class="sxs-lookup"><span data-stu-id="63aab-167">In this example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> with a custom `Add` activity is validated.</span></span> <span data-ttu-id="63aab-168">A atividade de `Add` tem dois argumentos necessários.</span><span class="sxs-lookup"><span data-stu-id="63aab-168">The `Add` activity has two required arguments.</span></span>  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 <span data-ttu-id="63aab-169">A seguir atividade de `Add` é usada em <xref:System.Activities.Statements.Sequence>, mas os dois argumentos necessárias não são associados.</span><span class="sxs-lookup"><span data-stu-id="63aab-169">The following `Add` activity is used in a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound.</span></span>  
  
```csharp  
Variable<int> Operand1 = new Variable<int> { Default = 10 };  
Variable<int> Operand2 = new Variable<int> { Default = 15 };  
Variable<int> Result = new Variable<int>();  
  
Activity wf = new Sequence  
{  
    Variables = { Operand1, Operand2, Result },  
    Activities =   
    {  
        new Add(),  
        new WriteLine  
        {  
            Text = new InArgument<string>(env => "The result is " + Result.Get(env))  
        }  
    }  
};  
```  
  
 <span data-ttu-id="63aab-170">Para o exemplo a seguir, a validação é executada com <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> definido como `true`, portanto somente a atividade de <xref:System.Activities.Statements.Sequence> raiz é validada.</span><span class="sxs-lookup"><span data-stu-id="63aab-170">For the following example, validation is performed with <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> set to `true`, so only the root <xref:System.Activities.Statements.Sequence> activity is validated.</span></span>  
  
```csharp  
ValidationSettings settings = new ValidationSettings  
{  
    SingleLevel = true  
};  
  
ValidationResults results = ActivityValidationServices.Validate(wf, settings);  
  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error: {0}", error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning: {0}", warning.Message);  
    }  
}  
```  
  
 <span data-ttu-id="63aab-171">Este código exibe a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="63aab-171">This code displays the following output:</span></span>  
  
 <span data-ttu-id="63aab-172">**Nenhum aviso ou erro** , embora o `Add` atividade exigiu argumentos que não estão associados, a validação for bem-sucedida, porque somente a atividade raiz é avaliada.</span><span class="sxs-lookup"><span data-stu-id="63aab-172">**No warnings or errors** Even though the `Add` activity has required arguments that are not bound, validation is successful because only the root activity is evaluated.</span></span> <span data-ttu-id="63aab-173">Esse tipo de validação é útil para validar somente os elementos específicos em uma árvore de atividade, como validação de uma alteração de propriedade de uma única atividade em um designer.</span><span class="sxs-lookup"><span data-stu-id="63aab-173">This type of validation is useful for validating only specific elements in an activity tree, such as validation of a property change of a single activity in a designer.</span></span> <span data-ttu-id="63aab-174">Observe que se esse fluxo de trabalho é chamado, a validação completa configurado no fluxo de trabalho é avaliado e <xref:System.Activities.InvalidWorkflowException> será lançada.</span><span class="sxs-lookup"><span data-stu-id="63aab-174">Note that if this workflow is invoked, the full validation configured in the workflow is evaluated and an <xref:System.Activities.InvalidWorkflowException> would be thrown.</span></span> <span data-ttu-id="63aab-175"><xref:System.Activities.Validation.ActivityValidationServices> e configurar <xref:System.Activities.Validation.ValidationSettings> somente validação chamada explicitamente pelo host, e não a validação que ocorre quando um fluxo de trabalho é chamado.</span><span class="sxs-lookup"><span data-stu-id="63aab-175"><xref:System.Activities.Validation.ActivityValidationServices> and <xref:System.Activities.Validation.ValidationSettings> configure only validation explicitly invoked by the host, and not the validation that occurs when a workflow is invoked.</span></span>

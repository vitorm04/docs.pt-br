---
title: Validação classe base imperativa
ms.date: 03/30/2017
ms.assetid: ae12537c-455e-42b1-82f4-cea4c46c023e
ms.openlocfilehash: ac77132e3469bdffa6f88f8c6d617c6faa1c9323
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2018
ms.locfileid: "49308286"
---
# <a name="imperative-code-based-validation"></a><span data-ttu-id="16f97-102">Validação classe base imperativa</span><span class="sxs-lookup"><span data-stu-id="16f97-102">Imperative Code-Based Validation</span></span>

<span data-ttu-id="16f97-103">A validação classe base imperativa fornece uma maneira simples para uma atividade fornece validação sobre se, e está disponível para as atividades que derivam de <xref:System.Activities.CodeActivity>, de <xref:System.Activities.AsyncCodeActivity>, e de <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="16f97-103">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and is available for activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="16f97-104">O código de validação que determina os erros ou avisos de validação é adicionado à atividade.</span><span class="sxs-lookup"><span data-stu-id="16f97-104">Validation code that determines any validation errors or warnings is added to the activity.</span></span>  
  
## <a name="using-code-based-validation"></a><span data-ttu-id="16f97-105">Usando a validação classe base</span><span class="sxs-lookup"><span data-stu-id="16f97-105">Using Code-Based Validation</span></span>

<span data-ttu-id="16f97-106">a validação classe base é suportada por atividades que derivam de <xref:System.Activities.CodeActivity>, de <xref:System.Activities.AsyncCodeActivity>, e de <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="16f97-106">Code-based validation is supported by activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="16f97-107">O código de validação pode ser colocado em uma substituição de <xref:System.Activities.CodeActivity.CacheMetadata%2A> , e os erros ou avisos de validação podem ser adicionados ao argumento de metadados.</span><span class="sxs-lookup"><span data-stu-id="16f97-107">Validation code can be placed in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override, and validation errors or warnings can be added to the metadata argument.</span></span> <span data-ttu-id="16f97-108">No exemplo a seguir, se o `Cost` é maior que o `Price`, um erro de validação é adicionado aos metadados.</span><span class="sxs-lookup"><span data-stu-id="16f97-108">In the following example, if the `Cost` is greater than the `Price`, a validation error is added to the metadata.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="16f97-109">Observe que `Cost` e `Price` não são argumentos a atividade, mas é propriedades que são definidas em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="16f97-109">Note that `Cost` and `Price` are not arguments to the activity, but are properties that are set at design time.</span></span> <span data-ttu-id="16f97-110">É por isso que seus valores podem ser validados em uma substituição de <xref:System.Activities.CodeActivity.CacheMetadata%2A> .</span><span class="sxs-lookup"><span data-stu-id="16f97-110">That is why their values can be validated in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span> <span data-ttu-id="16f97-111">O valor dos dados que correm através de um argumento não pode ser validado em tempo de design porque os dados não usam até o tempo de execução, mas os argumentos de atividade podem ser validados para garantir que estão associados usando os grupos de atributo e a sobrecarga de `RequiredArgument` .</span><span class="sxs-lookup"><span data-stu-id="16f97-111">The value of the data flowing through an argument cannot be validated at design time because the data does not flow until run time, but activity arguments can be validated to ensure that they are bound by using the `RequiredArgument` attribute and overload groups.</span></span> <span data-ttu-id="16f97-112">Esse código de exemplo considera o atributo de `RequiredArgument` para o argumento de `Description` , e se não está associado em um erro de validação é gerado.</span><span class="sxs-lookup"><span data-stu-id="16f97-112">This example code sees the `RequiredArgument` attribute for the `Description` argument, and if it is not bound then a validation error is generated.</span></span> <span data-ttu-id="16f97-113">Os argumentos necessários são abordados [argumentos necessários e grupos de sobrecarga](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md).</span><span class="sxs-lookup"><span data-stu-id="16f97-113">Required arguments are covered in [Required Arguments and Overload Groups](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md).</span></span>  
  
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
  
 <span data-ttu-id="16f97-114">Por padrão, um erro de validação é adicionado aos metadados quando <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> é chamado.</span><span class="sxs-lookup"><span data-stu-id="16f97-114">By default, a validation error is added to the metadata when <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> is called.</span></span> <span data-ttu-id="16f97-115">Para adicionar um aviso de validação, use a sobrecarga de <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> que leva <xref:System.Activities.Validation.ValidationError>, e especifica que <xref:System.Activities.Validation.ValidationError> representa um aviso definindo a propriedade de <xref:System.Activities.Validation.ValidationError.IsWarning%2A> .</span><span class="sxs-lookup"><span data-stu-id="16f97-115">To add a validation warning, use the <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> overload that takes a <xref:System.Activities.Validation.ValidationError>, and specify that the <xref:System.Activities.Validation.ValidationError> represents a warning by setting the <xref:System.Activities.Validation.ValidationError.IsWarning%2A> property.</span></span>  
  
 <span data-ttu-id="16f97-116">A validação ocorre quando um trabalho são alterados no designer de trabalho e todos os erros ou avisos de validação são exibidos no designer de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="16f97-116">Validation occurs when a workflow is modified in the workflow designer and any validation errors or warnings are displayed in the workflow designer.</span></span> <span data-ttu-id="16f97-117">Validação também ocorre em tempo de execução quando um fluxo de trabalho é chamado e se qualquer erro de validação ocorre, <xref:System.Activities.InvalidWorkflowException> é acionada pela lógica padrão de validação.</span><span class="sxs-lookup"><span data-stu-id="16f97-117">Validation also occurs at run time when a workflow is invoked and if any validation errors occur, an <xref:System.Activities.InvalidWorkflowException> is thrown by the default validation logic.</span></span> <span data-ttu-id="16f97-118">Para obter mais informações sobre como invocar a validação e acessar quaisquer erros ou avisos de validação, consulte [invocando a validação de atividade](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="16f97-118">For more information about invoking validation and accessing any validation warnings or errors, see [Invoking Activity Validation](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).</span></span>  
  
 <span data-ttu-id="16f97-119">Nenhuma exceções que são geradas de <xref:System.Activities.CodeActivity.CacheMetadata%2A> não são tratados como erros de validação.</span><span class="sxs-lookup"><span data-stu-id="16f97-119">Any exceptions that are thrown from <xref:System.Activities.CodeActivity.CacheMetadata%2A> are not treated as validation errors.</span></span> <span data-ttu-id="16f97-120">Essas exceções escaparão de chamada para <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> e devem ser tratadas pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="16f97-120">These exceptions will escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span>  
  
 <span data-ttu-id="16f97-121">a validação classe base é útil para validar a atividade que contém o código, mas não tem a visibilidade nas outras atividades no fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="16f97-121">Code-based validation is useful for validating the activity that contains the code, but it does not have visibility into the other activities in the workflow.</span></span> <span data-ttu-id="16f97-122">Validação declarativamente restrições fornece a capacidade de validar as relações entre uma atividade e outras atividades no fluxo de trabalho e é abordada a [restrições declarativas](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="16f97-122">Declarative constraints validation provides the ability to validate the relationships between an activity and other activities in the workflow, and is covered in the [Declarative Constraints](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md) topic.</span></span>

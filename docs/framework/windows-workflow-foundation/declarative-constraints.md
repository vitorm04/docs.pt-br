---
title: Restrições declarativas
ms.date: 03/30/2017
ms.assetid: 67001ed1-7f4d-4ada-ae57-a31176901a53
ms.openlocfilehash: e3ced8f6f88d698273ace5c8b74fe90b94fa9720
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945815"
---
# <a name="declarative-constraints"></a><span data-ttu-id="c805d-102">Restrições declarativas</span><span class="sxs-lookup"><span data-stu-id="c805d-102">Declarative Constraints</span></span>
<span data-ttu-id="c805d-103">As restrições declarativas fornecem um método poderoso de validação para uma atividade e suas relações com outras atividades.</span><span class="sxs-lookup"><span data-stu-id="c805d-103">Declarative constraints provide a powerful method of validation for an activity and its relationships with other activities.</span></span> <span data-ttu-id="c805d-104">As restrições são configuradas para uma atividade durante o processo de design, mas as restrições adicionais podem também ser especificadas pelo host de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c805d-104">Constraints are configured for an activity during the authoring process, but additional constraints can also be specified by the workflow host.</span></span> <span data-ttu-id="c805d-105">Este tópico fornece uma visão geral do uso de restrições declarativas para fornecer validação de atividade.</span><span class="sxs-lookup"><span data-stu-id="c805d-105">This topic provides an overview of using declarative constraints to provide activity validation.</span></span>  
  
## <a name="using-declarative-constraints"></a><span data-ttu-id="c805d-106">Usando restrições declarativas</span><span class="sxs-lookup"><span data-stu-id="c805d-106">Using Declarative Constraints</span></span>  
 <span data-ttu-id="c805d-107">Uma restrição é uma atividade que contém a lógica de validação.</span><span class="sxs-lookup"><span data-stu-id="c805d-107">A constraint is an activity that contains validation logic.</span></span> <span data-ttu-id="c805d-108">Esta atividade de restrição pode ser criada no código ou em XAML.</span><span class="sxs-lookup"><span data-stu-id="c805d-108">This constraint activity can be authored in code or in XAML.</span></span> <span data-ttu-id="c805d-109">Depois que uma atividade de restrição é criada, os autores de atividade adicionam esta restrição à propriedade de <xref:System.Activities.Activity.Constraints%2A> de atividade para validar, ou usam a restrição para fornecer validação adicionais usando a propriedade de <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> de uma instância de <xref:System.Activities.Validation.ValidationSettings> .</span><span class="sxs-lookup"><span data-stu-id="c805d-109">After a constraint activity is created, activity authors add this constraint to the <xref:System.Activities.Activity.Constraints%2A> property of the activity to validate, or they use the constraint to provide additional validation by using the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> property of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="c805d-110">A lógica de validação pode consistir de validações simples como validar os metadados de uma atividade, mas também pode executar a validação que leva em consideração a relação de atividade atual para seus pais, filhos, e atividades irmãos.</span><span class="sxs-lookup"><span data-stu-id="c805d-110">The validation logic can consist of simple validations such as validating an activity’s metadata, but it can also perform validation that takes into account the relationship of the current activity to its parent, children, and sibling activities.</span></span> <span data-ttu-id="c805d-111">As restrições são criadas usando a atividade de <xref:System.Activities.Validation.Constraint%601> , e várias atividades de validação adicionais são fornecidas para auxiliar na criação de erros e avisos de validação e fornecer informações sobre atividades relacionadas no fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c805d-111">Constraints are authored by using the <xref:System.Activities.Validation.Constraint%601> activity, and several additional validation activities are provided to assist with the creation of validation errors and warnings and to provide information about related activities in the workflow.</span></span>  
  
### <a name="assertvalidation-and-addvalidationerror"></a><span data-ttu-id="c805d-112">AssertValidation e AddValidationError</span><span class="sxs-lookup"><span data-stu-id="c805d-112">AssertValidation and AddValidationError</span></span>  
 <span data-ttu-id="c805d-113">A atividade de <xref:System.Activities.Validation.AssertValidation> avalia a expressão referenciada por sua propriedade de <xref:System.Activities.Validation.AssertValidation.Assertion%2A> , e se a expressão avaliada como `false`, um erro de validação ou aviso é adicionado a <xref:System.Activities.Validation.ValidationResults>.</span><span class="sxs-lookup"><span data-stu-id="c805d-113">The <xref:System.Activities.Validation.AssertValidation> activity evaluates the expression referenced by its <xref:System.Activities.Validation.AssertValidation.Assertion%2A> property, and if the expression evaluates to `false`, a validation error or warning is added to the <xref:System.Activities.Validation.ValidationResults>.</span></span> <span data-ttu-id="c805d-114">A propriedade de <xref:System.Activities.Validation.AssertValidation.Message%2A> descreve o erro de validação e a propriedade <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> indica se a falha de validação é um erro ou um aviso.</span><span class="sxs-lookup"><span data-stu-id="c805d-114">The <xref:System.Activities.Validation.AssertValidation.Message%2A> property describes the validation error and the <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> property indicates whether the validation failure is an error or a warning.</span></span> <span data-ttu-id="c805d-115">O valor padrão para <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> é `false`.</span><span class="sxs-lookup"><span data-stu-id="c805d-115">The default value for <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> is `false`.</span></span>  
  
 <span data-ttu-id="c805d-116">No exemplo a seguir, uma restrição é declarada que retorna um aviso de validação se <xref:System.Activities.Activity.DisplayName%2A> atividade estão sendo validada é dois caracteres ou menos de tamanho.</span><span class="sxs-lookup"><span data-stu-id="c805d-116">In the following example, a constraint is declared that returns a validation warning if the <xref:System.Activities.Activity.DisplayName%2A> of the activity being validated is two characters or less in length.</span></span> <span data-ttu-id="c805d-117">O parâmetro de tipo genérico usado para <xref:System.Activities.Validation.Constraint%601> especifica o tipo de atividade que é validada pela restrição.</span><span class="sxs-lookup"><span data-stu-id="c805d-117">The generic type parameter used for <xref:System.Activities.Validation.Constraint%601> specifies the type of activity that is validated by the constraint.</span></span> <span data-ttu-id="c805d-118">Esta restrição usa <xref:System.Activities.Activity> como o tipo genérico e pode ser usada para validar todos os tipos de atividades.</span><span class="sxs-lookup"><span data-stu-id="c805d-118">This constraint uses <xref:System.Activities.Activity> as the generic type and can be used to validate all types of activities.</span></span>  
  
```csharp  
public static Constraint ActivityDisplayNameIsNotSetWarning()  
{  
    DelegateInArgument<Activity> element = new DelegateInArgument<Activity>();  
  
    return new Constraint<Activity>  
    {  
        Body = new ActivityAction<Activity, ValidationContext>  
        {  
            Argument1 = element,  
            Handler = new AssertValidation  
            {  
                IsWarning = true,  
                Assertion = new InArgument<bool>(env => (element.Get(env).DisplayName.Length > 2)),  
                Message = new InArgument<string>("It is a best practice to have a DisplayName of more than 2 characters."),  
            }  
        }  
    };  
}  
```  
  
 <span data-ttu-id="c805d-119">Para especificar esta restrição para uma atividade, é adicionada a <xref:System.Activities.Activity.Constraints%2A> de atividade, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c805d-119">To specify this constraint for an activity, it is added to the <xref:System.Activities.Activity.Constraints%2A> of the activity, as shown in the following example code.</span></span>  
  
```csharp  
public sealed class SampleActivity : CodeActivity  
{  
    public SampleActivity()  
    {  
        base.Constraints.Add(ActivityDisplayNameIsNotSetWarning());  
    }  
  
    // Activity implementation omitted.  
}  
```  
  
 <span data-ttu-id="c805d-120">O host também pode especificar esta restrição para atividades em um fluxo de trabalho usando <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, que é abordado na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="c805d-120">The host could also specify this constraint for activities in a workflow by using <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, which is covered in the next section.</span></span>  
  
 <span data-ttu-id="c805d-121">A atividade de <xref:System.Activities.Validation.AddValidationError> é usada para gerar um erro ou um aviso de validação sem exigir a avaliação de uma expressão.</span><span class="sxs-lookup"><span data-stu-id="c805d-121">The <xref:System.Activities.Validation.AddValidationError> activity is used to generate a validation error or warning without requiring the evaluation of an expression.</span></span> <span data-ttu-id="c805d-122">Suas propriedades são semelhantes a <xref:System.Activities.Validation.AssertValidation> e pode ser usado em conjunto com atividades de controle de fluxo de uma restrição como a atividade de <xref:System.Activities.Statements.If> .</span><span class="sxs-lookup"><span data-stu-id="c805d-122">Its properties are similar to <xref:System.Activities.Validation.AssertValidation> and it can be used in conjunction with flow control activities of a constraint such as the <xref:System.Activities.Statements.If> activity.</span></span>
  
### <a name="workflow-relationship-activities"></a><span data-ttu-id="c805d-123">Atividades de relação de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c805d-123">Workflow Relationship Activities</span></span>

<span data-ttu-id="c805d-124">Várias atividades de validação estão disponíveis que fornecem informações sobre as outras atividades no fluxo de trabalho com relação a atividade que está sendo validada.</span><span class="sxs-lookup"><span data-stu-id="c805d-124">Several validation activities are available that provide information about the other activities in the workflow in relation to the activity being validated.</span></span> <span data-ttu-id="c805d-125"><xref:System.Activities.Validation.GetParentChain> retorna uma coleção de atividades que contém todas as atividades entre a atividade atual e a atividade de raiz.</span><span class="sxs-lookup"><span data-stu-id="c805d-125"><xref:System.Activities.Validation.GetParentChain> returns a collection of activities that contains all of the activities between the current activity and the root activity.</span></span> <span data-ttu-id="c805d-126"><xref:System.Activities.Validation.GetChildSubtree> fornece uma coleção de atividades que contém as atividades filho em um padrão recursiva, e <xref:System.Activities.Validation.GetWorkflowTree> obtém todas as atividades no fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c805d-126"><xref:System.Activities.Validation.GetChildSubtree> provides a collection of activities that contains the child activities in a recursive pattern, and <xref:System.Activities.Validation.GetWorkflowTree> gets all the activities in the workflow.</span></span>  
  
<span data-ttu-id="c805d-127">No exemplo a seguir, uma atividade de `CreateState` é definida.</span><span class="sxs-lookup"><span data-stu-id="c805d-127">In the following example, a `CreateState` activity is defined.</span></span> <span data-ttu-id="c805d-128">A atividade de `CreateState` deve estar contido dentro de uma atividade de `CreateCountry` , e o método de `GetParent` retorna uma restrição que impõe esse requisito.</span><span class="sxs-lookup"><span data-stu-id="c805d-128">The `CreateState` activity must be contained within a `CreateCountry` activity, and the `GetParent` method returns a constraint that enforces this requirement.</span></span> <span data-ttu-id="c805d-129">`GetParent` usa a atividade de <xref:System.Activities.Validation.GetParentChain> em conjunto com uma atividade de <xref:System.Activities.Statements.ForEach%601> verificar as atividades pai de atividade de `CreateState` para determinar se o requisito é atingido.</span><span class="sxs-lookup"><span data-stu-id="c805d-129">`GetParent` uses the <xref:System.Activities.Validation.GetParentChain> activity in conjunction with a <xref:System.Activities.Statements.ForEach%601> activity to inspect the parent activities of the `CreateState` activity to determine if the requirement is met.</span></span>  
  
```csharp  
public sealed class CreateState : CodeActivity  
{  
    public CreateState()  
    {  
        base.Constraints.Add(CheckParent());  
        this.Cities = new List<Activity>();              
    }  
  
    public List<Activity> Cities { get; set; }  
  
    public string Name { get; set; }    
  
    static Constraint CheckParent()  
    {  
        DelegateInArgument<CreateState> element = new DelegateInArgument<CreateState>();  
        DelegateInArgument<ValidationContext> context = new DelegateInArgument<ValidationContext>();                          
        Variable<bool> result = new Variable<bool>();  
        DelegateInArgument<Activity> parent = new DelegateInArgument<Activity>();  
  
        return new Constraint<CreateState>  
        {                                     
            Body = new ActivityAction<CreateState,ValidationContext>  
            {                      
                Argument1 = element,  
                Argument2 = context,  
                Handler = new Sequence  
                {  
                    Variables =  
                    {  
                        result   
                    },  
                    Activities =  
                    {  
                        new ForEach<Activity>  
                        {                                  
                            Values = new GetParentChain  
                            {  
                                ValidationContext = context                                      
                            },  
                            Body = new ActivityAction<Activity>  
                            {     
                                Argument = parent,   
                                Handler = new If()  
                                {                                            
                                    Condition = new InArgument<bool>((env) => object.Equals(parent.Get(env).GetType(),typeof(CreateCountry))),                                          
                                    Then = new Assign<bool>  
                                    {  
                                        Value = true,  
                                        To = result  
                                    }  
                                }  
                            }                                  
                        },  
                        new AssertValidation  
                        {  
                            Assertion = new InArgument<bool>(result),  
                            Message = new InArgument<string> ("CreateState has to be inside a CreateCountry activity"),                                                                  
                        }  
                    }  
                }  
            }  
        };  
    }  
  
    protected override void Execute(CodeActivityContext context)  
    {  
        // not needed for the sample  
    }  
}  
```
  
## <a name="additional-constraints"></a><span data-ttu-id="c805d-130">Restrições adicionais</span><span class="sxs-lookup"><span data-stu-id="c805d-130">Additional Constraints</span></span>  
 <span data-ttu-id="c805d-131">Os autores de host de fluxo de trabalho podem especificar restrições adicionais de validação para atividades em um fluxo de trabalho criando as restrições e adicionando ao dicionário de <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> de uma instância de <xref:System.Activities.Validation.ValidationSettings> .</span><span class="sxs-lookup"><span data-stu-id="c805d-131">Workflow host authors can specify additional validation constraints for activities in a workflow by creating constraints and adding them to the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> dictionary of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="c805d-132">Cada item em <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> contém o tipo de atividade para que as restrições se aplicam e uma lista de restrições adicionais para esse tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="c805d-132">Each item in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> contains the type of activity for which the constraints apply and a list of the additional constraints for that type of activity.</span></span> <span data-ttu-id="c805d-133">Quando a validação é chamada para o fluxo de trabalho, cada atividade do tipo especificado, incluindo classes derivadas, avalia as restrições.</span><span class="sxs-lookup"><span data-stu-id="c805d-133">When validation is invoked for the workflow, each activity of the specified type, including derived classes, evaluates the constraints.</span></span> <span data-ttu-id="c805d-134">Nesse exemplo, a restrição de `ActivityDisplayNameIsNotSetWarning` a seção anterior é aplicado a todas as atividades em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c805d-134">In this example, the `ActivityDisplayNameIsNotSetWarning` constraint from the previous section is applied to all activities in a workflow.</span></span>  
  
```csharp  
Activity wf = new Sequence  
{  
    // Workflow Details Omitted.  
};  
  
ValidationSettings settings = new ValidationSettings()  
{  
  
    AdditionalConstraints =  
    {  
        {typeof(Activity), new List<Constraint> {ActivityDisplayNameIsNotSetWarning()}},       
    }  
};  
  
// Validate the workflow.  
ValidationResults results = ActivityValidationServices.Validate(wf, settings);  
  
// Evaluate the results.  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error in " + error.Source.DisplayName + ": " + error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning in " + warning.Source.DisplayName + ": " + warning.Message);  
    }  
}  
```  
  
 <span data-ttu-id="c805d-135">Se a propriedade de <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> de <xref:System.Activities.Validation.ValidationSettings> é `true`, então somente as restrições adicionais especificadas são avaliadas quando a validação é chamada chamando o <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="c805d-135">If the <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> property of <xref:System.Activities.Validation.ValidationSettings> is `true`, then only the specified additional constraints are evaluated when validation is invoked by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="c805d-136">Isso pode ser útil para inspecionar fluxos de trabalho para configurações específicas de validação.</span><span class="sxs-lookup"><span data-stu-id="c805d-136">This can be useful for inspecting workflows for specific validation configurations.</span></span> <span data-ttu-id="c805d-137">Observe entretanto que quando o fluxo de trabalho é chamado, a lógica de validação configurou no fluxo de trabalho é avaliado e deve passar para o fluxo de trabalho inicia com êxito.</span><span class="sxs-lookup"><span data-stu-id="c805d-137">Note however that when the workflow is invoked, the validation logic configured in the workflow is evaluated and must pass for the workflow to successfully begin.</span></span> <span data-ttu-id="c805d-138">Para obter mais informações sobre como invocar a validação, consulte [invocando a validação de atividade](invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="c805d-138">For more information about invoking validation, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>

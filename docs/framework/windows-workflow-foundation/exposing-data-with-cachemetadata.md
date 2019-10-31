---
title: Expõem dados com CacheMetadata
ms.date: 03/30/2017
ms.assetid: 34832f23-e93b-40e6-a80b-606a855a00d9
ms.openlocfilehash: a044c896e56541ee954fc33853376eb8293c6ede
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945698"
---
# <a name="exposing-data-with-cachemetadata"></a><span data-ttu-id="5c2ec-102">Expõem dados com CacheMetadata</span><span class="sxs-lookup"><span data-stu-id="5c2ec-102">Exposing data with CacheMetadata</span></span>

<span data-ttu-id="5c2ec-103">Antes de executar uma atividade, o tempo de execução de fluxo de trabalho obtém qualquer informação sobre a atividade que precisa para manter sua execução.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-103">Before executing an activity, the workflow runtime obtains all of the information about the activity that it needs in order to maintain its execution.</span></span> <span data-ttu-id="5c2ec-104">O tempo de execução de fluxo de trabalho obtém essas informações durante a execução do método de <xref:System.Activities.Activity.CacheMetadata%2A> .</span><span class="sxs-lookup"><span data-stu-id="5c2ec-104">The workflow runtime gets this information during the execution of the <xref:System.Activities.Activity.CacheMetadata%2A> method.</span></span> <span data-ttu-id="5c2ec-105">A implementação padrão desse método oferece o tempo de execução com todos os argumentos públicos, variáveis, e atividades filhos exposto pela atividade é então executada; se a atividade precisará fornecer mais informações em tempo de execução desta (como membros particulares, ou atividades a ser agendadas pela atividade), esse método pode ser substituído para oferece.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-105">The default implementation of this method provides the runtime with all of the public arguments, variables, and child activities exposed by the activity at the time it is executed; if the activity needs to give more information to the runtime than this (such as private members, or activities to be scheduled by the activity), this method can be overridden to provide it.</span></span>

## <a name="default-cachemetadata-behavior"></a><span data-ttu-id="5c2ec-106">Comportamento padrão de CacheMetadata</span><span class="sxs-lookup"><span data-stu-id="5c2ec-106">Default CacheMetadata behavior</span></span>

<span data-ttu-id="5c2ec-107">A implementação padrão de <xref:System.Activities.NativeActivity.CacheMetadata%2A> para as atividades que derivam de <xref:System.Activities.NativeActivity> processa os tipos de seguinte método das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="5c2ec-107">The default implementation of <xref:System.Activities.NativeActivity.CacheMetadata%2A> for activities that derive from <xref:System.Activities.NativeActivity> processes the following method types in the following ways:</span></span>

- <span data-ttu-id="5c2ec-108"><xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, ou <xref:System.Activities.InOutArgument%601> (argumentos genéricos): Esses argumentos são expostos no tempo de execução como argumentos com um nome e tipo iguais ao tipo e o nome de propriedade exposta, a direção do argumento apropriado e alguns dados de validação.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-108"><xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, or <xref:System.Activities.InOutArgument%601> (generic arguments): These arguments are exposed to the runtime as arguments with a name and type equal to the exposed property name and type, the appropriate argument direction, and some validation data.</span></span>

- <span data-ttu-id="5c2ec-109"><xref:System.Activities.Variable> ou alguma subclasse disso: Esses membros são expostos no tempo de execução como variáveis públicas.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-109"><xref:System.Activities.Variable> or any subclass thereof: These members are exposed to the runtime as public variables.</span></span>

- <span data-ttu-id="5c2ec-110"><xref:System.Activities.Activity> ou alguma subclasse disso: Esses membros são expostos no tempo de execução como atividades filhos públicas.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-110"><xref:System.Activities.Activity> or any subclass thereof: These members are exposed to the runtime as public child activities.</span></span> <span data-ttu-id="5c2ec-111">O comportamento padrão pode ser implementado explicitamente chamando <xref:System.Activities.ActivityMetadata.AddImportedChild%2A>, passando a atividade filho.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-111">The default behavior can be implemented explicitly by calling <xref:System.Activities.ActivityMetadata.AddImportedChild%2A>, passing in the child activity.</span></span>

- <span data-ttu-id="5c2ec-112"><xref:System.Activities.ActivityDelegate> ou alguma subclasse disso: Esses membros são expostos no tempo de execução como representantes públicos.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-112"><xref:System.Activities.ActivityDelegate> or any subclass thereof: These members are exposed to the runtime as public delegates.</span></span>

- <span data-ttu-id="5c2ec-113"><xref:System.Collections.ICollection> do tipo <xref:System.Activities.Variable>: Todos os elementos na coleção são expostos no tempo de execução como variáveis públicas.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-113"><xref:System.Collections.ICollection> of type <xref:System.Activities.Variable>: All elements in the collection are exposed to the runtime as public variables.</span></span>

- <span data-ttu-id="5c2ec-114"><xref:System.Collections.ICollection> do tipo <xref:System.Activities.Activity>: Todos os elementos na coleção são expostos no tempo de execução como filhos públicos.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-114"><xref:System.Collections.ICollection> of type <xref:System.Activities.Activity>: All elements in the collection are exposed to the runtime as public children.</span></span>

- <span data-ttu-id="5c2ec-115"><xref:System.Collections.ICollection> do tipo <xref:System.Activities.ActivityDelegate>: Todos os elementos na coleção são expostos no tempo de execução como representantes públicos.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-115"><xref:System.Collections.ICollection> of type <xref:System.Activities.ActivityDelegate>: All elements in the collection are exposed to the runtime as public delegates.</span></span>

<span data-ttu-id="5c2ec-116"><xref:System.Activities.Activity.CacheMetadata%2A> para as atividades que derivam de <xref:System.Activities.Activity>, <xref:System.Workflow.Activities.CodeActivity>, e <xref:System.Activities.AsyncCodeActivity> também funcionam como anterior, exceto as seguintes diferenças:</span><span class="sxs-lookup"><span data-stu-id="5c2ec-116">The <xref:System.Activities.Activity.CacheMetadata%2A> for activities that derive from <xref:System.Activities.Activity>, <xref:System.Workflow.Activities.CodeActivity>, and <xref:System.Activities.AsyncCodeActivity> also function as above, except for the following differences:</span></span>

- <span data-ttu-id="5c2ec-117">As classes que derivam de <xref:System.Activities.Activity> não pode agendar atividades filho ou representantes, para que esses membros são expostos como filhos e delegados importados;</span><span class="sxs-lookup"><span data-stu-id="5c2ec-117">Classes that derive from <xref:System.Activities.Activity> cannot schedule child activities or delegates, so such members are exposed as imported children and delegates; the</span></span>

- <span data-ttu-id="5c2ec-118">As classes que derivam de <xref:System.Activities.CodeActivity> e <xref:System.Activities.AsyncCodeActivity> não suporta variáveis, filhos, ou representantes, portanto somente argumentos serão expostas.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-118">Classes that derive from <xref:System.Activities.CodeActivity> and <xref:System.Activities.AsyncCodeActivity> do not support variables, children, or delegates, so only arguments will be exposed.</span></span>

## <a name="overriding-cachemetadata-to-provide-information-to-the-runtime"></a><span data-ttu-id="5c2ec-119">Substituindo CacheMetadata para fornecer informações em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="5c2ec-119">Overriding CacheMetadata to provide information to the runtime</span></span>

<span data-ttu-id="5c2ec-120">O snippet de código a seguir demonstra como adicionar informações sobre membros para metadados de uma atividade durante a execução do método de <xref:System.Activities.Activity.CacheMetadata%2A> .</span><span class="sxs-lookup"><span data-stu-id="5c2ec-120">The following code snippet demonstrates how to add information about members to an activity’s metadata during the execution of the <xref:System.Activities.Activity.CacheMetadata%2A> method.</span></span> <span data-ttu-id="5c2ec-121">Observe que a base do método é chamada para armazenar em cachê todos os dados públicos sobre a atividade.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-121">Note that the base of the method is called to cache all public data about the activity.</span></span>

```csharp
protected override void CacheMetadata(NativeActivityMetadata metadata)
{
    base.CacheMetadata(metadata);
    metadata.AddImplementationChild(this._writeLine);
    metadata.AddVariable(this._myVariable);
    metadata.AddImplementationVariable(this._myImplementationVariable);

    RuntimeArgument argument = new RuntimeArgument("MyArgument", ArgumentDirection.In, typeof(SomeType));
    metadata.Bind(argument, this.SomeName);
    metadata.AddArgument(argument);
}
```

## <a name="using-cachemetadata-to-expose-implementation-children"></a><span data-ttu-id="5c2ec-122">Usando CacheMetadata para expor filhos de implementação</span><span class="sxs-lookup"><span data-stu-id="5c2ec-122">Using CacheMetadata to expose implementation children</span></span>

<span data-ttu-id="5c2ec-123">Para passar dados para atividades filhos que devem ser agendadas por uma atividade usando variáveis, é necessário adicionar variáveis como variáveis de implementação; variáveis públicas não podem ter seus valores definidos essa maneira.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-123">In order to pass data to child activities that are to be scheduled by an activity using variables, it is necessary to add the variables as implementation variables; public variables cannot have their values set this way.</span></span> <span data-ttu-id="5c2ec-124">A razão para isso é que as atividades são feitos para ser executadas mais como implementações das funções (que têm parâmetros), em vez das classes encapsuladas (que tem propriedades).</span><span class="sxs-lookup"><span data-stu-id="5c2ec-124">The reason for this is that activities are intended to be executed more as implementations of functions (which have parameters), rather than encapsulated classes (which have properties).</span></span> <span data-ttu-id="5c2ec-125">No entanto, há situações em que os argumentos devem ser explicitamente definidos, como ao usar <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, desde que a atividade agendada não tem acesso aos argumentos pai de atividade da maneira que uma atividade filho.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-125">However, there are situations in which the arguments must be explicitly set, such as when using <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, since the scheduled activity doesn't have access to the parent activity's arguments in the way a child activity would.</span></span>

<span data-ttu-id="5c2ec-126">O snippet de código a seguir demonstra como passar um formulário do argumento uma atividade nativo em uma atividade agendada usando <xref:System.Activities.Activity.CacheMetadata%2A>.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-126">The following code snippet demonstrates how to pass an argument form a native activity into a scheduled activity using <xref:System.Activities.Activity.CacheMetadata%2A>.</span></span>

```csharp
public sealed class ChildActivity : NativeActivity
{
    public WriteLine _writeLine;
    public InArgument<string> Message { get; set; }
    private Variable<string> MessageVariable { get; set; }
    public ChildActivity()
    {
        MessageVariable = new Variable<string>();
        _writeLine = new WriteLine
        {
            Text = new InArgument<string>(MessageVariable),
        };
    }
    protected override void CacheMetadata(NativeActivityMetadata metadata)
    {
        base.CacheMetadata(metadata);
        metadata.AddImplementationVariable(this.MessageVariable);
        metadata.AddImplementationChild(this._writeLine);
    }
    protected override void Execute(NativeActivityContext context)
    {
        string configuredMessage = context.GetValue(Message);
        context.SetValue(MessageVariable, configuredMessage);
        context.ScheduleActivity(this._writeLine);
    }
}
```

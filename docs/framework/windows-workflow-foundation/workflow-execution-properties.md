---
title: Propriedades de execução de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
ms.openlocfilehash: 96f5057986e256f485f60221d1c6ad3d2494be55
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566716"
---
# <a name="workflow-execution-properties"></a><span data-ttu-id="b8e2c-102">Propriedades de execução de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b8e2c-102">Workflow Execution Properties</span></span>
<span data-ttu-id="b8e2c-103">Com o armazenamento local (TLS) de segmento, CLR mantém um contexto de execução para cada segmento.</span><span class="sxs-lookup"><span data-stu-id="b8e2c-103">Through thread local storage (TLS), the CLR maintains an execution context for each thread.</span></span> <span data-ttu-id="b8e2c-104">Este contexto de execução determina propriedades de segmento conhecidos como a identidade da thread, a transação ambiente, e o conjunto de permissões atual além de propriedades definidos pelo usuário do segmento como slots nomeados.</span><span class="sxs-lookup"><span data-stu-id="b8e2c-104">This execution context governs well-known thread properties such as the thread identity, the ambient transaction, and the current permission set in addition to user-defined thread properties like named slots.</span></span>  
  
 <span data-ttu-id="b8e2c-105">Ao contrário dos programas que direcionam diretamente CLR, os programas de fluxo de trabalho são árvores hierarquicamente o escopo de atividades que executam em um ambiente com desconhecido.</span><span class="sxs-lookup"><span data-stu-id="b8e2c-105">Unlike programs directly targeting the CLR, workflow programs are hierarchically scoped trees of activities that execute in a thread-agnostic environment.</span></span> <span data-ttu-id="b8e2c-106">Isso significa que os mecanismos padrão de TLS diretamente não podem ser usados para determinar qual contexto está no escopo de um item de trabalho determinado.</span><span class="sxs-lookup"><span data-stu-id="b8e2c-106">This implies that the standard TLS mechanisms cannot directly be used to determine what context is in scope for a given work item.</span></span> <span data-ttu-id="b8e2c-107">Por exemplo, duas ramificações paralelos de execução podem usar transações diferentes, porém o agendador pode intercalar sua execução no mesmo segmento de CLR.</span><span class="sxs-lookup"><span data-stu-id="b8e2c-107">For example, two parallel branches of execution might use different transactions, yet the scheduler might interleave their execution on the same CLR thread.</span></span>  
  
 <span data-ttu-id="b8e2c-108">As propriedades de execução de fluxo de trabalho fornecem um mecanismo para adicionar propriedades específicas de contexto para o ambiente de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="b8e2c-108">Workflow execution properties provide a mechanism to add context specific properties to an activity’s environment.</span></span> <span data-ttu-id="b8e2c-109">Isso permite que uma atividade declare propriedades que estejam no escopo para sua subárvore e também fornece ganchos para configurar e rasgar para baixo TLS para interoperar corretamente com objetos CLR.</span><span class="sxs-lookup"><span data-stu-id="b8e2c-109">This allows an activity to declare which properties are in scope for its sub-tree and also provides hooks for setting up and tearing down TLS to properly interoperate with CLR objects.</span></span>  
  
## <a name="creating-and-using-workflow-execution-properties"></a><span data-ttu-id="b8e2c-110">Criando e usando propriedades de execução de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b8e2c-110">Creating and Using Workflow Execution Properties</span></span>  
 <span data-ttu-id="b8e2c-111">As propriedades de execução de fluxo de trabalho geralmente implementam a interface de <xref:System.Activities.IExecutionProperty> , embora as propriedades centradas sobre a mensagem podem implementar <xref:System.ServiceModel.Activities.ISendMessageCallback> e <xref:System.ServiceModel.Activities.IReceiveMessageCallback> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="b8e2c-111">Workflow execution properties usually implement the <xref:System.Activities.IExecutionProperty> interface, though properties focused on messaging may implement <xref:System.ServiceModel.Activities.ISendMessageCallback> and <xref:System.ServiceModel.Activities.IReceiveMessageCallback> instead.</span></span> <span data-ttu-id="b8e2c-112">Para criar uma propriedade de execução de fluxo de trabalho, crie uma classe que implementa a interface de <xref:System.Activities.IExecutionProperty> e implementar os membros <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> e <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span><span class="sxs-lookup"><span data-stu-id="b8e2c-112">To create a workflow execution property, create a class that implements the <xref:System.Activities.IExecutionProperty> interface and implement the members <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> and <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span></span> <span data-ttu-id="b8e2c-113">Esses membros fornecem a propriedade de execução com uma oportunidade para configurar e rasgar corretamente para baixo o armazenamento local de segmentos durante cada pulso de trabalho de atividade que contém a propriedade, incluindo todas as atividades filhos.</span><span class="sxs-lookup"><span data-stu-id="b8e2c-113">These members provide the execution property with an opportunity to properly set up and tear down the thread local storage during each pulse of work of the activity that contains the property, including any child activities.</span></span> <span data-ttu-id="b8e2c-114">Nesse exemplo, `ConsoleColorProperty` é criado que define `Console.ForegroundColor`.</span><span class="sxs-lookup"><span data-stu-id="b8e2c-114">In this example, a `ConsoleColorProperty` is created that sets the `Console.ForegroundColor`.</span></span>  
  
```csharp  
class ConsoleColorProperty : IExecutionProperty  
{  
    public const string Name = "ConsoleColorProperty";  
  
    ConsoleColor original;  
    ConsoleColor color;  
  
    public ConsoleColorProperty(ConsoleColor color)  
    {  
        this.color = color;  
    }  
  
    void IExecutionProperty.SetupWorkflowThread()  
    {  
        original = Console.ForegroundColor;  
        Console.ForegroundColor = color;  
    }  
  
    void IExecutionProperty.CleanupWorkflowThread()  
    {  
        Console.ForegroundColor = original;  
    }  
}  
```  
  
 <span data-ttu-id="b8e2c-115">Os autores de atividade podem usar essa propriedade para à atividade executam substituição.</span><span class="sxs-lookup"><span data-stu-id="b8e2c-115">Activity authors can use this property by registering it in the activity’s execute override.</span></span> <span data-ttu-id="b8e2c-116">Nesse exemplo, uma atividade de `ConsoleColorScope` é definida que registra `ConsoleColorProperty` adicionando à coleção de <xref:System.Activities.NativeActivityContext.Properties%2A> de <xref:System.Activities.NativeActivityContext>atual.</span><span class="sxs-lookup"><span data-stu-id="b8e2c-116">In this example, a `ConsoleColorScope` activity is defined that registers the `ConsoleColorProperty` by adding it to the <xref:System.Activities.NativeActivityContext.Properties%2A> collection of the current <xref:System.Activities.NativeActivityContext>.</span></span>  
  
```csharp  
public sealed class ConsoleColorScope : NativeActivity  
{  
    public ConsoleColorScope()  
        : base()  
    {  
    }  
  
    public ConsoleColor Color { get; set; }  
    public Activity Body { get; set; }  
  
    protected override void Execute(NativeActivityContext context)  
    {  
        context.Properties.Add(ConsoleColorProperty.Name, new ConsoleColorProperty(this.Color));  
  
        if (this.Body != null)  
        {  
            context.ScheduleActivity(this.Body);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="b8e2c-117">Quando o corpo da atividade inicia um pulso de trabalho, o método de <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> da propriedade é chamado, e quando o pulso de trabalho estiver concluída, <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> é chamado.</span><span class="sxs-lookup"><span data-stu-id="b8e2c-117">When the activity’s body starts a pulse of work, the <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> method of the property is called, and when the pulse of work is complete, the <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> is called.</span></span> <span data-ttu-id="b8e2c-118">Nesse exemplo, um fluxo de trabalho é criado que usa uma atividade de <xref:System.Activities.Statements.Parallel> com três ramificações.</span><span class="sxs-lookup"><span data-stu-id="b8e2c-118">In this example, a workflow is created that uses a <xref:System.Activities.Statements.Parallel> activity with three branches.</span></span> <span data-ttu-id="b8e2c-119">Os primeiros dois ramificações usam a atividade de `ConsoleColorScope` e o terceiro ramificação não.</span><span class="sxs-lookup"><span data-stu-id="b8e2c-119">The first two branches use the `ConsoleColorScope` activity and the third branch does not.</span></span> <span data-ttu-id="b8e2c-120">Todos os três ramificações contêm duas atividades de <xref:System.Activities.Statements.WriteLine> e uma atividade de <xref:System.Activities.Statements.Delay> .</span><span class="sxs-lookup"><span data-stu-id="b8e2c-120">All three branches contain two <xref:System.Activities.Statements.WriteLine> activities and a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="b8e2c-121">Quando a atividade de <xref:System.Activities.Statements.Parallel> executa, as atividades que estão contidas nas ramificações executam em uma maneira intercalada, mas como cada atividade filho executa a cor correta do console são aplicadas por `ConsoleColorProperty`.</span><span class="sxs-lookup"><span data-stu-id="b8e2c-121">When the <xref:System.Activities.Statements.Parallel> activity executes, the activities that are contained in the branches execute in an interleaved manner, but as each child activity executes the correct console color is applied by the `ConsoleColorProperty`.</span></span>  
  
```csharp  
Activity wf = new Parallel  
{  
    Branches =   
    {  
        new ConsoleColorScope  
        {  
            Color = ConsoleColor.Blue,  
            Body = new Sequence  
            {  
                Activities =   
                {  
                    new WriteLine  
                    {  
                        Text = "Start blue text."  
                    },  
                    new Delay  
                    {  
                        Duration = TimeSpan.FromSeconds(1)  
                    },  
                    new WriteLine  
                    {  
                        Text = "End blue text."  
                    }  
                }  
            }  
        },  
        new ConsoleColorScope  
        {  
            Color = ConsoleColor.Red,  
            Body = new Sequence  
            {  
                Activities =   
                {  
                    new WriteLine  
                    {  
                        Text = "Start red text."  
                    },  
                    new Delay  
                    {  
                        Duration = TimeSpan.FromSeconds(1)  
                    },  
                    new WriteLine  
                    {  
                        Text = "End red text."  
                    }  
                }  
            }  
        },  
        new Sequence  
        {  
            Activities =   
            {  
                new WriteLine  
                {  
                    Text = "Start default text."  
                },  
                new Delay  
                {  
                    Duration = TimeSpan.FromSeconds(1)  
                },  
                new WriteLine  
                {  
                    Text = "End default text."  
                }  
            }  
        }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
 <span data-ttu-id="b8e2c-122">Quando o fluxo de trabalho é chamado, a saída a seguir são gravadas para a janela do console.</span><span class="sxs-lookup"><span data-stu-id="b8e2c-122">When the workflow is invoked, the following output is written to the console window.</span></span>  
  
```  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
>  <span data-ttu-id="b8e2c-123">Embora não são mostradas na saída anteriores, cada linha de texto na janela de console é exibida na cor indicada.</span><span class="sxs-lookup"><span data-stu-id="b8e2c-123">Although it is not shown in the previous output, each line of text in the console window is displayed in the indicated color.</span></span>  
  
 <span data-ttu-id="b8e2c-124">As propriedades de execução de fluxo de trabalho podem ser usadas por autores personalizados de atividade, e também fornecem um mecanismo para o gerenciamento de forma para atividades como as atividades de <xref:System.ServiceModel.Activities.CorrelationScope> e de <xref:System.Activities.Statements.TransactionScope> .</span><span class="sxs-lookup"><span data-stu-id="b8e2c-124">Workflow execution properties can be used by custom activity authors, and they also provide the mechanism for handle management for activities such as the <xref:System.ServiceModel.Activities.CorrelationScope> and <xref:System.Activities.Statements.TransactionScope> activities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8e2c-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8e2c-125">See also</span></span>
- <xref:System.Activities.IExecutionProperty>
- <xref:System.Activities.IPropertyRegistrationCallback>
- <xref:System.Activities.RegistrationContext>

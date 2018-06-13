---
title: Escolher atividade
ms.date: 03/30/2017
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
ms.openlocfilehash: b6a49207c6c2e800c2e894f6223abdf0f5f6820d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520309"
---
# <a name="pick-activity"></a><span data-ttu-id="38a22-102">Escolher atividade</span><span class="sxs-lookup"><span data-stu-id="38a22-102">Pick Activity</span></span>
<span data-ttu-id="38a22-103">A atividade de <xref:System.Activities.Statements.Pick> simplifica a modelagem de um conjunto de disparadores de evento seguidos por seus manipuladores correspondentes.</span><span class="sxs-lookup"><span data-stu-id="38a22-103">The <xref:System.Activities.Statements.Pick> activity simplifies the modeling of a set of event triggers followed by their corresponding handlers.</span></span>  <span data-ttu-id="38a22-104">Uma atividade de <xref:System.Activities.Statements.Pick> contém uma coleção de atividades de <xref:System.Activities.Statements.PickBranch> , onde cada <xref:System.Activities.Statements.PickBranch> é um emparelhamento entre uma atividade de <xref:System.Activities.Statements.PickBranch.Trigger%2A> e uma atividade de <xref:System.Activities.Statements.PickBranch.Action%2A> .</span><span class="sxs-lookup"><span data-stu-id="38a22-104">A <xref:System.Activities.Statements.Pick> activity contains a collection of <xref:System.Activities.Statements.PickBranch> activities, where each <xref:System.Activities.Statements.PickBranch> is a pairing between a <xref:System.Activities.Statements.PickBranch.Trigger%2A> activity and an <xref:System.Activities.Statements.PickBranch.Action%2A> activity.</span></span>  <span data-ttu-id="38a22-105">Em tempo de execução, disparadores para todos as ramificações são executados paralelamente.</span><span class="sxs-lookup"><span data-stu-id="38a22-105">At execution time, the triggers for all branches are executed in parallel.</span></span>  <span data-ttu-id="38a22-106">Quando um disparador for concluída, então a ação correspondente é executada, e todos outros disparadores são canceladas.</span><span class="sxs-lookup"><span data-stu-id="38a22-106">When one trigger completes, then its corresponding action is executed, and all other triggers are canceled.</span></span>  <span data-ttu-id="38a22-107">O comportamento do [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.Activities.Statements.Pick> atividade é semelhante do [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] <xref:System.Workflow.Activities.ListenActivity> atividade.</span><span class="sxs-lookup"><span data-stu-id="38a22-107">The behavior of the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<xref:System.Activities.Statements.Pick> activity is similar to the [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]<xref:System.Workflow.Activities.ListenActivity> activity.</span></span>  
  
 <span data-ttu-id="38a22-108">Captura de tela a seguir do [usando a atividade escolher](../../../docs/framework/windows-workflow-foundation/samples/using-the-pick-activity.md) amostra do SDK mostra uma atividade de separar com duas ramificações.</span><span class="sxs-lookup"><span data-stu-id="38a22-108">The following screenshot from the [Using the Pick Activity](../../../docs/framework/windows-workflow-foundation/samples/using-the-pick-activity.md) SDK sample shows a Pick activity with two branches.</span></span>  <span data-ttu-id="38a22-109">Uma ramificação tem um gatilho chamado **entrada leitura**, uma atividade personalizada que lê a entrada da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="38a22-109">One branch has a trigger called **Read input**, a custom activity that reads input from the command line.</span></span> <span data-ttu-id="38a22-110">O segundo ramificação tem um disparador de atividade de <xref:System.Activities.Statements.Delay> .</span><span class="sxs-lookup"><span data-stu-id="38a22-110">The second branch has a <xref:System.Activities.Statements.Delay> activity trigger.</span></span> <span data-ttu-id="38a22-111">Se o **entrada leitura** atividade recebe os dados antes do <xref:System.Activities.Statements.Delay> concluir a atividade, <xref:System.Activities.Statements.Delay> atraso será cancelado e uma mensagem será gravada no console.</span><span class="sxs-lookup"><span data-stu-id="38a22-111">If the **Read input** activity receives data before the <xref:System.Activities.Statements.Delay> activity finishes, <xref:System.Activities.Statements.Delay> Delay will be canceled and a greeting will be written to the console.</span></span>  <span data-ttu-id="38a22-112">Caso contrário, se o **entrada leitura** atividade não recebe dados no tempo alocado, em seguida, ela será cancelada e uma mensagem de tempo limite será gravada no console.</span><span class="sxs-lookup"><span data-stu-id="38a22-112">Otherwise, if the **Read input** activity does not receive data in the allotted time, then it will be canceled and a timeout message will be written to the console.</span></span>  <span data-ttu-id="38a22-113">Este é um padrão comum usado para adicionar um tempo limite a qualquer ação.</span><span class="sxs-lookup"><span data-stu-id="38a22-113">This is a common pattern used to add a timeout to any action.</span></span>  
  
 <span data-ttu-id="38a22-114">![Escolher atividade](../../../docs/framework/windows-workflow-foundation/media/pickconceptual.JPG "PickConceptual")</span><span class="sxs-lookup"><span data-stu-id="38a22-114">![Pick Activity](../../../docs/framework/windows-workflow-foundation/media/pickconceptual.JPG "PickConceptual")</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="38a22-115">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="38a22-115">Best practices</span></span>  
 <span data-ttu-id="38a22-116">Ao usar a picareta, a ramificação que executa é a ramificação cujo disparador for concluído primeiro.</span><span class="sxs-lookup"><span data-stu-id="38a22-116">When using Pick, the branch that executes is the branch whose trigger completes first.</span></span>  <span data-ttu-id="38a22-117">Conceitualmente, todos os disparadores executam paralelamente, e um disparador pode ter executado a maioria de sua lógica antes de ser cancelado pela conclusão de um outro disparador.</span><span class="sxs-lookup"><span data-stu-id="38a22-117">Conceptually, all triggers execute in parallel, and one trigger may have executed the majority of its logic before it is canceled by the completion of another trigger.</span></span>  <span data-ttu-id="38a22-118">Com isso em mente, uma orientação então quando usar a atividade de picareta é manipular o disparador como representação de um único evento, e a colocar como pouca lógica como possível nele.</span><span class="sxs-lookup"><span data-stu-id="38a22-118">With this in mind, a general guideline to follow when using the Pick activity is to treat the trigger as representing a single event, and to put as little logic as possible into it.</span></span>  <span data-ttu-id="38a22-119">Idealmente, o disparador deve conter apenas lógica suficiente para receber um evento, e qualquer processamento do evento deve entrar em ação de ramificação.</span><span class="sxs-lookup"><span data-stu-id="38a22-119">Ideally, the trigger should contain just enough logic to receive an event, and all the processing of that event should go into the action of the branch.</span></span>  <span data-ttu-id="38a22-120">Este método minimiza a quantidade de sobreposição entre a execução de disparadores.</span><span class="sxs-lookup"><span data-stu-id="38a22-120">This method minimizes the amount of overlap between the execution of the triggers.</span></span>  <span data-ttu-id="38a22-121">Por exemplo, considere <xref:System.Activities.Statements.Pick> com dois disparadores, onde cada disparador contém uma atividade de <xref:System.ServiceModel.Activities.Receive> seguido pela lógica adicional.</span><span class="sxs-lookup"><span data-stu-id="38a22-121">For example, consider a <xref:System.Activities.Statements.Pick> with two triggers, where each trigger contains a <xref:System.ServiceModel.Activities.Receive> activity followed by additional logic.</span></span>  <span data-ttu-id="38a22-122">Se a lógica adicional apresenta um ponto ocioso, então existem a possibilidade de ambas as atividades de <xref:System.ServiceModel.Activities.Receive> que concluírem com êxito.</span><span class="sxs-lookup"><span data-stu-id="38a22-122">If the additional logic introduces an idle point, then there is the possibility of both <xref:System.ServiceModel.Activities.Receive> activities completing successfully.</span></span>  <span data-ttu-id="38a22-123">Um disparador concluirá totalmente, quando outro concluirá parcialmente.</span><span class="sxs-lookup"><span data-stu-id="38a22-123">One trigger will fully complete, while another will partially complete.</span></span>  <span data-ttu-id="38a22-124">Em alguns cenários, aceitar uma mensagem, e então concluir parcialmente o processamento delas são inaceitáveis.</span><span class="sxs-lookup"><span data-stu-id="38a22-124">In some scenarios, accepting a message, and then partially completing the processing of it is unacceptable.</span></span>  <span data-ttu-id="38a22-125">Portanto, ao usar atividades internos de mensagem de WF como <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply>, quando <xref:System.ServiceModel.Activities.Receive> são comumente usadas no disparador, <xref:System.ServiceModel.Activities.SendReply> e a outra lógica deve ser colocado em ação sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="38a22-125">Therefore, when using WF built-in messaging activities such as <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>, while <xref:System.ServiceModel.Activities.Receive> is commonly used in the trigger, <xref:System.ServiceModel.Activities.SendReply> and other logic should be put in the action whenever possible.</span></span>  
  
## <a name="using-the-pick-activity-in-the-designer"></a><span data-ttu-id="38a22-126">Usando a atividade de picareta no designer</span><span class="sxs-lookup"><span data-stu-id="38a22-126">Using the Pick activity in the designer</span></span>  
 <span data-ttu-id="38a22-127">Para usar Pick no designer, localize **escolher** e **PickBranch** na caixa de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="38a22-127">To use Pick in the designer, find **Pick** and **PickBranch** in the toolbox.</span></span>  <span data-ttu-id="38a22-128">Arrastar e soltar **escolher** para a tela.</span><span class="sxs-lookup"><span data-stu-id="38a22-128">Drag and drop **Pick** onto the canvas.</span></span>  <span data-ttu-id="38a22-129">Por padrão, um novo **escolher** atividade no designer conterá duas ramificações.</span><span class="sxs-lookup"><span data-stu-id="38a22-129">By default, a new **Pick** Activity in the designer will contain two branches.</span></span>  <span data-ttu-id="38a22-130">Para adicionar mais ramificações, arraste o **PickBranch** atividade e solte-o ao lado de ramificações existentes.</span><span class="sxs-lookup"><span data-stu-id="38a22-130">To add additional branches, drag the **PickBranch** activity and drop it next to existing branches.</span></span> <span data-ttu-id="38a22-131">Atividades podem ser descartadas até o **escolher** atividade em um a **gatilho** área ou **ação** área de qualquer **PickBranch**.</span><span class="sxs-lookup"><span data-stu-id="38a22-131">Activities can be dropped onto the **Pick** Activity into either the **Trigger** area or the **Action** area of any **PickBranch**.</span></span>  
  
## <a name="using-the-pick-activity-in-code"></a><span data-ttu-id="38a22-132">Usando a atividade de picareta no código</span><span class="sxs-lookup"><span data-stu-id="38a22-132">Using the Pick Activity in code</span></span>  
 <span data-ttu-id="38a22-133">A atividade de <xref:System.Activities.Statements.Pick> é usada preenchendo sua coleção de <xref:System.Activities.Statements.Pick.Branches%2A> com atividades de <xref:System.Activities.Statements.PickBranch> .</span><span class="sxs-lookup"><span data-stu-id="38a22-133">The <xref:System.Activities.Statements.Pick> activity is used by populating its <xref:System.Activities.Statements.Pick.Branches%2A> collection with <xref:System.Activities.Statements.PickBranch> activities.</span></span> <span data-ttu-id="38a22-134">As atividades cada um de <xref:System.Activities.Statements.PickBranch> possuem uma propriedade de <xref:System.Activities.Statements.PickBranch.Trigger%2A> de tipo <xref:System.Activities.Activity>.</span><span class="sxs-lookup"><span data-stu-id="38a22-134">The <xref:System.Activities.Statements.PickBranch> activities each have a <xref:System.Activities.Statements.PickBranch.Trigger%2A> property of type <xref:System.Activities.Activity>.</span></span> <span data-ttu-id="38a22-135">Quando a atividade especificada concluir a execução, <xref:System.Activities.Statements.PickBranch.Action%2A> executa.</span><span class="sxs-lookup"><span data-stu-id="38a22-135">When the specified activity completes execution, the <xref:System.Activities.Statements.PickBranch.Action%2A> executes.</span></span>  
  
 <span data-ttu-id="38a22-136">O exemplo de código demonstra como usar uma atividade de <xref:System.Activities.Statements.Pick> para implementar um tempo limite para uma atividade que lê uma linha de console.</span><span class="sxs-lookup"><span data-stu-id="38a22-136">The following code example demonstrates how to use a <xref:System.Activities.Statements.Pick> activity to implement a timeout for an activity that reads a line from the console.</span></span>  
  
```csharp  
Sequence body = new Sequence()  
{  
    Variables = { name },  
    Activities =   
   {  
       new System.Activities.Statements.Pick  
        {  
           Branches =   
           {  
               new PickBranch  
               {  
                   Trigger = new ReadLine  
                   {  
                      Result = name,  
                      BookmarkName = "name"  
                   },  
                   Action = new WriteLine   
                   {   
                       Text = ExpressionServices.Convert<string>(ctx => "Hello " +   
                           name.Get(ctx))   
                   }  
               },  
               new PickBranch  
               {  
                   Trigger = new Delay  
                   {  
                      Duration = new TimeSpan(0, 0, 5)  
                   },  
                   Action = new WriteLine  
                   {  
                      Text = "Time is up."  
                   }  
               }  
           }  
       }  
   }  
};  
```  
  
```xaml  
<Sequence xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <Variable x:TypeArguments="x:String" Name="username" />  
  </Sequence.Variables>  
  <Pick>  
    <PickBranch>  
      <PickBranch.Trigger>  
        <ReadLine BookmarkName="name" Result="username" />  
      </PickBranch.Trigger>  
      <WriteLine>[String.Concat("Hello ", username)]</WriteLine>  
    </PickBranch>  
    <PickBranch>  
      <PickBranch.Trigger>  
        <Delay>00:00:05</Delay>  
      </PickBranch.Trigger>  
      <WriteLine>Time is up.</WriteLine>  
    </PickBranch>  
  </Pick>  
</Sequence>  
```

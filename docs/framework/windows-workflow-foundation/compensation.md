---
title: Compensação
ms.date: 03/30/2017
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
ms.openlocfilehash: 75c5ed2f5e5c3a93834632ce499a2c8195fbc6bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182998"
---
# <a name="compensation"></a><span data-ttu-id="d7c13-102">Compensação</span><span class="sxs-lookup"><span data-stu-id="d7c13-102">Compensation</span></span>
<span data-ttu-id="d7c13-103">Compensação no Windows Workflow Foundation (WF) é o mecanismo pelo qual o trabalho previamente concluído pode ser desfeito ou compensado (seguindo a lógica definida pelo aplicativo) quando ocorre uma falha subseqüente.</span><span class="sxs-lookup"><span data-stu-id="d7c13-103">Compensation in Windows Workflow Foundation (WF) is the mechanism by which previously completed work can be undone or compensated (following the logic defined by the application) when a subsequent failure occurs.</span></span> <span data-ttu-id="d7c13-104">Esta seção descreve como usar a compensação em fluxos de trabalho.</span><span class="sxs-lookup"><span data-stu-id="d7c13-104">This section describes how to use compensation in workflows.</span></span>  
  
## <a name="compensation-vs-transactions"></a><span data-ttu-id="d7c13-105">Compensação vs. Transações</span><span class="sxs-lookup"><span data-stu-id="d7c13-105">Compensation vs. Transactions</span></span>  
 <span data-ttu-id="d7c13-106">Uma transação permite que você combine várias operações em uma única unidade de trabalho.</span><span class="sxs-lookup"><span data-stu-id="d7c13-106">A transaction allows you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="d7c13-107">Usar uma transação fornece ao aplicativo a capacidade de nulo () para reverter as alterações executadas dentro de transação se qualquer erro ocorre durante qualquer parte do processo de transação.</span><span class="sxs-lookup"><span data-stu-id="d7c13-107">Using a transaction gives your application the ability to abort (roll back) all changes executed from within the transaction if any errors occur during any part of the transaction process.</span></span> <span data-ttu-id="d7c13-108">No entanto, usar transações pode não ser adequado se o trabalho é longo.</span><span class="sxs-lookup"><span data-stu-id="d7c13-108">However, using transactions may not be appropriate if the work is long running.</span></span> <span data-ttu-id="d7c13-109">Por exemplo, um aplicativo de planejamento de traço é implementado como um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="d7c13-109">For example, a travel planning application is implemented as a workflow.</span></span> <span data-ttu-id="d7c13-110">As etapas de fluxo de trabalho podem consistir registrar um voo, uma aprovação de espera gerente e em seguida, pagar por voo.</span><span class="sxs-lookup"><span data-stu-id="d7c13-110">The steps of the workflow may consist of booking a flight, waiting for manager approval, and then paying for the flight.</span></span> <span data-ttu-id="d7c13-111">Esse processo pode levar muitos dias e não é prático para as etapas do registro e pagar por voo para participar na mesma transação.</span><span class="sxs-lookup"><span data-stu-id="d7c13-111">This process could take many days and it is not practical for the steps of booking and paying for the flight to participate in the same transaction.</span></span> <span data-ttu-id="d7c13-112">Em um cenário como isso, a compensação pode ser usada para desfazer a etapa de registro de fluxo de trabalho se houver uma falha posteriormente no processamento.</span><span class="sxs-lookup"><span data-stu-id="d7c13-112">In a scenario such as this, compensation could be used to undo the booking step of the workflow if there is a failure later in the processing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d7c13-113">Este tópico aborda a compensação em fluxos de trabalho.</span><span class="sxs-lookup"><span data-stu-id="d7c13-113">This topic covers compensation in workflows.</span></span> <span data-ttu-id="d7c13-114">Para obter mais informações sobre transações em <xref:System.Activities.Statements.TransactionScope>fluxos de trabalho, consulte [Transações](workflow-transactions.md) e .</span><span class="sxs-lookup"><span data-stu-id="d7c13-114">For more information about transactions in workflows, see [Transactions](workflow-transactions.md) and <xref:System.Activities.Statements.TransactionScope>.</span></span> <span data-ttu-id="d7c13-115">Para obter mais informações <xref:System.Transactions?displayProperty=nameWithType> sobre <xref:System.Transactions.Transaction?displayProperty=nameWithType>transações, consulte e .</span><span class="sxs-lookup"><span data-stu-id="d7c13-115">For more information about transactions, see <xref:System.Transactions?displayProperty=nameWithType> and <xref:System.Transactions.Transaction?displayProperty=nameWithType>.</span></span>  
  
## <a name="using-compensableactivity"></a><span data-ttu-id="d7c13-116">Usando CompensableActivity</span><span class="sxs-lookup"><span data-stu-id="d7c13-116">Using CompensableActivity</span></span>  
 <span data-ttu-id="d7c13-117"><xref:System.Activities.Statements.CompensableActivity> é a atividade de compensação central em [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d7c13-117"><xref:System.Activities.Statements.CompensableActivity> is the core compensation activity in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="d7c13-118">Todas as atividades que executa o trabalho que precise ser compensado são colocadas em <xref:System.Activities.Statements.CompensableActivity.Body%2A> de <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="d7c13-118">Any activities that perform work that may need to be compensated are placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="d7c13-119">Nesse exemplo, a etapa de retorno de comprar um voo é colocada em <xref:System.Activities.Statements.CompensableActivity.Body%2A> de <xref:System.Activities.Statements.CompensableActivity> e cancelar de fallback é colocado em <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="d7c13-119">In this example, the reservation step of purchasing a flight is placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> and the cancellation of the reservation is placed into the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>.</span></span> <span data-ttu-id="d7c13-120">Imediatamente depois de <xref:System.Activities.Statements.CompensableActivity> no fluxo de trabalho são duas atividades aguardando a aprovação gerente e conclua a etapa de compra de voo.</span><span class="sxs-lookup"><span data-stu-id="d7c13-120">Immediately following the <xref:System.Activities.Statements.CompensableActivity> in the workflow are two activities that wait for manager approval and then complete the purchasing step of the flight.</span></span> <span data-ttu-id="d7c13-121">Se uma condição de erro faz com que o fluxo de trabalho a ser cancelado após <xref:System.Activities.Statements.CompensableActivity> terminou com êxito, então as atividades no manipulador de <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> são agendadas e o voo é cancelado.</span><span class="sxs-lookup"><span data-stu-id="d7c13-121">If an error condition causes the workflow to be canceled after the <xref:System.Activities.Statements.CompensableActivity> has successfully completed, then the activities in the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> handler are scheduled and the flight is canceled.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 <span data-ttu-id="d7c13-122">O exemplo a seguir é o fluxo de trabalho em XAML.</span><span class="sxs-lookup"><span data-stu-id="d7c13-122">The following example is the workflow in XAML.</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 <span data-ttu-id="d7c13-123">Quando o fluxo de trabalho é chamado, a saída a seguir são exibidas no console.</span><span class="sxs-lookup"><span data-stu-id="d7c13-123">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="d7c13-124">**ReserveFlight: A permissão é permitido.**</span><span class="sxs-lookup"><span data-stu-id="d7c13-124">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="d7c13-125">**Aprovação do gerente: Aprovação do gerente recebida.** 
 **Voo de Compra: O bilhete é comprado.** 
 **Fluxo de trabalho concluído com sucesso com status: Fechado.**</span><span class="sxs-lookup"><span data-stu-id="d7c13-125">**ManagerApproval: Manager approval received.**
**PurchaseFlight: Ticket is purchased.**
**Workflow completed successfully with status: Closed.**</span></span>
> [!NOTE]
> <span data-ttu-id="d7c13-126">As atividades de exemplo neste tópico como `ReserveFlight` exibem seu nome e finalidade no console ajudar a ilustrar a ordem em que as atividades são executadas quando a compensação ocorre.</span><span class="sxs-lookup"><span data-stu-id="d7c13-126">The sample activities in this topic such as `ReserveFlight` display their name and purpose to the console to help illustrate the order in which the activities are executed when compensation occurs.</span></span>  
  
### <a name="default-workflow-compensation"></a><span data-ttu-id="d7c13-127">Compensação padrão de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="d7c13-127">Default Workflow Compensation</span></span>  
 <span data-ttu-id="d7c13-128">Por padrão, se o fluxo de trabalho é cancelado, a lógica de compensação é executada para quaisquer atividades compensável que tenha êxito completamente e não tem sido confirmada ou não foi compensada.</span><span class="sxs-lookup"><span data-stu-id="d7c13-128">By default, if the workflow is canceled, the compensation logic is run for any compensable activity that has successfully completely and has not already been confirmed or compensated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d7c13-129">Quando <xref:System.Activities.Statements.CompensableActivity> a for *confirmada,* a compensação pela atividade não pode mais ser invocada.</span><span class="sxs-lookup"><span data-stu-id="d7c13-129">When a <xref:System.Activities.Statements.CompensableActivity> is *confirmed*, compensation for the activity can no longer be invoked.</span></span> <span data-ttu-id="d7c13-130">O processo de confirmação é descrito posteriormente nesta seção.</span><span class="sxs-lookup"><span data-stu-id="d7c13-130">The confirmation process is described later in this section.</span></span>  
  
 <span data-ttu-id="d7c13-131">Nesse exemplo, uma exceção é lançada após o voo é reservado mas antes da etapa de aprovação do gerenciador.</span><span class="sxs-lookup"><span data-stu-id="d7c13-131">In this example, an exception is thrown after the flight is reserved but before the manager approval step.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 <span data-ttu-id="d7c13-132">Este exemplo é o fluxo de trabalho em XAML.</span><span class="sxs-lookup"><span data-stu-id="d7c13-132">This example is the workflow in XAML.</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:SimulatedErrorCondition />  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 [!code-csharp[CFX_CompensationExample#100](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#100)]  
  
 <span data-ttu-id="d7c13-133">Quando o fluxo de trabalho é chamado, a exceção simulada de condição de erro é tratada pelo aplicativo host em <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, o fluxo de trabalho é cancelado, e a lógica de compensação é chamada.</span><span class="sxs-lookup"><span data-stu-id="d7c13-133">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the compensation logic is invoked.</span></span>  
  
 <span data-ttu-id="d7c13-134">**ReserveFlight: A permissão é permitido.**</span><span class="sxs-lookup"><span data-stu-id="d7c13-134">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="d7c13-135">**SimulatedErrorCondition: Throwing a ApplicationException ( Lançar uma exceção de aplicativos).** 
 **Fluxo de trabalho Exceção não manuseada:**
**Sistema.AplicativoExceto: Condição simulada de erro no fluxo de trabalho.** 
 **CancelFlight: O bilhete está cancelado.** 
 **Fluxo de trabalho concluído com sucesso com status: cancelado.**</span><span class="sxs-lookup"><span data-stu-id="d7c13-135">**SimulatedErrorCondition: Throwing an ApplicationException.**
**Workflow Unhandled Exception:**
**System.ApplicationException: Simulated error condition in the workflow.**
**CancelFlight: Ticket is canceled.**
**Workflow completed successfully with status: Canceled.**</span></span>
### <a name="cancellation-and-compensableactivity"></a><span data-ttu-id="d7c13-136">Cancelar e CompensableActivity</span><span class="sxs-lookup"><span data-stu-id="d7c13-136">Cancellation and CompensableActivity</span></span>  
 <span data-ttu-id="d7c13-137">Se as atividades em <xref:System.Activities.Statements.CompensableActivity.Body%2A> de <xref:System.Activities.Statements.CompensableActivity> não foram concluídas e a atividade é cancelada, as atividades em <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> são executadas.</span><span class="sxs-lookup"><span data-stu-id="d7c13-137">If the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled, the activities in the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> are executed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d7c13-138"><xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> é invocado apenas se as atividades em <xref:System.Activities.Statements.CompensableActivity.Body%2A> de <xref:System.Activities.Statements.CompensableActivity> não foram concluídas e a atividade é cancelada.</span><span class="sxs-lookup"><span data-stu-id="d7c13-138">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is only invoked if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled.</span></span> <span data-ttu-id="d7c13-139"><xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> é executado somente se as atividades em <xref:System.Activities.Statements.CompensableActivity.Body%2A> de <xref:System.Activities.Statements.CompensableActivity> eles concluíram com êxito e a compensação está chamada posteriormente na atividade.</span><span class="sxs-lookup"><span data-stu-id="d7c13-139">The <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> is only executed if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have successfully completed and compensation is subsequently invoked on the activity.</span></span>  
  
 <span data-ttu-id="d7c13-140"><xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> fornece a autores de fluxo de trabalho a oportunidade de fornecer qualquer lógica apropriada cancelar.</span><span class="sxs-lookup"><span data-stu-id="d7c13-140">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> gives workflow authors the opportunity to provide any appropriate cancellation logic.</span></span> <span data-ttu-id="d7c13-141">No exemplo a seguir, uma exceção é lançada durante a execução de <xref:System.Activities.Statements.CompensableActivity.Body%2A>, e <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> é chamado em seguida.</span><span class="sxs-lookup"><span data-stu-id="d7c13-141">In the following example, an exception is thrown during the execution of the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, and then the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is invoked.</span></span>  
  
```csharp  
Activity wf = new Sequence()  
{  
    Activities =  
    {  
        new CompensableActivity  
        {  
            Body = new Sequence  
            {  
                Activities =
                {  
                    new ChargeCreditCard(),  
                    new SimulatedErrorCondition(),  
                    new ReserveFlight()  
                }  
            },  
            CompensationHandler = new CancelFlight(),  
            CancellationHandler = new CancelCreditCard()  
        },  
        new ManagerApproval(),  
        new PurchaseFlight()  
    }  
};  
```  
  
 <span data-ttu-id="d7c13-142">Este exemplo é o fluxo de trabalho em XAML</span><span class="sxs-lookup"><span data-stu-id="d7c13-142">This example is the workflow in XAML</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <Sequence>  
      <c:ChargeCreditCard />  
      <c:SimulatedErrorCondition />  
      <c:ReserveFlight />  
    </Sequence>  
    <CompensableActivity.CancellationHandler>  
      <c:CancelCreditCard />  
    </CompensableActivity.CancellationHandler>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 <span data-ttu-id="d7c13-143">Quando o fluxo de trabalho é chamado, a exceção simulada de condição de erro é tratada pelo aplicativo host em <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, o fluxo de trabalho é cancelado, e a lógica de cancelamento de <xref:System.Activities.Statements.CompensableActivity> é chamada.</span><span class="sxs-lookup"><span data-stu-id="d7c13-143">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the cancellation logic of the <xref:System.Activities.Statements.CompensableActivity> is invoked.</span></span> <span data-ttu-id="d7c13-144">Nesse exemplo, a lógica de compensação e a lógica de cancelamento metas têm diferentes.</span><span class="sxs-lookup"><span data-stu-id="d7c13-144">In this example, the compensation logic and the cancellation logic have different goals.</span></span> <span data-ttu-id="d7c13-145">Se <xref:System.Activities.Statements.CompensableActivity.Body%2A> concluída com êxito, então isso significa que o cartão de crédito foi carregado e o voo registrado, então a compensação devem desfazer as duas etapas.</span><span class="sxs-lookup"><span data-stu-id="d7c13-145">If the <xref:System.Activities.Statements.CompensableActivity.Body%2A> completed successfully, then this means the credit card was charged and the flight booked, so the compensation should undo both steps.</span></span> <span data-ttu-id="d7c13-146">(Neste exemplo, cancelar o voo cancela automaticamente as taxas do cartão de crédito.) No entanto, se o <xref:System.Activities.Statements.CompensableActivity> for <xref:System.Activities.Statements.CompensableActivity.Body%2A> cancelado, isso significa que <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> o não foi concluído e, portanto, a lógica das necessidades é ser capaz de determinar a melhor maneira de lidar melhor com o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="d7c13-146">(In this example, canceling the flight automatically cancels the credit card charges.) However, if the <xref:System.Activities.Statements.CompensableActivity> is canceled, this means the <xref:System.Activities.Statements.CompensableActivity.Body%2A> did not complete and so the logic of the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> needs to be able to determine how to best handle the cancellation.</span></span> <span data-ttu-id="d7c13-147">Nesse exemplo, <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> cancela a carga de cartão de crédito, mas como `ReserveFlight` era a atividade a mais recente em <xref:System.Activities.Statements.CompensableActivity.Body%2A>, não tenta cancelar o voo.</span><span class="sxs-lookup"><span data-stu-id="d7c13-147">In this example, the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> cancels the credit card charge, but since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, it does not attempt to cancel the flight.</span></span> <span data-ttu-id="d7c13-148">Desde que foi `ReserveFlight` a atividade a mais recente em <xref:System.Activities.Statements.CompensableActivity.Body%2A>, se tiver terminado com êxito em <xref:System.Activities.Statements.CompensableActivity.Body%2A> concluiria e nenhum cancelar seria possível.</span><span class="sxs-lookup"><span data-stu-id="d7c13-148">Since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, if it had successfully completed then the <xref:System.Activities.Statements.CompensableActivity.Body%2A> would have completed and no cancellation would be possible.</span></span>  
  
 <span data-ttu-id="d7c13-149">**ChargeCreditCard: Cartão de crédito de carregamento para o voo.**</span><span class="sxs-lookup"><span data-stu-id="d7c13-149">**ChargeCreditCard: Charge credit card for flight.**</span></span>  
<span data-ttu-id="d7c13-150">**SimulatedErrorCondition: Throwing a ApplicationException ( Lançar uma exceção de aplicativos).** 
 **Fluxo de trabalho Exceção não manuseada:**
**Sistema.AplicativoExceto: Condição simulada de erro no fluxo de trabalho.** 
 **CancelCreditCard: Cancele as taxas do cartão de crédito.** 
 **Fluxo de trabalho concluído com sucesso com status: cancelado.**</span><span class="sxs-lookup"><span data-stu-id="d7c13-150">**SimulatedErrorCondition: Throwing an ApplicationException.**
**Workflow Unhandled Exception:**
**System.ApplicationException: Simulated error condition in the workflow.**
**CancelCreditCard: Cancel credit card charges.**
**Workflow completed successfully with status: Canceled.**</span></span>  <span data-ttu-id="d7c13-151">Para obter mais informações sobre o cancelamento, consulte [Cancelamento](modeling-cancellation-behavior-in-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="d7c13-151">For more information about cancellation, see [Cancellation](modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a><span data-ttu-id="d7c13-152">Compensação explícita usando a atividade de compesação</span><span class="sxs-lookup"><span data-stu-id="d7c13-152">Explicit Compensation Using the Compensate Activity</span></span>  
 <span data-ttu-id="d7c13-153">Na seção anterior, a compensação implícita foi abordada.</span><span class="sxs-lookup"><span data-stu-id="d7c13-153">In the previous section, implicit compensation was covered.</span></span> <span data-ttu-id="d7c13-154">A compensação implícita pode ser adequado para cenários simples, mas se um controle mais explícito é necessário sobre programação de compensação que manipula a atividade de <xref:System.Activities.Statements.Compensate> pode ser usada.</span><span class="sxs-lookup"><span data-stu-id="d7c13-154">Implicit compensation can be appropriate for simple scenarios, but if more explicit control is required over the scheduling of compensation handling then the <xref:System.Activities.Statements.Compensate> activity can be used.</span></span> <span data-ttu-id="d7c13-155">Para iniciar o processo de compensação pela atividade de <xref:System.Activities.Statements.Compensate> , <xref:System.Activities.Statements.CompensationToken> de <xref:System.Activities.Statements.CompensableActivity> para que a compensação é desejada é usado.</span><span class="sxs-lookup"><span data-stu-id="d7c13-155">To initiate the compensation process with the <xref:System.Activities.Statements.Compensate> activity, the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> for which compensation is desired is used.</span></span> <span data-ttu-id="d7c13-156">A atividade de <xref:System.Activities.Statements.Compensate> pode ser usada para iniciar a compensação em qualquer <xref:System.Activities.Statements.CompensableActivity> concluído que não foi confirmada ou não foi compensada.</span><span class="sxs-lookup"><span data-stu-id="d7c13-156">The <xref:System.Activities.Statements.Compensate> activity can be used to initiate compensation on any completed <xref:System.Activities.Statements.CompensableActivity> that has not been confirmed or compensated.</span></span> <span data-ttu-id="d7c13-157">Por exemplo, uma atividade de <xref:System.Activities.Statements.Compensate> pode ser usada na seção de <xref:System.Activities.Statements.TryCatch.Catches%2A> de uma atividade de <xref:System.Activities.Statements.TryCatch> , ou após <xref:System.Activities.Statements.CompensableActivity> tiver concluído em qualquer momento que.</span><span class="sxs-lookup"><span data-stu-id="d7c13-157">For example, a <xref:System.Activities.Statements.Compensate> activity could be used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity, or any time after the <xref:System.Activities.Statements.CompensableActivity> has completed.</span></span> <span data-ttu-id="d7c13-158">Nesse exemplo, a atividade de <xref:System.Activities.Statements.Compensate> é usada na seção de <xref:System.Activities.Statements.TryCatch.Catches%2A> de uma atividade de <xref:System.Activities.Statements.TryCatch> para reverter a ação de <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="d7c13-158">In this example, the <xref:System.Activities.Statements.Compensate> activity is used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity to reverse the action of the <xref:System.Activities.Statements.CompensableActivity>.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 <span data-ttu-id="d7c13-159">Este exemplo é o fluxo de trabalho em XAML.</span><span class="sxs-lookup"><span data-stu-id="d7c13-159">This example is the workflow in XAML.</span></span>  
  
```xaml  
<TryCatch  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:s="clr-namespace:System;assembly=mscorlib"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <TryCatch.Variables>  
    <Variable  
       x:TypeArguments="CompensationToken"  
       x:Name="__ReferenceID0"  
       Name="token1" />  
  </TryCatch.Variables>  
  <TryCatch.Try>  
    <Sequence>  
      <CompensableActivity>  
        <CompensableActivity.Result>  
          <OutArgument  
             x:TypeArguments="CompensationToken">  
            <VariableReference  
               x:TypeArguments="CompensationToken"  
               Variable="{x:Reference __ReferenceID0}">  
              <VariableReference.Result>  
                <OutArgument  
                   x:TypeArguments="Location(CompensationToken)" />  
              </VariableReference.Result>  
            </VariableReference>  
          </OutArgument>  
        </CompensableActivity.Result>  
        <CompensableActivity.CompensationHandler>  
          <c:CancelFlight />  
        </CompensableActivity.CompensationHandler>  
        <CompensableActivity.ConfirmationHandler>  
          <c:ConfirmFlight />  
        </CompensableActivity.ConfirmationHandler>  
        <c:ReserveFlight />  
      </CompensableActivity>  
      <c:SimulatedErrorCondition />  
      <c:ManagerApproval />  
      <c:PurchaseFlight />  
    </Sequence>  
  </TryCatch.Try>  
  <TryCatch.Catches>  
    <Catch  
       x:TypeArguments="s:ApplicationException">  
      <ActivityAction  
         x:TypeArguments="s:ApplicationException">  
        <Compensate>  
          <Compensate.Target>  
            <InArgument  
               x:TypeArguments="CompensationToken">  
              <VariableValue  
                 x:TypeArguments="CompensationToken"  
                 Variable="{x:Reference __ReferenceID0}">  
                <VariableValue.Result>  
                  <OutArgument  
                     x:TypeArguments="CompensationToken" />  
                </VariableValue.Result>  
              </VariableValue>  
            </InArgument>  
          </Compensate.Target>  
        </Compensate>  
      </ActivityAction>  
    </Catch>  
  </TryCatch.Catches>  
</TryCatch>  
```  
  
 <span data-ttu-id="d7c13-160">Quando o fluxo de trabalho é chamado, a saída a seguir são exibidas no console.</span><span class="sxs-lookup"><span data-stu-id="d7c13-160">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="d7c13-161">**ReserveFlight: A permissão é permitido.**</span><span class="sxs-lookup"><span data-stu-id="d7c13-161">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="d7c13-162">**SimulatedErrorCondition: Throwing a ApplicationException ( Lançar uma exceção de aplicativos).** 
 **CancelFlight: O bilhete está cancelado.** 
 **Fluxo de trabalho concluído com sucesso com status: Fechado.**</span><span class="sxs-lookup"><span data-stu-id="d7c13-162">**SimulatedErrorCondition: Throwing an ApplicationException.**
**CancelFlight: Ticket is canceled.**
**Workflow completed successfully with status: Closed.**</span></span>
### <a name="confirming-compensation"></a><span data-ttu-id="d7c13-163">Compensação de confirmação</span><span class="sxs-lookup"><span data-stu-id="d7c13-163">Confirming Compensation</span></span>  
 <span data-ttu-id="d7c13-164">Por padrão, as atividades compensáveis podem ser compensadas em qualquer momento que depois que terminar.</span><span class="sxs-lookup"><span data-stu-id="d7c13-164">By default, compensable activities can be compensated any time after they have completed.</span></span> <span data-ttu-id="d7c13-165">Em alguns cenários isso pode não ser adequado.</span><span class="sxs-lookup"><span data-stu-id="d7c13-165">In some scenarios this may not be appropriate.</span></span> <span data-ttu-id="d7c13-166">No exemplo anterior a compensação para permitir a permissão foi cancelar a reserva.</span><span class="sxs-lookup"><span data-stu-id="d7c13-166">In the previous example the compensation to reserving the ticket was to cancel the reservation.</span></span> <span data-ttu-id="d7c13-167">No entanto, depois que o voo foi concluído essa etapa de compensação não é mais válido.</span><span class="sxs-lookup"><span data-stu-id="d7c13-167">However, after the flight has been completed this compensation step is no longer valid.</span></span> <span data-ttu-id="d7c13-168">Confirmando a atividade compensável chama a atividade especificada por <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="d7c13-168">Confirming the compensable activity invokes the activity specified by the <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span></span> <span data-ttu-id="d7c13-169">Um uso possível para este é permitir todos os recursos que são necessários para executar a compensação a ser liberada.</span><span class="sxs-lookup"><span data-stu-id="d7c13-169">One possible use for this is to allow any resources that are necessary to perform the compensation to be released.</span></span> <span data-ttu-id="d7c13-170">Depois que uma atividade compensável é confirmada não é possível que ele ser compensado, e se esta é tentada uma exceção de <xref:System.InvalidOperationException> é lançada.</span><span class="sxs-lookup"><span data-stu-id="d7c13-170">After a compensable activity is confirmed it is not possible for it to be compensated, and if this is attempted an <xref:System.InvalidOperationException> exception is thrown.</span></span> <span data-ttu-id="d7c13-171">Quando um fluxo de trabalho concluída com sucesso, as atividades compensáveis qualquer não confirmadas e não compensadas que eles concluíram com êxito são confirmadas em ordem inversa de conclusão.</span><span class="sxs-lookup"><span data-stu-id="d7c13-171">When a workflow completes successfully, all non-confirmed and non-compensated compensable activities that completed successfully are confirmed in reverse order of completion.</span></span> <span data-ttu-id="d7c13-172">Nesse exemplo o voo é reservado, comprado, e concluído, e a atividade é confirmada em compensável.</span><span class="sxs-lookup"><span data-stu-id="d7c13-172">In this example the flight is reserved, purchased, and completed, and then the compensable activity is confirmed.</span></span> <span data-ttu-id="d7c13-173">Para confirmar <xref:System.Activities.Statements.CompensableActivity>, use a atividade de <xref:System.Activities.Statements.Confirm> e especificar <xref:System.Activities.Statements.CompensationToken> de <xref:System.Activities.Statements.CompensableActivity> para confirmar.</span><span class="sxs-lookup"><span data-stu-id="d7c13-173">To confirm a <xref:System.Activities.Statements.CompensableActivity>, use the <xref:System.Activities.Statements.Confirm> activity and specify the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> to confirm.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 <span data-ttu-id="d7c13-174">Este exemplo é o fluxo de trabalho em XAML.</span><span class="sxs-lookup"><span data-stu-id="d7c13-174">This example is the workflow in XAML.</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <x:Reference>__ReferenceID0</x:Reference>  
  </Sequence.Variables>  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken">  
        <VariableReference  
           x:TypeArguments="CompensationToken">  
          <VariableReference.Result>  
            <OutArgument  
               x:TypeArguments="Location(CompensationToken)" />  
          </VariableReference.Result>  
          <VariableReference.Variable>  
            <Variable  
               x:TypeArguments="CompensationToken"  
               x:Name="__ReferenceID0"  
               Name="token1" />  
          </VariableReference.Variable>  
        </VariableReference>  
      </OutArgument>  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <CompensableActivity.ConfirmationHandler>  
      <c:ConfirmFlight />  
    </CompensableActivity.ConfirmationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
  <c:TakeFlight />  
  <Confirm>  
    <Confirm.Target>  
      <InArgument  
         x:TypeArguments="CompensationToken">  
        <VariableValue  
           x:TypeArguments="CompensationToken"  
           Variable="{x:Reference __ReferenceID0}">  
          <VariableValue.Result>  
            <OutArgument  
               x:TypeArguments="CompensationToken" />  
          </VariableValue.Result>  
        </VariableValue>  
      </InArgument>  
    </Confirm.Target>  
  </Confirm>  
</Sequence>  
```  
  
<span data-ttu-id="d7c13-175">Quando o fluxo de trabalho é chamado, a saída a seguir são exibidas no console.</span><span class="sxs-lookup"><span data-stu-id="d7c13-175">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
<span data-ttu-id="d7c13-176">**ReserveFlight: A permissão é permitido.**</span><span class="sxs-lookup"><span data-stu-id="d7c13-176">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="d7c13-177">**Aprovação do gerente: Aprovação do gerente recebida.** 
 **Voo de Compra: O bilhete é comprado.** 
 **TakeFlight: O vôo está concluído.** 
 **ConfirmFlight: O vôo foi tomado, nenhuma compensação possível.** 
 **Fluxo de trabalho concluído com sucesso com status: Fechado.**</span><span class="sxs-lookup"><span data-stu-id="d7c13-177">**ManagerApproval: Manager approval received.**
**PurchaseFlight: Ticket is purchased.**
**TakeFlight: Flight is completed.**
**ConfirmFlight: Flight has been taken, no compensation possible.**
**Workflow completed successfully with status: Closed.**</span></span>

## <a name="nesting-compensation-activities"></a><span data-ttu-id="d7c13-178">Atividades de compensação de aninhamento</span><span class="sxs-lookup"><span data-stu-id="d7c13-178">Nesting Compensation Activities</span></span>  

<span data-ttu-id="d7c13-179"><xref:System.Activities.Statements.CompensableActivity> pode ser colocado na seção de <xref:System.Activities.Statements.CompensableActivity.Body%2A> de outro <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="d7c13-179">A <xref:System.Activities.Statements.CompensableActivity> can be placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> section of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="d7c13-180"><xref:System.Activities.Statements.CompensableActivity> não pode ser colocado em um manipulador de outro <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="d7c13-180">A <xref:System.Activities.Statements.CompensableActivity> may not be placed into a handler of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="d7c13-181">É responsabilidade de um pai <xref:System.Activities.Statements.CompensableActivity> garantir que quando é cancelado, confirmado, ou compensado, todas as atividades compensáveis filhos que eles concluíram com êxito e não foram confirmadas ou não foram compensadas deve ser compensado ou confirmadas antes que o pai conclua o cancelar, confirmação, ou a compensação.</span><span class="sxs-lookup"><span data-stu-id="d7c13-181">It is the responsibility of a parent <xref:System.Activities.Statements.CompensableActivity> to ensure that when it is canceled, confirmed, or compensated, all child compensable activities that have completed successfully and have not already been confirmed or compensated must be confirmed or compensated before the parent completes cancellation, confirmation, or compensation.</span></span> <span data-ttu-id="d7c13-182">Se isso não é modelado explicitamente <xref:System.Activities.Statements.CompensableActivity> pai compensará implicitamente atividades compensáveis filho se o pai recebeu o cancelamento ou compensa o sinal.</span><span class="sxs-lookup"><span data-stu-id="d7c13-182">If this is not modeled explicitly the parent <xref:System.Activities.Statements.CompensableActivity> will implicitly compensate child compensable activities if the parent received the cancel or compensate signal.</span></span> <span data-ttu-id="d7c13-183">Se o pai recebeu o sinal de confirmação o pai confirmará implicitamente atividades compensáveis filhos.</span><span class="sxs-lookup"><span data-stu-id="d7c13-183">If the parent received the confirm signal the parent will implicitly confirm child compensable activities.</span></span> <span data-ttu-id="d7c13-184">Se a lógica para manipular cancelamento, confirmação, ou a compensação é modelada explicitamente no manipulador de <xref:System.Activities.Statements.CompensableActivity>pai, qualquer filho tratado não explicitamente será confirmado implicitamente.</span><span class="sxs-lookup"><span data-stu-id="d7c13-184">If the logic to handle cancellation, confirmation, or compensation is explicitly modeled in the handler of the parent <xref:System.Activities.Statements.CompensableActivity>, any child not explicitly handled will be implicitly confirmed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7c13-185">Confira também</span><span class="sxs-lookup"><span data-stu-id="d7c13-185">See also</span></span>

- <xref:System.Activities.Statements.CompensableActivity>
- <xref:System.Activities.Statements.Compensate>
- <xref:System.Activities.Statements.Confirm>
- <xref:System.Activities.Statements.CompensationToken>

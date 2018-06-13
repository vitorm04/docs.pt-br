---
title: Atraso absoluto
ms.date: 03/30/2017
ms.assetid: b483139a-39bb-4560-8003-8969a8fc2cd1
ms.openlocfilehash: 3a104f6b879e9cdc899bad2201ad1ed320a38a2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518379"
---
# <a name="absolute-delay"></a><span data-ttu-id="4497f-102">Atraso absoluto</span><span class="sxs-lookup"><span data-stu-id="4497f-102">Absolute Delay</span></span>
<span data-ttu-id="4497f-103">O principal cenário para esse exemplo é atrasar até <xref:System.DateTime> especificado usando temporizadores duráveis em um aplicativo de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4497f-103">The main scenario for this sample is to delay until a specified <xref:System.DateTime> using durable timers in a workflow application.</span></span> <span data-ttu-id="4497f-104">Isso é diferente de usar a atividade interno de <xref:System.Activities.Statements.Delay> porque isso permitirá que você atrasar apenas para <xref:System.TimeSpan> determinado (ou o número de minutos/segundos).</span><span class="sxs-lookup"><span data-stu-id="4497f-104">This is different from using the built-in <xref:System.Activities.Statements.Delay> activity as this will only allow you to delay for a given <xref:System.TimeSpan> (or number of minutes/seconds).</span></span>  
  
 <span data-ttu-id="4497f-105">Alguns cenários da vida real em que você pode querer fazer essa distinção incluir o seguinte:</span><span class="sxs-lookup"><span data-stu-id="4497f-105">Some real-life scenarios in which you may want to make this distinction include the following:</span></span>  
  
1.  <span data-ttu-id="4497f-106">Você deseja atrasar enviar um email por 30 segundos para certificar-se de que você não tiver feito erros.</span><span class="sxs-lookup"><span data-stu-id="4497f-106">You want to delay sending a mail for 30 seconds to make sure you didn’t make any errors.</span></span>  
  
2.  <span data-ttu-id="4497f-107">Você está trabalhando fora do tempo estipulado e deseja atrasar todos os seus email até que horários de negócios normais (como am 8).</span><span class="sxs-lookup"><span data-stu-id="4497f-107">You are working overtime and want to delay all of your mails until normal business hours (such as 8 am).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="4497f-108">Demonstra</span><span class="sxs-lookup"><span data-stu-id="4497f-108">Demonstrates</span></span>  
  
1.  <span data-ttu-id="4497f-109"><xref:System.Activities.Statements.DurableTimerExtension> para implementar o atraso absoluto</span><span class="sxs-lookup"><span data-stu-id="4497f-109"><xref:System.Activities.Statements.DurableTimerExtension> for implementing Absolute Delay</span></span>  
  
2.  <span data-ttu-id="4497f-110">Persistência de foundation usando <xref:System.Activities.WorkflowApplication> para timers duráveis</span><span class="sxs-lookup"><span data-stu-id="4497f-110">Setting up persistence using <xref:System.Activities.WorkflowApplication> for Durable Timers</span></span>  
  
3.  <span data-ttu-id="4497f-111">Uso de <xref:System.Activities.NativeActivity%601> para usar pontos de extensibilidade</span><span class="sxs-lookup"><span data-stu-id="4497f-111">Use of <xref:System.Activities.NativeActivity%601> for using Extensibility points</span></span>  
  
4.  <span data-ttu-id="4497f-112">Uso de <xref:System.Activities.CodeActivity%601> na atividade de SendEmail</span><span class="sxs-lookup"><span data-stu-id="4497f-112">Use of <xref:System.Activities.CodeActivity%601> in the SendEmail activity</span></span>  
  
5.  <xref:System.Activities.Statements.Delay>  
  
6.  <span data-ttu-id="4497f-113">Fluxo de trabalho XAML-only</span><span class="sxs-lookup"><span data-stu-id="4497f-113">XAML-only workflow</span></span>  
  
 <span data-ttu-id="4497f-114">Este exemplo demonstra como criar uma atividade personalizado que reduz <xref:System.DateTime> e use timers duráveis para registrar a duração de atraso.</span><span class="sxs-lookup"><span data-stu-id="4497f-114">This sample demonstrates how to create a custom activity which takes in a <xref:System.DateTime> and uses durable timers to register the delay duration.</span></span> <span data-ttu-id="4497f-115">Ao usar timers duráveis, você deve usar <xref:System.Activities.NativeActivity> para criar um marcador, porque você precisará registrar este indexador com a extensão timer.</span><span class="sxs-lookup"><span data-stu-id="4497f-115">When using durable timers, you must use a <xref:System.Activities.NativeActivity> to create a bookmark, as you will need to register this bookmark with the timer extension.</span></span> <span data-ttu-id="4497f-116">Nesse exemplo, quando o timer durável expira, o método de `OnTimerExpired` será chamado.</span><span class="sxs-lookup"><span data-stu-id="4497f-116">In this sample, when the durable timer expires, the `OnTimerExpired` method will be called.</span></span> <span data-ttu-id="4497f-117">Certifique-se de que você está adicionando a extensão do timer o evento de <xref:System.Activities.NativeActivity%601.CacheMetadata%2A> para garantir que você está fornecendo o tempo de execução essas informações.</span><span class="sxs-lookup"><span data-stu-id="4497f-117">Make sure that you are adding the timer extension in the <xref:System.Activities.NativeActivity%601.CacheMetadata%2A> event to ensure you are providing the runtime with this information.</span></span> <span data-ttu-id="4497f-118">O único o outro detalhes de implementação é que você precisará implementar a lógica para converter de <xref:System.DateTime> a <xref:System.TimeSpan>, como timers duráveis recolhem somente <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="4497f-118">The only other implementation detail is that you will need to implement logic to convert from <xref:System.DateTime> to <xref:System.TimeSpan>, as durable timers only take in a <xref:System.DateTime>.</span></span> <span data-ttu-id="4497f-119">Observe que há um lapso pequeno com precisão fazendo</span><span class="sxs-lookup"><span data-stu-id="4497f-119">Do note that there is a small lapse in accuracy by doing</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4497f-120">Há uma perda de precisão pequena converter de <xref:System.DateTime> a <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="4497f-120">There is a small loss of accuracy by converting from <xref:System.DateTime> to <xref:System.TimeSpan>.</span></span>  
  
 <span data-ttu-id="4497f-121">Este exemplo também demonstra como ativar persistência para <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="4497f-121">This sample also demonstrates how to turn on persistence for a <xref:System.Activities.WorkflowApplication>.</span></span> <span data-ttu-id="4497f-122">Para esse exemplo específico, nós estaremos usando timers duráveis em que dados de fluxo de trabalho serão descarregados na base de dados de persistência durante o tempo ocioso enquanto aguarda o timer para expirar.</span><span class="sxs-lookup"><span data-stu-id="4497f-122">For this particular sample, we will be using durable timers in which the workflow data will be unloaded into the persistence database during the idle time while waiting for timer to expire.</span></span> <span data-ttu-id="4497f-123">Essa implementação também pode ser usada para outras ações de persistência.</span><span class="sxs-lookup"><span data-stu-id="4497f-123">This implementation can also be used for other persistence actions.</span></span> <span data-ttu-id="4497f-124">Este exemplo mostra como configurar a cadeia de conexão de persistência com SQL Server, e como criar o armazenamento de instância para persistir os dados para o fluxo de trabalho instância.</span><span class="sxs-lookup"><span data-stu-id="4497f-124">This sample shows how to set up the persistence connection string with SQL Server, and how to create the instance store in order to persist the data for workflow instances.</span></span> <span data-ttu-id="4497f-125">A lógica é fornecida em como proceder o fluxo de trabalho depois que um evento é gerado que faz a instância de fluxo de trabalho viável.</span><span class="sxs-lookup"><span data-stu-id="4497f-125">Logic is provided on how to resume the workflow once an event is raised which makes the workflow instance runnable.</span></span>  
  
 <span data-ttu-id="4497f-126">Como você percorrer este exemplo, você verá a hora em que o atraso interno começa e for concluído, que por sua vez fará com que uma mensagem de email a ser enviada.</span><span class="sxs-lookup"><span data-stu-id="4497f-126">As you step through this sample, you will see the time in which the built-in delay begins and completes, which in turn will cause an email message to be sent.</span></span> <span data-ttu-id="4497f-127">A partir de aí, a atividade de AbsoluteDelay paralisará até <xref:System.DateTime> especificado (ou os 0 se <xref:System.DateTime> expirou) que por sua vez eles farão com que um email em cima de expiração.</span><span class="sxs-lookup"><span data-stu-id="4497f-127">From there, the AbsoluteDelay activity will halt until a specified <xref:System.DateTime> (or 0 seconds if the <xref:System.DateTime> has expired) which in turn will send out an email upon expiration.</span></span> <span data-ttu-id="4497f-128">Isso mostrará os dois exemplos diferentes de uso da funcionalidade interna de <xref:System.Activities.Statements.Delay> contra o uso de uma atividade de AbsoluteDelay.</span><span class="sxs-lookup"><span data-stu-id="4497f-128">This will show the two different use cases of the built-in <xref:System.Activities.Statements.Delay> functionality versus using an AbsoluteDelay activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4497f-129">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="4497f-129">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4497f-130">Garanta que você tenha SQL Server Express (ou superior) instalado em seu computador</span><span class="sxs-lookup"><span data-stu-id="4497f-130">Ensure you have SQL Server Express (or higher) installed on your machine</span></span>  
  
2.  <span data-ttu-id="4497f-131">Executar setup.cmd (de WF/Basic/Services/AbsoluteDelay/CS) em um prompt de comando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] para criar o base de dados de AbsoluteDelaySampleDB, crie o esquema de persistência e criar a lógica de persistência.</span><span class="sxs-lookup"><span data-stu-id="4497f-131">Run setup.cmd (from WF/Basic/Services/AbsoluteDelay/CS) in a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt to create the AbsoluteDelaySampleDB database, create the persistence schema and create the persistence logic.</span></span>  
  
3.  <span data-ttu-id="4497f-132">Abra a solução em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4497f-132">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
4.  <span data-ttu-id="4497f-133">Especificar a duração da atividade do atraso.</span><span class="sxs-lookup"><span data-stu-id="4497f-133">Specify the Duration in the Delay activity.</span></span>  
  
5.  <span data-ttu-id="4497f-134">Especificar o ExpirationTime na atividade de AbsoluteDelay.</span><span class="sxs-lookup"><span data-stu-id="4497f-134">Specify the ExpirationTime in the AbsoluteDelay activity.</span></span>  
  
6.  <span data-ttu-id="4497f-135">Atualizar os campos de SendMailTo, de SendMailFrom, de SendMailSubject, de SendMailBody, e de SmtpHost na atividade de SendMail.</span><span class="sxs-lookup"><span data-stu-id="4497f-135">Update the SendMailTo, SendMailFrom, SendMailSubject, SendMailBody, and SmtpHost fields in the SendMail activity.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4497f-136">Se você não incorpora um host válido SMTP, o aplicativo irá acionar uma exceção SMTP.</span><span class="sxs-lookup"><span data-stu-id="4497f-136">If you do not enter a valid SMTP host, the application will throw a SMTP exception.</span></span>  
  
7.  <span data-ttu-id="4497f-137">Compile a solução selecionando **criar**, **compilar solução**.</span><span class="sxs-lookup"><span data-stu-id="4497f-137">Build the solution by selecting **Build**, **Build Solution**.</span></span>  
  
8.  <span data-ttu-id="4497f-138">Executar a solução pressionando **F5**.</span><span class="sxs-lookup"><span data-stu-id="4497f-138">Run the solution by pressing **F5**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4497f-139">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="4497f-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4497f-140">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="4497f-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4497f-141">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="4497f-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4497f-142">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="4497f-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\AbsoluteDelay`

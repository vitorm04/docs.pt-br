---
title: Transferência
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: 52b0cf35a2f8bab17252d3711f3143738c2bc39c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587762"
---
# <a name="transfer"></a><span data-ttu-id="65bac-102">Transferência</span><span class="sxs-lookup"><span data-stu-id="65bac-102">Transfer</span></span>
<span data-ttu-id="65bac-103">Este tópico descreve a transferência no modelo de rastreamento de atividades do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="65bac-103">This topic describes transfer in the Windows Communication Foundation (WCF) activity tracing model.</span></span>  
  
## <a name="transfer-definition"></a><span data-ttu-id="65bac-104">Definição de transferência</span><span class="sxs-lookup"><span data-stu-id="65bac-104">Transfer Definition</span></span>  
 <span data-ttu-id="65bac-105">As transferências entre as atividades representam as relações causal entre os eventos nas atividades relacionadas nos pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="65bac-105">Transfers between activities represent causal relationships between events in the related activities within endpoints.</span></span> <span data-ttu-id="65bac-106">Duas atividades estão relacionadas com transferências quando os fluxos de controle entre essas atividades, por exemplo, uma chamada de método que atravessa limites de atividade.</span><span class="sxs-lookup"><span data-stu-id="65bac-106">Two activities are related with transfers when control flows between these activities, for example, a method call crossing activity boundaries.</span></span> <span data-ttu-id="65bac-107">No WCF, quando bytes são recebidos no serviço, a atividade escutar na é transferida para a atividade receber bytes em que o objeto de mensagem é criado.</span><span class="sxs-lookup"><span data-stu-id="65bac-107">In WCF, when bytes are incoming on the service, the Listen At activity is transferred to the Receive Bytes activity where the message object is created.</span></span> <span data-ttu-id="65bac-108">Para obter uma lista de cenários de rastreamento de ponta a ponta e suas respectivas atividades e design de rastreamento, consulte [cenários de rastreamento de ponta a ponta](end-to-end-tracing-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="65bac-108">For a list of end-to-end tracing scenarios, and their respective activity and tracing design, see [End-To-End Tracing Scenarios](end-to-end-tracing-scenarios.md).</span></span>  
  
 <span data-ttu-id="65bac-109">Para emitir rastreamentos de transferência, use a `ActivityTracing` configuração na origem do rastreamento, conforme demonstrado pelo código de configuração a seguir.</span><span class="sxs-lookup"><span data-stu-id="65bac-109">To emit transfer traces, use the `ActivityTracing` setting on the trace source as demonstrated by the following configuration code.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a><span data-ttu-id="65bac-110">Usando a transferência para correlacionar atividades nos pontos de extremidade</span><span class="sxs-lookup"><span data-stu-id="65bac-110">Using Transfer to Correlate Activities Within Endpoints</span></span>  
 <span data-ttu-id="65bac-111">Atividades e transferências permitem que o usuário Probabilistic localize a causa raiz de um erro.</span><span class="sxs-lookup"><span data-stu-id="65bac-111">Activities and transfers permit the user to probabilistically locate the root cause of an error.</span></span> <span data-ttu-id="65bac-112">Por exemplo, se transferimos para frente e para trás entre as atividades M e N, respectivamente nos componentes M e N, e uma falha ocorre em N logo após a transferência de volta para M, podemos desenhar a conclusão de que é provável que a passagem de N dados volte para M.</span><span class="sxs-lookup"><span data-stu-id="65bac-112">For example, if we transfer back and forth between activities M and N respectively in components M and N, and a crash happens in N right after the transfer back to M, we can draw the conclusion that it is likely due to N’s passing data back to M.</span></span>  
  
 <span data-ttu-id="65bac-113">Um rastreamento de transferência é emitido da atividade M para a atividade N quando há um fluxo de controle entre M e N. Por exemplo, N executa algum trabalho para M devido a uma chamada de método que atravessa os limites das atividades.</span><span class="sxs-lookup"><span data-stu-id="65bac-113">A transfer trace is emitted from activity M to activity N when there is a flow of control between M and N. For example, N performs some work for M because of a method call crossing the activities’ boundaries.</span></span> <span data-ttu-id="65bac-114">N pode já existir ou ter sido criado.</span><span class="sxs-lookup"><span data-stu-id="65bac-114">N may already exist or has been created.</span></span> <span data-ttu-id="65bac-115">N é gerado por M quando N é uma nova atividade que executa algum trabalho para M.</span><span class="sxs-lookup"><span data-stu-id="65bac-115">N is spawned by M when N is a new activity that performs some work for M.</span></span>  
  
 <span data-ttu-id="65bac-116">Uma transferência de M para N pode não ser seguida de uma transferência de N para M. Isso ocorre porque M pode gerar algum trabalho em N e não rastrear quando N concluir esse trabalho.</span><span class="sxs-lookup"><span data-stu-id="65bac-116">A transfer from M to N may not be followed by a transfer back from N to M. This is because M can spawn some work in N and do not track when N completes that work.</span></span> <span data-ttu-id="65bac-117">Na verdade, M pode terminar antes de N concluir sua tarefa.</span><span class="sxs-lookup"><span data-stu-id="65bac-117">In fact, M can terminate before N completes its task.</span></span> <span data-ttu-id="65bac-118">Isso acontece na atividade "Open ServiceHost" (M) que gera atividades de ouvinte (N) e, em seguida, termina.</span><span class="sxs-lookup"><span data-stu-id="65bac-118">This happens in the "Open ServiceHost" activity (M) that spawns Listener activities (N) and then terminates.</span></span> <span data-ttu-id="65bac-119">Uma transferência de volta de N para M significa que N concluiu o trabalho relacionado a M.</span><span class="sxs-lookup"><span data-stu-id="65bac-119">A transfer back from N to M means that N completed the work related to M.</span></span>  
  
 <span data-ttu-id="65bac-120">N pode continuar executando outro processamento não relacionado a M, por exemplo, uma atividade de autenticador existente (N) que mantém o recebimento de solicitações de logon (M) de diferentes atividades de logon.</span><span class="sxs-lookup"><span data-stu-id="65bac-120">N can continue performing other processing unrelated to M, for example, an existing authenticator activity (N) that keeps receiving login requests (M) from different login activities.</span></span>  
  
 <span data-ttu-id="65bac-121">Uma relação de aninhamento não existe necessariamente entre as atividades M e N. Isso pode ocorrer devido a dois motivos.</span><span class="sxs-lookup"><span data-stu-id="65bac-121">A nesting relationship does not necessarily exist between activities M and N. This can happen due to two reasons.</span></span> <span data-ttu-id="65bac-122">Primeiro, quando a atividade M não monitora o processamento real executado em N, embora M iniciado N. Em segundo lugar, quando N já existir.</span><span class="sxs-lookup"><span data-stu-id="65bac-122">First, when activity M does not monitor the actual processing performed in N although M initiated N. Second, when N already exists.</span></span>  
  
## <a name="example-of-transfers"></a><span data-ttu-id="65bac-123">Exemplo de transferências</span><span class="sxs-lookup"><span data-stu-id="65bac-123">Example of Transfers</span></span>  
 <span data-ttu-id="65bac-124">O exemplo a seguir lista dois exemplos de transferência.</span><span class="sxs-lookup"><span data-stu-id="65bac-124">The following lists two transfer examples.</span></span>  
  
- <span data-ttu-id="65bac-125">Quando você cria um host de serviço, o Construtor Obtém o controle do código de chamada ou o código de chamada transfere para o construtor.</span><span class="sxs-lookup"><span data-stu-id="65bac-125">When you create a service host, the constructor gains control from the calling code, or the calling code transfers to the constructor.</span></span> <span data-ttu-id="65bac-126">Quando o Construtor conclui a execução, ele retorna o controle para o código de chamada ou o Construtor transfere de volta para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="65bac-126">When the constructor has finished executing, it returns control to the calling code, or the constructor transfers back to the calling code.</span></span> <span data-ttu-id="65bac-127">Esse é o caso de uma relação aninhada.</span><span class="sxs-lookup"><span data-stu-id="65bac-127">This is the case of a nested relationship.</span></span>  
  
- <span data-ttu-id="65bac-128">Quando um ouvinte inicia o processamento de dados de transporte, ele cria um novo thread e passa para a atividade receber bytes o contexto apropriado para processamento, passagem de controle e dados.</span><span class="sxs-lookup"><span data-stu-id="65bac-128">When a listener starts processing transport data, it creates a new thread and hands to the Receive Bytes activity the appropriate context for processing, passing control and data.</span></span> <span data-ttu-id="65bac-129">Quando esse thread terminar de processar a solicitação, a atividade receber bytes não passará nada de volta para o ouvinte.</span><span class="sxs-lookup"><span data-stu-id="65bac-129">When that thread has finished processing the request, the Receive Bytes activity passes nothing back to the listener.</span></span> <span data-ttu-id="65bac-130">Nesse caso, temos uma transferência no, mas nenhuma transferência para fora da nova atividade thread.</span><span class="sxs-lookup"><span data-stu-id="65bac-130">In this case, we have a transfer in but no transfer out of the new thread activity.</span></span> <span data-ttu-id="65bac-131">As duas atividades estão relacionadas, mas não aninhadas.</span><span class="sxs-lookup"><span data-stu-id="65bac-131">The two activities are related but not nested.</span></span>  
  
## <a name="activity-transfer-sequence"></a><span data-ttu-id="65bac-132">Sequência de transferência de atividade</span><span class="sxs-lookup"><span data-stu-id="65bac-132">Activity Transfer Sequence</span></span>  
 <span data-ttu-id="65bac-133">Uma sequência de transferência de atividade bem formada inclui as etapas a seguir.</span><span class="sxs-lookup"><span data-stu-id="65bac-133">A well-formed activity transfer sequence includes the following steps.</span></span>  
  
1. <span data-ttu-id="65bac-134">Inicie uma nova atividade, que consiste em selecionar um novo gAId.</span><span class="sxs-lookup"><span data-stu-id="65bac-134">Begin a new activity, which consists of selecting a new gAId.</span></span>  
  
2. <span data-ttu-id="65bac-135">Emitir um rastreamento de transferência para esse novo gAId da ID da atividade atual</span><span class="sxs-lookup"><span data-stu-id="65bac-135">Emit a transfer trace to that new gAId from the current activity ID</span></span>  
  
3. <span data-ttu-id="65bac-136">Definir a nova ID em TLS</span><span class="sxs-lookup"><span data-stu-id="65bac-136">Set the new ID in TLS</span></span>  
  
4. <span data-ttu-id="65bac-137">Emita um rastreamento de início para indicar o início da nova atividade pelo.</span><span class="sxs-lookup"><span data-stu-id="65bac-137">Emit a start trace to indicate the beginning of the new activity by.</span></span>  
  
5. <span data-ttu-id="65bac-138">Retornar à atividade original consiste no seguinte:</span><span class="sxs-lookup"><span data-stu-id="65bac-138">Return to the original activity consists of the following:</span></span>  
  
6. <span data-ttu-id="65bac-139">Emitir um rastreamento de transferência para o gAId original</span><span class="sxs-lookup"><span data-stu-id="65bac-139">Emit a transfer trace to the original gAId</span></span>  
  
7. <span data-ttu-id="65bac-140">Emitir um rastreamento de interrupção para indicar o final da nova atividade</span><span class="sxs-lookup"><span data-stu-id="65bac-140">Emit a Stop trace to indicate the end of the new activity</span></span>  
  
8. <span data-ttu-id="65bac-141">Defina TLS para o antigo gAId.</span><span class="sxs-lookup"><span data-stu-id="65bac-141">Set TLS to the old gAId.</span></span>  
  
 <span data-ttu-id="65bac-142">O exemplo de código a seguir demonstra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="65bac-142">The following code example demonstrates how to do this.</span></span> <span data-ttu-id="65bac-143">Este exemplo pressupõe que uma chamada de bloqueio é feita ao transferir para a nova atividade e inclui rastreamentos de suspensão/retomada.</span><span class="sxs-lookup"><span data-stu-id="65bac-143">This sample assumes a blocking call is made when transferring to the new activity, and includes suspend/resume traces.</span></span>  
  
```csharp
// 0. Create a trace source  
TraceSource ts = new TraceSource("myTS");  

// 1. remember existing ("ambient") activity for clean up  
Guid oldGuid = Trace.CorrelationManager.ActivityId;  
// this will be our new activity  
Guid newGuid = Guid.NewGuid();

// 2. call transfer, indicating that we are switching to the new AID  
ts.TraceTransfer(667, "Transferring.", newGuid);  

// 3. Suspend the current activity.  
ts.TraceEvent(TraceEventType.Suspend, 667, "Suspend: Activity " + i-1);  

// 4. set the new AID in TLS  
Trace.CorrelationManager.ActivityId = newGuid;  

// 5. Emit the start trace  
ts.TraceEvent(TraceEventType.Start, 667, "Boundary: Activity " + i);  

// trace something  
ts.TraceEvent(TraceEventType.Information, 667, "Hello from activity " + i);  

// Perform Work  
// some work.  
// Return  
ts.TraceEvent(TraceEventType.Information, 667, "Work complete on activity " + i);

// 6. Emit the transfer returning to the original activity  
ts.TraceTransfer(667, "Transferring Back.", oldGuid);  

// 7. Emit the End trace  
ts.TraceEvent(TraceEventType.Stop, 667, "Boundary: Activity " + i);  

// 8. Change the tls variable to the original AID  
Trace.CorrelationManager.ActivityId = oldGuid;

// 9. Resume the old activity  
ts.TraceEvent(TraceEventType.Resume, 667, "Resume: Activity " + i-1);  
```  
  
## <a name="see-also"></a><span data-ttu-id="65bac-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="65bac-144">See also</span></span>

- [<span data-ttu-id="65bac-145">Configurando o rastreamento</span><span class="sxs-lookup"><span data-stu-id="65bac-145">Configuring Tracing</span></span>](configuring-tracing.md)
- [<span data-ttu-id="65bac-146">Utilizando o visualizador de rastreamento de serviço para visualização de rastreamento correlacionados e soluções de problemas</span><span class="sxs-lookup"><span data-stu-id="65bac-146">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="65bac-147">Cenários de rastreamento ponta a ponta</span><span class="sxs-lookup"><span data-stu-id="65bac-147">End-To-End Tracing Scenarios</span></span>](end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="65bac-148">Ferramenta Visualizador de rastreamento de serviço (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="65bac-148">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../service-trace-viewer-tool-svctraceviewer-exe.md)

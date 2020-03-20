---
title: Transferir
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: e0ebfff97cd33e7a588a1ab92399a97a0fbec039
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185701"
---
# <a name="transfer"></a><span data-ttu-id="4491d-102">Transferir</span><span class="sxs-lookup"><span data-stu-id="4491d-102">Transfer</span></span>
<span data-ttu-id="4491d-103">Este tópico descreve a transferência no modelo de rastreamento de atividades da Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4491d-103">This topic describes transfer in the Windows Communication Foundation (WCF) activity tracing model.</span></span>  
  
## <a name="transfer-definition"></a><span data-ttu-id="4491d-104">Definição de transferência</span><span class="sxs-lookup"><span data-stu-id="4491d-104">Transfer Definition</span></span>  
 <span data-ttu-id="4491d-105">As transferências entre as atividades representam relações causais entre eventos nas atividades relacionadas dentro dos pontos finais.</span><span class="sxs-lookup"><span data-stu-id="4491d-105">Transfers between activities represent causal relationships between events in the related activities within endpoints.</span></span> <span data-ttu-id="4491d-106">Duas atividades estão relacionadas com transferências quando o controle flui entre essas atividades, por exemplo, uma chamada de método que cruza os limites da atividade.</span><span class="sxs-lookup"><span data-stu-id="4491d-106">Two activities are related with transfers when control flows between these activities, for example, a method call crossing activity boundaries.</span></span> <span data-ttu-id="4491d-107">No WCF, quando os bytes estão chegando ao serviço, a atividade Listen At é transferida para a atividade Receive Bytes onde o objeto de mensagem é criado.</span><span class="sxs-lookup"><span data-stu-id="4491d-107">In WCF, when bytes are incoming on the service, the Listen At activity is transferred to the Receive Bytes activity where the message object is created.</span></span> <span data-ttu-id="4491d-108">Para obter uma lista de cenários de rastreamento de ponta a ponta e suas respectivas atividades e desenho de rastreamento, consulte [Cenários de rastreamento de ponta a ponta](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="4491d-108">For a list of end-to-end tracing scenarios, and their respective activity and tracing design, see [End-To-End Tracing Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).</span></span>  
  
 <span data-ttu-id="4491d-109">Para emitir vestígios `ActivityTracing` de transferência, use a configuração na fonte de rastreamento, conforme demonstrado pelo seguinte código de configuração.</span><span class="sxs-lookup"><span data-stu-id="4491d-109">To emit transfer traces, use the `ActivityTracing` setting on the trace source as demonstrated by the following configuration code.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a><span data-ttu-id="4491d-110">Usando transferência para correlacionar atividades dentro de endpoints</span><span class="sxs-lookup"><span data-stu-id="4491d-110">Using Transfer to Correlate Activities Within Endpoints</span></span>  
 <span data-ttu-id="4491d-111">Atividades e transferências permitem que o usuário localize probaticamente a causa raiz de um erro.</span><span class="sxs-lookup"><span data-stu-id="4491d-111">Activities and transfers permit the user to probabilistically locate the root cause of an error.</span></span> <span data-ttu-id="4491d-112">Por exemplo, se transferirmos para frente e para trás entre as atividades M e N respectivamente nos componentes M e N, e um acidente acontecer em N logo após a transferência de volta para M, podemos chegar à conclusão de que é provável que seja devido ao repasse de dados de N de volta para M.</span><span class="sxs-lookup"><span data-stu-id="4491d-112">For example, if we transfer back and forth between activities M and N respectively in components M and N, and a crash happens in N right after the transfer back to M, we can draw the conclusion that it is likely due to N’s passing data back to M.</span></span>  
  
 <span data-ttu-id="4491d-113">Um traço de transferência é emitido da atividade M para a atividade N quando há um fluxo de controle entre M e N. Por exemplo, N realiza alguns trabalhos para M por causa de uma chamada de método que cruza os limites das atividades.</span><span class="sxs-lookup"><span data-stu-id="4491d-113">A transfer trace is emitted from activity M to activity N when there is a flow of control between M and N. For example, N performs some work for M because of a method call crossing the activities’ boundaries.</span></span> <span data-ttu-id="4491d-114">N pode já existir ou ter sido criado.</span><span class="sxs-lookup"><span data-stu-id="4491d-114">N may already exist or has been created.</span></span> <span data-ttu-id="4491d-115">N é gerado por M quando N é uma nova atividade que realiza algum trabalho para M.</span><span class="sxs-lookup"><span data-stu-id="4491d-115">N is spawned by M when N is a new activity that performs some work for M.</span></span>  
  
 <span data-ttu-id="4491d-116">Uma transferência de M para N pode não ser seguida por uma transferência de volta de N para M. Isso porque M pode gerar algum trabalho em N e não rastrear quando N completa esse trabalho.</span><span class="sxs-lookup"><span data-stu-id="4491d-116">A transfer from M to N may not be followed by a transfer back from N to M. This is because M can spawn some work in N and do not track when N completes that work.</span></span> <span data-ttu-id="4491d-117">Na verdade, M pode terminar antes que N complete sua tarefa.</span><span class="sxs-lookup"><span data-stu-id="4491d-117">In fact, M can terminate before N completes its task.</span></span> <span data-ttu-id="4491d-118">Isso acontece na atividade "Open ServiceHost" (M) que gera atividades do Ouvinte (N) e, em seguida, termina.</span><span class="sxs-lookup"><span data-stu-id="4491d-118">This happens in the "Open ServiceHost" activity (M) that spawns Listener activities (N) and then terminates.</span></span> <span data-ttu-id="4491d-119">Uma transferência de Volta de N para M significa que N completou o trabalho relacionado a M.</span><span class="sxs-lookup"><span data-stu-id="4491d-119">A transfer back from N to M means that N completed the work related to M.</span></span>  
  
 <span data-ttu-id="4491d-120">N pode continuar realizando outros processamentos não relacionados a M, por exemplo, uma atividade autenticadora (N) existente que continua recebendo solicitações de login (M) de diferentes atividades de login.</span><span class="sxs-lookup"><span data-stu-id="4491d-120">N can continue performing other processing unrelated to M, for example, an existing authenticator activity (N) that keeps receiving login requests (M) from different login activities.</span></span>  
  
 <span data-ttu-id="4491d-121">Uma relação de aninhamento não existe necessariamente entre as atividades M e N. Isso pode acontecer por duas razões.</span><span class="sxs-lookup"><span data-stu-id="4491d-121">A nesting relationship does not necessarily exist between activities M and N. This can happen due to two reasons.</span></span> <span data-ttu-id="4491d-122">Primeiro, quando a atividade M não monitora o processamento real realizado em N, embora M tenha iniciado N. Segundo, quando N já existe.</span><span class="sxs-lookup"><span data-stu-id="4491d-122">First, when activity M does not monitor the actual processing performed in N although M initiated N. Second, when N already exists.</span></span>  
  
## <a name="example-of-transfers"></a><span data-ttu-id="4491d-123">Exemplo de Transferências</span><span class="sxs-lookup"><span data-stu-id="4491d-123">Example of Transfers</span></span>  
 <span data-ttu-id="4491d-124">A seguir lista dois exemplos de transferência.</span><span class="sxs-lookup"><span data-stu-id="4491d-124">The following lists two transfer examples.</span></span>  
  
- <span data-ttu-id="4491d-125">Quando você cria um host de serviço, o construtor obtém o controle do código de chamada ou do código de chamada transfere para o construtor.</span><span class="sxs-lookup"><span data-stu-id="4491d-125">When you create a service host, the constructor gains control from the calling code, or the calling code transfers to the constructor.</span></span> <span data-ttu-id="4491d-126">Quando o construtor terminar de executar, ele retorna o controle para o código de chamada, ou o construtor transfere de volta para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="4491d-126">When the constructor has finished executing, it returns control to the calling code, or the constructor transfers back to the calling code.</span></span> <span data-ttu-id="4491d-127">É o caso de uma relação aninhada.</span><span class="sxs-lookup"><span data-stu-id="4491d-127">This is the case of a nested relationship.</span></span>  
  
- <span data-ttu-id="4491d-128">Quando um ouvinte começa a processar dados de transporte, ele cria um novo segmento e mãos para a atividade Receive Bytes o contexto apropriado para processamento, controle de passagem e dados.</span><span class="sxs-lookup"><span data-stu-id="4491d-128">When a listener starts processing transport data, it creates a new thread and hands to the Receive Bytes activity the appropriate context for processing, passing control and data.</span></span> <span data-ttu-id="4491d-129">Quando esse segmento tiver terminado o processamento da solicitação, a atividade Receber Bytes não repassa nada para o ouvinte.</span><span class="sxs-lookup"><span data-stu-id="4491d-129">When that thread has finished processing the request, the Receive Bytes activity passes nothing back to the listener.</span></span> <span data-ttu-id="4491d-130">Neste caso, temos uma transferência, mas nenhuma transferência para fora da nova atividade de thread.</span><span class="sxs-lookup"><span data-stu-id="4491d-130">In this case, we have a transfer in but no transfer out of the new thread activity.</span></span> <span data-ttu-id="4491d-131">As duas atividades estão relacionadas, mas não estão aninhadas.</span><span class="sxs-lookup"><span data-stu-id="4491d-131">The two activities are related but not nested.</span></span>  
  
## <a name="activity-transfer-sequence"></a><span data-ttu-id="4491d-132">Sequência de transferência de atividades</span><span class="sxs-lookup"><span data-stu-id="4491d-132">Activity Transfer Sequence</span></span>  
 <span data-ttu-id="4491d-133">Uma seqüência de transferência de atividade bem formada inclui as seguintes etapas.</span><span class="sxs-lookup"><span data-stu-id="4491d-133">A well-formed activity transfer sequence includes the following steps.</span></span>  
  
1. <span data-ttu-id="4491d-134">Inicie uma nova atividade, que consiste em selecionar um novo gAId.</span><span class="sxs-lookup"><span data-stu-id="4491d-134">Begin a new activity, which consists of selecting a new gAId.</span></span>  
  
2. <span data-ttu-id="4491d-135">Emita um traço de transferência para esse novo gAId do ID de atividade atual</span><span class="sxs-lookup"><span data-stu-id="4491d-135">Emit a transfer trace to that new gAId from the current activity ID</span></span>  
  
3. <span data-ttu-id="4491d-136">Defina o novo ID em TLS</span><span class="sxs-lookup"><span data-stu-id="4491d-136">Set the new ID in TLS</span></span>  
  
4. <span data-ttu-id="4491d-137">Emita um traço de início para indicar o início da nova atividade por.</span><span class="sxs-lookup"><span data-stu-id="4491d-137">Emit a start trace to indicate the beginning of the new activity by.</span></span>  
  
5. <span data-ttu-id="4491d-138">O retorno à atividade original consiste no seguinte:</span><span class="sxs-lookup"><span data-stu-id="4491d-138">Return to the original activity consists of the following:</span></span>  
  
6. <span data-ttu-id="4491d-139">Emita um traço de transferência para o gAId original</span><span class="sxs-lookup"><span data-stu-id="4491d-139">Emit a transfer trace to the original gAId</span></span>  
  
7. <span data-ttu-id="4491d-140">Emita um rastreamento stop para indicar o fim da nova atividade</span><span class="sxs-lookup"><span data-stu-id="4491d-140">Emit a Stop trace to indicate the end of the new activity</span></span>  
  
8. <span data-ttu-id="4491d-141">Defina O TLS para o antigo gAId.</span><span class="sxs-lookup"><span data-stu-id="4491d-141">Set TLS to the old gAId.</span></span>  
  
 <span data-ttu-id="4491d-142">O exemplo de código a seguir demonstra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="4491d-142">The following code example demonstrates how to do this.</span></span> <span data-ttu-id="4491d-143">Esta amostra assume que uma chamada de bloqueio é feita ao transferir para a nova atividade, e inclui rastreamentos de suspensão/currículo.</span><span class="sxs-lookup"><span data-stu-id="4491d-143">This sample assumes a blocking call is made when transferring to the new activity, and includes suspend/resume traces.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4491d-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="4491d-144">See also</span></span>

- [<span data-ttu-id="4491d-145">Configurando o rastreamento</span><span class="sxs-lookup"><span data-stu-id="4491d-145">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [<span data-ttu-id="4491d-146">Utilizando o visualizador de rastreamento de serviço para visualização de rastreamento correlacionados e soluções de problemas</span><span class="sxs-lookup"><span data-stu-id="4491d-146">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="4491d-147">Cenários de rastreamento ponta a ponta</span><span class="sxs-lookup"><span data-stu-id="4491d-147">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="4491d-148">Ferramenta Visualizador de rastreamento de serviço (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="4491d-148">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)

---
title: Propagação
ms.date: 03/30/2017
ms.assetid: f8181e75-d693-48d1-b333-a776ad3b382a
ms.openlocfilehash: 732ae5cb1ce311b78728f8d5de0fd9102bf32499
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578949"
---
# <a name="propagation"></a><span data-ttu-id="c764f-102">Propagação</span><span class="sxs-lookup"><span data-stu-id="c764f-102">Propagation</span></span>
<span data-ttu-id="c764f-103">Este tópico descreve a propagação de atividade no modelo de rastreamento Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c764f-103">This topic describes activity propagation in the Windows Communication Foundation (WCF) tracing model.</span></span>  
  
## <a name="using-propagation-to-correlate-activities-across-endpoints"></a><span data-ttu-id="c764f-104">Usando a propagação para correlacionar atividades entre pontos de extremidade</span><span class="sxs-lookup"><span data-stu-id="c764f-104">Using Propagation to Correlate Activities Across Endpoints</span></span>  
 <span data-ttu-id="c764f-105">A propagação fornece ao usuário uma correlação direta de rastreamentos de erros para a mesma unidade de processamento entre pontos de extremidade de aplicativo, por exemplo, uma solicitação.</span><span class="sxs-lookup"><span data-stu-id="c764f-105">Propagation provides the user with direct correlation of error traces for the same unit of processing across application endpoints, for example, a request.</span></span> <span data-ttu-id="c764f-106">Os erros emitidos em diferentes pontos de extremidade para a mesma unidade de processamento são agrupados na mesma atividade, mesmo entre domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c764f-106">Errors emitted at different endpoints for the same unit of processing are grouped in the same activity, even across application domains.</span></span> <span data-ttu-id="c764f-107">Isso é feito por meio da propagação da ID da atividade nos cabeçalhos da mensagem.</span><span class="sxs-lookup"><span data-stu-id="c764f-107">This is done through propagation of the activity ID in the message headers.</span></span> <span data-ttu-id="c764f-108">Portanto, se um cliente expirar devido a um erro interno no servidor, os dois erros aparecerão na mesma atividade para correlação direta.</span><span class="sxs-lookup"><span data-stu-id="c764f-108">Therefore, if a client times out because of an internal error in the server, both errors appear in the same activity for direct correlation.</span></span>  
  
 <span data-ttu-id="c764f-109">Para fazer isso, use a `ActivityTracing` configuração, conforme demonstrado no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="c764f-109">To do this, use the `ActivityTracing` setting as demonstrated in the previous example.</span></span> <span data-ttu-id="c764f-110">Além disso, defina o `propagateActivity` atributo para a `System.ServiceModel` origem do rastreamento em todos os pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="c764f-110">In addition, set the `propagateActivity` attribute for the `System.ServiceModel` trace source at all endpoints.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity="true" >  
```  
  
 <span data-ttu-id="c764f-111">A propagação de atividade é um recurso configurável que faz com que o WCF adicione um cabeçalho a mensagens de saída, que inclui a ID de atividade no TLS.</span><span class="sxs-lookup"><span data-stu-id="c764f-111">Activity propagation is a configurable capability that causes WCF to add a header to outbound messages, which includes the activity ID on the TLS.</span></span> <span data-ttu-id="c764f-112">Ao incluir isso nos rastreamentos subsequentes no lado do servidor, podemos correlacionar as atividades do cliente e do servidor.</span><span class="sxs-lookup"><span data-stu-id="c764f-112">By including this on subsequent traces on the server side, we can correlate client and server activities.</span></span>  
  
## <a name="propagation-definition"></a><span data-ttu-id="c764f-113">Definição de propagação</span><span class="sxs-lookup"><span data-stu-id="c764f-113">Propagation Definition</span></span>  
 <span data-ttu-id="c764f-114">A gAId da atividade M será propagada para a atividade N se todas as condições a seguir se aplicarem.</span><span class="sxs-lookup"><span data-stu-id="c764f-114">Activity M’s gAId is propagated to activity N if all of the following conditions apply.</span></span>  
  
- <span data-ttu-id="c764f-115">N é criado por causa de M</span><span class="sxs-lookup"><span data-stu-id="c764f-115">N is created because of M</span></span>  
  
- <span data-ttu-id="c764f-116">O gAId da M é conhecido como N</span><span class="sxs-lookup"><span data-stu-id="c764f-116">M’s gAId is known to N</span></span>  
  
- <span data-ttu-id="c764f-117">GAId de N é igual a gAId de M.</span><span class="sxs-lookup"><span data-stu-id="c764f-117">N's gAId is equal to M’s gAId.</span></span>  
  
 <span data-ttu-id="c764f-118">O gAId é propagado por meio do cabeçalho da mensagem ActivityId, conforme ilustrado no esquema XML a seguir.</span><span class="sxs-lookup"><span data-stu-id="c764f-118">The gAId is propagated through the ActivityId message header, as illustrated in the following XML schema.</span></span>  
  
```xml  
<xsd:element name="ActivityId" type="integer" minOccurs="0">  
  <xsd:attribute name="CorrelationId" type="integer" minOccurs="0"/>  
</xsd:element>  
```  
  
 <span data-ttu-id="c764f-119">Veja a seguir um exemplo do cabeçalho da mensagem.</span><span class="sxs-lookup"><span data-stu-id="c764f-119">The following is an example of the message header.</span></span>  
  
```xml  
<MessageLogTraceRecord>  
  <s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope"
                      xmlns:a="http://www.w3.org/2005/08/addressing">  
    <s:Header>  
      <a:Action s:mustUnderstand="1">http://Microsoft.ServiceModel.Samples/ICalculator/Subtract  
      </a:Action>  
      <a:MessageID>urn:uuid:f0091eae-d339-4c7e-9408-ece34602f1ce  
      </a:MessageID>  
      <ActivityId CorrelationId="f94c6af1-7d5d-4295-b693-4670a8a0ce34"
               xmlns="http://schemas.microsoft.com/2004/09/ServiceModel/Diagnostics">  
        17f59a29-b435-4a15-bf7b-642ffc40eac8  
      </ActivityId>  
      <a:ReplyTo>  
          <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>  
      </a:ReplyTo>  
      <a:To s:mustUnderstand="1">net.tcp://localhost/servicemodelsamples/service</a:To>  
   </s:Header>  
   <s:Body>  
     <Subtract xmlns="http://Microsoft.ServiceModel.Samples">  
       <n1>145</n1>  
       <n2>76.54</n2>  
     </Subtract>  
   </s:Body>  
  </s:Envelope>  
</MessageLogTraceRecord>  
```  
  
## <a name="propagation-and-activity-boundaries"></a><span data-ttu-id="c764f-120">Limites de atividade e propagação</span><span class="sxs-lookup"><span data-stu-id="c764f-120">Propagation and Activity Boundaries</span></span>  
 <span data-ttu-id="c764f-121">Quando a ID da atividade é propagada entre pontos de extremidade, o receptor da mensagem emite um rastreamento de início e parada com essa ID de atividade (propagada).</span><span class="sxs-lookup"><span data-stu-id="c764f-121">When the activity ID is propagated across endpoints, the message receiver emits a Start and Stop traces with that (propagated) activity ID.</span></span> <span data-ttu-id="c764f-122">Portanto, há um rastreamento de iniciar e parar com esse gAId de cada origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c764f-122">Therefore, there is a Start and Stop trace with that gAId from each trace source.</span></span> <span data-ttu-id="c764f-123">Se os pontos de extremidade estiverem no mesmo processo e usarem o mesmo nome de origem de rastreamento, vários iniciar e parar com o mesmo layout (mesmo gAId, mesma origem de rastreamento, mesmo processo) serão criados.</span><span class="sxs-lookup"><span data-stu-id="c764f-123">If the endpoints are in the same process and use the same trace source name, multiple Start and Stop with the same lAId (same gAId, same trace source, same process) are created.</span></span>  
  
## <a name="synchronization"></a><span data-ttu-id="c764f-124">Sincronização</span><span class="sxs-lookup"><span data-stu-id="c764f-124">Synchronization</span></span>  
 <span data-ttu-id="c764f-125">Para sincronizar eventos entre pontos de extremidade que são executados em computadores diferentes, uma CorrelationId é adicionada ao cabeçalho ActivityId que é propagado nas mensagens.</span><span class="sxs-lookup"><span data-stu-id="c764f-125">To synchronize events across endpoints that run on different machines, a CorrelationId is added to the ActivityId header that is propagated in messages.</span></span> <span data-ttu-id="c764f-126">As ferramentas podem usar essa ID para sincronizar eventos entre máquinas com discrepância de relógio.</span><span class="sxs-lookup"><span data-stu-id="c764f-126">Tools can use this ID to synchronize events across machines with clock discrepancy.</span></span> <span data-ttu-id="c764f-127">Especificamente, a ferramenta do Visualizador de rastreamento de serviço usa essa ID para mostrar fluxos de mensagens entre pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="c764f-127">Specifically, the Service Trace Viewer tool uses this ID for showing message flows between endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c764f-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c764f-128">See also</span></span>

- [<span data-ttu-id="c764f-129">Configurando o rastreamento</span><span class="sxs-lookup"><span data-stu-id="c764f-129">Configuring Tracing</span></span>](configuring-tracing.md)
- [<span data-ttu-id="c764f-130">Utilizando o visualizador de rastreamento de serviço para visualização de rastreamento correlacionados e soluções de problemas</span><span class="sxs-lookup"><span data-stu-id="c764f-130">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="c764f-131">Cenários de rastreamento ponta a ponta</span><span class="sxs-lookup"><span data-stu-id="c764f-131">End-To-End Tracing Scenarios</span></span>](end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="c764f-132">Ferramenta Visualizador de rastreamento de serviço (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="c764f-132">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../service-trace-viewer-tool-svctraceviewer-exe.md)

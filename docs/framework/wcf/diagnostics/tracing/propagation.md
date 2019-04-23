---
title: Propagação
ms.date: 03/30/2017
ms.assetid: f8181e75-d693-48d1-b333-a776ad3b382a
ms.openlocfilehash: faa0e6ecb53963587e3fc253cd8beae1dc2c4bf5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59154031"
---
# <a name="propagation"></a><span data-ttu-id="4cf42-102">Propagação</span><span class="sxs-lookup"><span data-stu-id="4cf42-102">Propagation</span></span>
<span data-ttu-id="4cf42-103">Este tópico descreve a propagação de atividade no modelo de rastreamento do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4cf42-103">This topic describes activity propagation in the Windows Communication Foundation (WCF) tracing model.</span></span>  
  
## <a name="using-propagation-to-correlate-activities-across-endpoints"></a><span data-ttu-id="4cf42-104">Usando a propagação para correlacionar atividades entre pontos de extremidade</span><span class="sxs-lookup"><span data-stu-id="4cf42-104">Using Propagation to Correlate Activities Across Endpoints</span></span>  
 <span data-ttu-id="4cf42-105">Propagação fornece que o usuário com uma correlação direta de erro rastreamentos para a mesma unidade de processamento entre pontos de extremidade do aplicativo, por exemplo, uma solicitação.</span><span class="sxs-lookup"><span data-stu-id="4cf42-105">Propagation provides the user with direct correlation of error traces for the same unit of processing across application endpoints, for example, a request.</span></span> <span data-ttu-id="4cf42-106">Emitido em diferentes pontos de extremidade para a mesma unidade de processamento de erros são agrupados na mesma atividade, até mesmo entre domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4cf42-106">Errors emitted at different endpoints for the same unit of processing are grouped in the same activity, even across application domains.</span></span> <span data-ttu-id="4cf42-107">Isso é feito por meio de propagação da ID de atividade nos cabeçalhos da mensagem.</span><span class="sxs-lookup"><span data-stu-id="4cf42-107">This is done through propagation of the activity ID in the message headers.</span></span> <span data-ttu-id="4cf42-108">Portanto, se um cliente de tempo limite devido a um erro interno no servidor, ambos os erros aparecem na mesma atividade para correlação direta.</span><span class="sxs-lookup"><span data-stu-id="4cf42-108">Therefore, if a client times out because of an internal error in the server, both errors appear in the same activity for direct correlation.</span></span>  
  
 <span data-ttu-id="4cf42-109">Para fazer isso, use o `ActivityTracing` configuração conforme demonstrado no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="4cf42-109">To do this, use the `ActivityTracing` setting as demonstrated in the previous example.</span></span> <span data-ttu-id="4cf42-110">Além disso, defina as `propagateActivity` de atributo para o `System.ServiceModel` origem de rastreamento em todos os pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="4cf42-110">In addition, set the `propagateActivity` attribute for the `System.ServiceModel` trace source at all endpoints.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity="true" >  
```  
  
 <span data-ttu-id="4cf42-111">Propagação de atividade é uma funcionalidade configurável que faz com que o WCF adicionar um cabeçalho para as mensagens de saída, que inclui a ID de atividade no TLS.</span><span class="sxs-lookup"><span data-stu-id="4cf42-111">Activity propagation is a configurable capability that causes WCF to add a header to outbound messages, which includes the activity ID on the TLS.</span></span> <span data-ttu-id="4cf42-112">Por isso em rastreamentos subsequentes no lado do servidor, incluindo possamos correlacionar atividades do cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="4cf42-112">By including this on subsequent traces on the server side, we can correlate client and server activities.</span></span>  
  
## <a name="propagation-definition"></a><span data-ttu-id="4cf42-113">Definição de propagação</span><span class="sxs-lookup"><span data-stu-id="4cf42-113">Propagation Definition</span></span>  
 <span data-ttu-id="4cf42-114">GAId da atividade M é propagada para a atividade N se todas as condições a seguir se aplicam.</span><span class="sxs-lookup"><span data-stu-id="4cf42-114">Activity M’s gAId is propagated to activity N if all of the following conditions apply.</span></span>  
  
-   <span data-ttu-id="4cf42-115">N é criado por causa de M</span><span class="sxs-lookup"><span data-stu-id="4cf42-115">N is created because of M</span></span>  
  
-   <span data-ttu-id="4cf42-116">GAId do M é conhecido como N</span><span class="sxs-lookup"><span data-stu-id="4cf42-116">M’s gAId is known to N</span></span>  
  
-   <span data-ttu-id="4cf42-117">GAId do N é igual a gAId do M.</span><span class="sxs-lookup"><span data-stu-id="4cf42-117">N's gAId is equal to M’s gAId.</span></span>  
  
 <span data-ttu-id="4cf42-118">O gAId é propagada por meio do cabeçalho da mensagem ActivityId, conforme ilustrado no seguinte esquema XML.</span><span class="sxs-lookup"><span data-stu-id="4cf42-118">The gAId is propagated through the ActivityId message header, as illustrated in the following XML schema.</span></span>  
  
```xml  
<xsd:element name="ActivityId" type="integer" minOccurs="0">  
  <xsd:attribute name="CorrelationId" type="integer" minOccurs="0"/>  
</xsd:element>  
```  
  
 <span data-ttu-id="4cf42-119">O exemplo a seguir é um exemplo do cabeçalho da mensagem.</span><span class="sxs-lookup"><span data-stu-id="4cf42-119">The following is an example of the message header.</span></span>  
  
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
  
## <a name="propagation-and-activity-boundaries"></a><span data-ttu-id="4cf42-120">Limites de atividade e de propagação</span><span class="sxs-lookup"><span data-stu-id="4cf42-120">Propagation and Activity Boundaries</span></span>  
 <span data-ttu-id="4cf42-121">Quando a ID da atividade for propagada entre pontos de extremidade, o destinatário da mensagem emite um início e parada rastreia com essa ID de atividade (propagada).</span><span class="sxs-lookup"><span data-stu-id="4cf42-121">When the activity ID is propagated across endpoints, the message receiver emits a Start and Stop traces with that (propagated) activity ID.</span></span> <span data-ttu-id="4cf42-122">Portanto, há um rastreamento de início e parada com esse gAId em cada origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="4cf42-122">Therefore, there is a Start and Stop trace with that gAId from each trace source.</span></span> <span data-ttu-id="4cf42-123">Se os pontos de extremidade estiverem no mesmo processo e usem o mesmo nome de origem de rastreamento, são criados vários iniciar e parar com o mesmo layout (mesmo gAId, mesma origem de rastreamento, mesmo processo).</span><span class="sxs-lookup"><span data-stu-id="4cf42-123">If the endpoints are in the same process and use the same trace source name, multiple Start and Stop with the same lAId (same gAId, same trace source, same process) are created.</span></span>  
  
## <a name="synchronization"></a><span data-ttu-id="4cf42-124">Sincronização</span><span class="sxs-lookup"><span data-stu-id="4cf42-124">Synchronization</span></span>  
 <span data-ttu-id="4cf42-125">Para sincronizar os eventos em pontos de extremidade que são executados em máquinas diferentes, uma CorrelationId é adicionada ao cabeçalho da ActivityId é propagado nas mensagens.</span><span class="sxs-lookup"><span data-stu-id="4cf42-125">To synchronize events across endpoints that run on different machines, a CorrelationId is added to the ActivityId header that is propagated in messages.</span></span> <span data-ttu-id="4cf42-126">Ferramentas podem usar essa ID para sincronizar os eventos em máquinas com discrepância de relógio.</span><span class="sxs-lookup"><span data-stu-id="4cf42-126">Tools can use this ID to synchronize events across machines with clock discrepancy.</span></span> <span data-ttu-id="4cf42-127">Especificamente, a ferramenta Visualizador de rastreamento de serviço usa essa ID para mostrar os fluxos de mensagens entre pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="4cf42-127">Specifically, the Service Trace Viewer tool uses this ID for showing message flows between endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cf42-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4cf42-128">See also</span></span>

- [<span data-ttu-id="4cf42-129">Configurando o rastreamento</span><span class="sxs-lookup"><span data-stu-id="4cf42-129">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [<span data-ttu-id="4cf42-130">Usando o Visualizador de Rastreamento de Serviço para exibir rastreamentos correlacionados e solucionar problemas</span><span class="sxs-lookup"><span data-stu-id="4cf42-130">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="4cf42-131">Cenários de rastreamento ponta a ponta</span><span class="sxs-lookup"><span data-stu-id="4cf42-131">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="4cf42-132">Ferramenta Visualizador de rastreamento de serviço (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="4cf42-132">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)

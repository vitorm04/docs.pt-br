---
title: Propagação
ms.date: 03/30/2017
ms.assetid: f8181e75-d693-48d1-b333-a776ad3b382a
ms.openlocfilehash: f4e92c6dec163d191c507dd80bb0d9dc129c6e96
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803231"
---
# <a name="propagation"></a>Propagação
Este tópico descreve a propagação de atividade no modelo de rastreamento do Windows Communication Foundation (WCF).  
  
## <a name="using-propagation-to-correlate-activities-across-endpoints"></a>Usando a propagação para correlacionar atividades entre pontos de extremidade  
 Propagação fornece que ao usuário uma correlação direta de erro rastreamentos para a mesma unidade de processamento entre pontos de extremidade do aplicativo, por exemplo, uma solicitação. Emitido em diferentes pontos de extremidade para a mesma unidade de processamento de erros são agrupados na mesma atividade, mesmo em domínios de aplicativo. Isso é feito por meio de propagação de ID de atividade nos cabeçalhos da mensagem. Portanto, se um cliente de tempo limite devido a um erro interno no servidor, ambos os erros aparecem na mesma atividade de correlação direta.  
  
 Para fazer isso, use o `ActivityTracing` configuração como demonstrado no exemplo anterior. Além disso, defina o `propagateActivity` de atributo para o `System.ServiceModel` em todos os pontos de extremidade de origem do rastreamento.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity="true" >  
```  
  
 Propagação de atividade é um recurso configurável que faz com que o WCF adicionar um cabeçalho para as mensagens de saída, que inclui a ID de atividade no TLS. Incluindo isso em rastreamentos subsequentes no lado do servidor, podemos pode correlacionar atividades do cliente e servidor.  
  
## <a name="propagation-definition"></a>Definição de propagação  
 GAId da atividade M é propagada para a atividade N se todas as seguintes condições se aplicarem.  
  
-   N é criado devido a M  
  
-   GAId do M é conhecido por N  
  
-   GAId do N é igual ao gAId do M.  
  
 O gAId é propagada por meio do cabeçalho da mensagem ActivityId, conforme ilustrado no seguinte esquema XML.  
  
```xml  
<xsd:element name="ActivityId" type="integer" minOccurs="0">  
  <xsd:attribute name="CorrelationId" type="integer" minOccurs="0"/>  
</xsd:element>  
```  
  
 Este é um exemplo do cabeçalho da mensagem.  
  
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
          <a:Address>http://www.w3.org/2005/08/addressing/anonymous  
          </a:Address>  
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
  
## <a name="propagation-and-activity-boundaries"></a>Propagação e limites de atividade  
 Quando a ID da atividade é propagada por pontos de extremidade, o receptor da mensagem emite um início e parada rastreamentos com essa ID de atividade (propagadas). Portanto, há um rastreamento de início e parada com que gAId em cada origem de rastreamento. Se os pontos de extremidade estão no mesmo processo e usam o mesmo nome de origem de rastreamento, são criados vários iniciar e parar com o mesmo layout (gAId mesmo, mesma origem de rastreamento, mesmo processo).  
  
## <a name="synchronization"></a>Sincronização  
 Para sincronizar os eventos em pontos de extremidade que são executados em computadores diferentes, um CorrelationId é adicionado ao cabeçalho da ActivityId é propagado de mensagens. Ferramentas podem usá-la para sincronizar os eventos em máquinas com discrepância de relógio. Especificamente, a ferramenta do Visualizador de rastreamento de serviço usa essa ID para mostrar os fluxos de mensagens entre pontos de extremidade.  
  
## <a name="see-also"></a>Consulte também  
 [Configurando o rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [Usando o Visualizador de Rastreamento de Serviço para exibir rastreamentos correlacionados e solucionar problemas](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [Cenários de rastreamento ponta a ponta](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [Ferramenta Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)

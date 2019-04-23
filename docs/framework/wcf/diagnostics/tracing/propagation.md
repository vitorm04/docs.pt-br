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
# <a name="propagation"></a>Propagação
Este tópico descreve a propagação de atividade no modelo de rastreamento do Windows Communication Foundation (WCF).  
  
## <a name="using-propagation-to-correlate-activities-across-endpoints"></a>Usando a propagação para correlacionar atividades entre pontos de extremidade  
 Propagação fornece que o usuário com uma correlação direta de erro rastreamentos para a mesma unidade de processamento entre pontos de extremidade do aplicativo, por exemplo, uma solicitação. Emitido em diferentes pontos de extremidade para a mesma unidade de processamento de erros são agrupados na mesma atividade, até mesmo entre domínios de aplicativo. Isso é feito por meio de propagação da ID de atividade nos cabeçalhos da mensagem. Portanto, se um cliente de tempo limite devido a um erro interno no servidor, ambos os erros aparecem na mesma atividade para correlação direta.  
  
 Para fazer isso, use o `ActivityTracing` configuração conforme demonstrado no exemplo anterior. Além disso, defina as `propagateActivity` de atributo para o `System.ServiceModel` origem de rastreamento em todos os pontos de extremidade.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity="true" >  
```  
  
 Propagação de atividade é uma funcionalidade configurável que faz com que o WCF adicionar um cabeçalho para as mensagens de saída, que inclui a ID de atividade no TLS. Por isso em rastreamentos subsequentes no lado do servidor, incluindo possamos correlacionar atividades do cliente e servidor.  
  
## <a name="propagation-definition"></a>Definição de propagação  
 GAId da atividade M é propagada para a atividade N se todas as condições a seguir se aplicam.  
  
-   N é criado por causa de M  
  
-   GAId do M é conhecido como N  
  
-   GAId do N é igual a gAId do M.  
  
 O gAId é propagada por meio do cabeçalho da mensagem ActivityId, conforme ilustrado no seguinte esquema XML.  
  
```xml  
<xsd:element name="ActivityId" type="integer" minOccurs="0">  
  <xsd:attribute name="CorrelationId" type="integer" minOccurs="0"/>  
</xsd:element>  
```  
  
 O exemplo a seguir é um exemplo do cabeçalho da mensagem.  
  
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
  
## <a name="propagation-and-activity-boundaries"></a>Limites de atividade e de propagação  
 Quando a ID da atividade for propagada entre pontos de extremidade, o destinatário da mensagem emite um início e parada rastreia com essa ID de atividade (propagada). Portanto, há um rastreamento de início e parada com esse gAId em cada origem de rastreamento. Se os pontos de extremidade estiverem no mesmo processo e usem o mesmo nome de origem de rastreamento, são criados vários iniciar e parar com o mesmo layout (mesmo gAId, mesma origem de rastreamento, mesmo processo).  
  
## <a name="synchronization"></a>Sincronização  
 Para sincronizar os eventos em pontos de extremidade que são executados em máquinas diferentes, uma CorrelationId é adicionada ao cabeçalho da ActivityId é propagado nas mensagens. Ferramentas podem usar essa ID para sincronizar os eventos em máquinas com discrepância de relógio. Especificamente, a ferramenta Visualizador de rastreamento de serviço usa essa ID para mostrar os fluxos de mensagens entre pontos de extremidade.  
  
## <a name="see-also"></a>Consulte também

- [Configurando o rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [Usando o Visualizador de Rastreamento de Serviço para exibir rastreamentos correlacionados e solucionar problemas](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Cenários de rastreamento ponta a ponta](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [Ferramenta Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)

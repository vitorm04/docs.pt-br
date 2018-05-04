---
title: '&lt;adicionar&gt; &lt;filtros&gt;'
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: 2a26a94c01fdb04b8a9e2d381a28cc909bbdac8f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltfiltersgt"></a>&lt;adicionar&gt; &lt;filtros&gt;
Um filtro XPath que especifica o tipo de mensagem a ser registrada.  
  
 \<system.ServiceModel>  
\<diagnóstico >  
\<messageLogging >  
\<Filtros >  
\<add>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<filters>  
   <add filter="String"/>  
</filters>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|filtrar|Uma cadeia de caracteres que especifica uma consulta em um documento XML definido por uma expressão XPath 1.0. Para obter mais informações, consulte <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<Filtros >](../../../../../docs/framework/configure-apps/file-schema/wcf/filters.md)|Contém uma coleção de filtros XPath usados para controlar que tipo de mensagem é registrado.|  
  
## <a name="remarks"></a>Comentários  
 Os filtros são aplicados apenas na camada de transporte, especificada por `logMessagesAtTransportLevel` é `true`. Log de mensagem malformada e nível de serviço não são afetadas por filtros.  
  
 Para adicionar um filtro à coleção, use o `add` palavra-chave. Quando um ou mais filtros são definidos, apenas as mensagens que correspondem a pelo menos um dos filtros são registradas. Se nenhum filtro for definido, todas as mensagens passam.  
  
 Os filtros oferece suporte a sintaxe completa do XPath e são aplicados na ordem em que aparecem no arquivo de configuração. Um filtro sintaticamente incorreto resulta em uma exceção de configuração.  
  
 Este é um exemplo de como configurar um filtro que registra apenas as mensagens que têm uma seção de cabeçalho SOAP.  
  
## <a name="example"></a>Exemplo  
 Este é um exemplo de como configurar um filtro que registra apenas as mensagens que têm uma seção de cabeçalho SOAP.  
  
```xml  
<messageLogging logEntireMessage="true"  
     logMalformedMessages="true" logMessagesAtServiceLevel="true"  
     logMessagesAtTransportLevel="true" maxMessagesToLog="420">  
     <filters>  
        <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">  
                        /soap:Envelope/soap:Headers  
        </add>  
     </filters>  
</messageLogging>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>  
 <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>  
 [Configurando registros de mensagens em log](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)  
 [Configurando registros de mensagens em log](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)  
 [\<messageLogging >](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)

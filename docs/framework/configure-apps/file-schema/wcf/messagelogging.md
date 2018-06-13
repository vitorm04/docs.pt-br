---
title: '&lt;messageLogging&gt;'
ms.date: 03/30/2017
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
ms.openlocfilehash: e137070b71cf8a481eef3ea16260c135e29b4932
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750681"
---
# <a name="ltmessagelogginggt"></a>&lt;messageLogging&gt;
Este elemento define as configurações para os recursos de log de mensagens do Windows Communication Foundation (WCF).  
  
 \<system.ServiceModel>  
\<diagnóstico >  
\<messageLogging >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.serviceModel>  
   <diagnostics>  
       <messageLogging logEntireMessage="Boolean"  
          logMalformedMessages="Boolean"  
          logMessagesAtServiceLevel="Boolean"  
          logMessagesAtTransportLevel="Boolean"  
                    maxMessagesToLog="Integer"  
          maxSizeOfMessageToLog="Integer" >  
          <filters>  
                            <clear />  
          </filters>  
       </messageLogging>  
   </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`logEntireMessage`|Um valor booleano que especifica se a mensagem inteira (cabeçalho e corpo) é registrada. O padrão é `false`, que significa que somente o cabeçalho da mensagem é registrada. Essa configuração afeta todos os níveis de log de mensagem (serviço, transporte e malformado).|  
|`logMalformedMessages`|Um valor booleano que especifica se as mensagens malformadas são registradas. As mensagens malformadas não contam para o `maxMessagesToLog`. O padrão é `false`.|  
|`logMessagesAtServiceLevel`|Um valor booleano que especifica se as mensagens são rastreadas no nível de serviço (antes de transformações relacionadas a criptografia e transporte). O padrão é `false`.|  
|`logMessagesAtTransportLevel`|Um valor booleano que especifica se as mensagens são rastreadas no nível do transporte. Todos os filtros especificados no arquivo de configuração são aplicados e somente as mensagens que correspondem aos filtros são rastreadas. O padrão é `false`.|  
|`maxMessagesToLog`|Um inteiro positivo que especifica o número máximo de mensagens a serem registradas. O padrão é 1000.|  
|`maxSizeOfMessageToLog`|Um inteiro positivo que especifica o tamanho máximo, em bytes, de uma mensagem para log. Maiores que o limite de mensagens não serão registradas. Essa configuração afeta todos os níveis de rastreamento. O padrão é 262144(0x4000).|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|filtros|O `filters` elemento contém uma coleção de filtros de XPath. Quando o log de mensagens de transporte está habilitado (`logMessagesAtTransportLevel` é `true`), somente as mensagens que correspondem os filtros serão registradas.<br /><br /> Os filtros são aplicados apenas na camada de transporte. Log de mensagem malformada e nível de serviço não são afetadas por filtros.<br /><br /> O atributo somente para esse elemento, `filter`, é um XpathFilter.<br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|diagnósticos|Define as configurações de WCF para inspeção de tempo de execução e o controle para o administrador.|  
  
## <a name="remarks"></a>Comentários  
 As mensagens são registradas em três diferentes níveis da pilha: serviço, transporte e malformado. Cada nível pode ser ativado separadamente.  
  
 Filtros de XPath podem ser adicionados para registrar mensagens específicas nos níveis de serviço e transporte. Se nenhum filtro é definido, todas as mensagens são registradas. Filtros são aplicados somente aos cabeçalhos da mensagem. O corpo é ignorado. WCF ignora o corpo da mensagem para melhorar o desempenho. Se você deseja filtrar com base no conteúdo do corpo, você pode criar um ouvinte personalizado com um filtro que faz isso.  
  
 Você precisa criar um ouvinte de rastreamento para ativar o rastreamento de mensagem. O ouvinte em si pode ser qualquer ouvinte que funciona com o <xref:System.Diagnostics> arquitetura de rastreamento. O exemplo a seguir demonstra como criar um ouvinte tal.  
  
```xml  
<system.diagnostics>  
    <sources>  
          <source name="System.ServiceModel" switchValue="Verbose">  
              <listeners>  
                    <clear />  
                    <add type="System.Diagnostics.DefaultTraceListener" name="Default"  
                        traceOutputOptions="None" />  
                    <add name="ServiceModel Listener" traceOutputOptions="None" />  
               </listeners>  
        </source>  
            <source name="System.ServiceModel.MessageLogging">  
                <listeners>  
                    <clear />  
                    <add type="System.Diagnostics.DefaultTraceListener" name="Default"  
                        traceOutputOptions="None" />  
                    <add name="MessageLogging Listener" traceOutputOptions="None"/>  
               </listeners>  
        </source>  
    </sources>  
     <sharedListeners>  
            <add initializeData="C:\ItProTools\TraceLog.xml"  
                    type="System.Diagnostics.XmlWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
                    name="ServiceModel Listener"  
                    traceOutputOptions="LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack" />  
            <add initializeData="C:\ItProTools\MessageLog.log"  
                    type="System.Diagnostics.XmlWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
                   name="MessageLogging Listener"  
                   traceOutputOptions="LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack" />  
    </sharedListeners>  
</system.diagnostics>  
```  
  
## <a name="example"></a>Exemplo  
  
```xml  
<messageLogging logEntireMessage="true"  
    logMalformedMessages="true"  
    logMessagesAtServiceLevel="true"  
    logMessagesAtTransportLevel="true"  
    maxMessagesToLog="42"  
    maxSizeOfMessageToLog="42">  
     <filters>  
         <clear />  
     </filters>  
 </messageLogging>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement>  
 [Configurando registros de mensagens em log](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)

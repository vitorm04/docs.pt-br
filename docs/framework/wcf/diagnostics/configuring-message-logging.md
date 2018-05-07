---
title: Configurando registros de mensagens em log
ms.date: 03/30/2017
helpviewer_keywords:
- message logging [WCF]
ms.assetid: 0ff4c857-8f09-4b85-9dc0-89084706e4c9
ms.openlocfilehash: 4c75b0f27e82b8cfe9327a9911d27d4e435ddf81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="configuring-message-logging"></a>Configurando registros de mensagens em log
Este tópico descreve como você pode configurar o log de mensagens para diferentes cenários.  
  
## <a name="enabling-message-logging"></a>Habilitar o log de mensagem  
 Por padrão, o Windows Communication Foundation (WCF) não registra mensagens. Para ativar o log de mensagens, você deve adicionar um ouvinte de rastreamento para o `System.ServiceModel.MessageLogging` origem do rastreamento e definir atributos para o `<messagelogging>` elemento no arquivo de configuração.  
  
 O exemplo a seguir mostra como habilitar o registro em log e especifique opções adicionais.  
  
```xml  
<system.diagnostics>  
  <sources>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
                 <add name="messages"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\logs\messages.svclog" />  
          </listeners>  
      </source>  
    </sources>  
</system.diagnostics>  
  
<system.serviceModel>  
  <diagnostics>  
    <messageLogging   
         logEntireMessage="true"   
         logMalformedMessages="false"  
         logMessagesAtServiceLevel="true"   
         logMessagesAtTransportLevel="false"  
         maxMessagesToLog="3000"  
         maxSizeOfMessageToLog="2000"/>  
  </diagnostics>  
</system.serviceModel>  
```  
  
 Para obter mais informações sobre configurações de log de mensagem, consulte [configurações recomendadas para rastreamento e registro em log de mensagem](../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md).  
  
 Você pode usar `add` para especificar o nome e o tipo do ouvinte que você deseja usar. Na configuração de exemplo, o ouvinte é denominado "messages" e adiciona o ouvinte de rastreamento padrão do .NET Framework (`System.Diagnostics.XmlWriterTraceListener`) como o tipo a ser usado. Se você usar `System.Diagnostics.XmlWriterTraceListener`, você deve especificar o local do arquivo de saída e o nome no arquivo de configuração. Isso é feito definindo `initializeData` com o nome do arquivo de log. Caso contrário, o sistema gerará uma exceção. Você também pode implementar um ouvinte personalizado que emite os logs para um arquivo padrão.  
  
> [!NOTE]
>  Como o log de mensagem acessa o espaço em disco, você deve limitar o número de mensagens que são gravadas em disco para um serviço específico. Quando o limite da mensagem é atingido, um rastreamento no nível de informações é gerado e interromper todas as atividades de registro em log de mensagem.  
  
 O nível de log, bem como as opções adicionais, são discutidas na seção de opções e o nível de log.  
  
 O `switchValue` atributo de um `source` só é válido para o rastreamento. Se você especificar um `switchValue` de atributo para o `System.ServiceModel.MessageLogging` origem de rastreamento como segue, ele não tem nenhum efeito.  
  
```xml  
<source name="System.ServiceModel.MessageLogging" switchValue="Verbose">  
```  
  
 Se você quiser desabilitar a origem de rastreamento, você deve usar o `logMessagesAtServiceLevel`, `logMalformedMessages`, e `logMessagesAtTransportLevel` atributos do `messageLogging` elemento em vez disso. Você deve definir todos esses atributos para `false`. Isso pode ser feito usando o arquivo de configuração no exemplo de código anterior, por meio da interface do Editor de configuração UI, ou usando o WMI. Para obter mais informações sobre a ferramenta Editor de configuração, consulte [ferramenta Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md). Para obter mais informações sobre WMI, consulte [usando o Windows Management Instrumentation para diagnóstico](../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
## <a name="logging-levels-and-options"></a>Níveis de log e opções  
 Para mensagens de entrada, registro em log ocorre imediatamente depois que a mensagem é formada, imediatamente antes da mensagem obtém ao código do usuário no nível de serviço e quando as mensagens malformadas são detectadas.  
  
 Mensagens de saída, log ocorre imediatamente após a mensagem sair do código do usuário e imediatamente antes que a mensagem entre na conexão.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] registra mensagens em dois níveis diferentes, serviço e transporte. As mensagens malformadas também são registradas. As três categorias são independentes umas das outras e podem ser ativadas separadamente na configuração.  
  
 Você pode controlar o nível de log definindo o `logMessagesAtServiceLevel`, `logMalformedMessages`, e `logMessagesAtTransportLevel` atributos do `messageLogging` elemento.  
  
### <a name="service-level"></a>Nível de serviço  
 As mensagens registradas nesta camada estão prestes a insira (no recebimento) ou deixar (no envio) código do usuário. Se os filtros tiverem sido definidos, apenas as mensagens que correspondem aos filtros são registradas. Caso contrário, todas as mensagens de nível de serviço são registradas. Mensagens de infraestrutura (transações, canal par e segurança) também são registradas nesse nível, com exceção de mensagens do sistema de mensagens confiável. Em mensagens em fluxo, somente os cabeçalhos são registrados. Além disso, mensagens seguras são registradas descriptografados neste nível.  
  
### <a name="transport-level"></a>Nível de transporte  
 As mensagens registradas nesta camada estão prontas para ser codificada ou decodificada para ou depois de transporte na conexão. Se os filtros tiverem sido definidos, apenas as mensagens que correspondem aos filtros são registradas. Caso contrário, todas as mensagens na camada de transporte são registradas. Todas as mensagens de infraestrutura são registradas nesta camada, incluindo mensagens confiáveis. Em mensagens em fluxo, somente os cabeçalhos são registrados. Além disso, mensagens seguras são registradas como criptografados nesse nível, exceto se um transporte seguro, como HTTPS é usado.  
  
### <a name="malformed-level"></a>Nível malformado  
 As mensagens malformadas são mensagens que foram rejeitadas pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pilha em qualquer estágio do processamento. As mensagens malformadas são registradas como-é: criptografados se eles são, com o próprio não XML e assim por diante. `maxSizeOfMessageToLog` definido o tamanho da mensagem a ser registrado como CDATA. Por padrão, `maxSizeOfMessageToLog` é igual a 256 K. Para obter mais informações sobre esse atributo, consulte a seção de outras opções.  
  
### <a name="other-options"></a>Outras opções  
 Além dos níveis de log, o usuário pode especificar as seguintes opções:  
  
-   Registrar a mensagem inteira (`logEntireMessage` atributo): esse valor Especifica se a mensagem inteira (cabeçalho e corpo) é registrada. O valor padrão é `false`, que significa que apenas o cabeçalho é registrado. Essa configuração afeta os níveis de log de mensagem de transporte e de serviço.  
  
-   Máximo de mensagens para fazer logon (`maxMessagesToLog` atributo): esse valor Especifica o número máximo de mensagens a serem registradas. Todas as mensagens (serviço de transporte e mensagens malformadas) são contadas em direção a essa cota. Quando a cota for atingida, um rastreamento é emitido e nenhuma outra mensagem é registrada. O valor padrão é 10000.  
  
-   Tamanho máximo da mensagem para fazer logon (`maxSizeOfMessageToLog` atributo): esse valor Especifica o tamanho máximo de mensagens para fazer logon em bytes. As mensagens que excedem o limite de tamanho não são registradas e nenhuma outra atividade é executada para essa mensagem. Essa configuração afeta todos os níveis de rastreamento. Se o rastreamento de ServiceModel está ativado, um rastreamento de nível de aviso é emitido no primeiro ponto de registro em log (ServiceModelSend * ou TransportReceive) para notificar o usuário. O valor padrão para mensagens de nível transporte e de nível de serviço é de 256K, enquanto o valor padrão para mensagens malformadas é 4 KB.  
  
    > [!CAUTION]
    >  O tamanho da mensagem que é calculado a ser comparada com `maxSizeOfMessageToLog` é o tamanho de mensagem na memória antes de serialização. Esse tamanho pode ser diferente do que o comprimento real da cadeia de caracteres de mensagem que está sendo registrado e, em muitas ocasiões, é maior do que o tamanho real. Como resultado, as mensagens não podem ser registradas. Você pode considerar esse fato especificando o `maxSizeOfMessageToLog` atributo para 10% maior que o tamanho da mensagem esperada. Além disso, se as mensagens malformadas são registradas, o espaço em disco utilizado pelos logs de mensagem pode ser até 5 vezes o tamanho do valor especificado por `maxSizeOfMessageToLog`.  
  
 Se nenhum ouvinte de rastreamento é definido no arquivo de configuração, nenhuma saída de log será gerada, independentemente do nível de log especificado.  
  
 Opções de log de mensagem, como os atributos descritos nesta seção, podem ser alteradas em tempo de execução usando o Windows Management Instrumentation (WMI). Isso pode ser feito, acessando o [AppDomainInfo](../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) instância, que expõe essas propriedades Boolianas: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, e `LogMalformedMessages`. Portanto, se você configura um ouvinte de rastreamento para o log de mensagens, mas definir essas opções para `false` na configuração, você pode posteriormente alterá-los para `true` quando o aplicativo está sendo executado. Isso efetivamente habilita o log de mensagem em tempo de execução. Da mesma forma, se você habilitar o registro em log no arquivo de configuração de mensagem, você pode desabilitá-lo em tempo de execução usando a WMI. Para obter mais informações, consulte [usando o Windows Management Instrumentation para diagnóstico](../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
 O `source` campo em um log de mensagem especifica em qual contexto a mensagem é registrada: no envio/recebimento de uma mensagem de solicitação para uma solicitação-resposta ou solicitação de maneira 1, na camada de transporte ou modelo de serviço ou, no caso de uma mensagem malformada.  
  
 Para mensagens malformadas, `source` é igual a `Malformed`. Caso contrário, a fonte tem os seguintes valores com base no contexto.  
  
 Para a solicitação/resposta  
  
||Enviar solicitação|Solicitação de recepção|Enviar resposta|Receber a resposta|  
|-|------------------|---------------------|----------------|-------------------|  
|Camada de modelo de serviço|Serviço<br /><br /> Nível<br /><br /> Enviar<br /><br /> Solicitação|Serviço<br /><br /> Nível<br /><br /> Receber<br /><br /> Solicitação|Serviço<br /><br /> Nível<br /><br /> Enviar<br /><br /> Resposta|Serviço<br /><br /> Nível<br /><br /> Receber<br /><br /> Resposta|  
|Camada de transporte|Transporte<br /><br /> Enviar|Transporte<br /><br /> Receber|Transporte<br /><br /> Enviar|Transporte<br /><br /> Receber|  
  
 Para a solicitação unidirecional  
  
||Enviar solicitação|Solicitação de recepção|  
|-|------------------|---------------------|  
|Camada de modelo de serviço|Serviço<br /><br /> Nível<br /><br /> Enviar<br /><br /> Datagrama|Serviço<br /><br /> Nível<br /><br /> Receber<br /><br /> Datagrama|  
|Camada de transporte|Transporte<br /><br /> Enviar|Transporte<br /><br /> Receber|  
  
## <a name="message-filters"></a>Filtros de mensagem  
 Filtros de mensagem são definidos a `messageLogging` elemento de configuração de `diagnostics` seção de configuração. Elas são aplicadas em nível de serviço e transporte. Quando um ou mais filtros são definidos, apenas as mensagens que correspondem a pelo menos um dos filtros são registradas. Se nenhum filtro for definido, todas as mensagens passam.  
  
 Os filtros oferece suporte a sintaxe completa do XPath e são aplicados na ordem em que aparecem no arquivo de configuração. Um filtro sintaticamente incorreto resulta em uma exceção de configuração.  
  
 Filtros também fornecem um recurso de segurança usando o `nodeQuota` atributo, o que limita o número máximo de nós no DOM XPath que pode ser examinado para coincidir com o filtro.  
  
 O exemplo a seguir mostra como configurar um filtro que registra apenas as mensagens que têm uma seção de cabeçalho SOAP.  
  
```xml  
<messageLogging logEntireMessage="true"  
    logMalformedMessages="true"   
    logMessagesAtServiceLevel="true"  
    logMessagesAtTransportLevel="true"  
    maxMessagesToLog="420">  
    <filters>  
        <add nodeQuota="10" xmlns:soap="http://www.w3.org/2003/05/soap-envelope">  
                 /soap:Envelope/soap:Header  
        </add>  
     </filters>  
</messageLogging>  
```  
  
 Filtros não podem ser aplicados ao corpo de uma mensagem. Os filtros que tentam manipular o corpo da mensagem são removidos da lista de filtros. Um evento é emitido que indica que isso também. Por exemplo, o seguinte filtro será removido da tabela de filtros.  
  
```xml  
<add xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">/s:Envelope/s:Body[contains(text(), "Hello")]</add>  
```  
  
## <a name="configuring-a-custom-listener"></a>Configurando um ouvinte personalizado  
 Você também pode configurar um ouvinte personalizado com opções adicionais. Um ouvinte personalizado pode ser útil na filtragem de elementos PII específicas do aplicativo de mensagens antes de fazer logon. O exemplo a seguir demonstra uma configuração de ouvinte personalizado.  
  
```xml  
<system.diagnostics>  
   <sources>  
     <source name="System.ServiceModel.MessageLogging">  
           <listeners>  
             <add name="MyListener"   
                    type="YourCustomListener"  
                    initializeData="c:\logs\messages.svclog"  
                    maxDiskSpace="1000"/>  
           </listeners>  
     </source>  
   </sources>  
</system.diagnostics>  
```  
  
 Você deve estar ciente de que o `type` atributo deve ser definido como um nome qualificado do assembly do tipo.  
  
## <a name="see-also"></a>Consulte também  
 [\<messageLogging >](../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)  
 [Registro de mensagens em log](../../../../docs/framework/wcf/diagnostics/message-logging.md)  
 [Configurações recomendadas para rastreamento e registro de mensagem](../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md)

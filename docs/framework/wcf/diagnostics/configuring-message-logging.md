---
title: Configurando registros de mensagens em log
ms.date: 03/30/2017
helpviewer_keywords:
- message logging [WCF]
ms.assetid: 0ff4c857-8f09-4b85-9dc0-89084706e4c9
ms.openlocfilehash: 5b4da744151d8b667c0f944b1a0d51d1251bfae5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64652006"
---
# <a name="configuring-message-logging"></a>Configurando registros de mensagens em log
Este tópico descreve como você pode configurar o log de mensagens para diferentes cenários.  
  
## <a name="enabling-message-logging"></a>Habilitando o log de mensagem  
 Por padrão, o Windows Communication Foundation (WCF) não registra mensagens. Para ativar o log de mensagens, você deve adicionar um ouvinte de rastreamento para o `System.ServiceModel.MessageLogging` fonte de rastreamento e definir atributos para o `<messagelogging>` elemento no arquivo de configuração.  
  
 O exemplo a seguir mostra como habilitar o registro em log e especificar opções adicionais.  
  
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
  
 Para obter mais informações sobre as configurações de registro em log de mensagem, consulte [as configurações recomendadas para rastreamento e registro em log de mensagem](../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md).  
  
 Você pode usar `add` para especificar o nome e tipo do ouvinte que você deseja usar. Na configuração de exemplo, o ouvinte é denominado "messages" e adiciona o ouvinte de rastreamento padrão do .NET Framework (`System.Diagnostics.XmlWriterTraceListener`) como o tipo a ser usado. Se você usar `System.Diagnostics.XmlWriterTraceListener`, você deve especificar o local do arquivo de saída e o nome no arquivo de configuração. Isso é feito definindo `initializeData` para o nome do arquivo de log. Caso contrário, o sistema gerará uma exceção. Você também pode implementar um ouvinte personalizado que emite os logs para um arquivo padrão.  
  
> [!NOTE]
>  Como registro em log de mensagem acessa o espaço em disco, você deve limitar o número de mensagens que são gravados em disco para um serviço específico. Quando o limite da mensagem é atingido, um rastreamento no nível de informações é produzido e parar todas as atividades de registro em log de mensagem.  
  
 O nível de log, bem como as opções adicionais, são discutidas na seção de nível de registro em log e as opções.  
  
 O `switchValue` atributo de um `source` só é válido para o rastreamento. Se você especificar uma `switchValue` de atributo para o `System.ServiceModel.MessageLogging` origem de rastreamento como segue, ele não tem nenhum efeito.  
  
```xml  
<source name="System.ServiceModel.MessageLogging" switchValue="Verbose">  
```  
  
 Se você quiser desabilitar a origem de rastreamento, você deve usar o `logMessagesAtServiceLevel`, `logMalformedMessages`, e `logMessagesAtTransportLevel` atributos do `messageLogging` elemento em vez disso. Você deve definir todos esses atributos para `false`. Isso pode ser feito usando o arquivo de configuração no exemplo de código anterior, por meio da interface do Editor de configuração de UI, ou usando o WMI. Para obter mais informações sobre a ferramenta Editor de configuração, consulte [ferramenta de Editor de configuração (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md). Para obter mais informações sobre WMI, consulte [usando o Windows Management Instrumentation para diagnóstico](../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
## <a name="logging-levels-and-options"></a>Níveis de log e opções  
 Mensagens de entrada, registro em log ocorre imediatamente depois que a mensagem é formada, imediatamente antes da mensagem obtém ao código do usuário no nível de serviço, e quando mensagens malformadas são detectadas.  
  
 Para mensagens de saída, o registro em log ocorre imediatamente depois que a mensagem sair do código do usuário e imediatamente antes da mensagem é enviada durante a transmissão.  
  
 O WCF registra mensagens em dois níveis diferentes, serviço e transporte. Mensagens malformadas também são registradas. As três categorias são independentes uns dos outros e podem ser ativadas separadamente na configuração.  
  
 Você pode controlar o nível de log definindo o `logMessagesAtServiceLevel`, `logMalformedMessages`, e `logMessagesAtTransportLevel` atributos do `messageLogging` elemento.  
  
### <a name="service-level"></a>Nível de serviço  
 As mensagens registradas nesta camada estão prestes a insira (no recebimento) ou deixe (envio) código do usuário. Se os filtros tiverem sido definidos, apenas as mensagens que correspondem aos filtros são registradas. Caso contrário, todas as mensagens no nível de serviço estão registradas. Mensagens de infraestrutura (transações, canal de mesmo nível e segurança) também são registradas nesse nível, com exceção de mensagens do sistema de mensagens confiável. Em mensagens transmitidas, somente os cabeçalhos são registrados. Além disso, mensagens seguras são registradas descriptografados nesse nível.  
  
### <a name="transport-level"></a>Nível de transporte  
 As mensagens registradas nesta camada estão prontas para serem codificados ou decodificados de ou depois de transporte durante a transmissão. Se os filtros tiverem sido definidos, apenas as mensagens que correspondem aos filtros são registradas. Caso contrário, todas as mensagens na camada de transporte são registradas. Todas as mensagens de infraestrutura são registradas nessa camada, incluindo mensagens de reliable messaging. Em mensagens transmitidas, somente os cabeçalhos são registrados. Além disso, mensagens seguras são registradas como criptografado nesse nível, exceto se um transporte seguro, como o HTTPS é usado.  
  
### <a name="malformed-level"></a>Nível malformado  
 Mensagens malformadas são mensagens que são rejeitadas pela pilha do WCF em qualquer estágio do processamento. Mensagens malformadas são registradas como-está: criptografados se estiverem, com XML não adequada e assim por diante. `maxSizeOfMessageToLog` definido o tamanho da mensagem a ser registrada como CDATA. Por padrão, `maxSizeOfMessageToLog` é igual a 256 K. Para obter mais informações sobre esse atributo, consulte a seção de outras opções.  
  
### <a name="other-options"></a>Outras opções  
 Além dos níveis de registro em log, o usuário pode especificar as seguintes opções:  
  
- Toda mensagem de log (`logEntireMessage` atributo): Esse valor Especifica se a mensagem inteira (cabeçalho de mensagem e corpo) é registrada. O valor padrão é `false`, que significa que apenas o cabeçalho está registrado. Essa configuração afeta os níveis de log de mensagem de transporte e de serviço...  
  
- Máximo de mensagens para fazer logon (`maxMessagesToLog` atributo): Esse valor Especifica o número máximo de mensagens para fazer logon. Todas as mensagens (serviço de transporte e mensagens malformadas) são contadas para essa cota. Quando a cota for atingida, um rastreamento é emitido e nenhuma mensagem adicional será registrada. O valor padrão é 10000.  
  
- Tamanho máximo de mensagem a ser registrada (`maxSizeOfMessageToLog` atributo): Esse valor Especifica o tamanho máximo de mensagens para fazer logon em bytes. As mensagens que excedem o limite de tamanho não são registradas e nenhuma outra atividade é executada para a mensagem. Essa configuração afeta todos os níveis de rastreamento. Se o rastreamento de ServiceModel estiver ativada, um rastreamento de nível de aviso é emitido no primeiro ponto de registro em log (ServiceModelSend * ou TransportReceive) para notificar o usuário. O valor padrão para mensagens de nível transporte e de nível de serviço é de 256K, enquanto o valor padrão para mensagens malformadas for 4K.  
  
    > [!CAUTION]
    >  O tamanho da mensagem que é calculado a ser comparada com `maxSizeOfMessageToLog` é o tamanho da mensagem na memória antes da serialização. Esse tamanho pode ser diferente do que o comprimento real da cadeia de caracteres de mensagem que está sendo registrada e, em muitas ocasiões em que é maior do que o tamanho real. Como resultado, as mensagens não podem ser registradas. Você pode considerar esse fato, especificando o `maxSizeOfMessageToLog` atributo a ser 10% maior que o tamanho da mensagem esperada. Além disso, se mensagens malformadas são registradas, o espaço em disco utilizado pelos logs de mensagem pode ser até 5 vezes o tamanho do valor especificado por `maxSizeOfMessageToLog`.  
  
 Se nenhum ouvinte de rastreamento é definido no arquivo de configuração, nenhuma saída de log é gerada, independentemente do nível de log especificado.  
  
 Opções de registro em log de mensagem, como os atributos descritos nesta seção, podem ser alteradas em tempo de execução usando o Windows Management Instrumentation (WMI). Isso pode ser feito, acessando o [AppDomainInfo](../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) instância, que expõe essas propriedades Boolianas: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, e `LogMalformedMessages`. Portanto, se você configura um ouvinte de rastreamento para o log de mensagens, mas definir essas opções para `false` na configuração, você pode alterar a `true` quando o aplicativo está em execução. Isso permite que o log de mensagens em tempo de execução com eficiência. Da mesma forma, se você habilitar o registro em log no arquivo de configuração de mensagem, você pode desabilitá-lo em tempo de execução usando o WMI. Para obter mais informações, consulte [usando o Windows Management Instrumentation para diagnóstico](../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
 O `source` campo em um log de mensagem especifica no contexto em que a mensagem é registrada: no envio/recebimento de uma mensagem de solicitação para uma solicitação-resposta ou solicitação de maneira 1, na camada de transporte ou de modelo de serviço ou, no caso de uma mensagem malformada.  
  
 Para mensagens malformadas, `source` é igual a `Malformed`. Caso contrário, a fonte tem os seguintes valores com base no contexto.  
  
 Solicitação/resposta  
  
||Enviar solicitação|Receber a solicitação|Enviar resposta|Receber resposta|  
|-|------------------|---------------------|----------------|-------------------|  
|Camada de modelo de serviço|Serviço<br /><br /> Nível<br /><br /> Enviar<br /><br /> Solicitação|Serviço<br /><br /> Nível<br /><br /> Receber<br /><br /> Solicitação|Serviço<br /><br /> Nível<br /><br /> Enviar<br /><br /> Resposta|Serviço<br /><br /> Nível<br /><br /> Receber<br /><br /> Resposta|  
|camada de transporte|Transporte<br /><br /> Enviar|Transporte<br /><br /> Receber|Transporte<br /><br /> Enviar|Transporte<br /><br /> Receber|  
  
 Para a solicitação unidirecional  
  
||Enviar solicitação|Receber a solicitação|  
|-|------------------|---------------------|  
|Camada de modelo de serviço|Serviço<br /><br /> Nível<br /><br /> Enviar<br /><br /> Datagrama|Serviço<br /><br /> Nível<br /><br /> Receber<br /><br /> Datagrama|  
|camada de transporte|Transporte<br /><br /> Enviar|Transporte<br /><br /> Receber|  
  
## <a name="message-filters"></a>Filtros de mensagem  
 Filtros de mensagem são definidos os `messageLogging` elemento de configuração a `diagnostics` seção de configuração. Elas são aplicadas no nível de serviço e transporte. Quando um ou mais filtros são definidos, apenas as mensagens que correspondem a pelo menos um dos filtros são registradas. Se nenhum filtro for definido, todas as mensagens passam.  
  
 Filtros dão suporte a sintaxe completa do XPath e são aplicados na ordem em que aparecem no arquivo de configuração. Um filtro sintaticamente incorreto resulta em uma exceção de configuração.  
  
 Filtros também fornecem um recurso de segurança usando o `nodeQuota` atributo, que limita o número máximo de nós no DOM, XPath que podem ser examinadas para corresponderem ao filtro.  
  
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
  
 Filtros não podem ser aplicados ao corpo de uma mensagem. Os filtros que tentam manipular o corpo de uma mensagem são removidos da lista de filtros. Um evento é emitido que indica que essa também. Por exemplo, o filtro a seguir seria removido da tabela de filtros.  
  
```xml  
<add xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">/s:Envelope/s:Body[contains(text(), "Hello")]</add>  
```  
  
## <a name="configuring-a-custom-listener"></a>Configurar um ouvinte personalizado  
 Você também pode configurar um ouvinte personalizado com opções adicionais. Um ouvinte personalizado pode ser útil na filtragem de elementos PII específicos do aplicativo de mensagens antes de fazer logon. O exemplo a seguir demonstra uma configuração de ouvinte personalizado.  
  
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
  
 Você deve estar ciente que o `type` atributo deve ser definido como um nome qualificado do assembly do tipo.  
  
## <a name="see-also"></a>Consulte também

- [\<messageLogging>](../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
- [Registro de mensagens em log](../../../../docs/framework/wcf/diagnostics/message-logging.md)
- [Configurações recomendadas para rastreamento e registro de mensagem](../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md)

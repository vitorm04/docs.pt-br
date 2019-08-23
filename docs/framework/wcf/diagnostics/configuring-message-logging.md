---
title: Configurando registros de mensagens em log
ms.date: 03/30/2017
helpviewer_keywords:
- message logging [WCF]
ms.assetid: 0ff4c857-8f09-4b85-9dc0-89084706e4c9
ms.openlocfilehash: 8a51381db71f528bf3cf25f5c84d18aee805c57e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948370"
---
# <a name="configuring-message-logging"></a>Configurando registros de mensagens em log
Este tópico descreve como você pode configurar o log de mensagens para diferentes cenários.  
  
## <a name="enabling-message-logging"></a>Habilitando o log de mensagens  
 O Windows Communication Foundation (WCF) não registra mensagens por padrão. Para ativar o log de mensagens, você deve adicionar um ouvinte `System.ServiceModel.MessageLogging` de rastreamento à fonte de rastreamento e `<messagelogging>` definir atributos para o elemento no arquivo de configuração.  
  
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
  
 Para obter mais informações sobre configurações de log de mensagens, consulte [configurações recomendadas para rastreamento e log de mensagens](../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md).  
  
 Você pode usar `add` para especificar o nome e o tipo do ouvinte que deseja usar. Na configuração de exemplo, o ouvinte é chamado de "mensagens" e adiciona o ouvinte de`System.Diagnostics.XmlWriterTraceListener`rastreamento de .NET Framework padrão () como o tipo a ser usado. Se você usar `System.Diagnostics.XmlWriterTraceListener`o, deverá especificar o local e o nome do arquivo de saída no arquivo de configuração. Isso é feito definindo `initializeData` o nome do arquivo de log. Caso contrário, o sistema gera uma exceção. Você também pode implementar um ouvinte personalizado que emite logs para um arquivo padrão.  
  
> [!NOTE]
> Como o log de mensagens acessa o espaço em disco, você deve limitar o número de mensagens gravadas no disco para um serviço específico. Quando o limite de mensagens é atingido, um rastreamento no nível de informação é produzido e todas as atividades de log de mensagem são interrompidas.  
  
 O nível de log, bem como as opções adicionais, são discutidos na seção nível de log e opções.  
  
 O `switchValue` atributo de a `source` é válido somente para rastreamento. Se você especificar um `switchValue` atributo para a `System.ServiceModel.MessageLogging` origem de rastreamento da seguinte maneira, ele não terá nenhum efeito.  
  
```xml  
<source name="System.ServiceModel.MessageLogging" switchValue="Verbose">  
```  
  
 Se você quiser desabilitar a origem do rastreamento `logMessagesAtServiceLevel`, use os atributos, `logMalformedMessages` `messageLogging` , e `logMessagesAtTransportLevel` do elemento. Você deve definir todos esses atributos como `false`. Isso pode ser feito usando o arquivo de configuração no exemplo de código anterior, por meio da interface de interface do usuário do editor de configuração ou usando o WMI. Para obter mais informações sobre a ferramenta do editor de configuração, consulte [ferramenta do editor de configuração (SvcConfigEditor. exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md). Para obter mais informações sobre o WMI, consulte [usando instrumentação de gerenciamento do Windows para diagnóstico](../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
## <a name="logging-levels-and-options"></a>Níveis e opções de log  
 Para mensagens de entrada, o log ocorre imediatamente depois que a mensagem é formada, imediatamente antes de a mensagem chegar ao código do usuário no nível de serviço e quando as mensagens malformadas são detectadas.  
  
 Para mensagens de saída, o registro em log ocorre imediatamente após a mensagem sair do código do usuário e imediatamente antes de a mensagem entrar na conexão.  
  
 O WCF Registra mensagens em dois níveis diferentes, serviço e transporte. As mensagens malformadas também são registradas. As três categorias são independentes umas das outras e podem ser ativadas separadamente na configuração.  
  
 Você pode controlar o nível de log definindo os `logMessagesAtServiceLevel`atributos `logMalformedMessages`, e `logMessagesAtTransportLevel` do `messageLogging` elemento.  
  
### <a name="service-level"></a>Nível de serviço  
 As mensagens registradas nessa camada estão prestes a entrar (no recebimento) ou saem (no envio) do código de usuário. Se os filtros tiverem sido definidos, somente as mensagens que corresponderem aos filtros serão registradas. Caso contrário, todas as mensagens no nível de serviço serão registradas. As mensagens de infraestrutura (transações, canal par e segurança) também são registradas nesse nível, exceto para mensagens de mensagens confiáveis. Em mensagens transmitidas, somente os cabeçalhos são registrados em log. Além disso, as mensagens seguras são descriptografadas nesse nível.  
  
### <a name="transport-level"></a>Nível de transporte  
 As mensagens registradas nessa camada estão prontas para serem codificadas ou decodificadas para ou após o transporte na transmissão. Se os filtros tiverem sido definidos, somente as mensagens que corresponderem aos filtros serão registradas. Caso contrário, todas as mensagens na camada de transporte serão registradas. Todas as mensagens de infraestrutura são registradas nessa camada, incluindo mensagens de mensagens confiáveis. Em mensagens transmitidas, somente os cabeçalhos são registrados em log. Além disso, as mensagens seguras são registradas como criptografadas nesse nível, exceto se um transporte seguro, como HTTPS, for usado.  
  
### <a name="malformed-level"></a>Nível malformado  
 Mensagens malformadas são mensagens rejeitadas pela pilha do WCF em qualquer estágio do processamento. As mensagens malformadas são registradas como estão: criptografadas se forem assim, com XML não adequado e assim por diante. `maxSizeOfMessageToLog`definido o tamanho da mensagem a ser registrada como CDATA. Por padrão, `maxSizeOfMessageToLog` é igual a 256K. Para obter mais informações sobre esse atributo, consulte a seção outras opções.  
  
### <a name="other-options"></a>Outras opções  
 Além dos níveis de log, o usuário pode especificar as seguintes opções:  
  
- Registrar mensagem inteira (`logEntireMessage` atributo): Esse valor especifica se a mensagem inteira (cabeçalho e corpo da mensagem) é registrada. O valor padrão é `false`, o que significa que apenas o cabeçalho é registrado em log. Essa configuração afeta os níveis de log de mensagens de serviço e transporte.  
  
- Máximo de mensagens para log`maxMessagesToLog` (atributo): Esse valor especifica o número máximo de mensagens a serem registradas. Todas as mensagens (serviço, transporte e mensagens malformadas) são contadas em direção a essa cota. Quando a cota é atingida, um rastreamento é emitido e nenhuma mensagem adicional é registrada. O valor padrão é 10000.  
  
- Tamanho máximo da mensagem a ser registrada (`maxSizeOfMessageToLog` atributo): Esse valor especifica o tamanho máximo das mensagens para fazer logon em bytes. Mensagens que excedem o limite de tamanho não são registradas e nenhuma outra atividade é executada para essa mensagem. Essa configuração afeta todos os níveis de rastreamento. Se o rastreamento de ServiceModel estiver ativado, um rastreamento de nível de aviso será emitido no primeiro ponto de log (ServiceModelSend * ou TransportReceive) para notificar o usuário. O valor padrão para as mensagens de nível de serviço e nível de transporte é 256K, enquanto o valor padrão para mensagens malformadas é de 4K.  
  
    > [!CAUTION]
    >  O tamanho da mensagem que é computada para `maxSizeOfMessageToLog` comparação é o tamanho da mensagem na memória antes da serialização. Esse tamanho pode diferir do tamanho real da cadeia de caracteres de mensagem que está sendo registrada e, em muitas ocasiões, maior do que o tamanho real. Como resultado, as mensagens podem não ser registradas em log. Você pode considerar esse fato especificando que o `maxSizeOfMessageToLog` atributo seja 10% maior do que o tamanho esperado da mensagem. Além disso, se as mensagens malformadas forem registradas, o espaço em disco real utilizado pelos logs de mensagens poderá ter até cinco vezes o tamanho do valor `maxSizeOfMessageToLog`especificado por.  
  
 Se nenhum ouvinte de rastreamento for definido no arquivo de configuração, nenhuma saída de log será gerada, independentemente do nível de log especificado.  
  
 As opções de log de mensagens, como os atributos descritos nesta seção, podem ser alteradas em tempo de execução usando Instrumentação de Gerenciamento do Windows (WMI). Isso pode ser feito acessando a instância [AppDomainInfo](../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) , que expõe essas propriedades booleanas `LogMessagesAtServiceLevel`: `LogMessagesAtTransportLevel`, e `LogMalformedMessages`. Portanto, se você configurar um ouvinte de rastreamento para o log de mensagens, mas `false` definir essas opções como em configuração, você poderá `true` alterá-las posteriormente para quando o aplicativo estiver em execução. Isso efetivamente habilita o log de mensagens em tempo de execução. Da mesma forma, se você habilitar o log de mensagens em seu arquivo de configuração, poderá desabilitá-lo em tempo de execução usando o WMI. Para obter mais informações, consulte [usando instrumentação de gerenciamento do Windows para diagnóstico](../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
 O `source` campo em um log de mensagens especifica em qual contexto a mensagem é registrada: ao enviar/receber uma mensagem de solicitação, para uma solicitação de solicitação-resposta ou de 1-Way, no modelo de serviço ou na camada de transporte ou no caso de uma mensagem malformada.  
  
 Para mensagens malformadas, `source` é igual a. `Malformed` Caso contrário, a origem terá os valores a seguir com base no contexto.  
  
 Para solicitação/resposta  
  
||Enviar solicitação|Receber solicitação|Enviar resposta|Receber resposta|  
|-|------------------|---------------------|----------------|-------------------|  
|Camada do modelo de serviço|Serviço<br /><br /> Nível<br /><br /> Enviar<br /><br /> Solicitação|Serviço<br /><br /> Nível<br /><br /> Receber<br /><br /> Solicitação|Serviço<br /><br /> Nível<br /><br /> Enviar<br /><br /> Resposta|Serviço<br /><br /> Nível<br /><br /> Receber<br /><br /> Resposta|  
|Camada de transporte|Porta<br /><br /> Enviar|Porta<br /><br /> Receber|Porta<br /><br /> Enviar|Porta<br /><br /> Receber|  
  
 Para uma solicitação unidirecional  
  
||Enviar solicitação|Receber solicitação|  
|-|------------------|---------------------|  
|Camada do modelo de serviço|Serviço<br /><br /> Nível<br /><br /> Enviar<br /><br /> Datagrama|Serviço<br /><br /> Nível<br /><br /> Receber<br /><br /> Datagrama|  
|Camada de transporte|Porta<br /><br /> Enviar|Porta<br /><br /> Receber|  
  
## <a name="message-filters"></a>Filtros de mensagem  
 Os filtros `messageLogging` `diagnostics` de mensagem são definidos no elemento Configuration da seção de configuração. Eles são aplicados no nível de serviço e transporte. Quando um ou mais filtros são definidos, somente as mensagens que correspondem a pelo menos um dos filtros são registradas. Se nenhum filtro for definido, todas as mensagens passarão.  
  
 Os filtros dão suporte à sintaxe XPath completa e são aplicados na ordem em que aparecem no arquivo de configuração. Um filtro sintaticamente incorreto resulta em uma exceção de configuração.  
  
 Os filtros também fornecem um recurso de segurança `nodeQuota` usando o atributo, que limita o número máximo de nós no DOM XPath que pode ser examinado para corresponder ao filtro.  
  
 O exemplo a seguir mostra como configurar um filtro que registra somente as mensagens que têm uma seção de cabeçalho SOAP.  
  
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
  
 Os filtros não podem ser aplicados ao corpo de uma mensagem. Os filtros que tentam manipular o corpo de uma mensagem são removidos da lista de filtros. Um evento também é emitido, indicando isso. Por exemplo, o filtro a seguir seria removido da tabela de filtros.  
  
```xml  
<add xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">/s:Envelope/s:Body[contains(text(), "Hello")]</add>  
```  
  
## <a name="configuring-a-custom-listener"></a>Configurando um ouvinte personalizado  
 Você também pode configurar um ouvinte personalizado com opções adicionais. Um ouvinte personalizado pode ser útil na filtragem de elementos de PII específicos do aplicativo de mensagens antes do registro em log. O exemplo a seguir demonstra uma configuração de ouvinte personalizada.  
  
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
  
 Você deve estar ciente de que `type` o atributo deve ser definido como um nome de assembly qualificado do tipo.  
  
## <a name="see-also"></a>Consulte também

- [\<messageLogging>](../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
- [Registro de mensagens em log](../../../../docs/framework/wcf/diagnostics/message-logging.md)
- [Configurações recomendadas para rastreamento e registro de mensagem](../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md)

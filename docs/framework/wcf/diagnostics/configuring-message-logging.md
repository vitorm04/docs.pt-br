---
title: Configurando registros de mensagens em log
ms.date: 03/30/2017
helpviewer_keywords:
- message logging [WCF]
ms.assetid: 0ff4c857-8f09-4b85-9dc0-89084706e4c9
ms.openlocfilehash: 283f43239d6cf5aea5ea668397a52313ff526e2a
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345192"
---
# <a name="configuring-message-logging"></a>Configurando registros de mensagens em log

Este tópico descreve como você pode configurar o registro de mensagens para diferentes cenários.

## <a name="enabling-message-logging"></a>Habilitando o registro de mensagens

O Windows Communication Foundation (WCF) não registra mensagens por padrão. Para ativar o registro de mensagens, `System.ServiceModel.MessageLogging` você deve adicionar um `<messagelogging>` ouvinte de rastreamento à fonte de rastreamento e definir atributos para o elemento no arquivo de configuração.

O exemplo a seguir mostra como ativar o registro e especificar opções adicionais.

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

Para obter mais informações sobre as configurações de registro de mensagens, consulte [Configurações recomendadas para rastreamento e registro de mensagens](./tracing/recommended-settings-for-tracing-and-message-logging.md).

Você pode `add` usar para especificar o nome e o tipo do ouvinte que deseja usar. Na configuração de exemplo, o Ouvinte é chamado de "mensagens"`System.Diagnostics.XmlWriterTraceListener`e adiciona o rastreador padrão .NET Framework () como o tipo a ser usado. Se você `System.Diagnostics.XmlWriterTraceListener`usar, você deve especificar o local e o nome do arquivo de saída no arquivo de configuração. Isso é feito `initializeData` definindo o nome do arquivo de log. Caso contrário, o sistema lança uma exceção. Você também pode implementar um ouvinte personalizado que emite logs em um arquivo padrão.

> [!NOTE]
> Como o registro de mensagens acessa o espaço em disco, você deve limitar o número de mensagens que são gravadas em disco para um determinado serviço. Quando o limite de mensagem é atingido, um rastreamento no nível de Informação é produzido e todas as atividades de registro de mensagens são paradas.

O nível de registro, bem como as opções adicionais, são discutidos na seção Nível de Registro e Opções.

O `switchValue` atributo `source` de a só é válido para rastreamento. Se você `switchValue` especificar `System.ServiceModel.MessageLogging` um atributo para a fonte de rastreamento a seguir, ele não tem efeito.

```xml
<source name="System.ServiceModel.MessageLogging" switchValue="Verbose">
</source>
```

Se você quiser desativar a fonte de `logMessagesAtServiceLevel`rastreamento, `logMessagesAtTransportLevel` você deve `messageLogging` usar os atributos `logMalformedMessages`do elemento. Você deve definir todos `false`esses atributos para . Isso pode ser feito usando o arquivo de configuração no exemplo de código anterior, através da interface UI do Editor de Configuração ou usando o WMI. Para obter mais informações sobre a ferramenta Editor de configuração, consulte [Configuration Editor Tool (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md). Para obter mais informações sobre o WMI, consulte [Usando a Instrumentação de Gerenciamento do Windows para Diagnósticos](./wmi/index.md).

## <a name="logging-levels-and-options"></a>Níveis e opções de registro

Para mensagens recebidas, o registro acontece imediatamente após a forma da mensagem, imediatamente antes que a mensagem chegue ao código do usuário no nível de serviço e quando mensagens malformadas são detectadas.

Para mensagens de saída, o registro acontece imediatamente após a mensagem sair do código do usuário e imediatamente antes que a mensagem seja no fio.

O WCF registra mensagens em dois níveis diferentes, serviço e transporte. Mensagens malformadas também são registradas. As três categorias são independentes umas das outras e podem ser ativadas separadamente na configuração.

Você pode controlar o nível `logMessagesAtServiceLevel` `logMalformedMessages`de `logMessagesAtTransportLevel` registro definindo `messageLogging` os atributos e atributos do elemento.

### <a name="service-level"></a>Nível de serviço

As mensagens registradas nesta camada estão prestes a inserir (ao receber) ou deixar (no envio) o código do usuário. Se os filtros tiverem sido definidos, somente as mensagens que correspondem aos filtros serão registradas. Caso contrário, todas as mensagens no nível de serviço são registradas. Mensagens de infra-estrutura (transações, canal de pares e segurança) também são registradas neste nível, exceto para mensagens de mensagens confiáveis. Em mensagens transmitidas, apenas os cabeçalhos são registrados. Além disso, as mensagens seguras são registradas descriptografadas neste nível.

### <a name="transport-level"></a>Nível de transporte

As mensagens registradas nesta camada estão prontas para serem codificadas ou decodificadas para ou após o transporte no fio. Se os filtros tiverem sido definidos, somente as mensagens que correspondem aos filtros serão registradas. Caso contrário, todas as mensagens na camada de transporte são registradas. Todas as mensagens de infra-estrutura são registradas nesta camada, incluindo mensagens confiáveis. Em mensagens transmitidas, apenas os cabeçalhos são registrados. Além disso, as mensagens seguras são registradas como criptografadas neste nível, exceto se um transporte seguro como HTTPS for usado.

### <a name="malformed-level"></a>Nível malformado

Mensagens malformadas são mensagens que são rejeitadas pela pilha WCF em qualquer fase de processamento. Mensagens malformadas são registradas como estão: criptografadas se forem assim, com XML não adequado, e assim por diante. `maxSizeOfMessageToLog`definiu o tamanho da mensagem a ser registrada como CDATA. Por padrão, `maxSizeOfMessageToLog` é igual a 256K. Para obter mais informações sobre esse atributo, consulte a seção Outras Opções.

### <a name="other-options"></a>Outras opções

Além dos níveis de registro, o usuário pode especificar as seguintes opções:

- Log 'Mensagem inteira (`logEntireMessage` atributo): Este valor especifica se toda a mensagem (cabeçalho de mensagem e corpo) está registrada. O valor `false`padrão é , o que significa que apenas o cabeçalho está registrado. Essa configuração afeta os níveis de registro de mensagens de serviço e transporte..

- Máximo de mensagens`maxMessagesToLog` para log (atributo): Este valor especifica o número máximo de mensagens a serem logadas. Todas as mensagens (serviço, transporte e mensagens malformadas) são contadas para essa cota. Quando a cota é atingida, um rastreamento é emitido e nenhuma mensagem adicional é registrada. O valor padrão é 10000.

- Tamanho máximo da mensagem para log (`maxSizeOfMessageToLog` atributo): Este valor especifica o tamanho máximo das mensagens para fazer login. As mensagens que excedem o limite de tamanho não são registradas e nenhuma outra atividade é realizada para essa mensagem. Essa configuração afeta todos os níveis de rastreamento. Se o rastreamento serviceModel estiver ligado, um traço de nível de aviso será emitido no primeiro ponto de registro (ServiceModelSend* ou TransportReceive) para notificar o usuário. O valor padrão para mensagens de nível de serviço e nível de transporte é de 256K, enquanto o valor padrão para mensagens malformadas é 4K.

  > [!CAUTION]
  > O tamanho da mensagem que `maxSizeOfMessageToLog` é calculado para comparar é o tamanho da mensagem na memória antes da serialização. Este tamanho pode diferir do comprimento real da seqüência de mensagens que está sendo registrada, e em muitas ocasiões é maior do que o tamanho real. Como resultado, as mensagens podem não ser registradas. Você pode explicar esse fato `maxSizeOfMessageToLog` especificando que o atributo é 10% maior do que o tamanho esperado da mensagem. Além disso, se as mensagens malformadas forem registradas, o espaço em disco real utilizado pelos `maxSizeOfMessageToLog`registros de mensagens pode ser até 5 vezes o tamanho do valor especificado por .

Se nenhum ouvinte de rastreamento for definido no arquivo de configuração, nenhuma saída de registro será gerada independentemente do nível de registro especificado.

As opções de registro de mensagens, como os atributos descritos nesta seção, podem ser alteradas em tempo de execução usando o WMI (Windows Management Instrumentation, instrumentação de gerenciamento do Windows). Isso pode ser feito acessando a instância [AppDomainInfo,](./wmi/appdomaininfo.md) `LogMessagesAtTransportLevel`que `LogMalformedMessages`expõe essas propriedades booleanas: `LogMessagesAtServiceLevel`, e . Portanto, se você configurar um ouvinte de rastreamento para registro `false` de mensagens, mas `true` definir essas opções na configuração, você poderá alterá-las posteriormente para quando o aplicativo estiver sendo executado. Isso efetivamente permite o registro de mensagens em tempo de execução. Da mesma forma, se você habilitar o registro de mensagens em seu arquivo de configuração, você poderá desativá-lo em tempo de execução usando o WMI. Para obter mais informações, consulte [Usando a Instrumentação de Gerenciamento do Windows para Diagnósticos](./wmi/index.md).

O `source` campo em um registro de mensagem especifica em que contexto a mensagem é registrada: ao enviar/receber uma mensagem de solicitação, para uma solicitação-resposta ou solicitação de 1 via, no modelo de serviço ou camada de transporte, ou no caso de uma mensagem malformada.

Para mensagens `source` malformadas, `Malformed`é igual a . Caso contrário, a fonte tem os seguintes valores com base no contexto.

Para solicitação/resposta

||Enviar solicitação|Receber solicitação|Enviar resposta|Receber resposta|
|-|------------------|---------------------|----------------|-------------------|
|Camada do modelo de serviço|Serviço<br /><br /> Nível<br /><br /> Enviar<br /><br /> Solicitação|Serviço<br /><br /> Nível<br /><br /> Receber<br /><br /> Solicitação|Serviço<br /><br /> Nível<br /><br /> Enviar<br /><br /> Responder|Serviço<br /><br /> Nível<br /><br /> Receber<br /><br /> Responder|
|Camada de transporte|Transporte<br /><br /> Enviar|Transporte<br /><br /> Receber|Transporte<br /><br /> Enviar|Transporte<br /><br /> Receber|

Para solicitação unidirecional

||Enviar solicitação|Receber solicitação|
|-|------------------|---------------------|
|Camada do modelo de serviço|Serviço<br /><br /> Nível<br /><br /> Enviar<br /><br /> Datagrama|Serviço<br /><br /> Nível<br /><br /> Receber<br /><br /> Datagrama|
|Camada de transporte|Transporte<br /><br /> Enviar|Transporte<br /><br /> Receber|

## <a name="message-filters"></a>Filtros de mensagem

Os filtros de `messageLogging` mensagem são `diagnostics` definidos no elemento de configuração da seção de configuração. Eles são aplicados no nível de serviço e transporte. Quando um ou mais filtros são definidos, apenas mensagens que correspondem a pelo menos um dos filtros são registradas. Se nenhum filtro for definido, todas as mensagens passarão.

Os filtros suportam a sintaxe XPath completa e são aplicados na ordem em que aparecem no arquivo de configuração. Um filtro sintáticamente incorreto resulta em uma exceção de configuração.

Os filtros também fornecem `nodeQuota` um recurso de segurança usando o atributo, que limita o número máximo de nódulos no XPath DOM que podem ser examinados para corresponder ao filtro.

O exemplo a seguir mostra como configurar um filtro que registra apenas mensagens que tenham uma seção de cabeçalho SOAP.

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

Os filtros não podem ser aplicados no corpo de uma mensagem. Os filtros que tentam manipular o corpo de uma mensagem são removidos da lista de filtros. Um evento também é emitido que indica isso. Por exemplo, o filtro a seguir seria removido da tabela do filtro.

```xml
<add xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">/s:Envelope/s:Body[contains(text(), "Hello")]</add>
```

## <a name="configuring-a-custom-listener"></a>Configurando um ouvinte personalizado

Você também pode configurar um ouvinte personalizado com opções adicionais. Um ouvinte personalizado pode ser útil na filtragem de elementos PII específicos do aplicativo de mensagens antes de registrar. O exemplo a seguir demonstra uma configuração personalizada do ouvinte.

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

Você deve estar `type` ciente de que o atributo deve ser definido como um nome de montagem qualificado do tipo.

## <a name="see-also"></a>Confira também

- [\<>de mensagens](../../configure-apps/file-schema/wcf/messagelogging.md)
- [Registro em log de mensagens](message-logging.md)
- [Configurações recomendadas para registro de rastreamento e mensagens](./tracing/recommended-settings-for-tracing-and-message-logging.md)

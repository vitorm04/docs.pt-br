---
title: Registro de mensagem e rastreamento
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: 9ffb7a99540b953fc93a22d2296caf86f294d25d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143818"
---
# <a name="tracing-and-message-logging"></a>Registro de mensagem e rastreamento
Esta amostra demonstra como ativar o rastreamento e o registro de mensagens. Os traços e registros de mensagens resultantes são visualizados usando a [Ferramenta de Visualização de Rastreamento de Serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
## <a name="tracing"></a>Rastreamento  
 A Windows Communication Foundation (WCF) usa <xref:System.Diagnostics> o mecanismo de rastreamento definido no namespace. Neste modelo de rastreamento, os dados de rastreamento são produzidos por fontes de rastreamento que os aplicativos implementam. Cada fonte é identificada por um nome. Os consumidores de rastreamento criam rastreadores para as fontes de rastreamento para as quais eles querem recuperar informações. Para receber dados de rastreamento, você deve criar um ouvinte para a fonte de rastreamento. No WCF, isso pode ser feito adicionando o seguinte código ao arquivo de configuração `switchValue`do serviço ou do cliente, definindo a fonte de rastreamento do Modelo de Serviço:  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-service.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>  
```  
  
 Para obter mais informações sobre as fontes de rastreamento, consulte a seção Trace Source no tópico [Configurando rastreamento.](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
  
## <a name="activity-tracing-and-propagation"></a>Rastreamento e Propagação de Atividades  
 Tendo `ActivityTracing` ativado `propagateActivity` e `true` definido `system.ServiceModel` nas fontes de rastreamento tanto para o cliente quanto para o serviço, fornecem correlação de traços dentro de unidades lógicas de processamento (atividades), em atividades dentro de endpoints (através de transferências de atividades) e em atividades que abrangem vários pontos finais (através da propagação de ID de atividade).  
  
 Esses três mecanismos (atividades, transferências e propagação) podem ajudá-lo a localizar a causa raiz de um erro mais rapidamente usando a ferramenta Visualizador de rastreamento de serviço. Para obter mais informações, consulte [Usando o Visualizador de rastreamento de serviço para visualizar traços correlacionados e solução de problemas](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
 É possível estender o rastreamento fornecido pelo ServiceModel criando traços de atividade definidos pelo usuário. O rastreamento de atividades definido pelo usuário permite que o usuário crie atividades de rastreamento para:  
  
- Traços de grupo em unidades lógicas de trabalho.  
  
- Correlacionar atividades através de transferências e propagação.  
  
- Diminuir o custo de desempenho do rastreamento WCF (por exemplo, o custo do espaço em disco de um arquivo de log).  
  
 Para obter mais informações sobre o rastreamento de atividade definido pelo usuário, consulte a amostra [de rastreamento de extensão.](../../../../docs/framework/wcf/samples/extending-tracing.md)  
  
## <a name="message-logging"></a>Registro em log de mensagens  
 O registro de mensagens pode ser ativado tanto no cliente quanto no serviço de qualquer aplicativo WCF. Para habilitar o registro de mensagens, você deve adicionar o seguinte código ao cliente ou ao serviço:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics>  
      <!-- Enable Message Logging here. -->  
      <!-- log all messages received or sent at the transport or service model levels -->  
      <messageLogging logEntireMessage="true"  
                      maxMessagesToLog="300"  
                      logMessagesAtServiceLevel="true"  
                      logMalformedMessages="true"  
                      logMessagesAtTransportLevel="true" />  
    </diagnostics>  
  </system.serviceModel>  
</configuration>  
```  
  
 Quando uma mensagem é gravada, o tipo de rastreamento depende se ela está sendo rastreada no cliente ou no servidor. Por exemplo, uma mensagem "Adicionar" enviada a um cliente é rastreada na categoria "TransportWrite" no cliente, enquanto a mesma mensagem é rastreada na categoria "TransportRead" no serviço.  
  
 Configure o ouvinte de rastreamento adicionando <xref:System.Diagnostics> o seguinte código à seção do arquivo App.config do cliente ou ao arquivo Web.config do serviço:  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-client.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
```  
  
 As mensagens são registradas no formato XML no diretório de destino especificado no arquivo de configuração.  
  
> [!NOTE]
> Os arquivos trace não são criados sem criar inicialmente o diretório de log. Certifique-se de que o diretório C:\logs\ existe ou especifique um diretório de registro alternativo na configuração do ouvinte. Consulte as instruções iniciais de configuração no final deste documento para obter mais informações.  
  
 Para obter mais informações sobre o registro de mensagens, consulte o tópico [Configurando registro de mensagens.](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Antes de executar a amostra De rastreamento e registro de mensagens, crie o diretório C:\logs\ para que o serviço escreva os arquivos .svclog para. O nome deste diretório é definido no arquivo de configuração como o caminho para que os traços e mensagens sejam registrados e possam ser alterados. Dê ao usuário Network Service para gravar acesso ao diretório de logs.  
  
3. Para construir a edição C#, C++ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Para executar a amostra em uma configuração de computador único ou cruzado, siga as instruções em [Executar as amostras da Fundação](../../../../docs/framework/wcf/samples/running-the-samples.md)de Comunicação do Windows .  
  
> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a>Confira também

- [Rastreamento](../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [AppFabric que monitora Exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))

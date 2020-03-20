---
title: Estendendo rastreamento
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: a7231d340d2528a42c8cbb5294d812d52db92d54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183683"
---
# <a name="extending-tracing"></a>Estendendo rastreamento
Esta amostra demonstra como estender o recurso de rastreamento da Windows Communication Foundation (WCF) escrevendo traços de atividade definidos pelo usuário no código de cliente e serviço. Isso permite que o usuário crie atividades de rastreamento e rastreamentos em unidades lógicas de trabalho. Também é possível correlacionar atividades através de transferências (dentro do mesmo ponto final) e propagação (entre os pontos finais). Nesta amostra, o rastreamento é habilitado tanto para o cliente quanto para o serviço. Para obter mais informações sobre como ativar o rastreamento em arquivos de configuração de clientes e serviços, consulte [Rastreamento e Registro de Mensagens](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).  
  
 Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
> Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.  
  
> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a>Rastreamento e Propagação de Atividades  
 O rastreamento de atividades definido pelo usuário permite que o usuário crie suas próprias atividades de rastreamento para agrupar vestígios em unidades lógicas de trabalho, correlacionar atividades por meio de transferências e propagação e diminuir o custo de desempenho do rastreamento do WCF (por exemplo, o custo do espaço em disco de um arquivo de registro).  
  
### <a name="adding-custom-sources"></a>Adicionando fontes personalizadas  
 Os traços definidos pelo usuário podem ser adicionados ao código de cliente e de serviço. A adição de fontes de rastreamento aos arquivos de configuração do cliente ou de serviço permite que esses rastreamentos personalizados sejam gravados e exibidos na [Ferramenta de Visualização de Rastreamento de Serviço (SvcTraceViewer.exe).](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) O código a seguir mostra como adicionar `ServerCalculatorTraceSource` uma fonte de rastreamento definida pelo usuário nomeada ao arquivo de configuração.  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
        <source name="ServerCalculatorTraceSource" switchValue="Information,ActivityTracing">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
       <add initializeData="C:\logs\ServerTraces.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" traceOutputOptions="Callstack">  
            <filter type="" />  
        </add>  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>....  
....  
```  
  
### <a name="correlating-activities"></a>Atividades correlacionadas  
 Para correlacionar as atividades `propagateActivity` diretamente entre os `true` pontos `System.ServiceModel` finais, o atributo deve ser definido na fonte de rastreamento. Além disso, para propagar rastreamentos sem passar por atividades do WCF, o ServiceModel Activity Tracing deve ser desligado. Isso pode ser visto no seguinte exemplo de código.  
  
> [!NOTE]
> Desativar o ServiceModel Activity Ttrace não é o mesmo que `switchValue` ter o nível de rastreamento, denotado pela propriedade, definido como desligado.  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a>Redução do custo de desempenho  
 A `ActivityTracing` configuração `System.ServiceModel` na origem do rastreamento gera um arquivo de rastreamento que contém apenas traços de atividade definidos pelo usuário, sem que nenhum dos traços de atividade serviceModel seja incluído. Isso resulta em um arquivo de log de tamanho muito menor. No entanto, a oportunidade de correlacionar os traços de processamento wcf é perdida.  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de computador único ou cruzado, siga as instruções em [Executar as amostras da Fundação](../../../../docs/framework/wcf/samples/running-the-samples.md)de Comunicação do Windows .  
  
## <a name="see-also"></a>Confira também

- [AppFabric que monitora Exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))

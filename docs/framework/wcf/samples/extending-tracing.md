---
title: Estendendo rastreamento
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: 64f9d18b68e5f2604631a72579eb45bf7f7b8372
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716393"
---
# <a name="extending-tracing"></a>Estendendo rastreamento
Este exemplo demonstra como estender o recurso de rastreamento de Windows Communication Foundation (WCF) gravando rastreamentos de atividade definidos pelo usuário no código do cliente e do serviço. Isso permite que o usuário crie atividades de rastreamento e rastreamentos de grupo em unidades lógicas de trabalho. Também é possível correlacionar atividades por meio de transferências (dentro do mesmo ponto de extremidade) e da propagação (entre pontos de extremidade). Neste exemplo, o rastreamento está habilitado para o cliente e o serviço. Para obter mais informações sobre como habilitar o rastreamento em arquivos de configuração de cliente e serviço, consulte [rastreamento e log de mensagens](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).  
  
 Este exemplo é baseado na [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
> Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.  
  
> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras. Este exemplo está localizado no seguinte diretório.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a>Rastreamento e propagação de atividade  
 O rastreamento de atividade definido pelo usuário permite que o usuário crie suas próprias atividades de rastreamento para agrupar rastreamentos em unidades lógicas de trabalho, correlacionar atividades por meio de transferências e propagação e diminuir o custo de desempenho do rastreamento do WCF (por exemplo, o custo de espaço em disco de um arquivo de log).  
  
### <a name="adding-custom-sources"></a>Adicionando fontes personalizadas  
 Os rastreamentos definidos pelo usuário podem ser adicionados ao código do cliente e do serviço. A adição de fontes de rastreamento aos arquivos de configuração do cliente ou do serviço permite que esses rastreamentos personalizados sejam registrados e exibidos na [ferramenta do Visualizador de rastreamento de serviço (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). O código a seguir mostra como adicionar uma fonte de rastreamento definida pelo usuário chamada `ServerCalculatorTraceSource` ao arquivo de configuração.  
  
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
  
### <a name="correlating-activities"></a>Correlacionando atividades  
 Para correlacionar atividades diretamente entre pontos de extremidade, o atributo `propagateActivity` deve ser definido como `true` na fonte de rastreamento `System.ServiceModel`. Além disso, para propagar rastreamentos sem passar pelas atividades do WCF, o rastreamento de atividade de ServiceModel deve ser desativado. Isso pode ser visto no exemplo de código a seguir.  
  
> [!NOTE]
> Desativar o rastreamento de atividade de ServiceModel não é o mesmo que ter o nível de rastreamento, indicado pela propriedade `switchValue`, definido como off.  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a>Diminuindo o custo de desempenho  
 Definir `ActivityTracing` como off na fonte de rastreamento de `System.ServiceModel` gera um arquivo de rastreamento que contém apenas rastreamentos de atividade definidos pelo usuário, sem nenhum dos rastreamentos de atividade de ServiceModel incluídos. Isso resulta em um arquivo de log de tamanho muito menor. No entanto, a oportunidade de correlacionar rastreamentos de processamento do WCF é perdida.  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar o exemplo em uma configuração de computador único ou entre computadores, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Consulte também

- [Exemplos de monitoramento do AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)

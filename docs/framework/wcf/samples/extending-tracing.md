---
title: Estendendo rastreamento
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: 59291b6a57ba602e5fea84dcd571a8d767b7cc04
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806803"
---
# <a name="extending-tracing"></a>Estendendo rastreamento
Este exemplo demonstra como estender o recurso de rastreamento do Windows Communication Foundation (WCF), escrevendo rastreamentos de atividade definida pelo usuário no código de cliente e de serviço. Isso permite que o usuário criar atividades de rastreamento e o grupo de rastreamentos em unidades lógicas de trabalho. Também é possível correlacionar atividades por meio das transferências (dentro do mesmo ponto de extremidade) e propagação (através de pontos de extremidade). Neste exemplo, o rastreamento está habilitado para o cliente e o serviço. Para obter mais informações sobre como habilitar o rastreamento em arquivos de configuração de cliente e de serviço, consulte [rastreamento e registro em log de mensagem](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).  
  
 Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a>Rastreamento e a propagação de atividade  
 Rastreamento de atividade definida pelo usuário permite que o usuário criar suas próprias atividades de rastreamento para rastreamentos de grupo em unidades lógicas de trabalho, correlacionar atividades por meio de transferências e propagação e reduzir o custo de desempenho de rastreamento do WCF (por exemplo, o espaço em disco de custo de um arquivo de log).  
  
### <a name="adding-custom-sources"></a>Adicionando fontes personalizadas  
 Rastreamentos definidos pelo usuário podem ser adicionados ao código de cliente e de serviço. Adicionando fontes de rastreamento para os arquivos de configuração de cliente ou serviço permitem esses rastreamentos personalizados a ser registrado e exibido no [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). O código a seguir mostra como adicionar uma origem de rastreamento definido pelo usuário chamada `ServerCalculatorTraceSource` para o arquivo de configuração.  
  
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
  
### <a name="correlating-activities"></a>Correlacionar atividades  
 Para correlacionar atividades diretamente através de pontos de extremidade, o `propagateActivity` atributo deve ser definido como `true` no `System.ServiceModel` origem do rastreamento. Além disso, para propagar rastreamentos sem passar por meio de atividades WCF, rastreamento de atividade de ServiceModel deve ser desativada. Isso pode ser visto no exemplo de código a seguir.  
  
> [!NOTE]
>  Desativar o rastreamento de atividade de ServiceModel não é o mesmo como tendo o nível de rastreamento, indicado pelo `switchValue` propriedade, definida como off.  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a>Reduzindo o custo de desempenho  
 Configuração `ActivityTracing` desativada no `System.ServiceModel` Rastrear origem gera um arquivo de rastreamento que contém somente os rastreamentos atividade definida pelo usuário, sem qualquer um dos rastreamentos de atividade de ServiceModel incluídos. Isso resulta em um arquivo de log de tamanho muito menor. No entanto, a oportunidade de correlacionar processar os rastreamentos do WCF é perdida.  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de monitoramento do AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)

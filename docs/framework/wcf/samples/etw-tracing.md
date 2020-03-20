---
title: Rastreamento ETW
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: 07379a464e6635a3de10c08647dbc769a5885e4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183697"
---
# <a name="etw-tracing"></a>Rastreamento ETW
Esta amostra demonstra como implementar o rastreamento End-to-End (E2E) usando o ETW de eventos para Windows (ETW) e o `ETWTraceListener` que é fornecido com esta amostra. A amostra é baseada no [Rastreamento e](../../../../docs/framework/wcf/samples/getting-started-sample.md) inclui rastreamento ETW.  
  
> [!NOTE]
> Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.  
  
 Esta amostra assume que você está familiarizado com [rastreamento e registro de mensagens](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).  
  
 Cada fonte de <xref:System.Diagnostics> rastreamento no modelo de rastreamento pode ter vários ouvintes de rastreamento que determinam onde e como os dados são rastreados. O tipo de ouvinte define o formato no qual os dados de rastreamento são registrados. A amostra de código a seguir mostra como adicionar o ouvinte à configuração.  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel"
             switchValue="Verbose,ActivityTracing"  
             propagateActivity="true">  
            <listeners>  
                <add type=  
                   "System.Diagnostics.DefaultTraceListener"  
                   name="Default">  
                   <filter type="" />  
                </add>  
                <add name="ETW">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
        <add type=  
            "Microsoft.ServiceModel.Samples.EtwTraceListener, ETWTraceListener"  
            name="ETW" traceOutputOptions="Timestamp">  
            <filter type="" />  
       </add>  
    </sharedListeners>  
</system.diagnostics>  
```  
  
 Antes de usar este ouvinte, uma Sessão de Rastreamento eTW deve ser iniciada. Esta sessão pode ser iniciada usando Logman.exe ou Tracelog.exe. Um arquivo SetupETW.bat está incluído nesta amostra para que você possa configurar a Sessão de Rastreamento eTW juntamente com um arquivo CleanupETW.bat para encerrar a sessão e completar o arquivo de log.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico. Para obter mais informações sobre essas ferramentas, consulte<https://go.microsoft.com/fwlink/?LinkId=56580>  
  
 Ao usar o ETWTraceListener, os rastreamentos são registrados em arquivos binários .etl. Com o rastreamento servicemodel ligado, todos os traços gerados aparecem no mesmo arquivo. Use [a Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) para visualizar arquivos de log .etl e .svclog. O espectador cria uma visão de ponta a ponta do sistema que torna possível rastrear uma mensagem de sua fonte até seu destino e ponto de consumo.  
  
 O ETW Trace Listener suporta registro circular. Para habilitar esse recurso, vá `cmd` para **Iniciar**, **Executar** e digite para iniciar um console de comando. No comando a seguir, substitua o `<logfilename>` parâmetro pelo nome do seu arquivo de log.  
  
```console  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 Os `-f` `-max` interruptores são opcionais. Eles especificam o formato circular binário e o tamanho máximo do log de 1000MB, respectivamente. O `-p` switch é usado para especificar o provedor de rastreamento. Em nosso `"{411a0819-c24b-428c-83e2-26b41091702e}"` exemplo, está o GUID para "Provedor de Amostra de ETW XML".  
  
 Para iniciar a sessão, digite o seguinte comando.  
  
```console  
logman start Wcf  
```  
  
 Depois de terminar o registro, você pode interromper a sessão com o seguinte comando.  
  
```console  
logman stop Wcf  
```  
  
 Esse processo gera registros circulares binários que você pode processar com sua ferramenta de escolha, incluindo [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) ou Tracerpt.  
  
 Você também pode rever a amostra [de Rastreamento Circular](../../../../docs/framework/wcf/samples/circular-tracing.md) para obter mais informações sobre um ouvinte alternativo para realizar o registro circular.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de ter realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
    > [!NOTE]
    > Para usar os comandos RegisterProvider.bat, SetupETW.bat e CleanupETW.bat, você deve ser executado uma conta de administrador local. Se você estiver usando o Windows Vista ou posteriormente, você também deve executar o prompt de comando com privilégios elevados. Para isso, clique com o botão direito do mouse no ícone de solicitação de comando e clique **em Executar como administrador**.  
  
3. Antes de executar a amostra, execute RegisterProvider.bat no cliente e no servidor. Isso configura o arquivo ETWTracingSampleLog.etl resultante para gerar vestígios que podem ser lidos pelo Visualizador de rastreamento de serviço. Este arquivo pode ser encontrado na pasta C:\logs. Se essa pasta não existir, ela deve ser criada ou não são gerados vestígios. Em seguida, execute setupETW.bat nos computadores cliente e servidor para iniciar a Sessão de Rastreamento eTW. O arquivo SetupETW.bat pode ser encontrado na pasta CS\Client.  
  
4. Para executar a amostra em uma configuração de computador único ou cruzado, siga as instruções em [Executar as amostras da Fundação](../../../../docs/framework/wcf/samples/running-the-samples.md)de Comunicação do Windows .  
  
5. Quando a amostra estiver concluída, execute CleanupETW.bat para concluir a criação do arquivo ETWTracingSampleLog.etl.  
  
6. Abra o arquivo ETWTracingSampleLog.etl a partir do Visualizador de rastreamento de serviço. Você será solicitado a salvar o arquivo formatado binário como um arquivo .svclog.  
  
7. Abra o arquivo .svclog recém-criado dentro do Service Trace Viewer para visualizar os traços ETW e ServiceModel.  
  
> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a>Confira também

- [AppFabric que monitora Exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))

---
title: Rastreamento ETW
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
caps.latest.revision: "42"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ebffd082f5d1b07ab016c0e5e72d6ad23542147
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="etw-tracing"></a>Rastreamento ETW
Este exemplo demonstra como implementar o rastreamento de ponta a ponta (E2E) usando o rastreamento de eventos para Windows (ETW) e o `ETWTraceListener` que é fornecido com este exemplo. O exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) e inclui o rastreamento ETW.  
  
> [!NOTE]
>  Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.  
  
 Este exemplo pressupõe que você esteja familiarizado com [rastreamento e registro em log de mensagem](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).  
  
 Cada origem de rastreamento no <xref:System.Diagnostics> modelo de rastreamento pode ter vários ouvintes de rastreamento que determinam onde e como os dados são rastreados. O tipo de ouvinte define o formato no qual os dados de rastreamento serão registrados. O exemplo de código a seguir mostra como adicionar o ouvinte para a configuração.  
  
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
  
 Antes de usar este ouvinte, uma sessão de rastreamento ETW deve ser iniciada. Essa sessão pode ser iniciada usando Logman.exe ou Tracelog.exe. Um arquivo de SetupETW.bat é incluído com este exemplo, para que você pode configurar a sessão de rastreamento ETW junto com um arquivo CleanupETW.bat para fechar a sessão e concluir o arquivo de log.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico. Para obter mais informações sobre essas ferramentas, consulte [http://go.microsoft.com/fwlink/?LinkId=56580](http://go.microsoft.com/fwlink/?LinkId=56580)  
  
 Ao usar o ETWTraceListener, os rastreamentos serão registrados em arquivos. etl binário. Com o rastreamento de ServiceModel ativado, todos os rastreamentos gerados aparecem no mesmo arquivo. Use [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) para exibir os arquivos de log. etl e .svclog. O Visualizador de cria uma exibição de ponta a ponta do sistema que torna possível rastrear uma mensagem de sua origem para o destino e o ponto de consumo.  
  
 O ouvinte de rastreamento ETW oferece suporte ao registro em log circular. Para habilitar esse recurso, vá para **iniciar**, **executar** e tipo `cmd` para iniciar o console de comando. No comando a seguir, substitua o `<logfilename>` parâmetro com o nome do seu arquivo de log.  
  
```  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 O `-f` e `-max` switches são opcionais. Eles especificam o formato circular binário e o tamanho de log máximo de 1000MB respectivamente. O `-p` switch é usada para especificar o provedor de rastreamento. Em nosso exemplo, `"{411a0819-c24b-428c-83e2-26b41091702e}"` é o GUID "Provedor de exemplo do XML ETW".  
  
 Para iniciar a sessão, digite o comando a seguir.  
  
```  
Logman start Wcf  
```  
  
 Depois de concluir o registro em log, você pode parar a sessão com o comando a seguir.  
  
```  
Logman stop Wcf  
```  
  
 Esse processo gera logs circulares binários que você pode processar com a ferramenta de sua escolha, incluindo [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) ou Tracerpt.  
  
 Você também pode examinar o [rastreamento Circular](../../../../docs/framework/wcf/samples/circular-tracing.md) exemplo para obter mais informações sobre um ouvinte alternativa para executar o log circular.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
    > [!NOTE]
    >  Para usar os comandos RegisterProvider.bat, SetupETW.bat e CleanupETW.bat, você deve executar sob uma conta de administrador local. Se você estiver usando [!INCLUDE[wv](../../../../includes/wv-md.md)] ou posterior, você também deve executar o prompt de comando com privilégios elevados. Para fazer isso, clique no ícone de prompt de comando, clique em **executar como administrador**.  
  
3.  Antes de executar o exemplo, execute RegisterProvider.bat no cliente e no servidor. Isso configura o arquivo ETWTracingSampleLog.etl resultante para gerar rastreamentos podem ser lidos pelo Visualizador de rastreamento do serviço. Esse arquivo pode ser encontrado na pasta c:\Logs. Se essa pasta não existir, ele deve ser criado ou nenhum rastreamento é gerado. Em seguida, execute SetupETW.bat nos computadores cliente e servidor para iniciar a sessão de rastreamento ETW. O arquivo SetupETW.bat pode ser encontrado na pasta CS\Client.  
  
4.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5.  Quando o exemplo for concluído, execute CleanupETW.bat para concluir a criação do arquivo ETWTracingSampleLog.etl.  
  
6.  Abra o arquivo de ETWTracingSampleLog.etl de dentro do Visualizador de rastreamento de serviço. Você será solicitado a salvar o arquivo com formato binário como um arquivo de .svclog.  
  
7.  Abra o arquivo recém-criado .svclog de dentro do Visualizador de rastreamento de serviço para exibir os rastreamentos ETW e ServiceModel.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de monitoramento do AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)

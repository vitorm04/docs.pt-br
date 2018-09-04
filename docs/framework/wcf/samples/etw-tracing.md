---
title: Rastreamento ETW
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: 3e4dd141bd5f6a9d137b2fe981b3b412ec0c81e2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43558365"
---
# <a name="etw-tracing"></a>Rastreamento ETW
Este exemplo demonstra como implementar o rastreamento de ponta a ponta (E2E) usando o rastreamento de eventos para Windows (ETW) e o `ETWTraceListener` que é fornecido com este exemplo. O exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) e inclui o rastreamento ETW.  
  
> [!NOTE]
>  Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.  
  
 Este exemplo pressupõe que você esteja familiarizado com [rastreamento e registro em log de mensagem](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).  
  
 Cada origem de rastreamento no <xref:System.Diagnostics> modelo de rastreamento pode ter vários ouvintes de rastreamento que determinam onde e como os dados são rastreados. O tipo de ouvinte define o formato no qual os dados de rastreamento são registrados. O exemplo de código a seguir mostra como adicionar o ouvinte à configuração.  
  
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
  
 Antes de usar este ouvinte, uma sessão de rastreamento ETW deve ser iniciada. Esta sessão pode ser iniciada usando Logman.exe ou Tracelog.exe. Um arquivo de SetupETW.bat é incluído com este exemplo, para que você pode configurar a sessão de rastreamento ETW junto com um arquivo CleanupETW.bat para fechar a sessão e concluir o arquivo de log.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico. Para obter mais informações sobre essas ferramentas, consulte [https://go.microsoft.com/fwlink/?LinkId=56580](https://go.microsoft.com/fwlink/?LinkId=56580)  
  
 Ao usar o ETWTraceListener, os rastreamentos são registrados nos arquivos. etl binário. Com o rastreamento de ServiceModel ativado, todos os rastreamentos gerados são exibidos no mesmo arquivo. Use [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) para exibir os arquivos de log. etl e. svclog. O Visualizador de cria uma exibição de ponta a ponta do sistema que torna possível rastrear uma mensagem de sua origem para seu destino e o ponto de consumo.  
  
 O ouvinte de rastreamento ETW oferece suporte a log circular. Para habilitar esse recurso, vá para **inicie**, **execute** e digite `cmd` para iniciar um console de comando. No comando a seguir, substitua o `<logfilename>` parâmetro com o nome do seu arquivo de log.  
  
```  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 O `-f` e `-max` alternâncias são opcionais. Eles especificam o formato binário de circular e o tamanho máximo do log de 1000MB respectivamente. O `-p` switch é usada para especificar o provedor de rastreamento. Em nosso exemplo, `"{411a0819-c24b-428c-83e2-26b41091702e}"` é o GUID para o "Provedor de exemplo do XML ETW".  
  
 Para iniciar a sessão, digite o comando a seguir.  
  
```  
Logman start Wcf  
```  
  
 Depois de concluir o registro em log, você pode parar a sessão com o comando a seguir.  
  
```  
Logman stop Wcf  
```  
  
 Esse processo gera logs circulares binários que você pode processar com sua ferramenta de escolha, incluindo [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) ou Tracerpt.  
  
 Você também pode examinar a [rastreamento Circular](../../../../docs/framework/wcf/samples/circular-tracing.md) exemplo para obter mais informações sobre um ouvinte de alternativa para executar o log circular.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
    > [!NOTE]
    >  Para usar os comandos RegisterProvider.bat, SetupETW.bat e CleanupETW.bat, você deve executar sob uma conta de administrador local. Se você estiver usando [!INCLUDE[wv](../../../../includes/wv-md.md)] ou posterior, você também deve executar o prompt de comando com privilégios elevados. Para fazer isso, clique com botão direito no ícone do prompt de comando, clique em **executar como administrador**.  
  
3.  Antes de executar o exemplo, execute RegisterProvider.bat no cliente e servidor. Isso configura o arquivo ETWTracingSampleLog.etl resultante para gerar rastreamentos que podem ser lido pelo Visualizador de rastreamento de serviço. Esse arquivo pode ser encontrado na pasta C:\logs. Se essa pasta não existir, ele deverá ser criado ou nenhum rastreamentos são gerados. Em seguida, execute SetupETW.bat nos computadores cliente e servidor para iniciar a sessão de rastreamento de ETW. O arquivo SetupETW.bat pode ser encontrado na pasta CS\Client.  
  
4.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5.  Quando o exemplo for concluído, execute CleanupETW.bat para concluir a criação do arquivo ETWTracingSampleLog.etl.  
  
6.  Abra o arquivo ETWTracingSampleLog.etl de dentro do Visualizador de rastreamento de serviço. Você será solicitado a salvar o arquivo binário do formatado como um arquivo. svclog.  
  
7.  Abra o arquivo. svclog recém-criado no Visualizador de rastreamento do serviço para exibir os rastreamentos ETW e ServiceModel.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a>Consulte também  
 [AppFabric que monitora exemplos](https://go.microsoft.com/fwlink/?LinkId=193959)

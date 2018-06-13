---
title: Rastreamento circular
ms.date: 03/30/2017
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
ms.openlocfilehash: ce39a5d1b65bad78ff67154a7d8b62c2f19b1fa9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33503305"
---
# <a name="circular-tracing"></a>Rastreamento circular
Este exemplo demonstra a implementação de um ouvinte de rastreamento de buffer circular. Um cenário comum para serviços de produção é ter os serviços que estão disponíveis por longos períodos de tempo e ter o log de rastreamento habilitado em um nível baixo. Esses serviços consumam muito espaço em disco. Ao solucionar problemas de um serviço, os dados mais recentes no log de rastreamento são relevantes para resolver um problema. Este exemplo demonstra uma implementação de um ouvinte de rastreamento de buffer circular na qual somente os rastreamentos mais recentes são mantidos no disco até um período configurável de dados. Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) e inclui um ouvinte de rastreamento personalizada.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Este exemplo pressupõe que você esteja familiarizado com o [rastreamento e registro em log de mensagem](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) de exemplo e leu a documentação fornecida para o [rastreamento e registro em log de mensagem](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) exemplo.  
  
## <a name="circular-buffer-trace-listener"></a>Ouvinte de rastreamento de Buffer circular  
 O conceito inerente a implementação do ouvinte de rastreamento de Buffer Circular é ter dois arquivos de que cada uma podem armazenar até a metade dos dados do log de rastreamento desejado total. O ouvinte cria um arquivo e grava no arquivo até atingir o limite de metade do tamanho dos dados, no ponto em que alterna um segundo arquivo. Quando o ouvinte atinge o limite para o segundo arquivo - ele substitui o primeiro arquivo com novos rastreamentos.  
  
 Este ouvinte deriva o `XmlWriteTraceListener` e permite que os logs sejam exibidos com o [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Ao tentar exibir os logs, os dois arquivos de log podem facilmente recombined abrindo ambos os arquivos de log ao mesmo tempo em que a ferramenta do Visualizador de rastreamento de serviço. A ferramenta do Visualizador de rastreamento de serviço automaticamente cuida de classificação, os rastreamentos para que apareçam na ordem correta.  
  
## <a name="configuration"></a>Configuração  
 Um serviço pode ser configurado para usar o ouvinte de rastreamento de Buffer Circular, adicionando o código a seguir para elementos do ouvinte e fonte. O tamanho máximo de arquivo é especificado pela configuração de `maxFileSizeKB` atributo na configuração do ouvinte de rastreamento circular. Isso é demonstrado no código a seguir.  
  
```xml  
<system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel" switchValue="Information,ActivityTracing" propagateActivity="true">  
      <listeners>  
        <add name="CircularTraceListener" />  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="CircularTraceListener" type="Microsoft. Samples.ServiceModel.CircularTraceListener,CircularTraceListener"   
         initializeData="c:\logs\CircularTracing-service.svclog" maxFileSizeKB="100" />  
  </sharedListeners>  
  <trace autoflush="true" />  
</system.diagnostics>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de monitoramento do AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)

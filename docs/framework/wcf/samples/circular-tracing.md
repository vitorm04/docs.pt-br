---
title: Rastreamento circular
ms.date: 03/30/2017
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
ms.openlocfilehash: 1f6c5287e6a53ed26ee5c9ed477e08dafc512e3f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406176"
---
# <a name="circular-tracing"></a>Rastreamento circular
Este exemplo demonstra a implementação de um ouvinte de rastreamento de buffer circular. Um cenário comum para serviços de produção é ter serviços que estão disponíveis por longos períodos de tempo e tem o log de rastreamento habilitado em um nível baixo. Esses serviços consumam muito espaço em disco. Ao solucionar problemas de um serviço, os dados mais recentes no log de rastreamento são relevantes para resolver um problema. Este exemplo demonstra uma implementação de um ouvinte de rastreamento circular buffer no qual somente os rastreamentos mais recentes são mantidos em disco até um período configurável de dados. Este exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) e inclui um ouvinte de rastreamento personalizado.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Este exemplo pressupõe que você esteja familiarizado com o [rastreamento e registro em log de mensagem](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) de exemplo e que leu a documentação fornecida para o [rastreamento e registro em log de mensagem](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) exemplo.  
  
## <a name="circular-buffer-trace-listener"></a>Ouvinte de rastreamento de Buffer circular  
 O conceito por trás da implementação do ouvinte de rastreamento de Buffer Circular é ter dois arquivos que cada uma podem armazenar até a metade dos dados do log de rastreamento desejado total. O ouvinte cria um arquivo e grava a esse arquivo, até atingir o limite de metade do tamanho dos dados, no ponto em que ele muda para um segundo arquivo. Quando o ouvinte de atinge o limite para o segundo arquivo - ele substitui o primeiro arquivo com novos rastreamentos.  
  
 Este ouvinte deriva de `XmlWriteTraceListener` e permite que os logs sejam exibidos com o [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Ao tentar exibir os logs, os dois arquivos de log podem facilmente recombinados abrindo ambos os arquivos de log ao mesmo tempo em que a ferramenta Visualizador de rastreamento de serviço. A ferramenta Visualizador de rastreamento de serviço cuida automaticamente da classificação os rastreamentos para que eles apareçam na ordem correta.  
  
## <a name="configuration"></a>Configuração  
 Um serviço pode ser configurado para usar o ouvinte de rastreamento de Buffer Circular, adicionando o código a seguir para elementos de um ouvinte e o código-fonte. O tamanho máximo é especificado pela configuração de `maxFileSizeKB` atributo na configuração do ouvinte de rastreamento circular. Isso é demonstrado no código a seguir.  
  
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
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`  
  
## <a name="see-also"></a>Consulte também  
 [AppFabric que monitora exemplos](https://go.microsoft.com/fwlink/?LinkId=193959)

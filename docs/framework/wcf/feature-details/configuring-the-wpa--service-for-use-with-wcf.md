---
title: Configurando o Serviço de ativação de processos do Windows (WAS) para utilizar com o Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
ms.openlocfilehash: 2da2653f3d2bd3d998b0ebbe87ea33760315f7df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185298"
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a>Configurando o Serviço de ativação de processos do Windows (WAS) para utilizar com o Windows Communication Foundation
Este tópico descreve as etapas necessárias para configurar o Serviço de Ativação de Processos do Windows (também conhecido como WAS) no Windows Vista para hospedar serviços da Windows Communication Foundation (WCF) que não se comunicam através de protocolos de rede HTTP. As seções a seguir descrevem as etapas desta configuração:  
  
- Instale (ou confirme a instalação) dos componentes de ativação do WCF necessários.  
  
- Crie um site WAS com as vinculações do protocolo de rede que você deseja usar ou adicione um novo protocolo vinculando a um site existente.  
  
- Crie um aplicativo para hospedar seus serviços e permita que esse aplicativo use os protocolos de rede necessários.  
  
- Crie um serviço WCF que exponha um ponto final não-HTTP.  
  
## <a name="configuring-a-site-with-non-http-bindings"></a>Configuração de um site com vinculações não-HTTP  
 Para usar uma vinculação não-HTTP com WAS, a vinculação do site deve ser adicionada à configuração WAS. O armazenamento de configuração para WAS é o arquivo applicationHost.config, localizado no diretório %windir%\system32\inetsrv\config. Esta configuração é compartilhada por WAS e IIS 7.0.  
  
 aplicativoHost.config é um arquivo de texto XML que pode ser aberto com qualquer editor de texto padrão (como Bloco de Notas). No entanto, a ferramenta de configuração de linha de comando IIS 7.0 (appcmd.exe) é a maneira preferida de adicionar vinculações de sites não-HTTP.  
  
 O comando a seguir adiciona um site net.tcp vinculado ao site padrão usando appcmd.exe (este comando é inserido como uma única linha).  
  
```console  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 Este comando adiciona a nova vinculação net.tcp ao site padrão da Web adicionando a linha indicada abaixo ao arquivo applicationHost.config.  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
        <bindings>  
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            //The following line is added by the command.  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
        </bindings>  
    </site>  
</sites>  
```  
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a>Habilitando um aplicativo para usar protocolos não-HTTP  
 Você pode ativar ou desativar protocolos de rede individuais no nível do aplicativo. O comando a seguir ilustra como ativar os protocolos HTTP e net.tcp para um aplicativo que é executado no `Default Web Site`.  
  
```console  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 A lista de protocolos habilitados também \<pode ser definida no aplicativoPadrãos> elemento da configuração XML do site armazenado em ApplicationHost.config.  
  
 O código XML a seguir do aplicativoHost.config ilustra um site vinculado a protocolos HTTP e não-HTTP. A configuração adicional necessária para suportar protocolos não-HTTP é chamada com comentários.  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
    <application path="/">  
        <virtualDirectory path="/" physicalPath="D:\inetpub\wwwroot" />  
    </application>  
       <bindings>  
            //The following two lines are added by the command.  
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
       </bindings>  
    </site>  
    <siteDefaults>  
        <logFile
        customLogPluginClsid="{FF160663-DE82-11CF-BC0A-00AA006111E0}"  
          directory="D:\inetpub\logs\LogFiles" />  
        <traceFailedRequestsLogging
          directory="D:\inetpub\logs\FailedReqLogFiles" />  
    </siteDefaults>  
    <applicationDefaults
      applicationPool="DefaultAppPool"
      //The following line is inserted by the command.  
      enabledProtocols="http, net.tcp" />  
    <virtualDirectoryDefaults allowSubDirConfig="true" />  
</sites>  
```  
  
 Se você tentar ativar um serviço usando a ativação WAS para Não-HTTP e você não tiver instalado e configurado WAS, você poderá ver o seguinte erro:  
  
```output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 Se você ver este erro, certifique-se de que a ativação NÃO-HTTP será instalada e configurada corretamente. Para obter mais informações, [consulte Como instalar e configurar componentes de ativação do WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a>Construindo um serviço WCF que usa was para ativação não-HTTP  
 Uma vez que você execute as etapas para instalar e configurar WAS (veja [Como: Instalar e Configurar componentes de ativação wcf),](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)configurar um serviço para usar WAS para ativação é semelhante à configuração de um serviço hospedado no IIS.  
  
 Para obter instruções detalhadas sobre a construção de um serviço WCF ativado pelo WAS, consulte [Como: Hospedar um Serviço WCF no WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
## <a name="see-also"></a>Confira também

- [Hosting in Windows Process Activation Service](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md) (Hospedagem no Serviço de Ativação de Processos do Windows)
- [Recursos de hospedagem do Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))

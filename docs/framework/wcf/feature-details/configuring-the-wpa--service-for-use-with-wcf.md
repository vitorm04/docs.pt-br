---
title: Configurando o Serviço de ativação de processos do Windows (WAS) para utilizar com o Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
ms.openlocfilehash: a4c331465087c6910cb67a71d2153e08f82a6cd6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59147700"
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a>Configurando o Serviço de ativação de processos do Windows (WAS) para utilizar com o Windows Communication Foundation
Este tópico descreve as etapas necessárias para configurar o serviço de ativação de processos do Windows (também conhecido como WAS) no [!INCLUDE[wv](../../../../includes/wv-md.md)] para hospedar o Windows Communication Foundation (WCF) protocolos de rede de serviços que não se comunicam por HTTP. As seções a seguir descrevem as etapas para essa configuração:  
  
-   Instalar (ou confirmar a instalação do) os componentes de ativação do WCF necessários.  
  
-   Criar um site do WAS com as associações de protocolo de rede que você deseja usar, ou adicionar uma nova associação de protocolo para um site existente.  
  
-   Crie um aplicativo para hospedar seus serviços e permitir que o aplicativo use protocolos de rede necessários.  
  
-   Crie um serviço WCF que expõe um ponto de extremidade não-HTTP.  
  
## <a name="configuring-a-site-with-non-http-bindings"></a>Configurando um Site com associações não HTTP  
 Para usar uma associação não HTTP com WAS, a associação do site deve ser adicionada à configuração do WAS. O repositório de configuração para o WAS é o arquivo applicationHost. config, localizado no diretório %windir%\system32\inetsrv\config. Esse repositório de configuração é compartilhado pelo WAS e o IIS 7.0.  
  
 applicationHost. config é um arquivo de texto XML que pode ser aberto com qualquer editor de texto padrão (como o bloco de notas). No entanto, o [!INCLUDE[iisver](../../../../includes/iisver-md.md)] a ferramenta de configuração de linha de comando (appcmd.exe) é a maneira preferencial para adicionar associações de site não HTTP.  
  
 O comando a seguir adiciona uma associação de site do NET. TCP para o site padrão usando appcmd.exe (esse comando é inserido como uma única linha).  
  
```console  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 Este comando adiciona a nova associação de NET. TCP para o site padrão, adicionando a linha indicada a seguir ao arquivo applicationHost. config.  
  
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
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a>Permitindo que um aplicativo use protocolos não HTTP  
 Você pode habilitar ou desabilitar rede individuais protocolsat nível do aplicativo. O comando a seguir ilustra como habilitar protocolos HTTP e NET. TCP para um aplicativo que é executado no `Default Web Site`.  
  
```console  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 A lista de protocolos habilitados também pode ser definida \<applicationDefaults > elemento de configuração de XML do site armazenada no applicationHost. config.  
  
 O seguinte código XML do applicationHost. config ilustra um site ligado a HTTP e protocolos não HTTP. A configuração adicional necessária para dar suporte a protocolos não HTTP é chamada com comentários.  
  
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
  
 Se você tenta ativar um serviço usando o WAS para ativação não HTTP e você não tiver instalado e configurado o WAS, você poderá ver o seguinte erro:  
  
```output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 Se você vir esse erro garantir que o WAS para ativação não HTTP está instalada e configurada corretamente. Para obter mais informações, confira [Como: Instalar e configurar os componentes de ativação do WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a>Criando um WCF serviço que usa foi para a ativação não HTTP  
 Depois que você execute as etapas para instalar e configurar o WAS (consulte [como: Instalar e configurar componentes de ativação do WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), configurando um serviço para usar o WAS para ativação é semelhante à configuração de um serviço que é hospedado no IIS.  
  
 Para obter instruções detalhadas sobre a criação de um serviço WCF ativado pelo WAS, consulte [como: Hospedar um serviço WCF no WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
## <a name="see-also"></a>Consulte também

- [Hosting in Windows Process Activation Service](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md) (Hospedagem no Serviço de Ativação de Processos do Windows)
- [Recursos de hospedagem do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)

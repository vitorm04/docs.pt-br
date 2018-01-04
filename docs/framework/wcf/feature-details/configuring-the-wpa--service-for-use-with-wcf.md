---
title: "Configurando o Serviço de ativação de processos do Windows (WAS) para utilizar com o Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12df9e3760774b4dc8d4e8f73a09df5e79c2453e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a>Configurando o Serviço de ativação de processos do Windows (WAS) para utilizar com o Windows Communication Foundation
Este tópico descreve as etapas necessárias para configurar o serviço de ativação de processos do Windows (também conhecido como WAS) no [!INCLUDE[wv](../../../../includes/wv-md.md)] host [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] protocolos de rede de serviços que não se comunicam por HTTP. As seções a seguir descrevem as etapas para essa configuração:  
  
-   Instalar (ou confirmar a instalação de) o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] componentes de ativação necessários.  
  
-   Criar um site do WAS com as associações de protocolo de rede que deseja usar, ou adicionar uma nova associação de protocolo para um site existente.  
  
-   Crie um aplicativo para hospedar os serviços e permitir que o aplicativo usar protocolos de rede necessários.  
  
-   Criar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço que expõe um ponto de extremidade não HTTP.  
  
## <a name="configuring-a-site-with-non-http-bindings"></a>Configurando um Site com associações não HTTP  
 Para usar uma associação não HTTP com WAS, a associação do site deve ser adicionada à configuração de WAS. O repositório de configuração para o WAS é o arquivo applicationHost. config, localizado no diretório %windir%\system32\inetsrv\config. Esse repositório de configuração é compartilhado por WAS e o IIS 7.0.  
  
 applicationHost. config é um arquivo de texto XML que pode ser aberto com qualquer editor de texto padrão (como o bloco de notas). No entanto, o [!INCLUDE[iisver](../../../../includes/iisver-md.md)] ferramenta de configuração de linha de comando (appcmd.exe) é a melhor maneira de adicionar associações de site não HTTP.  
  
 O comando a seguir adiciona uma associação de site do NET. TCP para o site padrão usando appcmd.exe (este comando é inserido como uma única linha).  
  
```  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 Este comando adiciona a nova associação de NET. TCP para o site da Web padrão, adicionando a linha indicada abaixo no arquivo applicationHost. config.  
  
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
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a>Habilitar um aplicativo para usar protocolos não HTTP  
 Você pode habilitar ou desabilitar individuais da rede protocolsat nível do aplicativo. O comando a seguir ilustra como habilitar protocolos HTTP e NET. TCP para um aplicativo que é executado no `Default Web Site`.  
  
```  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 A lista de protocolos habilitados também pode ser definida no \<applicationDefaults > elemento da configuração do site XML armazenado em applicationHost. config.  
  
 O seguinte código XML de applicationHost. config ilustra um site associado ao HTTP e protocolos não HTTP. A configuração adicional necessária para oferecer suporte a protocolos não HTTP é chamada com comentários.  
  
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
  
 Se você tentar ativar um serviço usando o WAS para ativação não HTTP e você não tiver instalado e configurado o WAS você poderá ver o seguinte erro:  
  
```Output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 Se você vir esse erro garantir WAS para ativação não HTTP está instalada e configurada corretamente. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Como: instalar e configurar os componentes de ativação de WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a>Criando um WCF serviço que usa foi para ativação não HTTP  
 Depois de executar as etapas para instalar e configurar o WAS (consulte [como: instalar e configurar componentes de ativação do WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), como configurar um serviço para usar o WAS para ativação é semelhante à configuração de um serviço hospedado no IIS.  
  
 Para obter instruções detalhadas sobre como criar um ativado WAS [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de serviço, consulte [como: hospedar um serviço WCF em WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
## <a name="see-also"></a>Consulte também  
 [Hosting in Windows Process Activation Service](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md) (Hospedagem no Serviço de Ativação de Processos do Windows)  
 [Recursos de hospedagem do Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)

---
title: Configurando o Serviço de ativação de processos do Windows (WAS) para utilizar com o Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
ms.openlocfilehash: 6e74c81aa26ba7f8d093b8b3ec52f19eb3519905
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43489780"
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a><span data-ttu-id="7ddd2-102">Configurando o Serviço de ativação de processos do Windows (WAS) para utilizar com o Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="7ddd2-102">Configuring the Windows Process Activation Service for Use with Windows Communication Foundation</span></span>
<span data-ttu-id="7ddd2-103">Este tópico descreve as etapas necessárias para configurar o serviço de ativação de processos do Windows (também conhecido como WAS) no [!INCLUDE[wv](../../../../includes/wv-md.md)] para hospedar o Windows Communication Foundation (WCF) protocolos de rede de serviços que não se comunicam por HTTP.</span><span class="sxs-lookup"><span data-stu-id="7ddd2-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) in [!INCLUDE[wv](../../../../includes/wv-md.md)] to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="7ddd2-104">As seções a seguir descrevem as etapas para essa configuração:</span><span class="sxs-lookup"><span data-stu-id="7ddd2-104">The following sections outline the steps for this configuration:</span></span>  
  
-   <span data-ttu-id="7ddd2-105">Instalar (ou confirmar a instalação do) os componentes de ativação do WCF necessários.</span><span class="sxs-lookup"><span data-stu-id="7ddd2-105">Install (or confirm the installation of) the WCF activation components required.</span></span>  
  
-   <span data-ttu-id="7ddd2-106">Criar um site do WAS com as associações de protocolo de rede que você deseja usar, ou adicionar uma nova associação de protocolo para um site existente.</span><span class="sxs-lookup"><span data-stu-id="7ddd2-106">Create a WAS site with the network protocol bindings you wish to use, or add a new protocol binding to an existing site.</span></span>  
  
-   <span data-ttu-id="7ddd2-107">Crie um aplicativo para hospedar seus serviços e permitir que o aplicativo use protocolos de rede necessários.</span><span class="sxs-lookup"><span data-stu-id="7ddd2-107">Create an application to host your services and enable that application to use the required network protocols.</span></span>  
  
-   <span data-ttu-id="7ddd2-108">Crie um serviço WCF que expõe um ponto de extremidade não-HTTP.</span><span class="sxs-lookup"><span data-stu-id="7ddd2-108">Build a WCF service that exposes a non-HTTP endpoint.</span></span>  
  
## <a name="configuring-a-site-with-non-http-bindings"></a><span data-ttu-id="7ddd2-109">Configurando um Site com associações não HTTP</span><span class="sxs-lookup"><span data-stu-id="7ddd2-109">Configuring a Site with Non-HTTP bindings</span></span>  
 <span data-ttu-id="7ddd2-110">Para usar uma associação não HTTP com WAS, a associação do site deve ser adicionada à configuração do WAS.</span><span class="sxs-lookup"><span data-stu-id="7ddd2-110">To use a non-HTTP binding with WAS, the site binding must be added to the WAS configuration.</span></span> <span data-ttu-id="7ddd2-111">O repositório de configuração para o WAS é o arquivo applicationHost. config, localizado no diretório %windir%\system32\inetsrv\config.</span><span class="sxs-lookup"><span data-stu-id="7ddd2-111">The configuration store for WAS is the applicationHost.config file, located in the %windir%\system32\inetsrv\config directory.</span></span> <span data-ttu-id="7ddd2-112">Esse repositório de configuração é compartilhado pelo WAS e o IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="7ddd2-112">This configuration store is shared by both WAS and IIS 7.0.</span></span>  
  
 <span data-ttu-id="7ddd2-113">applicationHost. config é um arquivo de texto XML que pode ser aberto com qualquer editor de texto padrão (como o bloco de notas).</span><span class="sxs-lookup"><span data-stu-id="7ddd2-113">applicationHost.config is an XML text file that can be opened with any standard text editor (such as Notepad).</span></span> <span data-ttu-id="7ddd2-114">No entanto, o [!INCLUDE[iisver](../../../../includes/iisver-md.md)] a ferramenta de configuração de linha de comando (appcmd.exe) é a maneira preferencial para adicionar associações de site não HTTP.</span><span class="sxs-lookup"><span data-stu-id="7ddd2-114">However, the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] command-line configuration tool (appcmd.exe) is the preferred way to add non-HTTP site bindings.</span></span>  
  
 <span data-ttu-id="7ddd2-115">O comando a seguir adiciona uma associação de site do NET. TCP para o site padrão usando appcmd.exe (esse comando é inserido como uma única linha).</span><span class="sxs-lookup"><span data-stu-id="7ddd2-115">The following command adds a net.tcp site binding to the default Web site using appcmd.exe (this command is entered as a single line).</span></span>  
  
```  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 <span data-ttu-id="7ddd2-116">Este comando adiciona a nova associação de NET. TCP para o site padrão, adicionando a linha indicada a seguir ao arquivo applicationHost. config.</span><span class="sxs-lookup"><span data-stu-id="7ddd2-116">This command adds the new net.tcp binding to the default Web site by adding the line indicated below to the applicationHost.config file.</span></span>  
  
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
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a><span data-ttu-id="7ddd2-117">Permitindo que um aplicativo use protocolos não HTTP</span><span class="sxs-lookup"><span data-stu-id="7ddd2-117">Enabling an Application to Use Non-HTTP Protocols</span></span>  
 <span data-ttu-id="7ddd2-118">Você pode habilitar ou desabilitar rede individuais protocolsat nível do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7ddd2-118">You can enable or disable individual network protocolsat the application level.</span></span> <span data-ttu-id="7ddd2-119">O comando a seguir ilustra como habilitar protocolos HTTP e NET. TCP para um aplicativo que é executado no `Default Web Site`.</span><span class="sxs-lookup"><span data-stu-id="7ddd2-119">The following command illustrates how to enable both the HTTP and net.tcp protocols for an application that runs in the `Default Web Site`.</span></span>  
  
```  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 <span data-ttu-id="7ddd2-120">A lista de protocolos habilitados também pode ser definida \<applicationDefaults > elemento de configuração de XML do site armazenada no applicationHost. config.</span><span class="sxs-lookup"><span data-stu-id="7ddd2-120">The list of enabled protocols can also be set in the \<applicationDefaults> element of the site’s XML configuration stored in ApplicationHost.config.</span></span>  
  
 <span data-ttu-id="7ddd2-121">O seguinte código XML do applicationHost. config ilustra um site ligado a HTTP e protocolos não HTTP.</span><span class="sxs-lookup"><span data-stu-id="7ddd2-121">The following XML code from applicationHost.config illustrates a site bound to both HTTP and non-HTTP protocols.</span></span> <span data-ttu-id="7ddd2-122">A configuração adicional necessária para dar suporte a protocolos não HTTP é chamada com comentários.</span><span class="sxs-lookup"><span data-stu-id="7ddd2-122">The additional configuration required to support non-HTTP protocols is called out with comments.</span></span>  
  
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
  
 <span data-ttu-id="7ddd2-123">Se você tenta ativar um serviço usando o WAS para ativação não HTTP e você não tiver instalado e configurado o WAS, você poderá ver o seguinte erro:</span><span class="sxs-lookup"><span data-stu-id="7ddd2-123">If you attempt to activate a service using WAS for Non-HTTP activation and you have not installed and configured WAS you may see the following error:</span></span>  
  
```Output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 <span data-ttu-id="7ddd2-124">Se você vir esse erro garantir que o WAS para ativação não HTTP está instalada e configurada corretamente.</span><span class="sxs-lookup"><span data-stu-id="7ddd2-124">If you see this error ensure WAS for Non-HTTP Activation is installed and configured properly.</span></span> <span data-ttu-id="7ddd2-125">Para obter mais informações, consulte [como: instalar e configurar componentes de ativação do WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span><span class="sxs-lookup"><span data-stu-id="7ddd2-125">For more information, see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a><span data-ttu-id="7ddd2-126">Criando um WCF serviço que usa foi para a ativação não HTTP</span><span class="sxs-lookup"><span data-stu-id="7ddd2-126">Building a WCF Service That Uses WAS for Non-HTTP activation</span></span>  
 <span data-ttu-id="7ddd2-127">Depois que você execute as etapas para instalar e configurar o WAS (consulte [como: instalar e configurar componentes de ativação do WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), configurando um serviço para usar o WAS para ativação é semelhante à configuração de um serviço que é hospedado no IIS.</span><span class="sxs-lookup"><span data-stu-id="7ddd2-127">Once you perform the steps to install and configure WAS (see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), configuring a service to use WAS for activation is similar to configuring a service that is hosted in IIS.</span></span>  
  
 <span data-ttu-id="7ddd2-128">Para obter instruções detalhadas sobre a criação de um serviço WCF ativado pelo WAS, consulte [como: hospedar um serviço WCF no WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).</span><span class="sxs-lookup"><span data-stu-id="7ddd2-128">For detailed instructions about building a WAS-activated WCF service, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ddd2-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ddd2-129">See Also</span></span>  
 <span data-ttu-id="7ddd2-130">[Hosting in Windows Process Activation Service](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md) (Hospedagem no Serviço de Ativação de Processos do Windows)</span><span class="sxs-lookup"><span data-stu-id="7ddd2-130">[Hosting in Windows Process Activation Service](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)</span></span>  
 [<span data-ttu-id="7ddd2-131">Recursos de hospedagem do Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="7ddd2-131">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)

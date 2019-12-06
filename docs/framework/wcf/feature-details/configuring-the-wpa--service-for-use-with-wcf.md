---
title: Configurando o Serviço de ativação de processos do Windows (WAS) para utilizar com o Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
ms.openlocfilehash: 768674a5cc4b0710e03de8ef1c9fdb2c40a8f314
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74838033"
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a><span data-ttu-id="f7972-102">Configurando o Serviço de ativação de processos do Windows (WAS) para utilizar com o Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f7972-102">Configuring the Windows Process Activation Service for Use with Windows Communication Foundation</span></span>
<span data-ttu-id="f7972-103">Este tópico descreve as etapas necessárias para configurar o serviço de ativação de processos do Windows (também conhecido como WAS) no Windows Vista para hospedar serviços de Windows Communication Foundation (WCF) que não se comunicam por protocolos de rede HTTP.</span><span class="sxs-lookup"><span data-stu-id="f7972-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) in Windows Vista to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="f7972-104">As seções a seguir descrevem as etapas para essa configuração:</span><span class="sxs-lookup"><span data-stu-id="f7972-104">The following sections outline the steps for this configuration:</span></span>  
  
- <span data-ttu-id="f7972-105">Instale (ou confirme a instalação do) os componentes de ativação do WCF necessários.</span><span class="sxs-lookup"><span data-stu-id="f7972-105">Install (or confirm the installation of) the WCF activation components required.</span></span>  
  
- <span data-ttu-id="f7972-106">Crie um site do WAS com as associações de protocolo de rede que você deseja usar ou adicione uma nova associação de protocolo a um site existente.</span><span class="sxs-lookup"><span data-stu-id="f7972-106">Create a WAS site with the network protocol bindings you wish to use, or add a new protocol binding to an existing site.</span></span>  
  
- <span data-ttu-id="f7972-107">Crie um aplicativo para hospedar seus serviços e habilite esse aplicativo para usar os protocolos de rede necessários.</span><span class="sxs-lookup"><span data-stu-id="f7972-107">Create an application to host your services and enable that application to use the required network protocols.</span></span>  
  
- <span data-ttu-id="f7972-108">Crie um serviço WCF que expõe um ponto de extremidade não HTTP.</span><span class="sxs-lookup"><span data-stu-id="f7972-108">Build a WCF service that exposes a non-HTTP endpoint.</span></span>  
  
## <a name="configuring-a-site-with-non-http-bindings"></a><span data-ttu-id="f7972-109">Configurando um site com associações não HTTP</span><span class="sxs-lookup"><span data-stu-id="f7972-109">Configuring a Site with Non-HTTP bindings</span></span>  
 <span data-ttu-id="f7972-110">Para usar uma associação não HTTP com o WAS, a associação do site deve ser adicionada à configuração do WAS.</span><span class="sxs-lookup"><span data-stu-id="f7972-110">To use a non-HTTP binding with WAS, the site binding must be added to the WAS configuration.</span></span> <span data-ttu-id="f7972-111">O repositório de configuração para WAS é o arquivo applicationHost. config, localizado no diretório%windir%\system32\inetsrv\config</span><span class="sxs-lookup"><span data-stu-id="f7972-111">The configuration store for WAS is the applicationHost.config file, located in the %windir%\system32\inetsrv\config directory.</span></span> <span data-ttu-id="f7972-112">Esse repositório de configuração é compartilhado pelo WAS e pelo IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="f7972-112">This configuration store is shared by both WAS and IIS 7.0.</span></span>  
  
 <span data-ttu-id="f7972-113">applicationHost. config é um arquivo de texto XML que pode ser aberto com qualquer editor de texto padrão (como o bloco de notas).</span><span class="sxs-lookup"><span data-stu-id="f7972-113">applicationHost.config is an XML text file that can be opened with any standard text editor (such as Notepad).</span></span> <span data-ttu-id="f7972-114">No entanto, a ferramenta de configuração de linha de comando do IIS 7,0 (appcmd. exe) é a maneira preferida de adicionar associações de site não HTTP.</span><span class="sxs-lookup"><span data-stu-id="f7972-114">However, the IIS 7.0 command-line configuration tool (appcmd.exe) is the preferred way to add non-HTTP site bindings.</span></span>  
  
 <span data-ttu-id="f7972-115">O comando a seguir adiciona uma associação de site net. TCP ao site padrão usando AppCmd. exe (esse comando é inserido como uma única linha).</span><span class="sxs-lookup"><span data-stu-id="f7972-115">The following command adds a net.tcp site binding to the default Web site using appcmd.exe (this command is entered as a single line).</span></span>  
  
```console  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 <span data-ttu-id="f7972-116">Esse comando adiciona a nova associação net. TCP ao site padrão adicionando a linha indicada abaixo ao arquivo applicationHost. config.</span><span class="sxs-lookup"><span data-stu-id="f7972-116">This command adds the new net.tcp binding to the default Web site by adding the line indicated below to the applicationHost.config file.</span></span>  
  
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
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a><span data-ttu-id="f7972-117">Habilitando um aplicativo para usar protocolos não HTTP</span><span class="sxs-lookup"><span data-stu-id="f7972-117">Enabling an Application to Use Non-HTTP Protocols</span></span>  
 <span data-ttu-id="f7972-118">Você pode habilitar ou desabilitar a rede individual protocolsat o nível do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f7972-118">You can enable or disable individual network protocolsat the application level.</span></span> <span data-ttu-id="f7972-119">O comando a seguir ilustra como habilitar os protocolos HTTP e net. TCP para um aplicativo que é executado no `Default Web Site`.</span><span class="sxs-lookup"><span data-stu-id="f7972-119">The following command illustrates how to enable both the HTTP and net.tcp protocols for an application that runs in the `Default Web Site`.</span></span>  
  
```console  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 <span data-ttu-id="f7972-120">A lista de protocolos habilitados também pode ser definida no elemento \<applicationDefaults > da configuração XML do site armazenada em ApplicationHost. config.</span><span class="sxs-lookup"><span data-stu-id="f7972-120">The list of enabled protocols can also be set in the \<applicationDefaults> element of the site’s XML configuration stored in ApplicationHost.config.</span></span>  
  
 <span data-ttu-id="f7972-121">O código XML a seguir de applicationHost. config ilustra um site associado a protocolos HTTP e não HTTP.</span><span class="sxs-lookup"><span data-stu-id="f7972-121">The following XML code from applicationHost.config illustrates a site bound to both HTTP and non-HTTP protocols.</span></span> <span data-ttu-id="f7972-122">A configuração adicional necessária para dar suporte a protocolos não HTTP é chamada com comentários.</span><span class="sxs-lookup"><span data-stu-id="f7972-122">The additional configuration required to support non-HTTP protocols is called out with comments.</span></span>  
  
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
  
 <span data-ttu-id="f7972-123">Se você tentar ativar um serviço usando o WAS para ativação não HTTP e não tiver instalado e configurado, você poderá ver o seguinte erro:</span><span class="sxs-lookup"><span data-stu-id="f7972-123">If you attempt to activate a service using WAS for Non-HTTP activation and you have not installed and configured WAS you may see the following error:</span></span>  
  
```output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 <span data-ttu-id="f7972-124">Se você vir esse erro, verifique se a ativação não HTTP está instalada e configurada corretamente.</span><span class="sxs-lookup"><span data-stu-id="f7972-124">If you see this error ensure WAS for Non-HTTP Activation is installed and configured properly.</span></span> <span data-ttu-id="f7972-125">Para obter mais informações, consulte [como: instalar e configurar componentes de ativação do WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span><span class="sxs-lookup"><span data-stu-id="f7972-125">For more information, see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a><span data-ttu-id="f7972-126">Criar um serviço WCF que usa o WAS para ativação não HTTP</span><span class="sxs-lookup"><span data-stu-id="f7972-126">Building a WCF Service That Uses WAS for Non-HTTP activation</span></span>  
 <span data-ttu-id="f7972-127">Depois de executar as etapas para instalar e configurar o WAS (consulte [como instalar e configurar os componentes de ativação do WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), a configuração de um serviço para usar o was para a ativação é semelhante à configuração de um serviço hospedado no IIS.</span><span class="sxs-lookup"><span data-stu-id="f7972-127">Once you perform the steps to install and configure WAS (see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), configuring a service to use WAS for activation is similar to configuring a service that is hosted in IIS.</span></span>  
  
 <span data-ttu-id="f7972-128">Para obter instruções detalhadas sobre como criar um serviço WCF ativado, consulte [como hospedar um serviço WCF no was](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).</span><span class="sxs-lookup"><span data-stu-id="f7972-128">For detailed instructions about building a WAS-activated WCF service, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7972-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7972-129">See also</span></span>

- <span data-ttu-id="f7972-130">[Hosting in Windows Process Activation Service](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md) (Hospedagem no Serviço de Ativação de Processos do Windows)</span><span class="sxs-lookup"><span data-stu-id="f7972-130">[Hosting in Windows Process Activation Service](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)</span></span>
- [<span data-ttu-id="f7972-131">Recursos de hospedagem do Windows Server app Fabric</span><span class="sxs-lookup"><span data-stu-id="f7972-131">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)

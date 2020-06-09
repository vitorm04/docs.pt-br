---
title: Como configurar um serviço do WCF hospedado no IIS com SSL
ms.date: 03/30/2017
ms.assetid: df2fe31f-a4bb-4024-92ca-b74ba055e038
ms.openlocfilehash: fb3e87021c3dce1172250f33fd302916920af74d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597222"
---
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a><span data-ttu-id="4a2a4-102">Como configurar um serviço do WCF hospedado no IIS com SSL</span><span class="sxs-lookup"><span data-stu-id="4a2a4-102">How to: Configure an IIS-hosted WCF service with SSL</span></span>
<span data-ttu-id="4a2a4-103">Este tópico descreve como configurar um serviço WCF hospedado pelo IIS para usar a segurança de transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="4a2a4-103">This topic describes how to set up an IIS-hosted WCF service to use HTTP transport security.</span></span> <span data-ttu-id="4a2a4-104">A segurança de transporte HTTP requer que um certificado SSL seja registrado no IIS.</span><span class="sxs-lookup"><span data-stu-id="4a2a4-104">HTTP transport security requires an SSL certificate to be registered with IIS.</span></span> <span data-ttu-id="4a2a4-105">Se você não tiver um certificado SSL, poderá usar o IIS para gerar um certificado de teste.</span><span class="sxs-lookup"><span data-stu-id="4a2a4-105">If you do not have an SSL certificate you can use IIS to generate a test certificate.</span></span> <span data-ttu-id="4a2a4-106">Em seguida, você deve adicionar uma associação SSL ao site da Web e configurar as propriedades de autenticação do site.</span><span class="sxs-lookup"><span data-stu-id="4a2a4-106">Next you must add an SSL binding to the web site and configure the web site’s authentication properties.</span></span> <span data-ttu-id="4a2a4-107">Por fim, você precisa configurar o serviço WCF para usar HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4a2a4-107">Finally you need to configure the WCF service to use HTTPS.</span></span>  
  
### <a name="creating-a-self-signed-certificate"></a><span data-ttu-id="4a2a4-108">Criando um certificado autoassinado</span><span class="sxs-lookup"><span data-stu-id="4a2a4-108">Creating a Self-Signed Certificate</span></span>  
  
1. <span data-ttu-id="4a2a4-109">Abra o Gerenciador de Serviços de Informações da Internet (inetmgr. exe) e selecione o nome do computador no modo de exibição de árvore à esquerda.</span><span class="sxs-lookup"><span data-stu-id="4a2a4-109">Open Internet Information Services Manager (inetmgr.exe), and select your computer name in the left-hand tree view.</span></span> <span data-ttu-id="4a2a4-110">No lado direito da tela, selecione certificados de servidor</span><span class="sxs-lookup"><span data-stu-id="4a2a4-110">On the right-hand side of the screen select Server Certificates</span></span>  
  
     <span data-ttu-id="4a2a4-111">![Tela inicial do gerenciador do IIS](media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span><span class="sxs-lookup"><span data-stu-id="4a2a4-111">![IIS Manager Home Screen](media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span></span>  
  
2. <span data-ttu-id="4a2a4-112">Na janela certificados do servidor, clique no **criar certificado autoassinado....**</span><span class="sxs-lookup"><span data-stu-id="4a2a4-112">In the Server Certificates window click the **Create Self-Signed Certificate….**</span></span> <span data-ttu-id="4a2a4-113">Criar.</span><span class="sxs-lookup"><span data-stu-id="4a2a4-113">Link.</span></span>  
  
     <span data-ttu-id="4a2a4-114">![Criando um certificado auto&#45;assinado com o IIS](media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span><span class="sxs-lookup"><span data-stu-id="4a2a4-114">![Creating a self&#45;signed certificate with IIS](media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span></span>  
  
3. <span data-ttu-id="4a2a4-115">Insira um nome amigável para o certificado autoassinado e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="4a2a4-115">Enter a friendly name for the self-signed certificate and click **OK**.</span></span>  
  
     <span data-ttu-id="4a2a4-116">![Caixa de diálogo Criar certificado auto&#45;assinado](media/mg-mycert.jpg "mg_MyCert")</span><span class="sxs-lookup"><span data-stu-id="4a2a4-116">![Create Self&#45;Signed Certificate Dialog](media/mg-mycert.jpg "mg_MyCert")</span></span>  
  
     <span data-ttu-id="4a2a4-117">Os detalhes do certificado autoassinado recém-criado agora são mostrados na janela **certificados do servidor** .</span><span class="sxs-lookup"><span data-stu-id="4a2a4-117">The newly created self-signed certificate details are now shown in the **Server Certificates** window.</span></span>  
  
     <span data-ttu-id="4a2a4-118">![Janela do certificado de servidor](media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span><span class="sxs-lookup"><span data-stu-id="4a2a4-118">![Server Certificate Window](media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span></span>  
  
     <span data-ttu-id="4a2a4-119">O certificado gerado é instalado no repositório de autoridades de certificação raiz confiáveis.</span><span class="sxs-lookup"><span data-stu-id="4a2a4-119">The generated certificate is installed in the Trusted Root Certification Authorities store.</span></span>  
  
### <a name="add-ssl-binding"></a><span data-ttu-id="4a2a4-120">Adicionar Associação SSL</span><span class="sxs-lookup"><span data-stu-id="4a2a4-120">Add SSL Binding</span></span>  
  
1. <span data-ttu-id="4a2a4-121">Ainda no Serviços de Informações da Internet Manager, expanda a pasta **sites** e, em seguida, a pasta **site padrão** no modo de exibição de árvore no lado esquerdo da tela.</span><span class="sxs-lookup"><span data-stu-id="4a2a4-121">Still in Internet Information Services Manager, expand the **Sites** folder and then the **Default Web Site** folder in the tree view on the left-hand side of the screen.</span></span>  
  
2. <span data-ttu-id="4a2a4-122">Clique nas **associações....**</span><span class="sxs-lookup"><span data-stu-id="4a2a4-122">Click the **Bindings….**</span></span> <span data-ttu-id="4a2a4-123">No link na seção **ações** na parte superior direita da janela.</span><span class="sxs-lookup"><span data-stu-id="4a2a4-123">Link in the **Actions** section in the upper right hand portion of the window.</span></span>  
  
     <span data-ttu-id="4a2a4-124">![Adicionando a associação SSL](media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span><span class="sxs-lookup"><span data-stu-id="4a2a4-124">![Adding an SSL binding](media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span></span>  
  
3. <span data-ttu-id="4a2a4-125">Na janela ligações do site, clique no botão **Adicionar** .</span><span class="sxs-lookup"><span data-stu-id="4a2a4-125">In the Site Bindings window click the **Add** button.</span></span>  
  
     <span data-ttu-id="4a2a4-126">![Caixa de diálogo Associações do site](media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span><span class="sxs-lookup"><span data-stu-id="4a2a4-126">![Site Bindings Dialog](media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span></span>  
  
4. <span data-ttu-id="4a2a4-127">Na caixa de diálogo **Adicionar associação do site** , selecione https para o tipo e o nome amigável do certificado autoassinado que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="4a2a4-127">In the **Add Site Binding** dialog, select https for the type and the friendly name of the self-signed certificate you just created.</span></span>  
  
     <span data-ttu-id="4a2a4-128">![Exemplo de associação de site](media/mg-mycertbinding.jpg "mg_MyCertBinding")</span><span class="sxs-lookup"><span data-stu-id="4a2a4-128">![Site binding example](media/mg-mycertbinding.jpg "mg_MyCertBinding")</span></span>  
  
### <a name="configure-virtual-directory-for-ssl"></a><span data-ttu-id="4a2a4-129">Configurar o diretório virtual para SSL</span><span class="sxs-lookup"><span data-stu-id="4a2a4-129">Configure Virtual Directory for SSL</span></span>  
  
1. <span data-ttu-id="4a2a4-130">Ainda no Gerenciador de Serviços de Informações da Internet, selecione o diretório virtual que contém seu serviço WCF Secure.</span><span class="sxs-lookup"><span data-stu-id="4a2a4-130">Still in Internet Information Services Manager, select the virtual directory that contains your WCF secure service.</span></span>  
  
2. <span data-ttu-id="4a2a4-131">No painel central da janela, selecione configurações de **SSL** na seção IIS.</span><span class="sxs-lookup"><span data-stu-id="4a2a4-131">In the center pane of the window, select **SSL Settings** in the IIS section.</span></span>  
  
     <span data-ttu-id="4a2a4-132">![Configurações de SSL para o diretório virtual](media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span><span class="sxs-lookup"><span data-stu-id="4a2a4-132">![SSL Settings for virtual directory](media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span></span>  
  
3. <span data-ttu-id="4a2a4-133">No painel configurações de SSL, marque a caixa de seleção **exigir SSL** e clique no link **aplicar** na seção **ações** no lado direito da tela.</span><span class="sxs-lookup"><span data-stu-id="4a2a4-133">In the SSL Settings pane, select the **Require SSL** checkbox and click the **Apply** link in the **Actions** section on the right hand side of the screen.</span></span>  
  
     <span data-ttu-id="4a2a4-134">![Configurações de SSL do diretório virtual](media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span><span class="sxs-lookup"><span data-stu-id="4a2a4-134">![Virtual directory SSL settings](media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span></span>  
  
### <a name="configure-wcf-service-for-http-transport-security"></a><span data-ttu-id="4a2a4-135">Configurar o serviço WCF para segurança de transporte HTTP</span><span class="sxs-lookup"><span data-stu-id="4a2a4-135">Configure WCF Service for HTTP Transport Security</span></span>  
  
1. <span data-ttu-id="4a2a4-136">No Web. config do serviço WCF, configure a associação HTTP para usar a segurança de transporte, conforme mostrado no XML a seguir.</span><span class="sxs-lookup"><span data-stu-id="4a2a4-136">In the WCF service’s web.config configure the HTTP binding to use transport security as shown in the following XML.</span></span>  
  
    ```xml  
    <bindings>  
          <basicHttpBinding>  
            <binding name="secureHttpBinding">  
              <security mode="Transport">  
                <transport clientCredentialType="None"/>  
              </security>  
            </binding>  
          </basicHttpBinding>  
    </bindings>  
    ```  
  
2. <span data-ttu-id="4a2a4-137">Especifique o serviço e o ponto de extremidade de serviço, conforme mostrado no XML a seguir.</span><span class="sxs-lookup"><span data-stu-id="4a2a4-137">Specify your service and service endpoint as shown in the following XML.</span></span>  
  
    ```xml  
    <services>  
          <service name="MySecureWCFService.Service1">  
            <endpoint address=""  
                      binding="basicHttpBinding"  
                      bindingConfiguration="secureHttpBinding"  
                      contract="MySecureWCFService.IService1"/>  
  
            <endpoint address="mex"  
                      binding="mexHttpsBinding"  
                      contract="IMetadataExchange" />  
          </service>  
    </services>  
    ```  
  
## <a name="example"></a><span data-ttu-id="4a2a4-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4a2a4-138">Example</span></span>  
 <span data-ttu-id="4a2a4-139">Veja a seguir um exemplo completo de um arquivo Web. config para um serviço WCF usando a segurança de transporte HTTP</span><span class="sxs-lookup"><span data-stu-id="4a2a4-139">The following is a complete example of a web.config file for a WCF service using HTTP transport security</span></span>  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <services>  
      <service name="MySecureWCFService.Service1">  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  bindingConfiguration="secureHttpBinding"  
                  contract="MySecureWCFService.IService1"/>  
  
        <endpoint address="mex"  
                  binding="mexHttpsBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="secureHttpBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="None"/>  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <!-- To avoid disclosing metadata information, set the value below to false and remove the metadata endpoint above before deployment -->  
          <serviceMetadata httpsGetEnabled="true"/>  
          <!-- To receive exception details in faults for debugging purposes, set the value below to true.  Set to false before deployment to avoid disclosing exception information -->  
          <serviceDebug includeExceptionDetailInFaults="false"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
  </system.serviceModel>  
  <system.webServer>  
    <modules runAllManagedModulesForAllRequests="true"/>  
  </system.webServer>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4a2a4-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a2a4-140">See also</span></span>

- [<span data-ttu-id="4a2a4-141">Hospedagem no Internet Information Services</span><span class="sxs-lookup"><span data-stu-id="4a2a4-141">Hosting in Internet Information Services</span></span>](hosting-in-internet-information-services.md)
- [<span data-ttu-id="4a2a4-142">Instruções de hospedagem de serviço de informação de internet</span><span class="sxs-lookup"><span data-stu-id="4a2a4-142">Internet Information Service Hosting Instructions</span></span>](../samples/internet-information-service-hosting-instructions.md)
- [<span data-ttu-id="4a2a4-143">Práticas recomendadas de hospedagem de Serviços de Informações da Internet</span><span class="sxs-lookup"><span data-stu-id="4a2a4-143">Internet Information Services Hosting Best Practices</span></span>](internet-information-services-hosting-best-practices.md)
- [<span data-ttu-id="4a2a4-144">Hospedagem do IIS utilizando código embutido</span><span class="sxs-lookup"><span data-stu-id="4a2a4-144">IIS Hosting Using Inline Code</span></span>](../samples/iis-hosting-using-inline-code.md)

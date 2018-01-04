---
title: "Como configurar um serviço do WCF hospedado no IIS com SSL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df2fe31f-a4bb-4024-92ca-b74ba055e038
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b16ca5b4cfe615eedd9e532b12f61394806829bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a><span data-ttu-id="82206-102">Como configurar um serviço do WCF hospedado no IIS com SSL</span><span class="sxs-lookup"><span data-stu-id="82206-102">How to: Configure an IIS-hosted WCF service with SSL</span></span>
<span data-ttu-id="82206-103">Este tópico descreve como configurar um serviço WCF hospedado pelo IIS para usar a segurança de transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="82206-103">This topic describes how to set up an IIS-hosted WCF service to use HTTP transport security.</span></span> <span data-ttu-id="82206-104">Segurança de transporte HTTP requer um certificado SSL a ser registrado com o IIS.</span><span class="sxs-lookup"><span data-stu-id="82206-104">HTTP transport security requires an SSL certificate to be registered with IIS.</span></span> <span data-ttu-id="82206-105">Se você não tiver um certificado SSL que você pode usar o IIS para gerar um certificado de teste.</span><span class="sxs-lookup"><span data-stu-id="82206-105">If you do not have an SSL certificate you can use IIS to generate a test certificate.</span></span> <span data-ttu-id="82206-106">Em seguida, você deve adicionar uma associação SSL para o site da web e configurar as propriedades de autenticação do site da web.</span><span class="sxs-lookup"><span data-stu-id="82206-106">Next you must add an SSL binding to the web site and configure the web site’s authentication properties.</span></span> <span data-ttu-id="82206-107">Finalmente, você precisa configurar o serviço do WCF para usar HTTPS.</span><span class="sxs-lookup"><span data-stu-id="82206-107">Finally you need to configure the WCF service to use HTTPS.</span></span>  
  
### <a name="creating-a-self-signed-certificate"></a><span data-ttu-id="82206-108">Criando um certificado autoassinado</span><span class="sxs-lookup"><span data-stu-id="82206-108">Creating a Self-Signed Certificate</span></span>  
  
1.  <span data-ttu-id="82206-109">Abra o Gerenciador de serviços de informações da Internet (inetmgr.exe) e selecione o nome do computador no modo de exibição de árvore à esquerda.</span><span class="sxs-lookup"><span data-stu-id="82206-109">Open Internet Information Services Manager (inetmgr.exe), and select your computer name in the left-hand tree view.</span></span> <span data-ttu-id="82206-110">No lado direito da tela, selecione certificados de servidor</span><span class="sxs-lookup"><span data-stu-id="82206-110">On the right-hand side of the screen select Server Certificates</span></span>  
  
     <span data-ttu-id="82206-111">![Tela de inicial do Gerenciador do IIS](../../../../docs/framework/wcf/feature-details/media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span><span class="sxs-lookup"><span data-stu-id="82206-111">![IIS Manager Home Screen](../../../../docs/framework/wcf/feature-details/media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span></span>  
  
2.  <span data-ttu-id="82206-112">Na janela de certificados do servidor, clique no **criar um certificado autoassinado...**</span><span class="sxs-lookup"><span data-stu-id="82206-112">In the Server Certificates window click the **Create Self-Signed Certificate….**</span></span> <span data-ttu-id="82206-113">link.</span><span class="sxs-lookup"><span data-stu-id="82206-113">Link.</span></span>  
  
     <span data-ttu-id="82206-114">![Criando um self &#45; assinou o certificado com o IIS](../../../../docs/framework/wcf/feature-details/media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span><span class="sxs-lookup"><span data-stu-id="82206-114">![Creating a self&#45;signed certificate with IIS](../../../../docs/framework/wcf/feature-details/media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span></span>  
  
3.  <span data-ttu-id="82206-115">Insira um nome amigável para o certificado autoassinado e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="82206-115">Enter a friendly name for the self-signed certificate and click **OK**.</span></span>  
  
     <span data-ttu-id="82206-116">![Criar auto &#45; Caixa de diálogo do certificado de assinatura](../../../../docs/framework/wcf/feature-details/media/mg-mycert.jpg "mg_MyCert")</span><span class="sxs-lookup"><span data-stu-id="82206-116">![Create Self&#45;Signed Certificate Dialog](../../../../docs/framework/wcf/feature-details/media/mg-mycert.jpg "mg_MyCert")</span></span>  
  
     <span data-ttu-id="82206-117">Agora, os detalhes do certificado autoassinado criado recentemente são mostrados no **certificados de servidor** janela.</span><span class="sxs-lookup"><span data-stu-id="82206-117">The newly created self-signed certificate details are now shown in the **Server Certificates** window.</span></span>  
  
     <span data-ttu-id="82206-118">![Janela de certificado de servidor](../../../../docs/framework/wcf/feature-details/media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span><span class="sxs-lookup"><span data-stu-id="82206-118">![Server Certificate Window](../../../../docs/framework/wcf/feature-details/media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span></span>  
  
     <span data-ttu-id="82206-119">O certificado gerado é instalado em autoridades de certificação raiz confiáveis armazenar.</span><span class="sxs-lookup"><span data-stu-id="82206-119">The generated certificate is installed in the Trusted Root Certification Authorities store.</span></span>  
  
### <a name="add-ssl-binding"></a><span data-ttu-id="82206-120">Adicionar associação de SSL</span><span class="sxs-lookup"><span data-stu-id="82206-120">Add SSL Binding</span></span>  
  
1.  <span data-ttu-id="82206-121">Ainda no Gerenciador de serviços de informações da Internet, expanda o **Sites** pasta e, em seguida, o **Default Web Site** pasta na exibição de árvore no lado esquerdo da tela.</span><span class="sxs-lookup"><span data-stu-id="82206-121">Still in Internet Information Services Manager, expand the **Sites** folder and then the **Default Web Site** folder in the tree view on the left-hand side of the screen.</span></span>  
  
2.  <span data-ttu-id="82206-122">Clique o **associações...**</span><span class="sxs-lookup"><span data-stu-id="82206-122">Click the **Bindings….**</span></span> <span data-ttu-id="82206-123">Vincular a **ações** seção na parte superior direito da janela.</span><span class="sxs-lookup"><span data-stu-id="82206-123">Link in the **Actions** section in the upper right hand portion of the window.</span></span>  
  
     <span data-ttu-id="82206-124">![Adicionar uma associação SSL](../../../../docs/framework/wcf/feature-details/media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span><span class="sxs-lookup"><span data-stu-id="82206-124">![Adding an SSL binding](../../../../docs/framework/wcf/feature-details/media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span></span>  
  
3.  <span data-ttu-id="82206-125">Na janela de ligações de Site, clique no **adicionar** botão.</span><span class="sxs-lookup"><span data-stu-id="82206-125">In the Site Bindings window click the **Add** button.</span></span>  
  
     <span data-ttu-id="82206-126">![Caixa de diálogo ligações do site](../../../../docs/framework/wcf/feature-details/media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span><span class="sxs-lookup"><span data-stu-id="82206-126">![Site Bindings Dialog](../../../../docs/framework/wcf/feature-details/media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span></span>  
  
4.  <span data-ttu-id="82206-127">No **Adicionar associação do Site** caixa de diálogo, selecione https para o tipo e o nome amigável do certificado autoassinado apenas que você criou.</span><span class="sxs-lookup"><span data-stu-id="82206-127">In the **Add Site Binding** dialog, select https for the type and the friendly name of the self-signed certificate you just created.</span></span>  
  
     <span data-ttu-id="82206-128">![Exemplo de associação de site](../../../../docs/framework/wcf/feature-details/media/mg-mycertbinding.jpg "mg_MyCertBinding")</span><span class="sxs-lookup"><span data-stu-id="82206-128">![Site binding example](../../../../docs/framework/wcf/feature-details/media/mg-mycertbinding.jpg "mg_MyCertBinding")</span></span>  
  
### <a name="configure-virtual-directory-for-ssl"></a><span data-ttu-id="82206-129">Configurar o diretório Virtual para SSL</span><span class="sxs-lookup"><span data-stu-id="82206-129">Configure Virtual Directory for SSL</span></span>  
  
1.  <span data-ttu-id="82206-130">Ainda no Gerenciador de serviços de informações da Internet, selecione o diretório virtual que contém o serviço de segurança do WCF.</span><span class="sxs-lookup"><span data-stu-id="82206-130">Still in Internet Information Services Manager, select the virtual directory that contains your WCF secure service.</span></span>  
  
2.  <span data-ttu-id="82206-131">No painel central da janela, selecione **configurações de SSL** na seção do IIS.</span><span class="sxs-lookup"><span data-stu-id="82206-131">In the center pane of the window, select **SSL Settings** in the IIS section.</span></span>  
  
     <span data-ttu-id="82206-132">![Configurações de SSL para o diretório virtual](../../../../docs/framework/wcf/feature-details/media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span><span class="sxs-lookup"><span data-stu-id="82206-132">![SSL Settings for virtual directory](../../../../docs/framework/wcf/feature-details/media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span></span>  
  
3.  <span data-ttu-id="82206-133">No painel de configurações de SSL, selecione o **exigir SSL** caixa de seleção e clique no **aplicar** link no **ações** seção no lado direito da tela.</span><span class="sxs-lookup"><span data-stu-id="82206-133">In the SSL Settings pane, select the **Require SSL** checkbox and click the **Apply** link in the **Actions** section on the right hand side of the screen.</span></span>  
  
     <span data-ttu-id="82206-134">![Configurações de SSL do diretório virtual](../../../../docs/framework/wcf/feature-details/media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span><span class="sxs-lookup"><span data-stu-id="82206-134">![Virtual directory SSL settings](../../../../docs/framework/wcf/feature-details/media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span></span>  
  
### <a name="configure-wcf-service-for-http-transport-security"></a><span data-ttu-id="82206-135">Configurar o serviço do WCF para segurança de transporte HTTP</span><span class="sxs-lookup"><span data-stu-id="82206-135">Configure WCF Service for HTTP Transport Security</span></span>  
  
1.  <span data-ttu-id="82206-136">O WCF Web. config do serviço configura a associação HTTP para usar a segurança de transporte, conforme mostrado no seguinte XML.</span><span class="sxs-lookup"><span data-stu-id="82206-136">In the WCF service’s web.config configure the HTTP binding to use transport security as shown in the following XML.</span></span>  
  
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
  
2.  <span data-ttu-id="82206-137">Especifique seu serviço e o ponto de extremidade de serviço, conforme mostrado no seguinte XML.</span><span class="sxs-lookup"><span data-stu-id="82206-137">Specify your service and service endpoint as shown in the following XML.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="82206-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="82206-138">Example</span></span>  
 <span data-ttu-id="82206-139">Este é um exemplo completo de um arquivo Web. config para um serviço WCF usando a segurança de transporte HTTP</span><span class="sxs-lookup"><span data-stu-id="82206-139">The following is a complete example of a web.config file for a WCF service using HTTP transport security</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="82206-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82206-140">See Also</span></span>  
 [<span data-ttu-id="82206-141">Hospedagem nos Serviços de Informações da Internet</span><span class="sxs-lookup"><span data-stu-id="82206-141">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [<span data-ttu-id="82206-142">Instruções de hospedagem do Serviços de Informações da Internet</span><span class="sxs-lookup"><span data-stu-id="82206-142">Internet Information Service Hosting Instructions</span></span>](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)  
 [<span data-ttu-id="82206-143">Práticas recomendadas de hospedagem de Serviços de Informações da Internet</span><span class="sxs-lookup"><span data-stu-id="82206-143">Internet Information Services Hosting Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [<span data-ttu-id="82206-144">Hospedagem do IIS utilizando código embutido</span><span class="sxs-lookup"><span data-stu-id="82206-144">IIS Hosting Using Inline Code</span></span>](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)

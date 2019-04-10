---
title: 'Como: configurar um serviço do WCF hospedado no IIS com SSL'
ms.date: 03/30/2017
ms.assetid: df2fe31f-a4bb-4024-92ca-b74ba055e038
ms.openlocfilehash: 336c3800fc033cc12bd9c3fe168ae219b72cab91
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214112"
---
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a>Como: configurar um serviço do WCF hospedado no IIS com SSL
Este tópico descreve como configurar um serviço WCF hospedado pelo IIS para usar a segurança de transporte HTTP. Segurança de transporte HTTP requer um certificado SSL a ser registrado com o IIS. Se você não tiver um certificado SSL que você pode usar o IIS para gerar um certificado de teste. Em seguida, você deve adicionar uma associação SSL para o site da web e configurar as propriedades de autenticação do site da web. Por fim, você precisa configurar o serviço do WCF para usar HTTPS.  
  
### <a name="creating-a-self-signed-certificate"></a>Criando um certificado autoassinado  
  
1.  Abra o Gerenciador de serviços de informações da Internet (inetmgr.exe) e selecione o nome do computador no modo de exibição de árvore à esquerda. No lado direito da tela, selecione certificados de servidor  
  
     ![Tela de inicial do Gerenciador do IIS](../../../../docs/framework/wcf/feature-details/media/mg-inetmgrhome.jpg "mg_INetMgrHome")  
  
2.  Na janela de certificados de servidor, clique no **criar certificado autoassinado...** link.  
  
     ![Criando um self&#45;assinou o certificado com o IIS](../../../../docs/framework/wcf/feature-details/media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")  
  
3.  Insira um nome amigável para o certificado autoassinado e clique em **Okey**.  
  
     ![Criar Self&#45;caixa de diálogo de certificado assinado](../../../../docs/framework/wcf/feature-details/media/mg-mycert.jpg "mg_MyCert")  
  
     Os detalhes do certificado autoassinado recém-criado agora são mostrados na **certificados de servidor** janela.  
  
     ![Janela de certificado do servidor](../../../../docs/framework/wcf/feature-details/media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")  
  
     O certificado gerado é instalado em autoridades de certificação raiz confiáveis armazenar.  
  
### <a name="add-ssl-binding"></a>Adicionar associação SSL  
  
1.  Ainda no Gerenciador de serviços de informações da Internet, expanda o **Sites** pasta e, em seguida, o **Default Web Site** pasta na exibição de árvore no lado esquerdo da tela.  
  
2.  Clique o **associações...** Link na **ações** seção na parte superior direito da janela.  
  
     ![Adicionar uma associação SSL](../../../../docs/framework/wcf/feature-details/media/mg-addsslbinding.jpg "mg_AddSSLBinding")  
  
3.  Na janela de ligações de Site, clique no **adicionar** botão.  
  
     ![Caixa de diálogo ligações do site](../../../../docs/framework/wcf/feature-details/media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")  
  
4.  No **adicionar ligação do Site** selecione https para o tipo e o nome amigável do certificado autoassinado que você acabou de caixa de diálogo, criada.  
  
     ![Exemplo de associação de site](../../../../docs/framework/wcf/feature-details/media/mg-mycertbinding.jpg "mg_MyCertBinding")  
  
### <a name="configure-virtual-directory-for-ssl"></a>Configurar o diretório Virtual para SSL  
  
1.  Ainda no Gerenciador de serviços de informações da Internet, selecione o diretório virtual que contém o serviço de seguro do WCF.  
  
2.  No painel central da janela, selecione **configurações de SSL** na seção de IIS.  
  
     ![Configurações de SSL para o diretório virtual](../../../../docs/framework/wcf/feature-details/media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")  
  
3.  No painel de configurações de SSL, selecione a **exigir SSL** caixa de seleção e clique no **Apply** link no **ações** seção no lado direito da tela.  
  
     ![Configurações de SSL do diretório virtual](../../../../docs/framework/wcf/feature-details/media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")  
  
### <a name="configure-wcf-service-for-http-transport-security"></a>Configurar o serviço do WCF para segurança de transporte de HTTP  
  
1.  No WCF Web. config do serviço configurar a associação de HTTP para usar a segurança de transporte, conforme mostrado no seguinte XML.  
  
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
  
2.  Especifique seu serviço e o ponto de extremidade de serviço, conforme mostrado no XML a seguir.  
  
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
  
## <a name="example"></a>Exemplo  
 A seguir está um exemplo completo de um arquivo Web. config para um serviço WCF usando a segurança de transporte HTTP  
  
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
  
## <a name="see-also"></a>Consulte também

- [Hospedagem no Internet Information Services](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)
- [Instruções de hospedagem de serviço de informação de internet](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
- [Práticas recomendadas de hospedagem dos Serviços de Informações da Internet](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
- [Hospedagem do IIS utilizando código embutido](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)

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
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a>Como configurar um serviço do WCF hospedado no IIS com SSL
Este tópico descreve como configurar um serviço WCF hospedado pelo IIS para usar a segurança de transporte HTTP. A segurança de transporte HTTP requer que um certificado SSL seja registrado no IIS. Se você não tiver um certificado SSL, poderá usar o IIS para gerar um certificado de teste. Em seguida, você deve adicionar uma associação SSL ao site da Web e configurar as propriedades de autenticação do site. Por fim, você precisa configurar o serviço WCF para usar HTTPS.  
  
### <a name="creating-a-self-signed-certificate"></a>Criando um certificado autoassinado  
  
1. Abra o Gerenciador de Serviços de Informações da Internet (inetmgr. exe) e selecione o nome do computador no modo de exibição de árvore à esquerda. No lado direito da tela, selecione certificados de servidor  
  
     ![Tela inicial do gerenciador do IIS](media/mg-inetmgrhome.jpg "mg_INetMgrHome")  
  
2. Na janela certificados do servidor, clique no **criar certificado autoassinado....** Criar.  
  
     ![Criando um certificado auto&#45;assinado com o IIS](media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")  
  
3. Insira um nome amigável para o certificado autoassinado e clique em **OK**.  
  
     ![Caixa de diálogo Criar certificado auto&#45;assinado](media/mg-mycert.jpg "mg_MyCert")  
  
     Os detalhes do certificado autoassinado recém-criado agora são mostrados na janela **certificados do servidor** .  
  
     ![Janela do certificado de servidor](media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")  
  
     O certificado gerado é instalado no repositório de autoridades de certificação raiz confiáveis.  
  
### <a name="add-ssl-binding"></a>Adicionar Associação SSL  
  
1. Ainda no Serviços de Informações da Internet Manager, expanda a pasta **sites** e, em seguida, a pasta **site padrão** no modo de exibição de árvore no lado esquerdo da tela.  
  
2. Clique nas **associações....** No link na seção **ações** na parte superior direita da janela.  
  
     ![Adicionando a associação SSL](media/mg-addsslbinding.jpg "mg_AddSSLBinding")  
  
3. Na janela ligações do site, clique no botão **Adicionar** .  
  
     ![Caixa de diálogo Associações do site](media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")  
  
4. Na caixa de diálogo **Adicionar associação do site** , selecione https para o tipo e o nome amigável do certificado autoassinado que você acabou de criar.  
  
     ![Exemplo de associação de site](media/mg-mycertbinding.jpg "mg_MyCertBinding")  
  
### <a name="configure-virtual-directory-for-ssl"></a>Configurar o diretório virtual para SSL  
  
1. Ainda no Gerenciador de Serviços de Informações da Internet, selecione o diretório virtual que contém seu serviço WCF Secure.  
  
2. No painel central da janela, selecione configurações de **SSL** na seção IIS.  
  
     ![Configurações de SSL para o diretório virtual](media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")  
  
3. No painel configurações de SSL, marque a caixa de seleção **exigir SSL** e clique no link **aplicar** na seção **ações** no lado direito da tela.  
  
     ![Configurações de SSL do diretório virtual](media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")  
  
### <a name="configure-wcf-service-for-http-transport-security"></a>Configurar o serviço WCF para segurança de transporte HTTP  
  
1. No Web. config do serviço WCF, configure a associação HTTP para usar a segurança de transporte, conforme mostrado no XML a seguir.  
  
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
  
2. Especifique o serviço e o ponto de extremidade de serviço, conforme mostrado no XML a seguir.  
  
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
 Veja a seguir um exemplo completo de um arquivo Web. config para um serviço WCF usando a segurança de transporte HTTP  
  
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

- [Hospedagem no Internet Information Services](hosting-in-internet-information-services.md)
- [Instruções de hospedagem de serviço de informação de internet](../samples/internet-information-service-hosting-instructions.md)
- [Práticas recomendadas de hospedagem de Serviços de Informações da Internet](internet-information-services-hosting-best-practices.md)
- [Hospedagem do IIS utilizando código embutido](../samples/iis-hosting-using-inline-code.md)

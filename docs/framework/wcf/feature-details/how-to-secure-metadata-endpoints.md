---
title: Como proteger pontos de extremidade de metadados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
author: BrucePerlerMS
ms.openlocfilehash: f1dae4b9d2976ddbc941e49843324a29ec8885a4
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48781785"
---
# <a name="how-to-secure-metadata-endpoints"></a>Como proteger pontos de extremidade de metadados
Metadados para um serviço podem conter informações confidenciais sobre seu aplicativo que um usuário mal-intencionado pode aproveitar. Os consumidores do seu serviço também podem exigir um mecanismo seguro para obtenção de metadados sobre o serviço. Portanto, às vezes, é necessário publicar seus metadados usando um ponto de extremidade seguro.  
  
 Pontos de extremidade de metadados geralmente são protegidos usando os mecanismos de segurança padrão definidos no Windows Communication Foundation (WCF) para proteger pontos de extremidade do aplicativo. (Para obter mais informações, consulte [visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md).)  
  
 Este tópico explica as etapas para criar um ponto de extremidade protegido por um certificado Secure Sockets Layer (SSL) ou, em outras palavras, um ponto de extremidade HTTPS.  
  
### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a>Para criar uma empresa de metadados de HTTPS GET segura no código  
  
1.  Configure uma porta com um certificado x. 509 apropriado. O certificado deve vir de uma autoridade confiável, e deve ter um uso pretendido do "Autorização de serviço". Você deve usar a ferramenta HttpCfg.exe para anexar o certificado à porta. Ver [como: configurar uma porta com um certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
    > [!IMPORTANT]
    >  O assunto do certificado ou seu sistema de nome de domínio (DNS) deve corresponder ao nome do computador. Isso é essencial porque uma das primeiras etapas que executa o mecanismo HTTPS é verificar se o certificado é emitido para o mesmo identificador de URI (Uniform Resource) como o endereço no qual ele é invocado.  
  
2.  Criar uma nova instância da classe <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.  
  
3.  Defina a <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> propriedade do <xref:System.ServiceModel.Description.ServiceMetadataBehavior> classe para `true`.  
  
4.  Defina o <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> propriedade para uma URL apropriada. Observe que, se você especificar um endereço absoluto, a URL deve começar com o esquema "https://". Se você especificar um endereço relativo, você deve fornecer um endereço base HTTPS para seu host de serviço. Se essa propriedade não for definida, o endereço padrão é "", ou diretamente no endereço base HTTPS para o serviço.  
  
5.  Adicionar a instância à coleção de comportamentos que o <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> propriedade do <xref:System.ServiceModel.Description.ServiceDescription> classe retorna, conforme mostrado no código a seguir.  
  
     [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
     [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]  
  
### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a>Para criar uma empresa de metadados de HTTPS GET segura na configuração  
  
1.  Adicionar um [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento para o [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elemento do arquivo de configuração para seu serviço.  
  
2.  Adicionar um [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) elemento para o [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento.  
  
3.  Adicionar um [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elemento para o `<serviceBehaviors>` elemento.  
  
4.  Defina as `name` atributo do `<behavior>` elemento para um valor apropriado. O atributo `name` é necessário. O exemplo a seguir usa o valor `mySvcBehavior`.  
  
5.  Adicionar um [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) para o `<behavior>` elemento.  
  
6.  Defina o atributo `httpsGetEnabled` do elemento `<serviceMetadata>` como `true`.  
  
7.  Defina as `httpsGetUrl` atributo do `<serviceMetadata>` elemento para um valor apropriado. Observe que, se você especificar um endereço absoluto, a URL deve começar com o esquema "https://". Se você especificar um endereço relativo, você deve fornecer um endereço base HTTPS para seu host de serviço. Se essa propriedade não for definida, o endereço padrão é "", ou diretamente no endereço base HTTPS para o serviço.  
  
8.  Para usar o comportamento com um serviço, defina a `behaviorConfiguration` atributo o [ \<serviço >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) elemento como o valor do atributo name do elemento de comportamento. O código de configuração a seguir mostra um exemplo completo.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <serviceBehaviors>  
        <behavior name="mySvcBehavior">  
         <serviceMetadata httpsGetEnabled="true"   
              httpsGetUrl="https://localhost:8036/calcMetadata" />  
        </behavior>  
       </serviceBehaviors>  
      </behaviors>  
     <services>  
      <service behaviorConfiguration="mySvcBehavior"   
            name="Microsoft.Security.Samples.Calculator">  
       <endpoint address="http://localhost:8037/ServiceModelSamples/calculator"  
       binding="wsHttpBinding" bindingConfiguration=""     
       contract="Microsoft.Security.Samples.ICalculator" />  
      </service>  
     </services>  
    </system.serviceModel>  
    </configuration>  
    ```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma instância de um <xref:System.ServiceModel.ServiceHost> de classe e adiciona um ponto de extremidade. O código então cria uma instância da <xref:System.ServiceModel.Description.ServiceMetadataBehavior> de classe e define as propriedades para criar um ponto de troca de metadados seguros.  
  
 [!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
 [!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo de código usa os seguintes namespaces:  
  
-   <xref:System.ServiceModel?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Description?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>  
 [Como configurar uma porta com um certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [Trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Considerações de segurança com metadados](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)  
 [Protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)

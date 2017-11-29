---
title: Como proteger pontos de extremidade de metadados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: e28b4dec851cc4115c2688540ebee151c91e4cd0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-secure-metadata-endpoints"></a>Como proteger pontos de extremidade de metadados
Metadados para um serviço podem conter informações confidenciais sobre seu aplicativo que um usuário mal-intencionado pode aproveitar. Os consumidores de serviço também podem exigir um mecanismo seguro para obtenção de metadados sobre o serviço. Portanto, às vezes, é necessário publicar seus metadados usando um ponto de extremidade seguro.  
  
 Pontos de extremidade de metadados geralmente são protegidos por meio de mecanismos de segurança padrão definidos em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] para proteger pontos de extremidade do aplicativo. ([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md).)  
  
 Este tópico explica as etapas para criar um ponto de extremidade protegido por um certificado Secure Sockets Layer (SSL) ou, em outras palavras, um ponto de extremidade HTTPS.  
  
### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a>Para criar uma empresa de metadados de obter HTTPS segura no código  
  
1.  Configure uma porta com um certificado x. 509 apropriado. O certificado deve vir de uma autoridade confiável e deve ter um uso pretendido do "Serviço autorização". Você deve usar a ferramenta HttpCfg.exe para anexar o certificado para a porta. Consulte [como: configurar uma porta com um certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
    > [!IMPORTANT]
    >  O assunto do certificado ou seu sistema de nome de domínio (DNS) deve corresponder ao nome do computador. Isso é essencial porque uma das primeiras etapas que executa o mecanismo HTTPS é verificar se o certificado é emitido para o mesmo URI Uniform Resource Identifier () como o endereço no qual ele é invocado.  
  
2.  Criar uma nova instância da classe <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.  
  
3.  Definir o <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> propriedade o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> de classe para `true`.  
  
4.  Definir o <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> propriedade em uma URL apropriada. Observe que, se você especificar um endereço absoluto, a URL deve começar com o esquema "https://". Se você especificar um endereço relativo, você deve fornecer um endereço base HTTPS para o host de serviço. Se essa propriedade não é definida, o endereço padrão é "", ou diretamente no endereço base HTTPS para o serviço.  
  
5.  Adicionar a instância para a coleção de comportamentos que o <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> propriedade o <xref:System.ServiceModel.Description.ServiceDescription> classe retorna, conforme mostrado no código a seguir.  
  
     [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
     [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]  
  
### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a>Para criar uma empresa de metadados de obter HTTPS segura na configuração  
  
1.  Adicionar um [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento para o [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elemento do arquivo de configuração para o serviço.  
  
2.  Adicionar um [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) elemento para o [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento.  
  
3.  Adicionar um [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elemento para o `<serviceBehaviors>` elemento.  
  
4.  Definir o `name` atributo do `<behavior>` elemento para um valor apropriado. O atributo `name` é necessário. O exemplo a seguir usa o valor `mySvcBehavior`.  
  
5.  Adicionar um [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) para o `<behavior>` elemento.  
  
6.  Defina o atributo `httpsGetEnabled` do elemento `<serviceMetadata>` como `true`.  
  
7.  Definir o `httpsGetUrl` atributo do `<serviceMetadata>` elemento para um valor apropriado. Observe que, se você especificar um endereço absoluto, a URL deve começar com o esquema "https://". Se você especificar um endereço relativo, você deve fornecer um endereço base HTTPS para o host de serviço. Se essa propriedade não é definida, o endereço padrão é "", ou diretamente no endereço base HTTPS para o serviço.  
  
8.  Para usar o comportamento com um serviço, defina o `behaviorConfiguration` atributo do [ \<service >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) elemento para o valor do atributo name do elemento de comportamento. O código de configuração a seguir mostra um exemplo completo.  
  
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
 O exemplo a seguir cria uma instância de um <xref:System.ServiceModel.ServiceHost> classe e adiciona um ponto de extremidade. O código, em seguida, cria uma instância do <xref:System.ServiceModel.Description.ServiceMetadataBehavior> classe e define as propriedades para criar um ponto de troca de metadados seguros.  
  
 [!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
 [!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo de código usa os namespaces a seguir:  
  
-   <xref:System.ServiceModel?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Description?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>  
 [Como: configurar uma porta com um certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [Trabalhar com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Considerações de segurança com metadados](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)  
 [Protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)

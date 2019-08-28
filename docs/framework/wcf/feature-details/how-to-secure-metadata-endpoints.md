---
title: 'Como: proteger pontos de extremidade de metadados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
ms.openlocfilehash: c6439187560e15ec10f1eea4e1731421904e8643
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045291"
---
# <a name="how-to-secure-metadata-endpoints"></a>Como: proteger pontos de extremidade de metadados

Os metadados de um serviço podem conter informações confidenciais sobre o aplicativo que um usuário mal-intencionado pode aproveitar. Os consumidores do seu serviço também podem exigir um mecanismo seguro para obter metadados sobre seu serviço. Portanto, às vezes é necessário publicar seus metadados usando um ponto de extremidade seguro.

Os pontos de extremidade de metadados são geralmente protegidos usando os mecanismos de segurança padrão definidos no Windows Communication Foundation (WCF) para proteger os pontos de extremidade do aplicativo. (Para obter mais informações, consulte [visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md).)

Este tópico percorre as etapas para criar um ponto de extremidade protegido por um certificado protocolo SSL (SSL) ou, em outras palavras, um ponto de extremidade HTTPS.

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a>Para criar um ponto de extremidade de obtenção de metadados de HTTPS seguro no código

1. Configure uma porta com um certificado X. 509 apropriado. O certificado deve vir de uma autoridade confiável e deve ter um uso pretendido de "autorização de serviço". Você deve usar a ferramenta HttpCfg. exe para anexar o certificado à porta. Confira [Como Configure uma porta com um certificado](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)SSL.

    > [!IMPORTANT]
    > O assunto do certificado ou seu DNS (sistema de nomes de domínio) deve corresponder ao nome do computador. Isso é essencial porque uma das primeiras etapas que o mecanismo HTTPS executa é verificar se o certificado é emitido para o mesmo Uniform Resource Identifier (URI) que o endereço no qual ele é invocado.

2. Criar uma nova instância da classe <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.

3. Defina a <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> propriedade <xref:System.ServiceModel.Description.ServiceMetadataBehavior> da classe como `true`.

4. Defina a <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> Propriedade como uma URL apropriada. Observe que, se você especificar um endereço absoluto, a URL deverá começar com o esquema "https://". Se você especificar um endereço relativo, deverá fornecer um endereço base HTTPS para seu host de serviço. Se essa propriedade não for definida, o endereço padrão será "", ou diretamente no endereço base HTTPS para o serviço.

5. Adicione a instância à coleção <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> <xref:System.ServiceModel.Description.ServiceDescription> de comportamentos que a propriedade da classe retorna, conforme mostrado no código a seguir.

    [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
    [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a>Para criar um ponto de extremidade de obtenção de metadados de HTTPS seguro na configuração

1. Adicione um [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento de > de comportamentos ao [ \<elemento System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) do arquivo de configuração para seu serviço.

2. Adicione um elemento de [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) de portais ao [ \<elemento comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) .

3. Adicione um [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elemento de > de comportamento `<serviceBehaviors>` ao elemento.

4. Defina o `name` atributo `<behavior>` do elemento para um valor apropriado. O atributo `name` é necessário. O exemplo a seguir usa o `mySvcBehavior`valor.

5. Adicione [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) um`<behavior>` > de metadados ao elemento.

6. Defina o atributo `httpsGetEnabled` do elemento `<serviceMetadata>` como `true`.

7. Defina o `httpsGetUrl` atributo `<serviceMetadata>` do elemento para um valor apropriado. Observe que, se você especificar um endereço absoluto, a URL deverá começar com o esquema "https://". Se você especificar um endereço relativo, deverá fornecer um endereço base HTTPS para seu host de serviço. Se essa propriedade não for definida, o endereço padrão será "", ou diretamente no endereço base HTTPS para o serviço.

8. Para usar o comportamento com um serviço, defina o `behaviorConfiguration` atributo [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) do elemento > do serviço como o valor do atributo Name do elemento Behavior. O código de configuração a seguir mostra um exemplo completo.

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

O exemplo a seguir cria uma instância de <xref:System.ServiceModel.ServiceHost> uma classe e adiciona um ponto de extremidade. Em seguida, o código cria uma instância <xref:System.ServiceModel.Description.ServiceMetadataBehavior> da classe e define as propriedades para criar um ponto de troca de metadados seguro.

[!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
[!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]

## <a name="compiling-the-code"></a>Compilando o código

O exemplo de código usa os seguintes namespaces:

- <xref:System.ServiceModel?displayProperty=nameWithType>

- <xref:System.ServiceModel.Description?displayProperty=nameWithType>

## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [Como: Configurar uma porta com um certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Considerações de segurança com metadados](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [Protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)

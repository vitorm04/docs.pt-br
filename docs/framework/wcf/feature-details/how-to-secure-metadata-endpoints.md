---
title: Como proteger pontos de extremidade de metadados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
ms.openlocfilehash: ee64e53f49e15059c91982f2e64879b9f4c76d78
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834685"
---
# <a name="how-to-secure-metadata-endpoints"></a>Como proteger pontos de extremidade de metadados

Os metadados de um serviço podem conter informações confidenciais sobre o aplicativo que um usuário mal-intencionado pode aproveitar. Os consumidores do seu serviço também podem exigir um mecanismo seguro para obter metadados sobre seu serviço. Portanto, às vezes é necessário publicar seus metadados usando um ponto de extremidade seguro.

Os pontos de extremidade de metadados são geralmente protegidos usando os mecanismos de segurança padrão definidos no Windows Communication Foundation (WCF) para proteger os pontos de extremidade do aplicativo. Para obter mais informações, consulte [visão geral de segurança](security-overview.md).

Este tópico percorre as etapas para criar um ponto de extremidade protegido por um certificado protocolo SSL (SSL) ou, em outras palavras, um ponto de extremidade HTTPS.

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a>Para criar um ponto de extremidade de obtenção de metadados de HTTPS seguro no código

1. Configure uma porta com um certificado X. 509 apropriado. O certificado deve vir de uma autoridade confiável e deve ter um uso pretendido de "autorização de serviço". Você deve usar a ferramenta HttpCfg. exe para anexar o certificado à porta. Consulte [como: configurar uma porta com um certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).

    > [!IMPORTANT]
    > O assunto do certificado ou seu DNS (sistema de nomes de domínio) deve corresponder ao nome do computador. Isso é essencial porque uma das primeiras etapas que o mecanismo HTTPS executa é verificar se o certificado é emitido para o mesmo Uniform Resource Identifier (URI) que o endereço no qual ele é invocado.

2. Criar uma nova instância da classe <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.

3. Defina a propriedade <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> da classe <xref:System.ServiceModel.Description.ServiceMetadataBehavior> como `true`.

4. Defina a propriedade <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> como uma URL apropriada. Observe que, se você especificar um endereço absoluto, a URL deverá começar com o esquema "https://". Se você especificar um endereço relativo, deverá fornecer um endereço base HTTPS para seu host de serviço. Se essa propriedade não for definida, o endereço padrão será "", ou diretamente no endereço base HTTPS para o serviço.

5. Adicione a instância à coleção de comportamentos que a propriedade <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> da classe <xref:System.ServiceModel.Description.ServiceDescription> retorna, conforme mostrado no código a seguir.

    [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
    [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a>Para criar um ponto de extremidade de obtenção de metadados de HTTPS seguro na configuração

1. Adicione um elemento [> Behaviors de\<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) ao elemento [\<system. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) do arquivo de configuração para seu serviço.

2. Adicione um elemento de [> de\<](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) de portais ao elemento [> comportamentos de\<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) .

3. Adicione um elemento de [comportamento de\<>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) ao elemento `<serviceBehaviors>`.

4. Defina o atributo `name` do elemento `<behavior>` como um valor apropriado. O atributo `name` é necessário. O exemplo a seguir usa o valor `mySvcBehavior`.

5. Adicione um [> de\<de metadados](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) ao elemento `<behavior>`.

6. Defina o atributo `httpsGetEnabled` do elemento `<serviceMetadata>` como `true`.

7. Defina o atributo `httpsGetUrl` do elemento `<serviceMetadata>` como um valor apropriado. Observe que, se você especificar um endereço absoluto, a URL deverá começar com o esquema "https://". Se você especificar um endereço relativo, deverá fornecer um endereço base HTTPS para seu host de serviço. Se essa propriedade não for definida, o endereço padrão será "", ou diretamente no endereço base HTTPS para o serviço.

8. Para usar o comportamento com um serviço, defina o atributo `behaviorConfiguration` do elemento [\<do serviço de >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) como o valor do atributo Name do elemento Behavior. O código de configuração a seguir mostra um exemplo completo.

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

## <a name="example"></a>{1&gt;Exemplo&lt;1}

O exemplo a seguir cria uma instância de uma classe <xref:System.ServiceModel.ServiceHost> e adiciona um ponto de extremidade. Em seguida, o código cria uma instância da classe <xref:System.ServiceModel.Description.ServiceMetadataBehavior> e define as propriedades para criar um ponto de troca de metadados seguro.

[!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
[!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]

## <a name="compiling-the-code"></a>Compilando o Código

O exemplo de código usa os seguintes namespaces:

- <xref:System.ServiceModel?displayProperty=nameWithType>

- <xref:System.ServiceModel.Description?displayProperty=nameWithType>

## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [Como configurar uma porta com um certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Considerações de segurança com metadados](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [Protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)

---
title: Como especificar valores de credenciais de cliente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: 2417c2dd16224d6cbf00d3f1f4a8958420830b6c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319858"
---
# <a name="how-to-specify-client-credential-values"></a>Como especificar valores de credenciais de cliente

Usando o Windows Communication Foundation (WCF), o serviço pode especificar como um cliente é autenticado para o serviço. Por exemplo, um serviço pode estipular que o cliente seja autenticado com um certificado.

## <a name="to-determine-the-client-credential-type"></a>Para determinar o tipo de credencial do cliente

1. Recuperar metadados do ponto de extremidade de metadados do serviço. Os metadados geralmente consistem em dois arquivos: o código do cliente na linguagem de programação de sua escolha (o padrão C#é Visual) e um arquivo de configuração XML. Uma maneira de recuperar metadados é usar a ferramenta svcutil. exe para retornar o código do cliente e a configuração do cliente. Para obter mais informações, consulte [Recuperando metadados](./feature-details/retrieving-metadata.md) e [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).

2. Abra o arquivo de configuração XML. Se você usar a ferramenta svcutil. exe, o nome padrão do arquivo será output. config.

3. Localize o elemento de **> \<Security** com o atributo **Mode** ( **@no__t modo de 4security =** `MessageOrTransport` **>,** em que `MessageOrTransport` está definido como um dos modos de segurança.

4. Localize o elemento filho que corresponde ao valor de modo. Por exemplo, se o modo for definido como **Message**, localize o elemento **\<message >** contido no elemento **> \<security** .

5. Observe o valor atribuído ao atributo **ClientCredentialType** . O valor real depende de qual modo é usado, transporte ou mensagem.

O código XML a seguir mostra a configuração de um cliente usando a segurança de mensagem e exigindo um certificado para autenticar o cliente.

```xml
<security mode="Message">
    <transport clientCredentialType="Windows" proxyCredentialType="None"
        realm="" />
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"
    algorithmSuite="Default" establishSecurityContext="true" />
</security>
```

## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a>Exemplo: modo de transporte TCP com certificado como credencial do cliente

Este exemplo define o modo de segurança para o modo de transporte e define o valor de credencial do cliente para um certificado X. 509. Os procedimentos a seguir demonstram como definir o valor de credencial do cliente no cliente em código e configuração. Isso pressupõe que você tenha usado a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) para retornar os metadados (código e configuração) do serviço. Para obter mais informações, consulte [como: criar um cliente](how-to-create-a-wcf-client.md).

### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a>Para especificar o valor de credencial do cliente no código

1. Use a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar o código e a configuração do serviço.

2. Crie uma instância do cliente WCF usando o código gerado.

3. Na classe cliente, defina a propriedade <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> da classe <xref:System.ServiceModel.ClientBase%601> como um valor apropriado. Este exemplo define a propriedade como um certificado X. 509 usando o método <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> da classe <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>.

     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]

     Você pode usar qualquer uma das enumerações da classe <xref:System.Security.Cryptography.X509Certificates.X509FindType>. O nome da entidade é usado aqui no caso de o certificado ser alterado (devido a uma data de expiração). O uso do nome da entidade permite que a infraestrutura localize o certificado novamente.

### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a>Para especificar o valor de credencial do cliente no cliente na configuração

1. Adicione um elemento de [> de \<behavior](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) ao elemento de [> \<behaviors](../configure-apps/file-schema/wcf/behaviors.md) .

2. Adicione um elemento de [> de \<clientCredentials](../configure-apps/file-schema/wcf/clientcredentials.md) ao elemento de [> \<behaviors](../configure-apps/file-schema/wcf/behaviors.md) . Certifique-se de definir o atributo `name` necessário para um valor apropriado.

3. Adicione um elemento de [> de \<clientCertificate](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) ao elemento de [> \<clientCredentials](../configure-apps/file-schema/wcf/clientcredentials.md) .

4. Defina os seguintes atributos para os valores apropriados: `storeLocation`, `storeName`, `x509FindType` e `findValue`, conforme mostrado no código a seguir. Para obter mais informações sobre certificados, consulte [Working with Certificates](./feature-details/working-with-certificates.md) (Trabalhando com certificados).

    ```xml
    <behaviors>
       <endpointBehaviors>
          <behavior name="endpointCredentialBehavior">
            <clientCredentials>
              <clientCertificate findValue="Contoso.com"
                                 storeLocation="LocalMachine"
                                 storeName="TrustedPeople"
                                 x509FindType="FindBySubjectName" />
            </clientCredentials>
          </behavior>
       </endpointBehaviors>
    </behaviors>
    ```

5. Ao configurar o cliente, especifique o comportamento definindo o atributo `behaviorConfiguration` do elemento `<endpoint>`, conforme mostrado no código a seguir. O elemento Endpoint é um filho do elemento [\<client >](../configure-apps/file-schema/wcf/client.md) . Além disso, especifique o nome da configuração de associação definindo o atributo `bindingConfiguration` como a associação para o cliente. Se você estiver usando um arquivo de configuração gerado, o nome da Associação será gerado automaticamente. Neste exemplo, o nome é `"tcpBindingWithCredential"`.

    ```xml
    <client>
      <endpoint name =""
                address="net.tcp://contoso.com:8036/aloha"
                binding="netTcpBinding"
                bindingConfiguration="tcpBindingWithCredential"
                behaviorConfiguration="endpointCredentialBehavior" />
    </client>
    ```

## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [Programação de segurança do WCF](./feature-details/programming-wcf-security.md)
- [Selecionando um tipo de credencial](./feature-details/selecting-a-credential-type.md)
- [Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Trabalhando com certificados](./feature-details/working-with-certificates.md)
- [Como criar um cliente](how-to-create-a-wcf-client.md)
- [\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md)
- [\<Security >](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [\<message >](../configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [\<behavior >](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [\<behaviors >](../configure-apps/file-schema/wcf/behaviors.md)
- [\<clientCertificate >](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [\<clientCredentials >](../configure-apps/file-schema/wcf/clientcredentials.md)

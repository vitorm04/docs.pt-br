---
title: 'Como: especificar valores de credenciais de cliente'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: ecb8f7ef74f1f0625454eb2d6cebf9d282a5ece3
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59327094"
---
# <a name="how-to-specify-client-credential-values"></a>Como: especificar valores de credenciais de cliente
Usando o Windows Communication Foundation (WCF), o serviço pode especificar como um cliente é autenticado para o serviço. Por exemplo, um serviço pode estipular que o cliente seja autenticado com um certificado.  
  
### <a name="to-determine-the-client-credential-type"></a>Para determinar o tipo de credencial de cliente  
  
1. Recupere metadados do ponto de extremidade de metadados do serviço. Os metadados normalmente consistem em dois arquivos: o código do cliente na linguagem de programação de sua escolha (o padrão é o Visual C#) e um arquivo de configuração XML. Uma maneira de recuperar metadados é usar a ferramenta Svcutil.exe para retornar o código do cliente e a configuração do cliente. Para obter mais informações, consulte [metadados recuperando](../../../docs/framework/wcf/feature-details/retrieving-metadata.md) e [ferramenta Utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
2. Abra o arquivo de configuração XML. Se você usar a ferramenta Svcutil.exe, o nome padrão do arquivo é Output. config.  
  
3. Localizar o  **\<segurança >** elemento com o **modo** atributo (**< modo de segurança =** `MessageOrTransport` **>** onde `MessageOrTransport` é definido como um dos modos de segurança.  
  
4. Localize o elemento filho que corresponde ao valor do modo. Por exemplo, se o modo é definido como **mensagem**, localize o  **\<mensagem >** elemento contido no  **\<segurança >** elemento.  
  
5. Observe o valor atribuído a **clientCredentialType** atributo. O valor real depende de qual modo é usado, transporte ou mensagens.  
  
 O código XML a seguir mostra a configuração de um cliente usando a segurança de mensagem e que exigem um certificado autenticar o cliente.  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows" proxyCredentialType="None"  
        realm="" />  
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"  
    algorithmSuite="Default" establishSecurityContext="true" />  
</security>  
```  
  
## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a>Exemplo: Modo de transporte TCP com o certificado como credencial de cliente  
 Este exemplo define o modo de segurança para o modo de transporte e define o valor de credencial de cliente para um certificado X.509. Os procedimentos a seguir demonstram como definir o valor de credencial de cliente no cliente no código e a configuração. Isso pressupõe que você tenha usado o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para retornar os metadados (código e configuração) do serviço. Para obter mais informações, confira [Como: Criar um cliente](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a>Para especificar o valor de credencial de cliente no cliente no código  
  
1. Use o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar o código e a configuração do serviço.  
  
2. Crie uma instância do cliente WCF usando o código gerado.  
  
3. Na classe de cliente, defina as <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> propriedade do <xref:System.ServiceModel.ClientBase%601> classe para um valor apropriado. Este exemplo define a propriedade como um certificado X.509 usando o <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> método da <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> classe.  
  
     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]  
  
     Você pode usar qualquer uma das enumerações do <xref:System.Security.Cryptography.X509Certificates.X509FindType> classe. O nome da entidade é usado aqui, caso o certificado é alterado (devido a uma data de expiração). Usar o nome da entidade permite que a infraestrutura encontrar o certificado novamente.  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a>Para especificar o valor de credencial de cliente no cliente em configuração  
  
1. Adicionar um [ \<comportamento >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elemento para o [ \<comportamentos >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento.  
  
2. Adicionar um [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elemento para o [ \<comportamentos >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento. Certifique-se de definir o necessária `name` de atributo para um valor apropriado.  
  
3. Adicionar um [ \<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) elemento para o [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elemento.  
  
4. Defina os seguintes atributos para os valores apropriados: `storeLocation`, `storeName`, `x509FindType`, e `findValue`, conforme mostrado no código a seguir. Para obter mais informações sobre certificados, consulte [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md) (Trabalhando com certificados).  
  
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
  
5. Ao configurar o cliente, especifique o comportamento, definindo a `behaviorConfiguration` atributo do `<endpoint>` elemento, conforme mostrado no código a seguir. O elemento de ponto de extremidade é um filho de [ \<cliente >](../../../docs/framework/configure-apps/file-schema/wcf/client.md) elemento. Além disso, especifique o nome da configuração de associação, definindo o `bindingConfiguration` de atributo para a associação para o cliente. Se você estiver usando um arquivo de configuração gerado, o nome da associação é gerado automaticamente. Neste exemplo, o nome é `"tcpBindingWithCredential"`.  
  
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
- [Programação de segurança do WCF](../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [Selecionando um tipo de credencial](../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [Ferramenta Utilitário de Metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Trabalhando com certificados](../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Como: Criar um cliente](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [\<netTcpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)
- [\<segurança >](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [\<message>](../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [\<behavior>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [\<comportamentos >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
- [\<clientCertificate>](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [\<clientCredentials>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)

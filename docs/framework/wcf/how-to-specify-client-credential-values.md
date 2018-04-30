---
title: Como especificar valores de credenciais de cliente
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 856d33f88b55c35927998b15acc7bbf8ff1e9fe2
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-specify-client-credential-values"></a>Como especificar valores de credenciais de cliente
Usando [!INCLUDE[indigo1](../../../includes/indigo1-md.md)], o serviço pode especificar como um cliente é autenticado para o serviço. Por exemplo, um serviço pode estipular que o cliente seja autenticado com um certificado.  
  
### <a name="to-determine-the-client-credential-type"></a>Para determinar o tipo de credencial de cliente  
  
1.  Recupere metadados do ponto de extremidade de metadados do serviço. Os metadados normalmente consistem em dois arquivos: o código do cliente na linguagem de programação de sua escolha (o padrão é o Visual C#) e um arquivo de configuração XML. Uma maneira de recuperar metadados é usar a ferramenta Svcutil.exe para retornar o código do cliente e a configuração do cliente. Para obter mais informações, consulte [recuperar metadados](../../../docs/framework/wcf/feature-details/retrieving-metadata.md) e [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
2.  Abra o arquivo de configuração XML. Se você usar a ferramenta Svcutil.exe, o nome padrão do arquivo é Output.  
  
3.  Localizar o  **\<segurança >** elemento com o **modo** atributo (**< modo de segurança =** `MessageOrTransport` **>** onde `MessageOrTransport` é definido como um dos modos de segurança.  
  
4.  Localize o elemento filho que corresponde ao valor do modo. Por exemplo, se o modo é definido como **mensagem**, localize o  **\<mensagem >** elemento contido no  **\<segurança >** elemento.  
  
5.  Observe o valor atribuído a **clientCredentialType** atributo. O valor real depende de qual modo for usado, transporte ou mensagem.  
  
 O código XML a seguir mostra a configuração de um cliente usando a segurança de mensagem e que exigem um certificado autenticar o cliente.  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows" proxyCredentialType="None"  
        realm="" />  
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"  
    algorithmSuite="Default" establishSecurityContext="true" />  
</security>  
```  
  
## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a>Exemplo: O modo de transporte TCP com certificado como credenciais de cliente  
 Este exemplo define o modo de segurança para o modo de transporte e define o valor de credencial de cliente a um certificado x. 509. Os procedimentos a seguir demonstram como definir o valor de credencial de cliente no código e configuração do cliente. Isso pressupõe que você usou o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para retornar os metadados (código e configuração) do serviço. Para obter mais informações, consulte [como: criar um cliente](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a>Para especificar o valor de credencial de cliente no código do cliente  
  
1.  Use o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar o código e configuração do serviço.  
  
2.  Criar uma instância do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] cliente usando o código gerado.  
  
3.  Na classe de cliente, defina o <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> propriedade o <xref:System.ServiceModel.ClientBase%601> classe para um valor apropriado. Este exemplo define a propriedade como um certificado x. 509 usando o <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> método o <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> classe.  
  
     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]  
  
     Você pode usar qualquer uma das enumerações do <xref:System.Security.Cryptography.X509Certificates.X509FindType> classe. O nome da entidade é usado aqui, caso o certificado é alterado (devido a uma data de expiração). Usando o nome de entidade permite que a infraestrutura para encontrar o certificado novamente.  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a>Para especificar o valor de credencial de cliente no cliente de configuração  
  
1.  Adicionar um [ \<comportamento >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elemento para o [ \<comportamentos >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento.  
  
2.  Adicionar um [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elemento para o [ \<comportamentos >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento. Certifique-se de definir necessários `name` de atributo para um valor apropriado.  
  
3.  Adicionar um [ \<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) elemento para o [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elemento.  
  
4.  Defina os seguintes atributos com valores apropriados: `storeLocation`, `storeName`, `x509FindType`, e `findValue`, conforme mostrado no código a seguir. Para obter mais informações sobre certificados, consulte [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md) (Trabalhando com certificados).  
  
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
  
5.  Ao configurar o cliente, especifique o comportamento definindo o `behaviorConfiguration` atributo o `<endpoint>` elemento, conforme mostrado no código a seguir. O elemento de ponto de extremidade é um filho de [ \<cliente >](../../../docs/framework/configure-apps/file-schema/wcf/client.md) elemento. Além disso, especifique o nome da configuração de associação, definindo o `bindingConfiguration` de atributo para a associação para o cliente. Se você estiver usando um arquivo de configuração gerado, o nome da associação é gerado automaticamente. Neste exemplo, o nome é `"tcpBindingWithCredential"`.  
  
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
 <xref:System.ServiceModel.NetTcpBinding>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>  
 <xref:System.ServiceModel.ClientBase%601>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>  
 [Programação de segurança do WCF](../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 [Selecionando um tipo de credencial](../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Trabalhando com certificados](../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Como criar um cliente](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [\<netTcpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)  
 [\<security>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)  
 [\<message>](../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)  
 [\<comportamento >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)  
 [\<comportamentos >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
 [\<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)  
 [\<clientCredentials>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)

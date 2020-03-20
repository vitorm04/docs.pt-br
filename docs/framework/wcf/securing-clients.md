---
title: Protegendo clientes
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], security considerations
ms.assetid: 44c8578c-9a5b-4acd-8168-1c30a027c4c5
ms.openlocfilehash: bfb980e629ffb8f8543937a1850430c9bf6e9199
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183128"
---
# <a name="securing-clients"></a>Protegendo clientes
Na Windows Communication Foundation (WCF), o serviço dita os requisitos de segurança para os clientes. Ou seja, o serviço especifica qual modo de segurança usar e se o cliente deve ou não fornecer uma credencial. O processo de segurança de um cliente, portanto, é simples: use os metadados obtidos do serviço (se for publicado) e construa um cliente. Os metadados especificam como configurar o cliente. Se o serviço exigir que o cliente forneça uma credencial, então você deve obter uma credencial que se encaixe no requisito. Este tópico discute o processo com mais detalhes. Para obter mais informações sobre a criação de um serviço seguro, consulte [Protegendo serviços](securing-services.md).  
  
## <a name="the-service-specifies-security"></a>O serviço especifica a segurança  
 Por padrão, as vinculações wcf têm recursos de segurança ativados. (A exceção <xref:System.ServiceModel.BasicHttpBinding>é o .) Portanto, se o serviço foi criado usando o WCF, há uma maior chance de que ele implemente segurança para garantir autenticação, confidencialidade e integridade. Nesse caso, os metadados que o serviço fornece indicarão o que é necessário para estabelecer um canal de comunicação seguro. Se os metadados de serviço não incluirem quaisquer requisitos de segurança, não há como impor um esquema de segurança, como o Secure Sockets Layer (SSL) sobre HTTP, em um serviço. Se, no entanto, o serviço exigir que o cliente forneça uma credencial, então o desenvolvedor, implantador ou administrador cliente deve fornecer a credencial real que o cliente usará para autenticar-se ao serviço.  
  
## <a name="obtaining-metadata"></a>Obtenção de metadados  
 Ao criar um cliente, o primeiro passo é obter os metadados para o serviço com o que o cliente irá se comunicar. Isso pode ser feito de duas maneiras. Primeiro, se o serviço publicar um ponto final de troca de metadados (MEX) ou disponibilizar seus metadados em HTTP ou HTTPS, você poderá baixar os metadados usando a [ServiceModel Metadata Utility Tool (Svcutil.exe),](servicemodel-metadata-utility-tool-svcutil-exe.md)que gera tanto arquivos de código para um cliente quanto um arquivo de configuração. (Para obter mais informações sobre o uso da ferramenta, consulte [Acessando serviços usando um cliente WCF](accessing-services-using-a-wcf-client.md).) Se o serviço não publicar um ponto final do MEX e também não disponibilizar seus metadados via HTTP ou HTTPS, você deve entrar em contato com o criador do serviço para obter documentação que descreva os requisitos de segurança e os metadados.  
  
> [!IMPORTANT]
> Recomenda-se que os metadados venham de uma fonte confiável e que não sejam adulterados. Os metadados recuperados usando o protocolo HTTP são enviados em texto não criptografado e podem ser adulterados. Se o serviço <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> usar as propriedades e, use a URL que o criador do serviço forneceu para baixar os dados usando o protocolo HTTPS.  
  
## <a name="validating-security"></a>Validação de segurança  
 As fontes de metadados podem ser divididas em duas categorias amplas: fontes de confiança e fontes não confiáveis. Se você confiar em uma fonte e tiver baixado o código do cliente e outros metadados do ponto final MEX seguro dessa fonte, então você pode construir o cliente, fornecê-lo com as credenciais certas e executá-lo sem outras preocupações.  
  
 No entanto, se você optar por baixar um cliente e metadados de uma fonte que você conhece pouco, certifique-se de validar as medidas de segurança que o código usa. Por exemplo, você não deve simplesmente criar um cliente que envie suas informações pessoais ou financeiras para um serviço, a menos que o serviço exija confidencialidade e integridade (no mínimo). Você deve confiar no proprietário do serviço na medida em que você está disposto a divulgar tais informações, porque tais informações serão visíveis para eles.  
  
 Como regra geral, portanto, ao usar códigos e metadados de uma fonte não confiável, verifique o código e os metadados para garantir que ele atenda ao nível de segurança que você precisa.  
  
## <a name="setting-a-client-credential"></a>Configuração de uma credencial do cliente  
 Definir uma credencial de cliente em um cliente consiste em duas etapas:  
  
1. Determine o *tipo de credencial* do cliente que o serviço requer. Isso é feito por um dos dois métodos. Primeiro, se você tiver documentação do criador do serviço, ele deve especificar o tipo de credencial do cliente (se houver) que o serviço requer. Em segundo lugar, se você tiver apenas um arquivo de configuração gerado pela ferramenta Svcutil.exe, você pode examinar as vinculações individuais para determinar qual tipo de credencial é necessário.  
  
2. Especifique uma credencial real do cliente. A credencial real do cliente é chamada de *valor de credencial* do cliente para distingui-lo do tipo. Por exemplo, se o tipo de credencial do cliente especificar um certificado, você deve fornecer um certificado X.509 que é emitido por uma autoridade de certificação que o serviço confia.  
  
### <a name="determining-the-client-credential-type"></a>Determinando o tipo de credencial do cliente  
 Se você tiver o arquivo de configuração gerado pela ferramenta Svcutil.exe, examine as [ \<vinculações>](../configure-apps/file-schema/wcf/bindings.md) seção para determinar qual tipo de credencial do cliente é necessário. Dentro da seção estão elementos de vinculação que especificam os requisitos de segurança. Especificamente, examine \<a segurança> Elemento de cada vinculação. Esse elemento inclui `mode` o atributo, que você pode`Message`definir `Transport`para `TransportWithMessageCredential`um dos três valores possíveis ( , ou ). O valor do atributo determina o modo, e o modo determina qual dos elementos da criança é significativo.  
  
 O `<security>` elemento pode `<transport>` conter `<message>` um ou elemento, ou ambos. O elemento significativo é aquele que corresponde ao modo de segurança. Por exemplo, o código a seguir `"Message"`especifica que o modo de `<message>` segurança `"Certificate"`é , e o tipo de credencial do cliente para o elemento é . Neste caso, `<transport>` o elemento pode ser ignorado. No entanto, o `<message>` elemento especifica que um certificado X.509 deve ser fornecido.  

```xml  
<wsHttpBinding>  
    <binding name="WSHttpBinding_ICalculator">  
       <security mode="Message">  
           <transport clientCredentialType="Windows"
                      realm="" />  
           <message clientCredentialType="Certificate"
                    negotiateServiceCredential="true"  
                    algorithmSuite="Default"
                    establishSecurityContext="true" />  
       </security>  
    </binding>  
</wsHttpBinding>  
```  

 Observe que `clientCredentialType` se o `"Windows"`atributo estiver definido como , como mostrado no exemplo a seguir, você não precisa fornecer um valor de credencial real. Isso porque a segurança integrada do Windows fornece a credencial real (um token Kerberos) da pessoa que está executando o cliente.  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows "
        realm="" />  
</security>  
```  
  
### <a name="setting-the-client-credential-value"></a>Definindo o valor de credencial do cliente  
 Se for determinado que o cliente deve fornecer uma credencial, use o método apropriado para configurar o cliente. Por exemplo, para definir um <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> certificado de cliente, use o método.  
  
 Uma forma comum de credencial é o certificado X.509. Você pode fornecer a credencial de duas maneiras:  
  
- Programando-o no código do `SetCertificate` cliente (usando o método).  
  
 Adicionando [ \<](../configure-apps/file-schema/wcf/behaviors.md) uma seção de comportamentos>do arquivo `clientCredentials` de configuração para o cliente e usando o elemento (mostrado abaixo).  
  
#### <a name="setting-a-clientcredentials-value-in-code"></a>Definindo \<um clienteCredenciais> Valor em Código  
 Para definir um <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> <xref:System.ServiceModel.ClientBase%601> [ \<clienteCredenciais>](../configure-apps/file-schema/wcf/clientcredentials.md) valor em código, você deve acessar a propriedade da classe. A propriedade <xref:System.ServiceModel.Description.ClientCredentials> retorna um objeto que permite o acesso a vários tipos de credenciais, conforme mostrado na tabela a seguir.  
  
|Propriedade ClientCredential|Descrição|Observações|  
|-------------------------------|-----------------|-----------|  
|<xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>|Retorna um<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>|Representa um certificado X.509 fornecido pelo cliente para autenticar-se ao serviço.|  
|<xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>|Retorna um<xref:System.ServiceModel.Security.HttpDigestClientCredential>|Representa uma credencial http digest. A credencial é um hash do nome de usuário e senha.|  
|<xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>|Retorna um<xref:System.ServiceModel.Security.IssuedTokenClientCredential>|Representa um token de segurança personalizado emitido por um Serviço de Token de Segurança, comumente usado em cenários de federação.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>|Retorna um <xref:System.ServiceModel.Security.PeerCredential>|Representa uma credencial peer para participação em uma malha Peer em um domínio do Windows.|  
|<xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>|Retorna um<xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>|Representa um certificado X.509 fornecido pelo serviço em uma negociação fora da banda.|  
|<xref:System.ServiceModel.Description.ClientCredentials.UserName%2A>|Retorna um <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>|Representa um par de nome de usuário e senha.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>|Retorna um <xref:System.ServiceModel.Security.WindowsClientCredential>|Representa uma credencial de cliente do Windows (uma credencial Kerberos). As propriedades da classe são somente leitura.|  
  
#### <a name="setting-a-clientcredentials-value-in-configuration"></a>Definindo \<um valor de>> de clientes na configuração  
 Os valores de credencial são especificados usando um [ \<](../configure-apps/file-schema/wcf/clientcredentials.md) comportamento de ponto final como elementos filho do elemento clientAs>. O elemento utilizado depende do tipo de credencial do cliente. Por exemplo, o exemplo a seguir mostra a configuração para definir um certificado X.509 usando o [ \<>de certificado de cliente ](../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)<.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>
        <behavior name="myEndpointBehavior">  
          <clientCredentials>  
            <clientCertificate findvalue="myMachineName"
            storeLocation="Current" X509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>
      </endpointBehaviors>
    </behaviors>
  </system.serviceModel>  
</configuration>  
```  
  
 Para definir a credencial do cliente na configuração, adicione um [ \<elemento de>de endpointBehaviors](../configure-apps/file-schema/wcf/endpointbehaviors.md) ao arquivo de configuração. Além disso, o elemento de comportamento adicionado deve ser `behaviorConfiguration` vinculado ao ponto final do serviço usando o atributo [ \< \<](../configure-apps/file-schema/wcf/endpoint-of-client.md) do ponto final> do elemento>cliente, conforme mostrado no exemplo a seguir. O valor `behaviorConfiguration` do atributo deve corresponder `name` ao valor do atributo de comportamento.  

```xml
<configuration>
  <system.serviceModel>
    <client>
      <endpoint address="http://localhost/servicemodelsamples/service.svc"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                behaviorConfiguration="myEndpointBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </client>
  </system.serviceModel>
</configuration>
```
  
> [!NOTE]
> Alguns dos valores de credencial do cliente não podem ser definidos usando arquivos de configuração de aplicativos, por exemplo, nome de usuário e senha, ou valores de usuário e senha do Windows. Tais valores de credencial podem ser especificados apenas em código.  
  
 Para obter mais informações sobre como definir a credencial do cliente, consulte [Como: Especificar valores de credencial do cliente](how-to-specify-client-credential-values.md).  
  
> [!NOTE]
> `ClientCredentialType`é ignorado `SecurityMode` quando é `"TransportWithMessageCredential",` definido como mostrado na configuração de amostra a seguir.  
  
```xml  
<wsHttpBinding>  
    <binding name="PingBinding">  
        <security mode="TransportWithMessageCredential"  >  
           <message  clientCredentialType="UserName"
               establishSecurityContext="false"
               negotiateServiceCredential="false" />  
           <transport clientCredentialType="Certificate"  />  
         </security>  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [\<vinculações>](../configure-apps/file-schema/wcf/bindings.md)
- [Ferramenta Editor de configuração (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md)
- [Protegendo serviços](securing-services.md)
- [Usando um cliente do WCF para acessar serviços](accessing-services-using-a-wcf-client.md)
- [Como especificar valores de credenciais do cliente](how-to-specify-client-credential-values.md)
- [Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Como especificar o tipo de credencial do cliente](how-to-specify-the-client-credential-type.md)

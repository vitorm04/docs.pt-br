---
title: 'Como: configurar credenciais em um serviço de federação'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 149ab165-0ef3-490a-83a9-4322a07bd98a
ms.openlocfilehash: 33df685b4d14130ae00d59012706b7637924c9be
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295426"
---
# <a name="how-to-configure-credentials-on-a-federation-service"></a>Como: configurar credenciais em um serviço de federação
No Windows Communication Foundation (WCF), criar um serviço federado consiste dos seguintes procedimentos principais:  
  
1. Configurando um <xref:System.ServiceModel.WSFederationHttpBinding> ou associação personalizada semelhante. Para obter mais informações sobre como criar uma associação apropriada, consulte [como: Criar um WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).  
  
2. Configurando o <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> que controla os tokens emitidos como apresentados ao serviço são autenticados.  
  
 Este tópico fornece detalhes sobre a segunda etapa. Para obter mais informações sobre o funcionamento de um serviço federado, consulte [federação](../../../../docs/framework/wcf/feature-details/federation.md).  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-code"></a>Para definir as propriedades de IssuedTokenServiceCredential no código  
  
1. Use o <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A> propriedade do <xref:System.ServiceModel.Description.ServiceCredentials> classe para retornar uma referência a um <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> instância. A propriedade é acessada a partir de <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> propriedade do <xref:System.ServiceModel.ServiceHostBase> classe.  
  
2. Defina as <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> propriedade para `true` se emitido por conta própria, como os tokens [!INCLUDE[infocard](../../../../includes/infocard-md.md)] cartões são autenticados. O padrão é `false`.  
  
3. Preencher a coleção retornada pela <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> propriedade com instâncias da <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> classe. Cada instância representa um emissor do qual o serviço autenticará tokens.  
  
    > [!NOTE]
    >  Ao contrário da coleção do lado do cliente retornada pelo <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> propriedade, a coleção de certificados conhecidos não é uma coleção com chave. O serviço aceita os tokens que os certificados especificados emitem, independentemente do endereço do cliente que enviou a mensagem que contém o token emitido (sujeito às restrições adicionais, que são descritas posteriormente neste tópico).  
  
4. Defina as <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> propriedade para um do <xref:System.ServiceModel.Security.X509CertificateValidationMode> valores de enumeração. Isso pode ser feito apenas em código. O padrão é <xref:System.IdentityModel.Selectors.X509CertificateValidator.ChainTrust%2A>.  
  
5. Se o <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> estiver definida como <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>, em seguida, atribuir uma instância de custom <xref:System.IdentityModel.Selectors.X509CertificateValidator> de classe para o <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> propriedade.  
  
6. Se o <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> é definido como `ChainTrust` ou `PeerOrChainTrust`, defina as <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.RevocationMode%2A> propriedade com um valor apropriado do <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> enumeração. Observe que o modo de revogação não é usado na `PeerTrust` ou `Custom` modos de validação.  
  
7. Se necessário, atribua uma instância de um personalizado <xref:System.IdentityModel.Tokens.SamlSerializer> de classe para o <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.SamlSerializer%2A> propriedade. Um serializador personalizado de asserções marcação linguagem SAML (Security) é necessária, por exemplo, para analisar as declarações de SAML personalizadas.  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-configuration"></a>Para definir as propriedades de IssuedTokenServiceCredential na configuração  
  
1. Criar uma `<issuedTokenAuthentication>` elemento como um filho de um <`serviceCredentials`> elemento.  
  
2. Defina a `allowUntrustedRsaIssuers` atributo do `<issuedTokenAuthentication>` elemento a ser `true` se autenticando um token emitido por conta própria, como um [!INCLUDE[infocard](../../../../includes/infocard-md.md)] cartão.  
  
3. Criar uma `<knownCertificates>` elemento como um filho de `<issuedTokenAuthentication>` elemento.  
  
4. Criar do zero ou mais `<add>` elementos como filhos a `<knownCertificates>` elemento e especifique como localizar o certificado usando o `storeLocation`, `storeName`, `x509FindType`, e `findValue` atributos.  
  
5. Se necessário, defina as `samlSerializer` atributo da <`issuedTokenAuthentication`> elemento para o nome do tipo personalizado <xref:System.IdentityModel.Tokens.SamlSerializer> classe.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define as propriedades de um <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> no código.  
  
 [!code-csharp[C_FederatedService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedservice/cs/source.cs#2)]
 [!code-vb[C_FederatedService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedservice/vb/source.vb#2)]  
  
 Para um serviço federado autenticar um cliente que, a seguir deve ser verdadeiras sobre o token emitido:  
  
-   Quando a assinatura do token emitido usa um identificador de chave de segurança RSA, os <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> propriedade deve ser `true`.  
  
-   Quando a assinatura do token emitido usa um número de série do emissor de x. 509, o identificador de chave de assunto de x. 509 ou o identificador de segurança de impressão digital X.509, o token emitido deve ser assinado por um certificado na coleção retornada pelo <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> propriedade do <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>classe.  
  
-   Quando o token emitido é assinado usando um certificado X.509, o certificado deve validar pela semântica especificada pelo valor da <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> propriedade, independentemente se o certificado foi enviado para a terceira parte confiável como um <xref:System.IdentityModel.Tokens.X509RawDataKeyIdentifierClause> ou foi obtido do <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> propriedade. Para obter mais informações sobre validação de certificado X.509, consulte [trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 Por exemplo, definindo a <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> para <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerTrust> seria autenticar qualquer token emitido cujo certificado de autenticação está no `TrustedPeople` repositório de certificados. Nesse caso, defina as <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.TrustedStoreLocation%2A> propriedade para um <xref:System.Security.Cryptography.X509Certificates.StoreLocation.CurrentUser> ou <xref:System.Security.Cryptography.X509Certificates.StoreLocation.LocalMachine>. Você pode selecionar outros modos, incluindo <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>. Quando `Custom` é selecionado, você deve atribuir uma instância das <xref:System.IdentityModel.Selectors.X509CertificateValidator> de classe para o <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CustomCertificateValidator%2A> propriedade. O validador personalizado pode validar certificados usando qualquer critério, que ele gosta. Para obter mais informações, confira [Como: Criar um serviço que utiliza um validador de certificado personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
## <a name="see-also"></a>Consulte também

- [Federação](../../../../docs/framework/wcf/feature-details/federation.md)
- [Federação e confiabilidade](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)
- [Exemplo de federação](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Como: Desabilitar sessões seguras em um WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Como: Criar um WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [Como: Criar um cliente federado](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Modos de autenticação de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)

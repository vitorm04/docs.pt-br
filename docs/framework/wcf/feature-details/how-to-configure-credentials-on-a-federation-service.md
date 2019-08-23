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
ms.openlocfilehash: 792d2f1b113c0743bd91ccf2f7ff894d7f7d319f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912193"
---
# <a name="how-to-configure-credentials-on-a-federation-service"></a>Como: configurar credenciais em um serviço de federação
No Windows Communication Foundation (WCF), a criação de um serviço federado consiste nos seguintes procedimentos principais:  
  
1. Configurando uma <xref:System.ServiceModel.WSFederationHttpBinding> associação personalizada ou semelhante. Para obter mais informações sobre como criar uma associação apropriada [, consulte Como: Crie um WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).  
  
2. Configurar o <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> que controla como os tokens emitidos apresentados ao serviço são autenticados.  
  
 Este tópico fornece detalhes sobre a segunda etapa. Para obter mais informações sobre como um serviço federado funciona, consulte [Federação](../../../../docs/framework/wcf/feature-details/federation.md).  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-code"></a>Para definir as propriedades de IssuedTokenServiceCredential no código  
  
1. Use a <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A> propriedade <xref:System.ServiceModel.Description.ServiceCredentials> da classe para retornar uma referência a uma <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> instância. A propriedade é acessada <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> da propriedade <xref:System.ServiceModel.ServiceHostBase> da classe.  
  
2. Defina a <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> Propriedade como `true` se os tokens emitidos por conta própria, como os cartões do CardSpace, forem autenticados. O padrão é `false`.  
  
3. Preencha a coleção retornada pela <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> Propriedade com instâncias <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> da classe. Cada instância representa um emissor do qual o serviço irá autenticar tokens.  
  
    > [!NOTE]
    > Ao contrário da coleção do lado do cliente retornada <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> pela propriedade, a coleção de certificados conhecida não é uma coleção com chave. O serviço aceita os tokens que os certificados especificados emitem independentemente do endereço do cliente que enviou a mensagem que contém o token emitido (sujeito às restrições adicionais, que são descritas posteriormente neste tópico).  
  
4. Defina a <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> Propriedade como um <xref:System.ServiceModel.Security.X509CertificateValidationMode> dos valores de enumeração. Isso pode ser feito apenas no código. O padrão é <xref:System.IdentityModel.Selectors.X509CertificateValidator.ChainTrust%2A>.  
  
5. Se a <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> propriedade for definida como <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>, atribua uma instância da classe personalizada <xref:System.IdentityModel.Selectors.X509CertificateValidator> à <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> propriedade.  
  
6. Se o <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> for definido como `ChainTrust` ou `PeerOrChainTrust`, <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.RevocationMode%2A> defina<xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> a propriedade como um valor apropriado da enumeração. Observe que o modo de revogação não é usado `PeerTrust` nos `Custom` modos de validação ou.  
  
7. Se necessário, atribua uma instância de uma classe <xref:System.IdentityModel.Tokens.SamlSerializer> personalizada <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.SamlSerializer%2A> à propriedade. Um serializador SAML (Security Asserties Markup Language) personalizado é necessário, por exemplo, para analisar declarações SAML personalizadas.  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-configuration"></a>Para definir as propriedades de IssuedTokenServiceCredential na configuração  
  
1. Crie um `<issuedTokenAuthentication>` elemento como um filho de um elemento`serviceCredentials`< >.  
  
2. Defina o `allowUntrustedRsaIssuers` atributo `<issuedTokenAuthentication>` do elemento como `true` se estiver autenticando um token emitido por conta própria, como um cartão do CardSpace.  
  
3. Crie um `<knownCertificates>` elemento como um filho `<issuedTokenAuthentication>` do elemento.  
  
4. Crie zero ou mais `<add>` elementos como filhos `<knownCertificates>` do elemento e especifique como localizar o certificado usando `findValue` os `storeLocation`atributos, `storeName`, `x509FindType`e.  
  
5. Se necessário, defina o `samlSerializer` atributo do elemento <`issuedTokenAuthentication`> como o nome do tipo da classe personalizada <xref:System.IdentityModel.Tokens.SamlSerializer> .  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define as propriedades de <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> um no código.  
  
 [!code-csharp[C_FederatedService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedservice/cs/source.cs#2)]
 [!code-vb[C_FederatedService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedservice/vb/source.vb#2)]  
  
 Para que um serviço federado autentique um cliente, o seguinte deve ser verdadeiro sobre o token emitido:  
  
- Quando a assinatura digital do token emitido usa um identificador de chave de segurança RSA <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> , a propriedade `true`deve ser.  
  
- Quando a assinatura do token emitido usa um número de série do emissor x. 509, x. 509 identificador de chave de entidade ou o identificador de segurança de impressão digital x. 509, o token emitido deve ser assinado por um certificado <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> na coleção retornada pela propriedade do <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>classe.  
  
- Quando o token emitido é assinado usando um certificado X. 509, o certificado deve validar de acordo com a semântica especificada pelo valor da <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> Propriedade, independentemente de o certificado ter sido enviado à terceira parte confiável como uma <xref:System.IdentityModel.Tokens.X509RawDataKeyIdentifierClause> ou foi obtido <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> da propriedade. Para obter mais informações sobre a validação de certificado X. 509, consulte [trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 Por exemplo, a configuração <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> de <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerTrust> para autenticará qualquer token emitido cujo certificado de autenticação esteja `TrustedPeople` no repositório de certificados. Nesse caso, defina a <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.TrustedStoreLocation%2A> propriedade <xref:System.Security.Cryptography.X509Certificates.StoreLocation.CurrentUser> como ou <xref:System.Security.Cryptography.X509Certificates.StoreLocation.LocalMachine>. Você pode selecionar outros modos, incluindo <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>. Quando `Custom` é selecionado, você deve atribuir uma instância <xref:System.IdentityModel.Selectors.X509CertificateValidator> da classe à <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CustomCertificateValidator%2A> propriedade. O validador personalizado pode validar certificados usando qualquer critério que ele goste. Para obter mais informações, confira [Como: Crie um serviço que empregue um validador](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)de certificado personalizado.  
  
## <a name="see-also"></a>Consulte também

- [Federação](../../../../docs/framework/wcf/feature-details/federation.md)
- [Federação e confiabilidade](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)
- [Exemplo de federação](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Como: Desabilitar sessões seguras em um WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Como: Criar um WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [Como: Criar um cliente federado](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Modos de autenticação de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)

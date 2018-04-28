---
title: Como configurar credenciais em um serviço de federação
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
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 149ab165-0ef3-490a-83a9-4322a07bd98a
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ffb33ea70f67e209648e470656a2719404dd7f2d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-configure-credentials-on-a-federation-service"></a>Como configurar credenciais em um serviço de federação
Em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], criar um serviço federado consiste nos seguintes procedimentos principais:  
  
1.  Configurando um <xref:System.ServiceModel.WSFederationHttpBinding> ou associação personalizada semelhante. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] criar uma associação apropriado, consulte [como: criar uma WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).  
  
2.  Configurando o <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> que controla os tokens emitidos como apresentados para o serviço são autenticados.  
  
 Este tópico fornece detalhes sobre a segunda etapa. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] como funciona um serviço federado, consulte [federação](../../../../docs/framework/wcf/feature-details/federation.md).  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-code"></a>Para definir as propriedades de IssuedTokenServiceCredential no código  
  
1.  Use o <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A> propriedade o <xref:System.ServiceModel.Description.ServiceCredentials> classe para retornar uma referência a um <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> instância. A propriedade for acessada do <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> propriedade o <xref:System.ServiceModel.ServiceHostBase> classe.  
  
2.  Definir o <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> propriedade `true` se emitido por conta própria tokens como [!INCLUDE[infocard](../../../../includes/infocard-md.md)] cartões devem ser autenticadas. O padrão é `false`.  
  
3.  Preencher a coleção retornada pelo <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> propriedade com instâncias da <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> classe. Cada instância representa um emissor do qual o serviço autenticará tokens.  
  
    > [!NOTE]
    >  Ao contrário do lado do cliente coleção retornada pelo <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> propriedade, a coleção de certificados conhecidos não é uma coleção com chave. O serviço aceita os tokens que emitem certificados especificados, independentemente do endereço do cliente que enviou a mensagem que contém o token emitido (sujeito às restrições adicionais, que são descritos posteriormente neste tópico).  
  
4.  Definir o <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> propriedade para um do <xref:System.ServiceModel.Security.X509CertificateValidationMode> valores de enumeração. Isso pode ser feito somente no código. O padrão é <xref:System.IdentityModel.Selectors.X509CertificateValidator.ChainTrust%2A>.  
  
5.  Se o <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> está definida como <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>, atribua uma instância personalizado <xref:System.IdentityModel.Selectors.X509CertificateValidator> de classe para o <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> propriedade.  
  
6.  Se o <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> é definido como `ChainTrust` ou `PeerOrChainTrust`, defina o <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.RevocationMode%2A> propriedade para um valor apropriado do <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> enumeração. Observe que o modo de revogação não é usado em `PeerTrust` ou `Custom` modos de validação.  
  
7.  Se necessário, atribuir uma instância de um personalizado <xref:System.IdentityModel.Tokens.SamlSerializer> de classe para o <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.SamlSerializer%2A> propriedade. Um serializador personalizado de segurança asserções Markup Language (SAML) é necessário, por exemplo, para analisar as asserções SAML personalizadas.  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-configuration"></a>Para definir as propriedades de IssuedTokenServiceCredential na configuração  
  
1.  Criar um `<issuedTokenAuthentication>` elemento como um filho de um <`serviceCredentials`> elemento.  
  
2.  Definir o `allowUntrustedRsaIssuers` atributo do `<issuedTokenAuthentication>` elemento `true` se autenticando um token emitido por conta própria, como um [!INCLUDE[infocard](../../../../includes/infocard-md.md)] cartão.  
  
3.  Criar um `<knownCertificates>` elemento como um filho de `<issuedTokenAuthentication>` elemento.  
  
4.  Criar do zero ou mais `<add>` elementos como filhos do `<knownCertificates>` elemento e especifique como localizar o certificado usando o `storeLocation`, `storeName`, `x509FindType`, e `findValue` atributos.  
  
5.  Se necessário, defina o `samlSerializer` atributo do <`issuedTokenAuthentication`> elemento para o nome do tipo personalizado <xref:System.IdentityModel.Tokens.SamlSerializer> classe.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define as propriedades de um <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> no código.  
  
 [!code-csharp[C_FederatedService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedservice/cs/source.cs#2)]
 [!code-vb[C_FederatedService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedservice/vb/source.vb#2)]  
  
 Para um serviço federado autenticar um cliente, o seguinte deve ser verdadeiro sobre o token emitido:  
  
-   Quando a assinatura digital do token emitido usa um identificador de chave de segurança RSA, a <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> propriedade deve ser `true`.  
  
-   Quando a assinatura do token emitido usa um identificador de segurança de impressão digital de x. 509, número de série do emissor de x. 509 ou identificador de chave de assunto x. 509, o token emitido deve ser assinado por um certificado na coleção retornada pelo <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> propriedade o <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>classe.  
  
-   Quando o token emitido é assinado usando um certificado x. 509, valide o certificado pela semântica especificada pelo valor da <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> propriedade, independentemente se o certificado foi enviado para a terceira parte confiável como um <xref:System.IdentityModel.Tokens.X509RawDataKeyIdentifierClause> ou foi obtido do <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> propriedade. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Validação de certificado x. 509, consulte [trabalhar com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 Por exemplo, se você definir o <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> para <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerTrust> autenticados qualquer token emitido cujo certificado de assinatura está no `TrustedPeople` repositório de certificados. Nesse caso, defina o <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.TrustedStoreLocation%2A> propriedade como <xref:System.Security.Cryptography.X509Certificates.StoreLocation.CurrentUser> ou <xref:System.Security.Cryptography.X509Certificates.StoreLocation.LocalMachine>. Você pode selecionar outros modos, incluindo <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>. Quando `Custom` é selecionada, você deve atribuir a uma instância do <xref:System.IdentityModel.Selectors.X509CertificateValidator> de classe para o <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CustomCertificateValidator%2A> propriedade. O validador personalizado pode validar certificados usando qualquer critério que desejar. Para obter mais informações, consulte [como: criar um serviço que utiliza um validador de certificado personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
## <a name="see-also"></a>Consulte também  
 [Federação](../../../../docs/framework/wcf/feature-details/federation.md)  
 [Federação e confiabilidade](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)  
 [Exemplo de federação](../../../../docs/framework/wcf/samples/federation-sample.md)  
 [Como: desabilitar sessões seguras em um WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 [Como criar um WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [Como criar um cliente federado](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Modos de autenticação de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)

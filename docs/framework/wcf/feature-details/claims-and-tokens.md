---
title: Declarações e tokens
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], and tokens
ms.assetid: eff167f3-33f8-483d-a950-aa3e9f97a189
ms.openlocfilehash: 223b86310d90c877df15a99c90a0a72ea780734a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784274"
---
# <a name="claims-and-tokens"></a>Declarações e tokens
Este tópico descreve os vários tipos de declaração que o Windows Communication Foundation (WCF) cria dos tokens padrão que ele dá suporte.  
  
 Você pode examinar as declarações de uma credencial de cliente usando o <xref:System.IdentityModel.Claims.ClaimSet> e <xref:System.IdentityModel.Claims.Claim> classes. O `ClaimSet` contém uma coleção de `Claim` objetos. Cada `Claim` tem os seguintes membros importantes:  
  
- O <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> propriedade retorna um identificador de URI (Uniform Resource) que especifica o tipo de declaração que estão sendo feita. Por exemplo, um tipo de declaração pode ser uma impressão digital de um certificado, nesse caso, o URI é `http://schemas.microsoft.com/ws/20005/05/identity/claims/thumprint`.  
  
- O <xref:System.IdentityModel.Claims.Claim.Right%2A> propriedade retorna um URI que especifica o direito da declaração. Direitos predefinidos são encontrados na <xref:System.IdentityModel.Claims.Rights> classe (<xref:System.IdentityModel.Claims.Rights.Identity%2A>, <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>).  
  
- O <xref:System.IdentityModel.Claims.Claim.Resource%2A> propriedade retorna o recurso associado à declaração.  
  
 Cada <xref:System.IdentityModel.Claims.ClaimSet> também tem um <xref:System.IdentityModel.Claims.ClaimSet.Issuer%2A> propriedade, que representa o <xref:System.IdentityModel.Claims.ClaimSet> da `Issuer`.  
  
## <a name="windows-accounts"></a>Contas do Windows  
 Em que uma credencial de cliente é mapeado para uma conta de usuário do Windows, resultante <xref:System.IdentityModel.Claims.ClaimSet> tem os seguintes valores:  
  
- O `Issuer` é o valor retornado pela propriedade estática de Windows do <xref:System.IdentityModel.Claims.ClaimSet> classe.  
  
- As declarações na coleção são:  
  
    - Um <xref:System.IdentityModel.Claims.Claim> com um <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> o valor de identificador de segurança (SID), um <xref:System.IdentityModel.Claims.Claim.Right%2A> valor da propriedade `Identity`e um <xref:System.IdentityModel.Claims.Claim.Resource%2A> que retorna o valor real de SID. Um SID é um valor exclusivo que o controlador de domínio emite a cada usuário. O SID é usado para identificar o usuário em interações com a segurança do Windows.  
  
    - Um <xref:System.IdentityModel.Claims.Claim> com um <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> valor do SID, um <xref:System.IdentityModel.Claims.Claim.Right%2A> de `PossessProperty`e um <xref:System.IdentityModel.Claims.Claim.Resource%2A> do valor do SID.  
  
    - Um <xref:System.IdentityModel.Claims.Claim> com um <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> dos <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, uma <xref:System.IdentityModel.Claims.Claim.Right%2A> de `PossessProperty` e um <xref:System.IdentityModel.Claims.Claim.Resource%2A> da cadeia de caracteres que contém o nome de usuário (por exemplo, "MYMACHINE\Bob").  
  
    - Declarações de SID adicional com <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> para vários grupos o usuário pertence.  
  
## <a name="certificates"></a>Certificados  
 Em que a credencial do cliente é um certificado resultante <xref:System.IdentityModel.Claims.ClaimSet> tem os seguintes valores:  
  
- Para certificados emitidos por conta própria, o `Issuer` é o <xref:System.IdentityModel.Claims.ClaimSet> em si. O <xref:System.IdentityModel.Claims.ClaimSet> retorna um <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> dos <xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A>, uma <xref:System.IdentityModel.Claims.Claim.Right%2A> de `Identity`e uma <xref:System.IdentityModel.Claims.Claim.Resource%2A> valor que é um <xref:System.Byte> matriz que contém a impressão digital do certificado.  
  
- Um certificado emitido por uma autoridade de certificação, o emissor é o `ClaimSet` que representa o certificado da autoridade de certificação.  
  
- O `Claims` na coleção incluem:  
  
    - Um `Claim` com um `ClaimType` da impressão digital, um `Right` de PossessProperty e um `Resource` que é uma matriz de bytes que contém a impressão digital do certificado  
  
    - Declarações de PossessProperty adicionais de vários tipos, incluindo X500DistinguishedName, Dns, nome, Upn e Rsa, representam várias propriedades do certificado. O recurso para a declaração Rsa é a chave pública associada ao certificado. **Observação** onde o tipo de credencial de cliente é um certificado que o serviço é mapeado para um Windows conta, dois `ClaimSet` objetos são gerados. O primeiro contém todas as declarações relacionadas à conta do Windows e o segundo contém todas as declarações relacionadas ao certificado.  
  
## <a name="user-namepassword"></a>Nome de usuário/senha  
 Em que a credencial do cliente é um nome e senha do usuário (ou equivalente) que não é mapeado para uma conta do Windows, resultante `ClaimSet` é emitida por estático <xref:System.IdentityModel.Claims.ClaimSet.System%2A> propriedade do `ClaimSet` classe. O `ClaimSet` contém uma `Identity` do tipo de declaração <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A> cujo recurso é o nome de usuário do cliente fornece. Uma declaração correspondente tem uma `Right` de `PossessProperty`.  
  
## <a name="rsa-keys"></a>RSA Keys  
 Em uma chave RSA não associada a um certificado é usada, resultante `ClaimSet` é emitido por conta própria e contém um `Identity` do tipo de declaração <xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A> cujo recurso é a chave RSA. Uma declaração correspondente tem uma `Right` de `PossessProperty`.  
  
## <a name="saml"></a>SAML  
 Em que o cliente autentica com um token de declarações marcação linguagem SAML (Security) resultante `ClaimSet` é emitida pela entidade que assinou o token SAML, geralmente o certificado do serviço de token de segurança (STS) que emitiu o token SAML. O `ClaimSet` contém várias declarações como encontrado no token SAML. Se o token SAML contém um `SamlSubject` com um não -`null` nome, então um `Identity` declaração com um tipo de <xref:System.IdentityModel.Claims.ClaimTypes.NameIdentifier%2A> e um tipo de recurso de <xref:System.IdentityModel.Tokens.SamlNameIdentifierClaimResource> são criados.  
  
## <a name="identity-claims-and-servicesecuritycontextisanonymous"></a>Declarações de identidade e ServiceSecurityContext.IsAnonymous  
 Se nenhum dos `ClaimSet` objetos resultantes de credenciais do cliente contêm uma declaração com um `Right` de `Identity,` o <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> propriedade retorna `true`. Se um ou mais essas declarações estão presentes, o `IsAnonymous` propriedade retorna `false`.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.IdentityModel.Claims.ClaimSet>
- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- [Gerenciando reivindicações e autorização com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)

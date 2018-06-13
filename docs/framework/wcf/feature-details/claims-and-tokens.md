---
title: Declarações e tokens
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], and tokens
ms.assetid: eff167f3-33f8-483d-a950-aa3e9f97a189
ms.openlocfilehash: 087deeef91367210db936f2976a3846d0279dcba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491849"
---
# <a name="claims-and-tokens"></a>Declarações e tokens
Este tópico descreve os vários tipos de declaração cria Windows Communication Foundation (WCF) dos tokens padrão que ele suporta.  
  
 Você pode examinar as declarações de uma credencial de cliente usando o <xref:System.IdentityModel.Claims.ClaimSet> e <xref:System.IdentityModel.Claims.Claim> classes. O `ClaimSet` contém uma coleção de `Claim` objetos. Cada `Claim` tem os seguintes membros importantes:  
  
-   O <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> propriedade retorna um identificador de recursos uniforme (URI) que especifica o tipo de declaração que estão sendo feita. Por exemplo, um tipo de declaração pode ser uma impressão digital de um certificado, em cujo caso o URI é http:schemas.microsoft.com/ws/20005/05/identity/claims/thumprint.  
  
-   O <xref:System.IdentityModel.Claims.Claim.Right%2A> propriedade retorna um URI que especifica à direita da declaração. Direitos predefinidos são encontrados no <xref:System.IdentityModel.Claims.Rights> classe (<xref:System.IdentityModel.Claims.Rights.Identity%2A>, <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>).  
  
-   O <xref:System.IdentityModel.Claims.Claim.Resource%2A> propriedade retorna o recurso associado à declaração.  
  
 Cada <xref:System.IdentityModel.Claims.ClaimSet> também tem um <xref:System.IdentityModel.Claims.ClaimSet.Issuer%2A> propriedade, que representa o <xref:System.IdentityModel.Claims.ClaimSet> do `Issuer`.  
  
## <a name="windows-accounts"></a>Contas do Windows  
 Em que uma credencial de cliente é mapeado para uma conta de usuário do Windows, o resultante <xref:System.IdentityModel.Claims.ClaimSet> tem os seguintes valores:  
  
-   O `Issuer` é o valor retornado pela propriedade Windows estática do <xref:System.IdentityModel.Claims.ClaimSet> classe.  
  
-   As declarações da coleção são:  
  
    -   Um <xref:System.IdentityModel.Claims.Claim> com um <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> valor de identificador de segurança (SID), um <xref:System.IdentityModel.Claims.Claim.Right%2A> valor da propriedade `Identity`e um <xref:System.IdentityModel.Claims.Claim.Resource%2A> que retorna o valor de SID real. Um SID é um valor exclusivo que emite o controlador de domínio para cada usuário. O SID é usado para identificar o usuário em interações com a segurança do Windows.  
  
    -   Um <xref:System.IdentityModel.Claims.Claim> com um <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> valor do SID, um <xref:System.IdentityModel.Claims.Claim.Right%2A> de `PossessProperty`e um <xref:System.IdentityModel.Claims.Claim.Resource%2A> do valor de SID.  
  
    -   Um <xref:System.IdentityModel.Claims.Claim> com um <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> de <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, um <xref:System.IdentityModel.Claims.Claim.Right%2A> de `PossessProperty` e um <xref:System.IdentityModel.Claims.Claim.Resource%2A> de cadeia de caracteres que contém o nome de usuário (por exemplo, "MYMACHINE\Bob").  
  
    -   Declarações de SID adicional com <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> para vários grupos o usuário pertence.  
  
## <a name="certificates"></a>Certificados  
 Em que a credencial do cliente é um certificado resultante <xref:System.IdentityModel.Claims.ClaimSet> tem os seguintes valores:  
  
-   Para certificados emitidos por conta própria, o `Issuer` é o <xref:System.IdentityModel.Claims.ClaimSet> em si. O <xref:System.IdentityModel.Claims.ClaimSet> retorna um <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> de <xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A>, um <xref:System.IdentityModel.Claims.Claim.Right%2A> de `Identity`e um <xref:System.IdentityModel.Claims.Claim.Resource%2A> valor que é um <xref:System.Byte> matriz que contém a impressão digital do certificado.  
  
-   Um certificado emitido por uma autoridade de certificação, o emissor é a `ClaimSet` que representa o certificado da autoridade de certificação.  
  
-   O `Claims` na coleção incluem:  
  
    -   Um `Claim` com um `ClaimType` de impressão digital, um `Right` de PossessProperty e um `Resource` que é uma matriz de bytes que contém a impressão digital do certificado  
  
    -   Declarações de PossessProperty adicionais de vários tipos, incluindo X500DistinguishedName, o Dns, o nome, o Upn e Rsa, representam várias propriedades do certificado. O recurso para a declaração de Rsa é a chave pública associada ao certificado. **Observação** onde o tipo de credencial de cliente é um certificado que o serviço é mapeado para uma janela de conta, dois `ClaimSet` objetos são gerados. O primeiro contém todas as declarações relacionadas à conta do Windows e o segundo contém todas as declarações relacionadas ao certificado.  
  
## <a name="user-namepassword"></a>Nome de usuário/senha  
 Em que a credencial do cliente é um nome e senha do usuário (ou equivalente) que não é mapeado para uma conta do Windows, o resultante `ClaimSet` emitido por estático <xref:System.IdentityModel.Claims.ClaimSet.System%2A> propriedade o `ClaimSet` classe. O `ClaimSet` contém um `Identity` de declaração de tipo <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A> fornece cujo recurso é o nome de usuário do cliente. Uma declaração correspondente tiver uma `Right` de `PossessProperty`.  
  
## <a name="rsa-keys"></a>Chaves RSA  
 Em uma chave RSA não associada a um certificado é usada, resultante `ClaimSet` é emitido por conta própria e contém um `Identity` do tipo de declaração <xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A> cujo recurso é a chave RSA. Uma declaração correspondente tiver uma `Right` de `PossessProperty`.  
  
## <a name="saml"></a>SAML  
 Em que o cliente se autentica com um token de segurança asserções Markup Language (SAML) resultante `ClaimSet` é emitida pela entidade que assinou o token SAML, geralmente o certificado de serviço de token de segurança (STS) que emitiu o token SAML. O `ClaimSet` contém várias declarações como encontrado no token SAML. Se o token SAML contiver um `SamlSubject` com não`null` nome, então um `Identity` de declaração com um tipo de <xref:System.IdentityModel.Claims.ClaimTypes.NameIdentifier%2A> e um tipo de recurso de <xref:System.IdentityModel.Tokens.SamlNameIdentifierClaimResource> são criados.  
  
## <a name="identity-claims-and-servicesecuritycontextisanonymous"></a>Declarações de identidade e ServiceSecurityContext.IsAnonymous  
 Se nenhuma a `ClaimSet` objetos resultantes das credenciais do cliente contém uma declaração com um `Right` de `Identity,` o <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> propriedade retorna `true`. Se uma ou mais tais declarações estiverem presentes, o `IsAnonymous` propriedade retorna `false`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IdentityModel.Claims.ClaimSet>  
 <xref:System.IdentityModel.Claims.Claim>  
 <xref:System.IdentityModel.Claims.Rights>  
 <xref:System.IdentityModel.Claims.ClaimTypes>  
 [Gerenciando reivindicações e autorização com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)

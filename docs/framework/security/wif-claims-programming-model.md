---
title: Modelo de programação de declarações do WIF
ms.date: 03/30/2017
ms.assetid: 149cb875-9b1c-4695-b88a-fbf1725a02f9
author: BrucePerlerMS
ms.openlocfilehash: 19dbf5ed8852ea8d3ad9be078cb575c6e4dc06ed
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631901"
---
# <a name="wif-claims-programming-model"></a>Modelo de programação de declarações do WIF
Os desenvolvedores do ASP.NET e do WCF (Windows Communication Foundation) normalmente usam as interfaces de IIdentity e IPrincipal para trabalhar com as informações de identidade do usuário. No .NET 4.5, o WIF (Windows Identity Foundation) foi integrado, de modo que as declarações agora estejam sempre presentes para qualquer entidade de segurança, conforme ilustrado no seguinte diagrama:

 ![Diagrama que mostra o modelo de programação de declarações do WIF.](./media/wif-claims-programming-model/wif-claims-programming-model.png)

 No .NET 4.5, System.Security.Claims contém as novas classes ClaimsPrincipal e ClaimsIdentity (consulte o diagrama acima). Todas as entidades de segurança do .NET agora são derivadas de ClaimsPrincipal. Todas as classes de identidade internas, como FormsIdentity para o ASP.NET e WindowsIdentity, agora são derivadas de ClaimsIdentity. Da mesma forma, todas as classes de entidade de segurança internas como GenericPrincipal e WindowsPrincipal são derivadas de ClaimsPrincipal.

 Uma declaração é representada pela classe <xref:System.Security.Claims.Claim>. Essa classe tem as seguintes propriedades importantes:

- <xref:System.Security.Claims.Claim.Type%2A> representa o tipo de declaração e geralmente é um URI. Por exemplo, a declaração de endereço de email é representada como `http://schemas.microsoft.com/ws/2008/06/identity/claims/email`.

- <xref:System.Security.Claims.Claim.Value%2A> contém o valor da declaração e é representado como uma cadeia de caracteres. Por exemplo, o endereço de email pode ser representado como "someone@contoso.com".

- <xref:System.Security.Claims.Claim.ValueType%2A> representa o tipo do valor de declaração e geralmente é um URI. Por exemplo, o tipo de cadeia de caracteres é representado como `http://www.w3.org/2001/XMLSchema#string`. O tipo de valor deve ser um QName de acordo com o esquema XML. O valor deve estar no formato `namespace#format` para permitir que o WIF produza um valor de QName válido. Se o namespace não for um namespace bem-definido, o XML gerado provavelmente não poderá ser validado pelo esquema, porque não haverá um arquivo XSD publicado para esse namespace. O tipo de valor padrão é `http://www.w3.org/2001/XMLSchema#string`. Para obter informações sobre os tipos de valor conhecido que pode ser usado com segurança, consulte o [W3C XML Schema](https://www.w3.org/2001/XMLSchema) página.

- <xref:System.Security.Claims.Claim.Issuer%2A> é o identificador do STS (serviço de token de segurança) que emitiu a declaração. Isso pode ser representado como a URL do STS ou um nome que representa o STS, como `https://sts1.contoso.com/sts`.

- <xref:System.Security.Claims.Claim.OriginalIssuer%2A> é o identificador do STS que emitiu originalmente a declaração, independentemente de quantos STSs estão na cadeia. Isso é representado exatamente como <xref:System.Security.Claims.Claim.Issuer%2A>.

- <xref:System.Security.Claims.Claim.Subject%2A> é a entidade cuja identidade está sendo examinada. Contém <xref:System.Security.Claims.ClaimsIdentity>.

- <xref:System.Security.Claims.Claim.Properties%2A> é um dicionário que permite ao desenvolvedor fornecer dados específicos ao aplicativo a serem transferidos durante a transmissão junto com as outras propriedades e pode ser usado para a validação personalizada.

## <a name="identity-delegation"></a>Delegação de identidade
Uma propriedade importante de <xref:System.Security.Claims.ClaimsIdentity> é <xref:System.Security.Claims.ClaimsIdentity.Actor%2A>. Essa propriedade permite a delegação de credenciais em um sistema de várias camadas em que uma camada intermediária atua como o cliente para fazer solicitações para um serviço back-end.

### <a name="accessing-claims-through-threadcurrentprincipal"></a>Acessando declarações por meio de Thread.CurrentPrincipal
Para acessar o conjunto atual de declarações do usuário em um aplicativo RP, use `Thread.CurrentPrincipal`.

O exemplo de código a seguir mostra o uso desse método para obter uma System.Security.Claims.ClaimsIdentity:

```csharp
ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;
```

Para obter mais informações, consulte <xref:System.Security.Claims>.

### <a name="role-claim-type"></a>Tipo de declaração de função
Parte da configuração do aplicativo RP é determinar qual deve ser o tipo de declaração da função. Esse tipo de declaração é usado por System.Security.Claims.ClaimsPrincipal.IsInRole(System.String). O tipo de declaração padrão é `http://schemas.microsoft.com/ws/2008/06/identity/claims/role`.

### <a name="claims-extracted-by-windows-identity-foundation-from-different-token-types"></a>Declarações extraídas pelo Windows Identity Foundation de diferentes tipos de token
O WIF dá suporte a várias combinações de mecanismos de autenticação prontos para uso. A tabela a seguir lista as declarações que o WIF extrai de diferentes tipos de token.

|Tipo de token|Declaração gerada|Mapeada para o token de acesso do Windows|
|-|-|-|
|SAML 1.1|1.  Todas as declarações de System.IdentityModel.SecurityTokenService.GetOutputClaimsIdentity(System.Security.Claims.ClaimsPrincipal,System.IdentityModel.Protocols.WSTrust.RequestSecurityToken,System.IdentityModel.Scope).<br />2.  A declaração `http://schemas.microsoft.com/ws/2008/06/identity/claims/confirmationkey` que contém a serialização XML da chave de confirmação, caso o token contenha um token de prova.<br />3.  A declaração `http://schemas.microsoft.com/ws/2008/06/identity/claims/samlissuername` do elemento Issuer.<br />4.  As declarações AuthenticationMethod AuthenticationInstant, se o token contém uma instrução de autenticação.|Além das declarações listadas em “SAML 1.1”, exceto declarações do tipo `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name`, as declarações relacionadas à autenticação do Windows serão adicionadas e a identidade será representada por WindowsClaimsIdentity.|
|SAML 2.0|O mesmo que “SAML 1.1”.|O mesmo que “SAML 1.1 mapeado para a conta do Windows”.|
|X509|1.  Declarações com o nome diferenciado do X500, emailName, dnsName, SimpleName, UpnName, UrlName, thumbprint, RsaKey (isso pode ser extraído usando o método RSACryptoServiceProvider.ExportParameters da propriedade X509Certificate2.PublicKey.Key), DsaKey (isso pode ser extraído usando o método DSACryptoServiceProvider.ExportParameters da propriedade X509Certificate2.PublicKey.Key), propriedades SerialNumber do certificado X509.<br />2.  Declaração AuthenticationMethod com o valor `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/x509`. A declaração AuthenticationInstant com o valor da hora em que o certificado foi validado no formato XmlSchema DateTime.|1.  Ela usa o nome de domínio totalmente qualificado da conta do Windows como o valor da declaração `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name`. .<br />2.  As declarações do Certificado X509 não mapeadas para o Windows e declarações da conta do Windows obtidas ao mapear o certificado para o Windows.|
|UPN|1.  As declarações são semelhantes às declarações descritas na seção de autenticação do Windows.<br />2.  Declaração AuthenticationMethod com o valor `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/password`. A declaração AuthenticationInstant com o valor da hora em que a senha foi validada no formato XmlSchema DateTime.||
|Windows (Kerberos ou NTLM)|1.  Declarações geradas do token de acesso, como: PrimarySID, DenyOnlyPrimarySID, PrimaryGroupSID, DenyOnlyPrimaryGroupSID, GroupSID, DenyOnlySID e nome<br />2.  AuthenticationMethod com o valor `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/windows`. AuthenticationInstant com o valor da hora em que o token de acesso do Windows foi criado no formato XMLSchema DateTime.||
|Par de chaves RSA|1.  A declaração `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/rsa` com o valor de RSAKeyValue.<br />2.  Declaração AuthenticationMethod com o valor `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/signature`. A declaração AuthenticationInstant com o valor da hora em que a chave RSA foi autenticada (ou seja, a assinatura foi verificada) no formato XMLSchema DateTime.||

|Tipo de autenticação|URI emitido na declaração “AuthenticationMethod”|
|-|-|
|Senha|`urn:oasis:names:tc:SAML:1.0:am:password`|
|Kerberos|`urn:ietf:rfc:1510`|
|SecureRemotePassword|`urn:ietf:rfc:2945`|
|TLSClient|`urn:ietf:rfc:2246`|
|X509|`urn:oasis:names:tc:SAML:1.0:am:X509-PKI`|
|PGP|`urn:oasis:names:tc:SAML:1.0:am:PGP`|
|Spki|`urn:oasis:names:tc:SAML:1.0:am:SPKI`|
|XmlDSig|`urn:ietf:rfc:3075`|
|Não especificado|`urn:oasis:names:tc:SAML:1.0:am:unspecified`|

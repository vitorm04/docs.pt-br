---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: b27f337189a7d0b66ffd38e032b5eb864e5094a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152626"
---
# <a name="samlsecuritytokenrequirement"></a>\<samlSecurityTokenRequirement>
Fornece configuração <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> para <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> a classe, a classe ou uma classe derivada de qualquer uma dessas classes. Representado pela <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> classe.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de configuração de identidade**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de segurançaTokenHandlers**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<adicionar>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement
            issuerCertificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
            issuerCertificateRevocationMode="NoCheck||Offline||Online"  
            issuerCertificateTrustedStoreLocation="CurrentLocation||LocalMachine"  
            issuerCertificateValidator="Namespace.Class Assembly"  
            mapToWindows=xs:boolean  
          <nameClaimType value=xs:string />  
          <roleClaimType value=xs:string />  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|mapToWindows|Especifica se o manipulador de tokens deve mapear o token de validação para uma conta do Windows usando a reclamação UPN de entrada. O padrão é "falso".|  
|emissorCertificadoRevocaçãoMode|Um <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valor que especifica o modo de revogação a ser usado para o certificado X.509. O valor padrão é "Online".|  
|emissorCertificadoValidaçãoMode|Um <xref:System.ServiceModel.Security.X509CertificateValidationMode> valor que especifica o modo de validação a ser usado para o certificado X.509. O valor padrão é "PeerOrChainTrust".|  
|emissorRetercertificadoDeconfiançaLocalizaçãodeArmazenamento|Um <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valor que especifica a loja de certificados X.509. O valor padrão é "LocalMachine".|  
|emissorCertificadode certificado|Um tipo personalizado que <xref:System.IdentityModel.Selectors.X509CertificateValidator>deriva de . Se `issuerCertificateValidationMode` o atributo for "Personalizado", uma instância desse tipo será usada para validação de certificado de emissor.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<>de nameClaimType](nameclaimtype.md)|Define o tipo de <xref:System.Security.Principal.IIdentity.Name%2A> solicitação que especifica a propriedade.|  
|[\<>roleClaimType](roleclaimtype.md)|Especifica o tipo de solicitação que define as <xref:System.Security.Claims.ClaimsIdentity> reivindicações do <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> tipo de função na coleção de objetos retornados pelo método do manipulador de tokens.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<adicionar>](add.md)|Adiciona o manipulador de token de segurança especificado à coleção do manipulador de tokens.|  
  
## <a name="remarks"></a>Comentários  
 O `<samlSecurityTokenRequirement>` elemento é <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> representado pela classe no modelo do `SamlSecurityTokenRequirement` objeto e <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> é <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>usado para configurar a propriedade em um ou a .  
  
## <a name="example"></a>Exemplo  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement issuerCertificateValidationMode="PeerOrChainTrust"  
                                  issuerCertificateRevocationMode="Online"  
                                  issuerCertificateTrustedStoreLocation="LocalMachine"  
                                  mapToWindows="false">  
  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```

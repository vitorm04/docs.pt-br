---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: d0a1f8dd0c29aaee56c2ca1162cc70cc1e5ed106
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942675"
---
# <a name="issuernameregistry"></a>\<issuerNameRegistry>
Configura o registro de nome do emissor que é usado pelos manipuladores na coleção de manipuladores de token.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration>  
\<issuerNameRegistry>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry type=xs:string>  
          <optionalCustomConfigurationElements />  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|tipo|Um tipo que deriva da <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe. Para obter mais informações sobre como especificar um personalizado `type`, consulte [referências de tipo personalizado].|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<trustedIssuers>](trustedissuers.md)|Quando o `type` atributo especifica o registro de nome do emissor baseado em configuração ( <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> a classe), o elemento de [ \<> trustedIssuers](trustedissuers.md) deve ser especificado. O `<add>` `<remove>` [ \<elemento > trustedIssuers](trustedissuers.md) pode levar, `<clear>`ou elementos como elementos filho.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Fornece a configuração para uma coleção de manipuladores de token de segurança.|  
  
## <a name="remarks"></a>Comentários  
 Todos os tokens do emissor são validados usando um registro de nome do emissor. Esse é um objeto derivado da <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe. O registro de nome do emissor é usado para associar um nome mnemônico ao material criptográfico que é necessário para verificar as assinaturas de tokens produzidas pelo emissor correspondente. O registro de nome do emissor mantém uma lista de emissores que são confiáveis para o aplicativo RP (terceira parte confiável). O tipo do registro de nome do emissor é especificado usando o `type` atributo. O `<issuerNameRegistry>` elemento pode ter um ou mais elementos filho que fornecem a configuração para o tipo especificado. Você fornece a lógica que processa esses elementos filho substituindo o <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> método.  
  
 O WIF fornece um tipo de registro de nome de emissor único pronto para uso <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> , a classe. Essa classe usa um conjunto de certificados de emissor confiável que são especificados na configuração do. Ele requer um elemento de configuração filho `<trustedIssuers>`,, sob o qual a coleção de certificados de emissor confiável está configurada. Os certificados confiáveis são especificados usando a forma codificada ASN. 1 da impressão digital do certificado e são adicionados ou removidos da coleção `<add>`usando `<clear>`elementos, `<remove>` ou.  
  
 O `<issuerNameRegistry>` elemento é representado <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> pela classe.  
  
> [!NOTE]
> A especificação `<issuerNameRegistry>` do elemento como um elemento filho [ \<do elemento > identityConfiguration](identityconfiguration.md) foi preterida, mas ainda tem suporte para compatibilidade com versões anteriores. As configurações no `<securityTokenHandlerConfiguration>` elemento substituem aquelas `<identityConfiguration>` no elemento.  
  
## <a name="example"></a>Exemplo  
 O XML a seguir mostra como especificar o registro de nome do emissor baseado em configuração.  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>

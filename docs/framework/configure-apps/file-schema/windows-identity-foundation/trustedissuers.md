---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 32aad3529ded6d0234b1bcb388ecbbc3b0a11c87
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944266"
---
# <a name="trustedissuers"></a>\<trustedIssuers>
Configura a lista de certificados de emissor confiável usados pelo registro de nome do emissor baseado em configuração (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration>  
\<issuerNameRegistry>  
\<trustedIssuers>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry>  
          <trustedIssuers>  
            <add thumbprint=xs:string name=xs:string>  
            <clear>  
            <remove thumbprint=xs:string>  
          </trustedIssuers>  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 Nenhum  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|Adiciona um certificado à coleção de emissores confiáveis. O certificado é especificado com o `thumbprint` atributo. Esse atributo é necessário e deve conter a forma codificada ASN. 1 da impressão digital do certificado. O `name` atributo é opcional e pode ser usado para especificar um nome amigável para o certificado.|  
|`<clear>`|Limpa todos os certificados da coleção de emissores confiáveis.|  
|`<remove thumbprint=xs:string>`|Remove um certificado da coleção de emissores confiáveis. O certificado é especificado com o `thumbprint` atributo. Esse atributo é necessário.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<issuerNameRegistry>](issuernameregistry.md)|Configura o registro de nome do emissor. **Importante:**  O `type` atributo <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> `<trustedIssuers>` do elemento deve fazer referência à classe para que o elemento seja válido. `<issuerNameRegistry>`|  
  
## <a name="remarks"></a>Comentários  
 O Windows Identity Foundation (WIF) fornece uma única implementação da <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe pronta para uso, a <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe. O registro de nome do emissor de configuração mantém uma lista de emissores confiáveis que são carregados da configuração. A lista associa cada nome de emissor com o certificado X. 509 necessário para verificar a assinatura de tokens produzidos pelo emissor. A lista de certificados de emissor confiável é especificada no `<trustedIssuers>` elemento. Cada elemento na lista associa um nome de emissor mnemônico ao certificado X. 509 necessário para verificar a assinatura dos tokens produzidos por esse emissor. Os certificados confiáveis são especificados usando a forma codificada ASN. 1 da impressão digital do certificado e são adicionados a `<add>` coleção usando o elemento. Você pode limpar ou remover os emissores (certificados) da lista usando os `<clear>` elementos `<remove>` e.  
  
 O `type` atributo <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> `<trustedIssuers>` do elemento deve fazer referência à classe para que o elemento seja válido. `<issuerNameRegistry>`  
  
## <a name="example"></a>Exemplo  
 O XML a seguir mostra como especificar o registro de nome do emissor baseado em configuração.  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>

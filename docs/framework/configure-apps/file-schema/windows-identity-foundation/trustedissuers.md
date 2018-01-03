---
title: '&lt;trustedIssuers&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 26f3d4f0b272168083bed2bbe249532181a6db67
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="lttrustedissuersgt"></a>&lt;trustedIssuers&gt;
Define a lista de certificados de emissor confiável usado pelo registro de nome do emissor de configuração (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).  
  
 \<System. IdentityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
\<issuerNameRegistry >  
\<trustedIssuers >  
  
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
|`<add thumbprint=xs:string name=xs:string>`|Adiciona um certificado para a coleção de emissores confiáveis. O certificado é especificado com o `thumbprint` atributo. Esse atributo é necessário e deve conter o formulário codificado de ASN. 1 da impressão digital do certificado. O `name` atributo é opcional e pode ser usado para especificar um nome amigável para o certificado.|  
|`<clear>`|Limpa todos os certificados da coleção de emissores confiáveis.|  
|`<remove thumbprint=xs:string>`|Remove um certificado da coleção de emissores confiáveis. O certificado é especificado com o `thumbprint` atributo. Esse atributo é necessário.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|Configura o registro do nome do emissor. **Importante:** o `type` atributo do `<issuerNameRegistry>` deve fazer referência a elemento o <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> de classe para o `<trustedIssuers>` elemento válido.|  
  
## <a name="remarks"></a>Comentários  
 Windows Identity Foundation (WIF) fornece uma implementação única do <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe predefinido de <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe. O registro de nome de emissor de configuração mantém uma lista de emissores confiáveis que é carregada de configuração. A lista associa cada nome do emissor do certificado x. 509 que é necessária para verificar a assinatura de tokens produzido pelo emissor. A lista de certificados de emissor confiável especificada no `<trustedIssuers>` elemento. Cada elemento na lista associa um nome de emissor mnemônico com o certificado x. 509 que é necessária para verificar a assinatura de tokens produzido por esse emissor. Certificados de confiança são especificados usar o ASN. 1 codificado em forma de impressão digital do certificado e são adicionados a coleção usando `<add>` elemento. Você pode limpar ou remover emissores (certificados) da lista usando o `<clear>` e `<remove>` elementos.  
  
 O `type` atributo do `<issuerNameRegistry>` deve fazer referência a elemento o <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> de classe para o `<trustedIssuers>` elemento válido.  
  
## <a name="example"></a>Exemplo  
 O XML a seguir mostra como especificar o emissor de configuração com base em registro de nome.  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>

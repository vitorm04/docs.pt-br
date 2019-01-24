---
title: '&lt;trustedIssuers&gt;'
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 1459027ae22344d5b1abc917c490b8e98fa0f2c3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54633879"
---
# <a name="lttrustedissuersgt"></a>&lt;trustedIssuers&gt;
Configura a lista de certificados do emissor confiável usado pelo registro de nome do emissor e baseada em configuração (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).  
  
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
|`<add thumbprint=xs:string name=xs:string>`|Adiciona um certificado para a coleção de emissores confiáveis. O certificado é especificado com o `thumbprint` atributo. Esse atributo é obrigatório e deve conter o formulário codificado do ASN.1 da impressão digital do certificado. O `name` atributo é opcional e pode ser usado para especificar um nome amigável para o certificado.|  
|`<clear>`|Limpa todos os certificados da coleção de emissores confiáveis.|  
|`<remove thumbprint=xs:string>`|Remove um certificado da coleção de emissores confiáveis. O certificado é especificado com o `thumbprint` atributo. Esse atributo é necessário.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<issuerNameRegistry>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|Configura o registro do nome do emissor. **Importante:**  O `type` atributo do `<issuerNameRegistry>` deve fazer referência a elemento o <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe para o `<trustedIssuers>` elemento a ser válido.|  
  
## <a name="remarks"></a>Comentários  
 Windows Identity Foundation (WIF) fornece uma única implementação do <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe imediato, o <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe. O registro do nome de emissor configuração mantém uma lista de emissores confiáveis carregado a partir da configuração. A lista associa cada nome do emissor do certificado X.509 que é necessário para verificar a assinatura de tokens produzidos pelo emissor. A lista de certificados do emissor confiável é especificada sob o `<trustedIssuers>` elemento. Cada elemento na lista associa um nome de emissor mnemônico com o certificado X.509 que é necessário para verificar a assinatura de tokens produzidos por esse emissor. Certificados de confiança são especificados usar o ASN. 1 codificada em forma de impressão digital do certificado e são adicionados a coleção usando `<add>` elemento. Você pode limpar e remover emissores (certificados) da lista usando o `<clear>` e `<remove>` elementos.  
  
 O `type` atributo do `<issuerNameRegistry>` deve fazer referência a elemento o <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe para o `<trustedIssuers>` elemento a ser válido.  
  
## <a name="example"></a>Exemplo  
 O XML a seguir mostra como especificar o emissor de configuração com base em registro do nome.  
  
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

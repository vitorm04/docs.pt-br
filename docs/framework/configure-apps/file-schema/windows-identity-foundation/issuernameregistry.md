---
title: '&lt;issuerNameRegistry&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 0c0552e06564e09832cf78afeb8f183a0a0dc94c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltissuernameregistrygt"></a>&lt;issuerNameRegistry&gt;
Configura o registro de nome de emissor que é usado por manipuladores na coleção de manipulador de token.  
  
 \<System. IdentityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
\<issuerNameRegistry >  
  
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
|tipo|Um tipo que deriva de <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe. Para obter mais informações sobre como especificar um personalizado `type`, consulte [referências de tipo personalizado].|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<trustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)|Quando o `type` atributo especifica o registro de nome de emissor com base em configuração (o <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe), o [ \<trustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) elemento deve ser especificado. O [ \<trustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) elemento pode levar `<add>`, `<clear>`, ou `<remove>` elementos como elementos filho.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Fornece manipuladores de token de configuração para uma coleção de segurança.|  
  
## <a name="remarks"></a>Comentários  
 Todos os tokens do emissor são validados usando um registro de nome de emissor. Este é um objeto que deriva de <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe. O registro do nome do emissor é usado para associar um mnemônico nome para o material criptográfico é necessária para verificar as assinaturas dos tokens produzidos pelo emissor correspondente. O registro do nome do emissor mantém uma lista de emissores confiáveis para aplicativo de terceira parte (RP). O tipo de registro de nome de emissor é especificado usando o `type` atributo. O `<issuerNameRegistry>` elemento pode ter um ou mais elementos filho que fornecem a configuração para o tipo especificado. Forneça a lógica que processa esses elementos filho, substituindo o <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> método.  
  
 WIF fornece um emissor único tipo de registro de nome sem a necessidade de <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe. Essa classe usa um conjunto de certificados de emissor confiável estão especificados na configuração. Ele requer um elemento de configuração filho, `<trustedIssuers>`, em que a coleção de certificados do emissor confiável está configurada. Confiável certificados são especificados usar o ASN. 1 codificado em forma de impressão digital do certificado e é adicionado ou removido da coleção usando `<add>`, `<clear>`, ou `<remove>` elementos.  
  
 O `<issuerNameRegistry>` elemento é representado pela <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> classe.  
  
> [!NOTE]
>  Especificando o `<issuerNameRegistry>` como um elemento filho do [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elemento foi substituído, mas ainda há suporte para compatibilidade com versões anteriores. Configurações de `<securityTokenHandlerConfiguration>` elemento substituem aquelas no `<identityConfiguration>` elemento.  
  
## <a name="example"></a>Exemplo  
 O XML a seguir mostra como especificar o emissor de configuração com base em registro de nome.  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>

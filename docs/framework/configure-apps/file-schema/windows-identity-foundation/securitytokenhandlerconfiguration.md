---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: e3e65820fa4dc341371d4f67689a288cd3f63951
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152561"
---
# <a name="securitytokenhandlerconfiguration"></a>\<> de configuração dedecontatosdeproblemas de segurança
Fornece configuração para a coleção de manipuladores de tokens.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de configuração de identidade**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de segurançaTokenHandlers**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<Configuradodefalha>**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration saveBootstrapContext=xs:boolean  
          maximumClockSkew=TimeSpan>  
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
|salvarBootstrapContext|Especifica se os tokens bootstrap devem ser incluídos no token da sessão. O valor também pode ser definido em uma `saveBootstrapContext` coleção de manipuladores de tokens definindo o atributo no elemento [ \<identityConfiguration>.](identityconfiguration.md) Um valor definido na coleção do manipulador de tokens substitui o valor definido no serviço.|  
|máximoClockSkew|A <xref:System.TimeSpan> que especifica a distorção máxima permitida do relógio. Controla a distorção máxima do relógio permitida ao realizar operações sensíveis ao tempo, como validar o tempo de expiração de uma sessão de login. O padrão é 5 minutos, "00:05:00". Para obter mais informações <xref:System.TimeSpan> sobre como especificar valores, consulte [Timespan Values](../windows-workflow-foundation/index.md). A distorção máxima do relógio também pode ser `maximumClockSkew` definida no nível de serviço, definindo o atributo no elemento [ \<identityConfiguration>.](identityconfiguration.md) Um valor definido na coleção do manipulador de tokens substitui o valor definido no serviço.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<audiênciaUris>](audienceuris.md)|Especifica o conjunto de URIs que são identificadores aceitáveis desta parte que depende. Opcional.|  
|[\<caches>](caches.md)|Registra os caches usados para tokens de sessão e detecção de replay de tokens. Pode ser especificado no nível de serviço ou em uma coleção de manipulador de tokens de segurança. Opcional.|  
|[\<>de validação de certificados](certificatevalidation.md)|Controla as configurações que os manipuladores de tokens usam para validar certificados. Pode ser especificado no nível de serviço ou em uma coleção de manipulador de tokens de segurança. Essas configurações são substituídas se um manipulador específico estiver configurado com seu próprio validador. Opcional.|  
|[\<emissorNomeregistro>](issuernameregistry.md)|Configura o registro de nome do emissor que é usado pelos manipuladores na coleção do manipulador de tokens. Opcional.|  
|[\<emissorTokenResolver>](issuertokenresolver.md)|Registra o resolver token emissor usado pelos manipuladores na coleção de manipuladores de tokens. O resolver token do emissor é usado para resolver o token de assinatura em tokens e mensagens recebidas. Opcional.|  
|[\<serviceTokenResolver>](servicetokenresolver.md)|Registra o resolver token de serviço que é usado pelos manipuladores na coleção de manipuladores de tokens. O resolvede token de serviço é usado para resolver o token de criptografia em tokens e mensagens recebidas. Opcional.|  
|[\<ReproduçãoDetecção de erros>](tokenreplaydetection.md)|Permite a detecção de replay de token e especifica o tempo de expiração dos tokens. Pode ser especificado no nível de serviço ou em uma coleção de manipulador de tokens de segurança. Opcional.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<>de segurançaTokenHandlers](securitytokenhandlers.md)|Especifica uma coleção de manipuladores de tokens de segurança que estão registrados com o ponto final.|  
  
## <a name="remarks"></a>Comentários  
 Esta seção fornece <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> valores de propriedade para um objeto. As configurações configuradas nesta seção sobrepõem as configuradas no serviço. Algumas dessas configurações podem, por sua vez, ser substituídas por configurações especificadas quando um manipulador é adicionado à coleção de manipuladores de tokens de segurança.  
  
## <a name="example"></a>Exemplo  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>
      <securityTokenHandlerConfiguration>  
  
        <audienceUris>  
          <clear/>  
          <add value="http://www.example.com/myapp/" />  
        </audienceUris>  
  
        <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel">  
          <trustedIssuers>  
            <add thumbprint="97249e1a … 4c9158de" name="contoso.com" />  
          </trustedIssuers>  
        </issuerNameRegistry>  
  
        <issuerTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
        <serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```

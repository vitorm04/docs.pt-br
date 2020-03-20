---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 0983380e553acfe246d6b987784d818b8ae85b17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152574"
---
# <a name="servicetokenresolver"></a>\<> serviceTokenResolver
Registra o resolver token de serviço que é usado pelos manipuladores na coleção de manipuladores de tokens. O resolvede token de serviço é usado para resolver o token de criptografia em tokens e mensagens recebidas.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de configuração de identidade**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de segurançaTokenHandlers**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<Configuradodefalha>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
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
|type|Especifica o tipo de solução do token de serviço. Ou <xref:System.IdentityModel.Selectors.SecurityTokenResolver> o tipo ou um tipo <xref:System.IdentityModel.Selectors.SecurityTokenResolver> que deriva da classe. Para obter mais informações `type` sobre como especificar o atributo, consulte [Referências de tipo personalizado]. Obrigatórios.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<Configuradodefalha>](securitytokenhandlerconfiguration.md)|Fornece configuração para uma coleção de manipuladores de tokens de segurança.|  
  
## <a name="remarks"></a>Comentários  
 O resolvede token de serviço pode ser usado para resolver o token de criptografia em tokens e mensagens recebidas. Ele é usado para recuperar a chave que deve ser usada para descriptografar tokens de entrada. Você deve `type` especificar o atributo. O tipo especificado <xref:System.IdentityModel.Selectors.SecurityTokenResolver> pode ser um ou um <xref:System.IdentityModel.Selectors.SecurityTokenResolver> tipo personalizado que deriva da classe.  
  
 Alguns manipuladores de token permitem que você especifique as configurações de resolução de token de serviço na configuração. As configurações em manipuladores de token individuais anulam as especificadas na coleção de manipuladores de tokens de segurança.  
  
> [!NOTE]
> Especificando `<serviceTokenResolver>` o elemento como elemento filho do [ \<](identityconfiguration.md) elemento identityConfiguration>foi preterido, mas ainda é suportado para compatibilidade retrógrada. As configurações `<securityTokenHandlerConfiguration>` do elemento sobrepõem as do `<identityConfiguration>` elemento.  
  
## <a name="example"></a>Exemplo  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```

---
title: '&lt;windowsAuthentication&gt; of &lt;serviceCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: 9872b1f2520661ff3f31cef94b6822bb345ebfdf
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltwindowsauthenticationgt-of-ltservicecredentialsgt"></a>&lt;windowsAuthentication&gt; of &lt;serviceCredentials&gt;
Especifica as configurações de uma credencial de serviço do Windows.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<serviceBehaviors >  
\<comportamento >  
\<serviceCredentials>  
\<windowsAuthentication >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<windowsAuthentication  
      allowAnonymousLogons="Boolean"  
      includeWindowsGroups="Boolean" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`includeWindowsGroups`|Um atributo booleano opcional que especifica se o sistema inclui grupos do Windows no contexto de segurança. O padrão é `true`.<br /><br /> A configuração desse atributo `true` tem um impacto de desempenho que resulta em uma expansão de grupo completo. Defina este atributo como `false` se você não precisa estabelecer a lista de grupos de um usuário pertence.|  
|`allowAnonymousLogons`|Um atributo booleano opcional que especifica se chamadores anônimos, não autenticados são permitidos. O padrão é `false`.<br /><br /> Quando o `clientCredentialType` atributo de uma associação é definido como `Windows`, o sistema não permite chamadores anônimos. Isso significa que somente domínio ou grupo de trabalho autenticado chamadores têm permissão para acessar o sistema. Você pode substituir esse comportamento usando esse atributo.<br /><br /> Use essa configuração com extrema cautela.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<serviceCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Especifica a credencial a ser usado na autenticação do serviço e as configurações de relacionadas à validação de credenciais do cliente.|  
  
## <a name="remarks"></a>Comentários  
 Use esse elemento para especificar se deseja permitir acesso de usuários anônimos do Windows, definindo o `allowAnonymousLogons` atributo. Você também pode especificar se deseja incluir informações de grupo ao qual pertencem os usuários no AuthorizationContext, definindo o `includeWindowsGroups` atributo. Se for definido como `true` (a configuração padrão), o serviço pode determinar os grupos do Windows ao qual o cliente pertence.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.WindowsServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>  
 <xref:System.ServiceModel.Security.WindowsServiceCredential>

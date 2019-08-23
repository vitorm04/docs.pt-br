---
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: 399158632d5c17a35ded02691ba35a231e6cdc6e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940541"
---
# <a name="usernameauthentication"></a>\<userNameAuthentication>
Especifica as credenciais de um serviço com base no nome de usuário e senha.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<> de portais  
\<> de comportamento  
\<serviceCredentials>  
\<userNameAuthentication>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|Um <xref:System.TimeSpan> valor que especifica o período máximo de tempo em que um token é armazenado em cache. O padrão é 00:15:00.|  
|`cacheLogonTokens`|Um valor booliano que especifica se os tokens de logon são armazenados em cache. O padrão é `false`.|  
|`customUserNamePasswordValidatorType`|Uma cadeia de caracteres que especifica o tipo de validador de senha de nome de usuário personalizado a ser usado. O padrão é uma cadeia de caracteres vazia.|  
|`includeWindowsGroups`|Um valor booliano que especifica se os grupos do Windows estão incluídos no contexto de segurança. O padrão é `true`.<br /><br /> Definir esse atributo para `true` tem um impacto no desempenho conforme ele resulta em uma expansão de grupo completo. Defina essa propriedade como `false` se você não precisar estabelecer a lista de grupos aos quais um usuário pertence.|  
|`maxCacheLogonTokens`|Um inteiro que especifica o número máximo de tokens de logon para armazenar em cache. Esse valor deve ser maior que zero. O padrão é 128.|  
|`membershipProviderName`|Quando o `clientCredentialType` atributo de uma associação é definido como `username`, o nome de usuário é mapeado para contas do Windows. Você pode substituir esse comportamento usando esse atributo, que é uma cadeia de caracteres que contém o nome <xref:System.Web.Security.MembershipProvider> do valor que fornece o mecanismo de validação de senha relevante.|  
|`userNamePasswordValidationMode`|Especifica a maneira como a senha de nome de usuário é validada. Os valores válidos são:<br /><br /> -Windows<br />-MembershipProvider<br />-Personalizado<br /><br /> O padrão é Windows. Esse atributo é do tipo <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|Especifica a credencial a ser usada na autenticação do serviço e as configurações relacionadas à validação de credenciais do cliente.|  
  
## <a name="remarks"></a>Comentários  
 Se nenhuma das associações usadas por um serviço estiver configurada para autenticação baseada em nome de usuário/senha, os atributos desse elemento serão ignorados. Isso inclui `customUserNamePasswordValidatorType` `includeWindowsGroups` ,,e`userNamePasswordValidationMode`. `membershipProviderName`  
  
 Se nenhuma das associações usadas por um serviço estiver configurada para usar a autenticação do Windows para nome de usuário/senha, as configurações relacionadas ao cache de tokens de logon serão ignoradas. Isso inclui o `cacheLogonTokenLifetime`, `cacheLogonTokens`o e `maxCacheLogonTokens`o.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>

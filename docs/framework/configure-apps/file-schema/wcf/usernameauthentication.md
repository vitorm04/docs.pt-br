---
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: 5a4cf8d429198b889f2bb362294ba3841c814b26
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788694"
---
# <a name="usernameauthentication"></a>\<userNameAuthentication>
Especifica as credenciais de um serviço com base no nome de usuário e senha.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<serviceBehaviors>  
\<behavior>  
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
|`cacheLogonTokenLifetime`|Um <xref:System.TimeSpan> que especifica o comprimento máximo de tempo que um token é armazenado em cache. O padrão é 15:00:00.|  
|`cacheLogonTokens`|Um valor booliano que especifica se tokens de logon são armazenadas em cache. O padrão é `false`.|  
|`customUserNamePasswordValidatorType`|Uma cadeia de caracteres que especifica o tipo de validador de senha do nome de usuário personalizado a ser usado. O padrão é uma cadeia de caracteres vazia.|  
|`includeWindowsGroups`|Um valor booliano que especifica se os grupos do Windows são incluídos no contexto de segurança. O padrão é `true`.<br /><br /> Definir esse atributo como `true` tem um impacto no desempenho, já que resulta em uma expansão de grupo completo. Defina essa propriedade como `false` se você não precisar estabelecer a lista de grupos de um usuário pertence.|  
|`maxCacheLogonTokens`|Um inteiro que especifica o número máximo de tokens de logon ao cache. Esse valor deve ser maior que zero. O padrão é 128.|  
|`membershipProviderName`|Quando o `clientCredentialType` atributo de uma associação é definido como `username`, o nome de usuário é mapeado para contas do Windows. Você pode substituir esse comportamento usando esse atributo, o que é uma cadeia de caracteres que contém o nome da <xref:System.Web.Security.MembershipProvider> valor que fornece o mecanismo de validação de senha relevantes.|  
|`userNamePasswordValidationMode`|Especifica a maneira na qual nome de usuário a senha é validada. Os valores válidos são:<br /><br /> -   Windows<br />-MembershipProvider<br />-Custom<br /><br /> O padrão é Windows. Esse atributo é do tipo <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<serviceCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Especifica a credencial a ser usada na autenticação de serviço, e configurações relacionadas à validação de credenciais do cliente.|  
  
## <a name="remarks"></a>Comentários  
 Se nenhuma das associações usadas por um serviço estiver configurada para autenticação baseada em nome/senha do usuário, os atributos desse elemento são ignorados. Eles incluem `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, e `userNamePasswordValidationMode`.  
  
 Se nenhuma das associações usadas por um serviço estiver configurada para usar a autenticação do Windows para o nome de usuário/senha, as configurações relacionadas ao cache de tokens de logon serão ignoradas. Isso inclui o `cacheLogonTokenLifetime`, `cacheLogonTokens`, e `maxCacheLogonTokens`.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>

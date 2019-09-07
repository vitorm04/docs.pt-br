---
title: <secureConversationAuthentication> de <serviceCredential>
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: 336969c654f332ae3d838d8fd6d1c4243838539c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399938"
---
# <a name="secureconversationauthentication-of-servicecredential"></a>\<secureConversationAuthentication > de \<> do incredential
Especifica as configurações para um serviço de conversa segura.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> secureConversationAuthentication**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`securityStateEncoderType`|Uma cadeia de caracteres que especifica o <xref:System.ServiceModel.Security.SecurityStateEncoder> tipo de a ser usado.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|Especifica a credencial a ser usada na autenticação do serviço e as configurações relacionadas à validação da credencial do cliente.|  
  
## <a name="remarks"></a>Comentários  
 Use este elemento de configuração para especificar uma lista de tipos de declaração conhecidos para a serialização de cookies do SCT (token de contexto de segurança), bem como um codificador para codificar e proteger informações de cookies. Para obter mais informações sobre o SCT <xref:System.ServiceModel.Security.SecureConversationServiceCredential>, consulte.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>

---
title: <secureConversationAuthentication> de <serviceCredential>
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: 61034c2c66a6d8e27a87ec5380aa7297247eb31e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935830"
---
# <a name="secureconversationauthentication-of-servicecredential"></a>\<secureConversationAuthentication > de \<> do incredential
Especifica as configurações para um serviço de conversa segura.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<> de portais  
\<> de comportamento  
\<serviceCredentials>  
\<secureConversationAuthentication>  
  
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

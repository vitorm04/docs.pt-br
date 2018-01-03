---
title: '&lt;RSA&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c382cb6c28825bdf590017cda986a576311423af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltrsagt"></a>&lt;RSA&gt;
Um cliente WCF seguro que se conecta a um ponto de extremidade com esta identidade verifica que as declarações apresentadas pelo servidor contém uma declaração que contém a chave pública RSA usada para construir essa identidade.  
  
 \<identidade >  
\<RSA >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<rsa value = "String" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os elementos pai de atributos e elementos filho  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|Valor |Cadeia de caracteres opcional. O RSA valor da chave pública a ser comparado com o cliente.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<identidade >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Especifica a identidade do serviço para ser autenticado pelo cliente.|  
  
## <a name="remarks"></a>Comentários  
 Uma verificação RSA permite restringir especificamente a autenticação para um único certificado com base em sua chave RSA ou gerado seu próprio valor de chave RSA. Este permite mais rígida a autenticação de uma chave RSA específica às custas de serviço não trabalhar com os clientes existentes se o valor da chave RSA é alterado.  
  
 Para obter mais informações sobre como usar a identidade para validar um serviço para um cliente, consulte [autenticação e identidade de serviço](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="example"></a>Exemplo  
 O código de configuração a seguir especifica o valor da chave pública de um certificado x. 509 que é usado para autenticar um servidor.  
  
```xml  
<identity>  
  <rsa value = "0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000"/>  
</identity>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.RsaEndpointIdentity>  
 [Autenticação e identidade de serviço](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [\<identidade >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)

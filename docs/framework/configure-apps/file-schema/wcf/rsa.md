---
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 0e307069bd3a98153cc66147ba7bcf511cf13a8e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091649"
---
# <a name="rsa"></a>\<rsa>
Um cliente WCF seguro que se conecta a um ponto de extremidade com esta identidade verifica que as declarações apresentadas pelo servidor contém uma afirmação que contém a chave pública RSA usada para construir essa identidade.  
  
 \<identity>  
\<rsa>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|Valor |Cadeia de caracteres opcional. O RSA valor da chave pública a ser comparado com o cliente.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Especifica a identidade do serviço para ser autenticado pelo cliente.|  
  
## <a name="remarks"></a>Comentários  
 Uma verificação RSA permite que você restrinja especificamente a autenticação para um único certificado com base em sua chave RSA ou gerado seu próprio valor de chave RSA. Este permite mais rígida a autenticação de uma chave RSA específica à custa o serviço não é mais trabalhar com os clientes existentes se o valor da chave RSA é alterado.  
  
 Para obter mais informações sobre como usar a identidade para validar um serviço para um cliente, consulte [identidade de serviço e autenticação](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="example"></a>Exemplo  
 O código de configuração a seguir especifica o valor de chave pública de um certificado X.509 que é usado para autenticar um servidor.  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [Identidade e autenticação de serviço](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)

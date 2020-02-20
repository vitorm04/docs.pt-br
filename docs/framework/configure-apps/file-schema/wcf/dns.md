---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: e49a564c9793b371425b2b787586bb9d3cbed58b
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452221"
---
# <a name="dns"></a>\<> DNS
Especifica a identidade esperada do servidor. Essa identidade é válida para o modo de autenticação de certificado X509 se o certificado do servidor contiver um DNS com o mesmo valor. Ele também é válido para o modo de autenticação do Windows se o SPN tiver o mesmo valor.  
  
Para obter mais informações sobre como definir o valor do elemento, consulte [identidade e autenticação de serviço](../../../wcf/feature-details/service-identity-and-authentication.md).  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cliente**](client.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ponto de extremidade**](endpoint-of-client.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**Identity**](identity.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dns >**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|DESCRIÇÃO|  
|---------------|-----------------|  
|value|O DNS do certificado. O DNS é um protocolo padrão do setor usado para localizar computadores em uma rede baseada em IP. Os usuários podem lembrar nomes de exibição, como `https://go.microsoft.com/fwlink/?prd=10929` ou `https://go.microsoft.com/fwlink/?LinkID=96165`, mais fáceis do que endereços baseados em número, como 207.46.131.137.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|DESCRIÇÃO|  
|-------------|-----------------|  
|[identidade de \<>](identity.md)|Especifica a identidade do serviço a ser autenticado pelo cliente.|  
  
## <a name="example"></a>Exemplo  
 O código de configuração a seguir especifica o DNS de um certificado X. 509 que é usado para autenticar um servidor.  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [Autenticação e identidade de serviço](../../../wcf/feature-details/service-identity-and-authentication.md)
- [identidade de \<>](identity.md)

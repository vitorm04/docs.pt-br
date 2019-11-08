---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: c5c7ec2b18143ff4d71540a60e24b8225ca4db16
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738597"
---
# <a name="sslstreamsecurity"></a>\<sslStreamSecurity >
Representa um elemento de associação personalizado que suporta segurança de canal usando um fluxo SSL.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**CustomBinding**](custombinding.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<sslStreamSecurity >**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|requireClientCertificate|Um valor booliano que especifica se um certificado de cliente é necessário para essa associação. O padrão é `false`.|  
|sslProtocols|Um valor de sinalizador de enumeração SslProtocols que especifica quais SslProtocols têm suporte. O padrão é Ssl3&#124;TLS&#124;Tls11&#124;Tls12.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<binding >](bindings.md)|Define todos os recursos de associação da associação personalizada.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [Associações](../../../wcf/bindings.md)
- [Estendendo associações](../../../wcf/extending/extending-bindings.md)
- [Associações personalizadas](../../../wcf/extending/custom-bindings.md)
- [\<CustomBinding](custombinding.md)

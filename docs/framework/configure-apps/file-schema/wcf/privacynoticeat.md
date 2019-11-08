---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 2ff70d3a8636970434582e417e4549ab6b433fc1
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738770"
---
# <a name="privacynoticeat"></a>\<privacyNoticeAt >
Representa um elemento de configuração que especifica um aviso de privacidade usado na associação `wsFederationHttp`.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**CustomBinding**](custombinding.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<privacyNotice >**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a>Digite  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`url`|Uma cadeia de caracteres que especifica o URI no qual o aviso de privacidade está localizado.|  
|`version`|Um inteiro que especifica a versão deste aviso de privacidade.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<binding >](bindings.md)|Define todos os recursos de associação da associação personalizada.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Associações](../../../wcf/bindings.md)
- [Estendendo associações](../../../wcf/extending/extending-bindings.md)
- [Associações personalizadas](../../../wcf/extending/custom-bindings.md)
- [\<CustomBinding](custombinding.md)

---
title: '&lt;compositeDuplex&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 80c8f3954cccbce8e93ab9d8c516fdfd6c7bff10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcompositeduplexgt"></a>&lt;compositeDuplex&gt;
Define o elemento de associação que é usado quando o cliente deve expor um ponto de extremidade para o serviço enviar mensagens de volta ao cliente.  
  
 \<System. ServiceModel >  
\<associações >  
\<customBinding >  
\<associação >  
\<compositeDuplex >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|clientBaseAddress|Um URI que define o endereço do canal de retorno no modo duplex. O serviço usa este endereço para contato e estabelecer uma conexão com o cliente.<br /><br /> Se esse atributo não estiver definido, um endereço padrão "`full qualified name+default port\TemporaryIndigoAddress\guid`" é gerado. O padrão é `null`.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<associação >](../../../../../docs/framework/misc/binding.md)|Define todos os recursos de associação da associação personalizada.|  
  
## <a name="remarks"></a>Comentários  
 Este elemento de configuração é usado com transportes que não permitem a comunicação duplex nativamente, por exemplo, HTTP. TCP, por outro lado, permite a comunicação duplex nativamente e não requer o uso desse elemento de associação para o serviço enviar mensagens para um cliente.  
  
 O cliente deve expor um endereço para o serviço fazer contato e estabelecer uma conexão. Este endereço de cliente é fornecido pelo `clientBaseAddress` atributo. Observe que Windows Communication Foundation (WCF) gera automaticamente um ClientBaseAddress se um não for explicitamente definido pelo usuário.  
  
## <a name="example"></a>Exemplo  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.CompositeDuplexElement>  
 <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

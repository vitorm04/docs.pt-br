---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: 1e5ecc2b937aa0cdb159a6cbd1222fe6d4af79fb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159839"
---
# <a name="compositeduplex"></a>\<compositeDuplex>
Define o elemento de associação que é usado quando o cliente deve expor um ponto de extremidade para o serviço enviar mensagens de volta ao cliente.  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<compositeDuplex>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|clientBaseAddress|Um URI que define o endereço do canal de retorno no modo duplex. O serviço usa esse endereço para tornar o contato e estabelecer uma conexão com o cliente.<br /><br /> Se esse atributo não é definido, um endereço padrão "`full qualified name+default port\TemporaryIndigoAddress\guid`" é gerado. O padrão é `null`.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<binding>](../../../../../docs/framework/misc/binding.md)|Define todos os recursos de associação de associação personalizada.|  
  
## <a name="remarks"></a>Comentários  
 Este elemento de configuração é usado com os transportes que não permitem comunicações duplex nativamente, por exemplo, HTTP. TCP, por outro lado, permite que as comunicações duplex nativamente e não requer o uso desse elemento de associação para o serviço enviar mensagens para um cliente.  
  
 O cliente deve expor um endereço para o serviço para que entre em contato com e estabelecer uma conexão. Esse endereço de cliente é fornecido pelo `clientBaseAddress` atributo. Observe que Windows Communication Foundation (WCF) gera automaticamente um ClientBaseAddress se um não é explicitamente definido pelo usuário.  
  
## <a name="example"></a>Exemplo  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Associações](../../../../../docs/framework/wcf/bindings.md)
- [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

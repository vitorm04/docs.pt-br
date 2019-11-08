---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 79c3c68d69bf3cf5a018e6cf62f34e5ec2ce0cd5
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738927"
---
# <a name="mexhttpsbinding"></a>\<mexHttpsBinding >
Especifica as configurações para uma associação usada para a troca de mensagens WS-MetadataExchange (WS-MEX) por HTTPS.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexHttpsBinding >**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<mexHttpsBinding>
  <binding closeTimeout="TimeSpan"
            name="string"
            openTimeout="TimeSpan"
            receiveTimeout="TimeSpan"
            sendTimeout="TimeSpan">
  </binding>
</mexHttpsBinding>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`closeTimeout`|Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|`name`|Uma cadeia de caracteres que contém o nome da configuração da associação. Esse valor deve ser exclusivo porque é usado como uma identificação para a associação. Cada associação tem um atributo `name` e `namespace` que, juntos, o identificam exclusivamente nos metadados do serviço. Além disso, esse nome é exclusivo entre associações do mesmo tipo. A partir do [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome. Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|`receiveTimeout`|Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:10:00.|  
|`sendTimeout`|Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<bindings >](bindings.md)|Esse elemento contém uma coleção de associações padrão e personalizadas.|  
  
## <a name="remarks"></a>Comentários  
 Essa associação é essencialmente uma associação `WSHttpBinding` que dá suporte à segurança em nível de transporte usando certificados. Para obter mais informações sobre como configurar e usar esse ponto de extremidade de metadados, consulte [como: configurar uma associação de WS-Metadata Exchange personalizada](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [como recuperar metadados em uma associação não MEX](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)e o [ponto de extremidade de metadados seguro personalizado](../../../wcf/samples/custom-secure-metadata-endpoint.md) de exemplo .  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [Como publicar metadados para um serviço usando um arquivo de configuração](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Publicando e recuperando metadados através de uma associação personalizada](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [Como configurar uma associação personalizada do WS-Metadata Exchange](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [Como recuperar metadados por meio de uma associação não MEX](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [Ponto de extremidade de metadados seguros personalizado](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [Metadados](../../../wcf/feature-details/metadata.md)
- [Associações](../../../wcf/bindings.md)
- [Configurando associações fornecidas pelo sistema](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Usando associações para configurar serviços e clientes](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding >](bindings.md)

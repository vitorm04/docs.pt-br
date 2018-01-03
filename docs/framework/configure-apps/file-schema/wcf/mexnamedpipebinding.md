---
title: '&lt;mexNamedPipeBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 193412fa-3260-414c-92c6-b32ed3b94a34
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 08108be229eac4963886cf65cccc062df3ab634f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltmexnamedpipebindinggt"></a>&lt;mexNamedPipeBinding&gt;
Especifica as configurações de uma associação usada para a troca de mensagens WS-MetadataExchange (WS-MEX) sobre pipe nomeado.  
  
 \<sistema. ServiceModel >  
\<associações >  
\<mexNamedPipeBinding >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<mexNamedPipeBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       name="string"   
       openTimeout="TimeSpan"   
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan">  
   </binding>  
</mexNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`closeTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de fechamento concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|`name`|Uma cadeia de caracteres que contém o nome da configuração da associação. Esse valor deve ser exclusivo, porque ele é usado como uma identificação para a associação. Cada associação tem um `name` e `namespace` de atributo que juntos exclusivamente identificá-lo nos metadados do serviço. Além disso, esse nome é exclusivo entre as associações do mesmo tipo. Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome. Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de abertura concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|`receiveTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:10:00.|  
|`sendTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<associações >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Esse elemento contém uma coleção de associações padrão e personalizadas.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexNamedPipeBinding%2A>  
 <xref:System.ServiceModel.Configuration.MexNamedPipeBindingElement>  
 [Como publicar metadados para um serviço usando um arquivo de configuração](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [Publicando e recuperando metadados através de uma associação personalizada](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [Metadados](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)

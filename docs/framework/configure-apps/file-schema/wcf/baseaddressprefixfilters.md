---
title: '&lt;baseAddressPrefixFilters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0a1c2e5e887ceaadf3db6f51991d53c3db8fb6ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltbaseaddressprefixfiltersgt"></a>&lt;baseAddressPrefixFilters&gt;
Representa uma coleção de elementos de configuração que especificam a passagem por meio de filtros, que fornecem um mecanismo para obter as associações de serviços de informações da Internet (IIS) apropriado ao hospedar o [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] aplicativo no IIS.  
  
> [!WARNING]
>  \<baseAddressPrefixFilters > não reconhece "localhost", use o nome do computador totalmente qualificado em vez disso.  
  
 \<sistema. ServiceModel >  
\<ServiceHostingEnvironment >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="string"/>  
     </baseAddressPrefixFilters>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddressprefixfilter.md)|Adiciona um elemento de configuração que especifica um filtro de prefixo para os endereços base usados pelo host de serviço.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Define o tipo que o ambiente de hospedagem de serviço instancia para um transporte particular.|  
  
## <a name="remarks"></a>Comentários  
 Um filtro de prefixo fornece uma maneira para provedores de hospedagem compartilhadas especificar os URIs são usados pelo serviço. Ele permite que os hosts compartilhados hospedar vários aplicativos com diferentes endereços base para o mesmo esquema no mesmo site.  
  
 Sites da Web do IIS são contêineres de aplicativos virtuais que contêm diretórios virtuais. O aplicativo em um site pode ser acessado por meio de um ou mais associações de IIS. Associações do IIS fornecem duas informações: protocolo de associação e informações de associação. Associação de protocolo (por exemplo, HTTP) define o esquema durante o qual a comunicação ocorre, e (por exemplo, endereço IP, porta e cabeçalho de host) de informações de associação contém dados usados para acessar o site.  
  
 O IIS oferece suporte à especificação várias associações de IIS para cada site, o que resulta em vários endereços de base para cada esquema. Porque um [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] serviço hospedado em um site permite que a associação apenas um endereço base para cada esquema, você pode usar o recurso de filtro de prefixo para escolher o endereço base necessário do serviço hospedado. Os endereços base entrados fornecidos pelo IIS, são filtrados com base no filtro de lista de prefixo opcional.  
  
 Por exemplo, seu site pode conter os seguintes endereços de base.  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 Você pode usar o seguinte arquivo de configuração para especificar um filtro de prefixo no nível do appdomain.  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="net.tcp://test1.fabrikam.com:8000"/>  
        <add prefix="http://test2.fabrikam.com:9000"/>  
    </baseAddressPrefixFilters>  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 Neste exemplo, `net.tcp://test1.fabrikam.com:8000` e `http://test2.fabrikam.com:9000` são os endereços base somente para seus respectivos esquemas, que têm permissão para ser passado.  
  
 Por padrão, quando o prefixo não for especificado, todos os endereços são passados. Especifica o prefixo permite apenas o endereço base correspondente para esse esquema deverá ser passado.  
  
> [!NOTE]
>  O filtro não oferece suporte a todos os curingas. Além disso, o baseAddresses fornecida pelo IIS pode ter endereços associados a outros esquemas não está presentes no `baseAddressPrefixFilters` lista. Esses endereços não serão filtrados.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [Hospedagem](../../../../../docs/framework/wcf/feature-details/hosting.md)

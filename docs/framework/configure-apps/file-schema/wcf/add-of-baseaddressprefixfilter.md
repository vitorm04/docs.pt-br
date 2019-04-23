---
title: <add> de <baseAddressPrefixFilter>
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: a58a29e44fff3d653d04da271e3b240f2969611f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59143891"
---
# <a name="add-of-baseaddressprefixfilter"></a>\<add> of \<baseAddressPrefixFilter>
Representa um elemento de configuração que especifica um filtro de passagem, que fornece um mecanismo para coletar as associações de serviços de informações da Internet (IIS) apropriadas ao hospedar um aplicativo do Windows Communication Foundation (WCF) no IIS.  
  
 \<system.ServiceModel>  
\<ServiceHostingEnvironment>  
\<baseAddressPrefixFilters>  
\<add>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
  </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|prefix|Um URI que é usado para corresponder a uma parte de um endereço básico.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|Uma coleção de elementos de configuração que especificam filtros de passagem, que fornecem um mecanismo para coletar as associações de IIS apropriadas ao hospedar um aplicativo do Windows Communication Foundation (WCF) no IIS.|  
  
## <a name="remarks"></a>Comentários  
 Um filtro de prefixo fornece uma maneira para os provedores de hospedagem compartilhadas especificar quais URIs devem ser usados pelo serviço. Ele permite que os hosts compartilhados hospedar vários aplicativos com diferentes endereços base para o mesmo esquema no mesmo site.  
  
 Sites da Web do IIS são contêineres para aplicativos virtuais que contêm os diretórios virtuais. O aplicativo em um site pode ser acessado por meio de um ou mais associação do IIS. Associações do IIS fornecem dois tipos de informação: informações de associação e o protocolo de associação. Associação de protocolo (por exemplo, HTTP) define o esquema no qual a comunicação ocorre, e informações (por exemplo, endereço IP, porta, cabeçalho de host) de associação contém dados usados para acessar o site.  
  
 IIS dá suporte à especificação de várias associações de IIS para cada site, o que resulta em vários endereços de base para cada esquema. Como um serviço WCF hospedado em um site permite que a associação para apenas um endereço base para cada esquema, você pode usar o recurso de filtro de prefixo para escolher o endereço base necessário do serviço hospedado. Os endereços base entrados fornecidos pelo IIS, são filtrados com base no filtro de lista de prefixo opcional.  
  
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
      <add prefix="net.tcp://test1.fabrikam.com:8000" />
      <add prefix="http://test2.fabrikam.com:9000" />
    </baseAddressPrefixFilters>
  </serviceHostingEnvironment>
</system.serviceModel>
```  
  
 Neste exemplo, `net.tcp://test1.fabrikam.com:8000` e `http://test2.fabrikam.com:9000` são os endereços base somente para seus respectivos esquemas que têm permissão para ser passado.  
  
 Por padrão, quando o prefixo não for especificado, todos os endereços são passados. Especificar o prefixo permite apenas o endereço base correspondente para que o esquema deve ser passado.  
  
> [!NOTE]
>  O filtro não oferece suporte a curingas. Além disso, o baseAddresses fornecida pelo IIS podem ter endereços associados a outros esquemas não está presentes no `baseAddressPrefixFilters` lista. Esses endereços não serão filtrados.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [Hospedagem](../../../../../docs/framework/wcf/feature-details/hosting.md)

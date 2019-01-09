---
title: '&lt;baseAddressPrefixFilters&gt;'
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 04579980201b397e7ed92f55ffcb19e54de18aaa
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149222"
---
# <a name="ltbaseaddressprefixfiltersgt"></a>&lt;baseAddressPrefixFilters&gt;
Representa uma coleção de elementos que especificam a passam por meio de filtros, que fornecem um mecanismo para coletar as associações de serviços de informações da Internet (IIS) apropriadas ao hospedar o aplicativo do Windows Communication Foundation (WCF) no IIS de configuração.  
  
> [!WARNING]
>  \<baseAddressPrefixFilters > não reconhece "localhost", use o nome totalmente qualificado do computador em vez disso.  
  
 \<system.ServiceModel>  
\<serviceHostingEnvironment >  
  
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
 Um filtro de prefixo fornece uma maneira para os provedores de hospedagem compartilhadas especificar quais URIs devem ser usados pelo serviço. Ele permite que os hosts compartilhados hospedar vários aplicativos com diferentes endereços base para o mesmo esquema no mesmo site.  
  
 Sites da Web do IIS são contêineres para aplicativos virtuais que contêm os diretórios virtuais. O aplicativo em um site pode ser acessado por meio de uma ou mais associações de IIS. Associações do IIS fornecem dois tipos de informação: informações de associação e o protocolo de associação. Associação de protocolo (por exemplo, HTTP) define o esquema no qual a comunicação ocorre, e informações (por exemplo, endereço IP, porta, cabeçalho de host) de associação contém dados usados para acessar o site.  
  
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
  
 Neste exemplo, `net.tcp://test1.fabrikam.com:8000` e `http://test2.fabrikam.com:9000` são os endereços base somente para seus respectivos esquemas, que têm permissão para ser passado.  
  
 Por padrão, quando o prefixo não for especificado, todos os endereços são passados. Especificar o prefixo permite apenas o endereço base correspondente para que o esquema deve ser passado.  
  
> [!NOTE]
>  O filtro não oferece suporte a curingas. Além disso, o baseAddresses fornecida pelo IIS podem ter endereços associados a outros esquemas não está presentes no `baseAddressPrefixFilters` lista. Esses endereços não serão filtrados.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [Hospedagem](../../../../../docs/framework/wcf/feature-details/hosting.md)

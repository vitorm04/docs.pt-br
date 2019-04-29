---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: bff19f106d86c73dea80b8b57bb73442eaa2cf9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704031"
---
# <a name="filter"></a>\<filter>

Define um filtro de roteamento, que determina o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, como também quaisquer dados de apoio ou parâmetros exigidos pelo filtro.

\<system.serviceModel> \<routing> \<filters> \<filter>
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<routing>
  <filters>
    <filter customType="String"
            filterData="String"
            filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
            name="String" />
  </filters>
</routing>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

| Atributo  | Descrição |
| ---------- | ----------- |
| customType | Uma cadeia de caracteres que contém o nome de tipo totalmente qualificado do tipo a ser usado como um filtro personalizado. Se `filterType` é definido como `custom`, este atributo contém o nome do tipo totalmente qualificado da classe para criar.  `filterData` também pode conter valores a serem usados durante a avaliação do filtro de tipo personalizado. |
| filterData | Uma cadeia de caracteres que contém os dados de filtro. Para obter mais informações sobre como especificar esse atributo, consulte <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>. |
| filterType | Uma cadeia de caracteres que contém o tipo de filtro. Esse atributo é do <xref:System.ServiceModel.Routing.Configuration.FilterType> tipo.  Para obter mais informações sobre como isso funciona com o `filterData` atributo, consulte <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>. |
| name       | Uma cadeia de caracteres que contém o nome exclusivo deste elemento de filtro. |

### <a name="child-elements"></a>Elementos filho

nenhuma.

### <a name="parent-elements"></a>Elementos pai

| Elemento | Descrição |
| ------- | ----------- |
| [\<routing>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | Uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas. |

## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>

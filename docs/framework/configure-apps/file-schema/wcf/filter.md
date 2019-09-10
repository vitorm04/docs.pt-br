---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 6e78275aaeb202405e327302455d56fa431d7f27
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855250"
---
# <a name="filter"></a>\<filter>

Define um filtro de roteamento, que determina o tipo de Windows Communication Foundation (WCF<xref:System.ServiceModel.Dispatcher.MessageFilter> ) a ser usado ao avaliar mensagens recebidas, bem como quaisquer dados de suporte ou parâmetros exigidos pelo filtro.

[ **\<system.serviceModel>** ](system-servicemodel.md)\
&nbsp;&nbsp;[ **\<routing>** ](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Filtros >** ](filters-of-routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de filtro**  
  
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
| customType | Uma cadeia de caracteres que contém o nome do tipo totalmente qualificado do tipo personalizado a ser usado como um filtro. Se `filterType` é definido como `custom`, esse atributo contém o nome de tipo totalmente qualificado da classe a ser criada.  `filterData`também pode conter valores a serem usados durante a avaliação do filtro de tipo personalizado. |
| filterData | Uma cadeia de caracteres que contém os dados de filtro. Para obter mais informações sobre como especificar esse atributo, consulte <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>. |
| filterType | Uma cadeia de caracteres que contém o tipo de filtro. Esse atributo é do <xref:System.ServiceModel.Routing.Configuration.FilterType> tipo.  Para obter mais informações sobre como isso funciona com `filterData` o atributo, <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>consulte. |
| name       | Uma cadeia de caracteres que contém o nome exclusivo deste elemento de filtro. |

### <a name="child-elements"></a>Elementos filho

nenhuma.

### <a name="parent-elements"></a>Elementos pai

| Elemento | Descrição |
| ------- | ----------- |
| [\<routing>](routing.md) | Uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo de Windows Communication Foundation<xref:System.ServiceModel.Dispatcher.MessageFilter> (WCF) a ser usado ao avaliar mensagens de entrada. |

## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>

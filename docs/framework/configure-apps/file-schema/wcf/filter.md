---
title: '&lt;filtro&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 186c511cd8a69cef5e30e369641628a10a0972d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltfiltergt"></a>&lt;filtro&gt;

Define um filtro de roteamento, que determina o tipo de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, como também quaisquer dados de apoio ou parâmetros exigidos pelo filtro.

\<System. ServiceModel > \<roteamento > \<filtros > \<filtro >

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
| customType | Uma cadeia de caracteres que contém o nome de tipo totalmente qualificado do tipo personalizado a ser usado como um filtro. Se `filterType` é definido como `custom`, este atributo contém o nome de tipo totalmente qualificado da classe para criar.  `filterData`também pode conter valores a serem usados durante a avaliação do filtro de tipo personalizado. |
| filterData | Uma cadeia de caracteres que contém os dados de filtro. Para obter mais informações sobre como especificar esse atributo, consulte <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>. |
| filterType | Uma cadeia de caracteres que contém o tipo de filtro. Esse atributo é de <xref:System.ServiceModel.Routing.Configuration.FilterType> tipo.  Para obter mais informações sobre como isso funciona com o `filterData` de atributo, consulte <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>. |
| name       | Uma cadeia de caracteres que contém o nome exclusivo deste elemento de filtro. |

### <a name="child-elements"></a>Elementos filho

nenhuma.

### <a name="parent-elements"></a>Elementos pai

| Elemento | Descrição |
| ------- | ----------- |
| [\<roteamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | Uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo de [!INCLUDE[ indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas. |

## <a name="see-also"></a>Consulte também

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>    
<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>   
<xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>   

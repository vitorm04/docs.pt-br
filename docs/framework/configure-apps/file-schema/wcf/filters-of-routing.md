---
title: '&lt;filtros&gt; de &lt;roteamento&gt;'
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: 9f0fa9bf51d264346738172f57a8efca7950fdb7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753109"
---
# <a name="ltfiltersgt-of-ltroutinggt"></a>&lt;filtros&gt; de &lt;roteamento&gt;

Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo do Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas.

[**\<System. ServiceModel >**](system-servicemodel.md)   
&nbsp;&nbsp;[**\<roteamento >**](routing.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<Filtros >**

## <a name="syntax"></a>Sintaxe

```xml
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String" 
              filterData="String" 
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath" 
              name="String" />
    </filters>
  </routing>
</system.serviceModel>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

Nenhum

### <a name="child-elements"></a>Elementos filho

|     | Descrição |
| --- | ----------- |
| [**\<Filtro >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | Contém um filtro de roteamento que determina o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> será usada ao avaliar mensagens recebidas. |

### <a name="parent-elements"></a>Elementos pai

|     | Descrição |
| --- | ----------- |
| [**\<roteamento >**](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, bem como o roteamento de tabelas que definem os pontos de extremidade de destino para envie mensagens para quando houver correspondência de filtro. |

## <a name="see-also"></a>Consulte também

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>

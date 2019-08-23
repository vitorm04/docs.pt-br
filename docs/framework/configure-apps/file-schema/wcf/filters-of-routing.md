---
title: <filters> de <routing>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: ba60958ad33b46b40285f3f70001273bb3af3a63
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925613"
---
# <a name="filters-of-routing"></a>\<Filtros > do \<> de roteamento

Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo de Windows Communication Foundation <xref:System.ServiceModel.Dispatcher.MessageFilter> (WCF) a ser usado ao avaliar mensagens de entrada.

[ **\<system.serviceModel>** ](system-servicemodel.md)   
&nbsp;&nbsp;[ **\<routing>** ](routing.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<filters>**
  
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
| [ **\<filter>** ](filter.md) | Contém um filtro de roteamento que determina o tipo de Windows Communication Foundation (WCF<xref:System.ServiceModel.Dispatcher.MessageFilter> ) será usado ao avaliar mensagens de entrada. |

### <a name="parent-elements"></a>Elementos pai

|     | Descrição |
| --- | ----------- |
| [ **\<routing>** ](routing.md) | Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo de Windows Communication Foundation<xref:System.ServiceModel.Dispatcher.MessageFilter> (WCF) a ser usado ao avaliar mensagens de entrada, bem como tabelas de roteamento que definem os pontos de extremidade de destino para enviar mensagens para quando um filtro corresponder. |

## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>

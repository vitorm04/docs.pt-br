---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: fcf2d4eec93fd7127c6f800e1c739ad1fac49203
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399967"
---
# <a name="routing"></a>\<> de roteamento

Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo de Windows Communication Foundation <xref:System.ServiceModel.Dispatcher.MessageFilter> (WCF) a ser usado ao avaliar mensagens de entrada, bem como tabelas de roteamento que definem os pontos de extremidade de destino para enviar mensagens para quando um filtro corresponder.

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<> de roteamento**
  
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
    <routingTables>
      <table name="String">
        <entries>
          <add endpoint="String"
               filterName="String"
               priority="Integer" />
        </entries>
      </table>
    </routingTables>
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
| [ **\<filters>** ](filters-of-routing.md) | Contém um conjunto de filtros de roteamento que determinam o tipo de Windows Communication Foundation (WCF) MessageFilter será usado ao avaliar mensagens de entrada. |
| [ **\<filterTables>** ](filtertables.md) | Contém mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para especificar qual ponto de extremidades usar quando o filtro corresponde. |

### <a name="parent-elements"></a>Elementos pai

|     | Descrição |
| --- | ----------- |
| **\<system.ServiceModel>** | O elemento raiz de todos os elementos de configuração do WCF. |

## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>

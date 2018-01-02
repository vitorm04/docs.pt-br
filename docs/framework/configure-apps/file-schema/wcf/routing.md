---
title: '&lt;roteamento&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ef71753a4b0ff20a966842119adb6e637ded1f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltroutinggt"></a>&lt;roteamento&gt;

Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, bem como o roteamento de tabelas que definem os pontos de extremidade de destino para enviar mensagens quando um corresponde ao filtro.

[**\<System. ServiceModel >**](system-servicemodel.md)   
&nbsp;&nbsp;**\<roteamento >**

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
| [**\<Filtros >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | Contém um conjunto de filtros de roteamento que determinam o tipo de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] MessageFilter será usada ao avaliar mensagens recebidas. |
| [**\<filterTables >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | Contém os mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para especificar qual ponto de extremidade a ser usado ao correspondências de filtro. |

### <a name="parent-elements"></a>Elementos pai

|     | Descrição |
| --- | ----------- |
| **\<sistema. ServiceModel >** | O elemento raiz de todos os elementos de configuração do WCF. |

## <a name="see-also"></a>Consulte também

<xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>

---
title: '&lt;namespaceTable&gt;'
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: 31d661f39f9e3de0f7012c7fa52d4964e7ee4a69
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748874"
---
# <a name="ltnamespacetablegt"></a>&lt;namespaceTable&gt;

Representa uma seção de configuração para definir um conjunto de elementos que contêm namespace para mapeamentos de prefixo que podem ser usadas em filtros de XPath para roteamento.

**\<System. ServiceModel >**   
&nbsp;&nbsp;**\<roteamento >**   
&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable >**

## <a name="syntax"></a>Sintaxe

```xml
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String" prefix="String" />
    </namespaceTable>
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
| [**\<Filtro >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | Define um mapeamento de prefixo de namespace usado para expressões XPath. |

### <a name="parent-elements"></a>Elementos pai

|     | Descrição |
| --- | ----------- |
| [**\<roteamento >**](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, bem como o roteamento de tabelas que definem os pontos de extremidade de destino para envie mensagens para quando houver correspondência de filtro. |

## <a name="see-also"></a>Consulte também

<xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>

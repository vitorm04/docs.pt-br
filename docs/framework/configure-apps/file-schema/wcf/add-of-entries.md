---
title: '&lt;adicionar&gt; &lt;entradas&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d62236c604cd91c2dfe4b92cfaac4004fc18d439
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltaddgt-of-ltentriesgt"></a>&lt;adicionar&gt; &lt;entradas&gt;
Representa uma entrada de roteamento que mapeia um filtro para um ponto de extremidade do cliente que foi definido anteriormente. As mensagens que correspondem a este filtro serão enviadas para este destino.  
  
 \<System. ServiceModel >  
\<roteamento >  
\<routingTables >  
\<Tabela >  
\<entradas >  
\<add>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|backupList|Uma cadeia de caracteres que especifica uma referência a uma lista de pontos de extremidade de backup.|  
|ponto de extremidade|Uma cadeia de caracteres que especifica uma referência a um ponto de extremidade do cliente que receberá as mensagens que correspondem ao filtro especificado pelo `filterName` atributo.|  
|filterName|Uma cadeia de caracteres que especifica uma referência a um elemento de filtro.|  
|priority|Um inteiro que especifica a prioridade desta entrada.<br /><br /> As entradas na tabela de roteamento com base na prioridade, com 0, sendo a prioridade mais baixa serão avaliadas. Todas as entradas para uma prioridade específica são avaliadas simultaneamente, se nenhuma correspondência de entrada foi encontrada para a prioridade atual, o próximo nível de prioridade será avaliado.<br /><br /> Esse valor é opcional.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<roteamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Uma seção de configuração que contém as entradas de mapeamento de roteamento.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType> 

---
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: c68479737cefe542a10a404a8b31a4820a430ffb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855204"
---
# \<filterTables>
<span data-ttu-id="b7fba-101">Representa uma seção de configuração para definir tabelas de roteamento que contêm mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para enviar mensagens quando o filtro for correspondente.</span><span class="sxs-lookup"><span data-stu-id="b7fba-101">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTables>**  
  
## <a name="syntax"></a><span data-ttu-id="b7fba-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7fba-102">Syntax</span></span>  
  
```xml  
<routing>
  <filterTables>
    <filterTable name="String">
      <entries>
        <add backupList="String"
             endpointName="String"
             filterName="String"
             priority="Integer" />
      </entries>
    </filterTable>
  </filterTables>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7fba-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b7fba-103">Attributes and Elements</span></span>  
 <span data-ttu-id="b7fba-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b7fba-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7fba-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="b7fba-105">Attributes</span></span>  
 <span data-ttu-id="b7fba-106">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b7fba-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b7fba-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b7fba-107">Child Elements</span></span>  
  
|<span data-ttu-id="b7fba-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="b7fba-108">Element</span></span>|<span data-ttu-id="b7fba-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7fba-109">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="b7fba-110">Uma tabela de roteamento que contém mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para envio de mensagens quando o filtro é correspondente.</span><span class="sxs-lookup"><span data-stu-id="b7fba-110">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b7fba-111">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b7fba-111">Parent Elements</span></span>  
  
|<span data-ttu-id="b7fba-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="b7fba-112">Element</span></span>|<span data-ttu-id="b7fba-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7fba-113">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="b7fba-114">Uma seção de configuração que contém filtros de roteamento e tabelas de roteamento.</span><span class="sxs-lookup"><span data-stu-id="b7fba-114">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b7fba-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="b7fba-115">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>

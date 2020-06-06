---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: ffe2538fa2c3cb680285cfaa68c975c0f9d4b1bd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855284"
---
# \<entries>
<span data-ttu-id="04e93-101">Uma entrada de roteamento que contém mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para envio de mensagens quando o filtro é correspondente.</span><span class="sxs-lookup"><span data-stu-id="04e93-101">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<entries>**  
  
## <a name="syntax"></a><span data-ttu-id="04e93-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="04e93-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04e93-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="04e93-103">Attributes and Elements</span></span>  
 <span data-ttu-id="04e93-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="04e93-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04e93-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="04e93-105">Attributes</span></span>  
 <span data-ttu-id="04e93-106">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="04e93-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="04e93-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="04e93-107">Child Elements</span></span>  
  
|<span data-ttu-id="04e93-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="04e93-108">Element</span></span>|<span data-ttu-id="04e93-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="04e93-109">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="04e93-110">Mapeia um filtro para um ponto de extremidade do cliente que foi definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="04e93-110">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="04e93-111">As mensagens correspondentes a este filtro serão enviadas para esse destino.</span><span class="sxs-lookup"><span data-stu-id="04e93-111">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="04e93-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="04e93-112">Parent Elements</span></span>  
  
|<span data-ttu-id="04e93-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="04e93-113">Element</span></span>|<span data-ttu-id="04e93-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="04e93-114">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="04e93-115">Uma seção de configuração que contém uma tabela de roteamento.</span><span class="sxs-lookup"><span data-stu-id="04e93-115">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="04e93-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="04e93-116">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>

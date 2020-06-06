---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 918a365004efea82f4ef4c8868f6821d4bb6da18
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855183"
---
# \<filterTable>
<span data-ttu-id="fdfe1-101">Representa uma tabela de roteamento que contém uma lista de filtros para avaliar as mensagens e o ponto de extremidade do cliente para rotear mensagens se o filtro for avaliado como verdadeiro.</span><span class="sxs-lookup"><span data-stu-id="fdfe1-101">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTable>**  
  
## <a name="syntax"></a><span data-ttu-id="fdfe1-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fdfe1-102">Syntax</span></span>  
  
```xml  
<routing>
  <filterTables>
     name="String">
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fdfe1-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fdfe1-103">Attributes and Elements</span></span>  
 <span data-ttu-id="fdfe1-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fdfe1-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fdfe1-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="fdfe1-105">Attributes</span></span>  
  
|<span data-ttu-id="fdfe1-106">Elemento</span><span class="sxs-lookup"><span data-stu-id="fdfe1-106">Element</span></span>|<span data-ttu-id="fdfe1-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="fdfe1-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fdfe1-108">name</span><span class="sxs-lookup"><span data-stu-id="fdfe1-108">name</span></span>|<span data-ttu-id="fdfe1-109">Uma cadeia de caracteres que contém o nome exclusivo deste elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="fdfe1-109">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fdfe1-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fdfe1-110">Child Elements</span></span>  
  
|<span data-ttu-id="fdfe1-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="fdfe1-111">Element</span></span>|<span data-ttu-id="fdfe1-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="fdfe1-112">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="fdfe1-113">Mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para enviar mensagens quando o filtro for correspondente.</span><span class="sxs-lookup"><span data-stu-id="fdfe1-113">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fdfe1-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fdfe1-114">Parent Elements</span></span>  
  
|<span data-ttu-id="fdfe1-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="fdfe1-115">Element</span></span>|<span data-ttu-id="fdfe1-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="fdfe1-116">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="fdfe1-117">Uma seção de configuração que contém tabelas de roteamento.</span><span class="sxs-lookup"><span data-stu-id="fdfe1-117">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fdfe1-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="fdfe1-118">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>

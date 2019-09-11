---
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: c68479737cefe542a10a404a8b31a4820a430ffb
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855204"
---
# <a name="filtertables"></a><span data-ttu-id="e41f5-101">\<> filterTables</span><span class="sxs-lookup"><span data-stu-id="e41f5-101">\<filterTables></span></span>
<span data-ttu-id="e41f5-102">Representa uma seção de configuração para definir tabelas de roteamento que contêm mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para enviar mensagens quando o filtro for correspondente.</span><span class="sxs-lookup"><span data-stu-id="e41f5-102">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
<span data-ttu-id="e41f5-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e41f5-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e41f5-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e41f5-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e41f5-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de roteamento**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="e41f5-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="e41f5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> filterTables**</span><span class="sxs-lookup"><span data-stu-id="e41f5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTables>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e41f5-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e41f5-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e41f5-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e41f5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e41f5-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e41f5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e41f5-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="e41f5-110">Attributes</span></span>  
 <span data-ttu-id="e41f5-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e41f5-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e41f5-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e41f5-112">Child Elements</span></span>  
  
|<span data-ttu-id="e41f5-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="e41f5-113">Element</span></span>|<span data-ttu-id="e41f5-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="e41f5-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e41f5-115">\<filters></span><span class="sxs-lookup"><span data-stu-id="e41f5-115">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="e41f5-116">Uma tabela de roteamento que contém mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para envio de mensagens quando o filtro é correspondente.</span><span class="sxs-lookup"><span data-stu-id="e41f5-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e41f5-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e41f5-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e41f5-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="e41f5-118">Element</span></span>|<span data-ttu-id="e41f5-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="e41f5-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e41f5-120">\<routing></span><span class="sxs-lookup"><span data-stu-id="e41f5-120">\<routing></span></span>](routing.md)|<span data-ttu-id="e41f5-121">Uma seção de configuração que contém filtros de roteamento e tabelas de roteamento.</span><span class="sxs-lookup"><span data-stu-id="e41f5-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e41f5-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e41f5-122">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>

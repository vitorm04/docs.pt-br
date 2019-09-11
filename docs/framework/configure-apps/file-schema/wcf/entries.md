---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: ffe2538fa2c3cb680285cfaa68c975c0f9d4b1bd
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855284"
---
# <a name="entries"></a><span data-ttu-id="8599e-101">\<entradas ></span><span class="sxs-lookup"><span data-stu-id="8599e-101">\<entries></span></span>
<span data-ttu-id="8599e-102">Uma entrada de roteamento que contém mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para envio de mensagens quando o filtro é correspondente.</span><span class="sxs-lookup"><span data-stu-id="8599e-102">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
<span data-ttu-id="8599e-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8599e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8599e-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8599e-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8599e-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de roteamento**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="8599e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="8599e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> filterTables**](filtertables.md)</span><span class="sxs-lookup"><span data-stu-id="8599e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)</span></span>\
<span data-ttu-id="8599e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de FilterTable**](filtertable.md)</span><span class="sxs-lookup"><span data-stu-id="8599e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)</span></span>\
<span data-ttu-id="8599e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<entradas >**</span><span class="sxs-lookup"><span data-stu-id="8599e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<entries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8599e-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8599e-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8599e-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8599e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8599e-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8599e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8599e-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="8599e-112">Attributes</span></span>  
 <span data-ttu-id="8599e-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8599e-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8599e-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8599e-114">Child Elements</span></span>  
  
|<span data-ttu-id="8599e-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="8599e-115">Element</span></span>|<span data-ttu-id="8599e-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="8599e-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8599e-117">\<filters></span><span class="sxs-lookup"><span data-stu-id="8599e-117">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="8599e-118">Mapeia um filtro para um ponto de extremidade do cliente que foi definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="8599e-118">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="8599e-119">As mensagens correspondentes a este filtro serão enviadas para esse destino.</span><span class="sxs-lookup"><span data-stu-id="8599e-119">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8599e-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8599e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="8599e-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="8599e-121">Element</span></span>|<span data-ttu-id="8599e-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="8599e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8599e-123">\<routing></span><span class="sxs-lookup"><span data-stu-id="8599e-123">\<routing></span></span>](routing.md)|<span data-ttu-id="8599e-124">Uma seção de configuração que contém uma tabela de roteamento.</span><span class="sxs-lookup"><span data-stu-id="8599e-124">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8599e-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8599e-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>

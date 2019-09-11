---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 918a365004efea82f4ef4c8868f6821d4bb6da18
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855183"
---
# <a name="filtertable"></a><span data-ttu-id="28506-101">\<filterTable></span><span class="sxs-lookup"><span data-stu-id="28506-101">\<filterTable></span></span>
<span data-ttu-id="28506-102">Representa uma tabela de roteamento que contém uma lista de filtros para avaliar as mensagens e o ponto de extremidade do cliente para rotear mensagens se o filtro for avaliado como verdadeiro.</span><span class="sxs-lookup"><span data-stu-id="28506-102">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
<span data-ttu-id="28506-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="28506-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="28506-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="28506-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="28506-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de roteamento**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="28506-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="28506-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> filterTables**](filtertables.md)</span><span class="sxs-lookup"><span data-stu-id="28506-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)</span></span>\
<span data-ttu-id="28506-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de FilterTable**</span><span class="sxs-lookup"><span data-stu-id="28506-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTable>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28506-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="28506-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28506-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="28506-109">Attributes and Elements</span></span>  
 <span data-ttu-id="28506-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="28506-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28506-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="28506-111">Attributes</span></span>  
  
|<span data-ttu-id="28506-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="28506-112">Element</span></span>|<span data-ttu-id="28506-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="28506-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="28506-114">name</span><span class="sxs-lookup"><span data-stu-id="28506-114">name</span></span>|<span data-ttu-id="28506-115">Uma cadeia de caracteres que contém o nome exclusivo deste elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="28506-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28506-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="28506-116">Child Elements</span></span>  
  
|<span data-ttu-id="28506-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="28506-117">Element</span></span>|<span data-ttu-id="28506-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="28506-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28506-119">\<filters></span><span class="sxs-lookup"><span data-stu-id="28506-119">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="28506-120">Mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para enviar mensagens quando o filtro for correspondente.</span><span class="sxs-lookup"><span data-stu-id="28506-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="28506-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="28506-121">Parent Elements</span></span>  
  
|<span data-ttu-id="28506-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="28506-122">Element</span></span>|<span data-ttu-id="28506-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="28506-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28506-124">\<routing></span><span class="sxs-lookup"><span data-stu-id="28506-124">\<routing></span></span>](routing.md)|<span data-ttu-id="28506-125">Uma seção de configuração que contém tabelas de roteamento.</span><span class="sxs-lookup"><span data-stu-id="28506-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="28506-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28506-126">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>

---
title: <add> de <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 80726cc22cb56013c85c7704c28579b1337666c9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850542"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="7e4cf-102">\<Adicionar > de \<BackupList ></span><span class="sxs-lookup"><span data-stu-id="7e4cf-102">\<add> of \<backupList></span></span>
<span data-ttu-id="7e4cf-103">Representa um elemento de configuração que define um elemento de ponto de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="7e4cf-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
<span data-ttu-id="7e4cf-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7e4cf-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7e4cf-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7e4cf-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7e4cf-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de roteamento**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="7e4cf-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="7e4cf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> backupLists**](backuplists.md)</span><span class="sxs-lookup"><span data-stu-id="7e4cf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)</span></span>\
<span data-ttu-id="7e4cf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de BackupList**](backuplist.md)</span><span class="sxs-lookup"><span data-stu-id="7e4cf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupList>**](backuplist.md)</span></span>\
<span data-ttu-id="7e4cf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adicionar >**</span><span class="sxs-lookup"><span data-stu-id="7e4cf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e4cf-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7e4cf-110">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e4cf-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7e4cf-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7e4cf-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7e4cf-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e4cf-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="7e4cf-113">Attributes</span></span>  
  
|<span data-ttu-id="7e4cf-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="7e4cf-114">Attribute</span></span>|<span data-ttu-id="7e4cf-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e4cf-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7e4cf-116">name</span><span class="sxs-lookup"><span data-stu-id="7e4cf-116">name</span></span>|<span data-ttu-id="7e4cf-117">Uma cadeia de caracteres que especifica o nome do ponto de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="7e4cf-117">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7e4cf-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7e4cf-118">Child Elements</span></span>  
 <span data-ttu-id="7e4cf-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7e4cf-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7e4cf-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7e4cf-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7e4cf-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="7e4cf-121">Element</span></span>|<span data-ttu-id="7e4cf-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e4cf-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e4cf-123">\<routing></span><span class="sxs-lookup"><span data-stu-id="7e4cf-123">\<routing></span></span>](routing.md)|<span data-ttu-id="7e4cf-124">Contém uma lista de pontos de extremidade que você deseja que o serviço de roteamento use caso o ponto de extremidade primário não possa ser acessado.</span><span class="sxs-lookup"><span data-stu-id="7e4cf-124">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7e4cf-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e4cf-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>

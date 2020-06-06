---
title: <add> de <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 80726cc22cb56013c85c7704c28579b1337666c9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850542"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="93a54-102">\<add> de \<backupList></span><span class="sxs-lookup"><span data-stu-id="93a54-102">\<add> of \<backupList></span></span>
<span data-ttu-id="93a54-103">Representa um elemento de configuração que define um elemento de ponto de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="93a54-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupList>**](backuplist.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="93a54-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="93a54-104">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93a54-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="93a54-105">Attributes and Elements</span></span>  
 <span data-ttu-id="93a54-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="93a54-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93a54-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="93a54-107">Attributes</span></span>  
  
|<span data-ttu-id="93a54-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="93a54-108">Attribute</span></span>|<span data-ttu-id="93a54-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="93a54-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="93a54-110">name</span><span class="sxs-lookup"><span data-stu-id="93a54-110">name</span></span>|<span data-ttu-id="93a54-111">Uma cadeia de caracteres que especifica o nome do ponto de extremidade de backup.</span><span class="sxs-lookup"><span data-stu-id="93a54-111">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="93a54-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="93a54-112">Child Elements</span></span>  
 <span data-ttu-id="93a54-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="93a54-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="93a54-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="93a54-114">Parent Elements</span></span>  
  
|<span data-ttu-id="93a54-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="93a54-115">Element</span></span>|<span data-ttu-id="93a54-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="93a54-116">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="93a54-117">Contém uma lista de pontos de extremidade que você deseja que o serviço de roteamento use caso o ponto de extremidade primário não possa ser acessado.</span><span class="sxs-lookup"><span data-stu-id="93a54-117">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="93a54-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="93a54-118">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>

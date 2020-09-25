---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: dbf0ba565d4e3e2d65b4a81eb5d345fa90fb43c7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181421"
---
# \<persistenceProvider>

<span data-ttu-id="7275a-101">Especifica o tipo da implementação do provedor de persistência a ser usado, bem como o tempo limite a ser usado para operações de persistência.</span><span class="sxs-lookup"><span data-stu-id="7275a-101">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistenceProvider>**  
  
## <a name="syntax"></a><span data-ttu-id="7275a-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7275a-102">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7275a-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7275a-103">Attributes and Elements</span></span>  

 <span data-ttu-id="7275a-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7275a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7275a-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="7275a-105">Attributes</span></span>  
  
|<span data-ttu-id="7275a-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="7275a-106">Attribute</span></span>|<span data-ttu-id="7275a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7275a-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7275a-108">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="7275a-108">persistenceOperationTimeout</span></span>|<span data-ttu-id="7275a-109">Um <xref:System.TimeSpan> valor que especifica o tempo limite usado para operações de persistência.</span><span class="sxs-lookup"><span data-stu-id="7275a-109">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="7275a-110">O padrão é "00:00:30".</span><span class="sxs-lookup"><span data-stu-id="7275a-110">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="7275a-111">tipo</span><span class="sxs-lookup"><span data-stu-id="7275a-111">type</span></span>|<span data-ttu-id="7275a-112">Uma cadeia de caracteres que especifica o tipo do alocador de provedor de persistência a ser usado.</span><span class="sxs-lookup"><span data-stu-id="7275a-112">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7275a-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7275a-113">Child Elements</span></span>  

 <span data-ttu-id="7275a-114">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="7275a-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7275a-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7275a-115">Parent Elements</span></span>  
  
|<span data-ttu-id="7275a-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="7275a-116">Element</span></span>|<span data-ttu-id="7275a-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="7275a-117">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="7275a-118">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="7275a-118">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7275a-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="7275a-119">Remarks</span></span>  

 <span data-ttu-id="7275a-120">Esse elemento Especifica o provedor de persistência a ser usado para serializar o estado de um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="7275a-120">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="7275a-121">Ele deve ser usado junto com o `wsHttpContextBinding` que passa informações de estado em cabeçalhos HTTP.</span><span class="sxs-lookup"><span data-stu-id="7275a-121">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7275a-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="7275a-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>

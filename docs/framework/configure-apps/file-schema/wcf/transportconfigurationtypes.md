---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 6545e1f1be2695d165b89a38c7218e0acdc88bfc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162017"
---
# \<transportConfigurationTypes>

<span data-ttu-id="ff60f-101">Representa uma coleção de elementos de configuração que identificam o tipo de um transporte específico.</span><span class="sxs-lookup"><span data-stu-id="ff60f-101">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="ff60f-102">Isso pode ser usado para adicionar protocolos WAS personalizados.</span><span class="sxs-lookup"><span data-stu-id="ff60f-102">This can be used to add custom WAS protocols.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transportConfigurationTypes>**  
  
## <a name="syntax"></a><span data-ttu-id="ff60f-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="ff60f-103">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff60f-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ff60f-104">Attributes and Elements</span></span>  

 <span data-ttu-id="ff60f-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ff60f-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff60f-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="ff60f-106">Attributes</span></span>  
  
|<span data-ttu-id="ff60f-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="ff60f-107">Attribute</span></span>|<span data-ttu-id="ff60f-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff60f-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ff60f-109">name</span><span class="sxs-lookup"><span data-stu-id="ff60f-109">name</span></span>|<span data-ttu-id="ff60f-110">O nome do transporte</span><span class="sxs-lookup"><span data-stu-id="ff60f-110">The name of the transport</span></span>|  
|<span data-ttu-id="ff60f-111">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="ff60f-111">transportConfigurationType</span></span>|<span data-ttu-id="ff60f-112">O tipo que implementa o transporte</span><span class="sxs-lookup"><span data-stu-id="ff60f-112">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff60f-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ff60f-113">Child Elements</span></span>  
  
|<span data-ttu-id="ff60f-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="ff60f-114">Element</span></span>|<span data-ttu-id="ff60f-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff60f-115">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-transportconfigurationtype.md)|<span data-ttu-id="ff60f-116">Adiciona um elemento de configuração que identifica o tipo de um transporte específico.</span><span class="sxs-lookup"><span data-stu-id="ff60f-116">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ff60f-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ff60f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ff60f-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="ff60f-118">Element</span></span>|<span data-ttu-id="ff60f-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff60f-119">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="ff60f-120">Define o tipo que o ambiente de Hospedagem de serviço instancia para um transporte específico.</span><span class="sxs-lookup"><span data-stu-id="ff60f-120">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ff60f-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="ff60f-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="ff60f-122">Hosting</span><span class="sxs-lookup"><span data-stu-id="ff60f-122">Hosting</span></span>](../../../wcf/feature-details/hosting.md)

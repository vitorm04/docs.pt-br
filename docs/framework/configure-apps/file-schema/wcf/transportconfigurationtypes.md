---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 4be08f780c1095b0016bd130b5719a2a7307d019
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854931"
---
# <a name="transportconfigurationtypes"></a><span data-ttu-id="27e8d-101">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="27e8d-101">\<transportConfigurationTypes></span></span>
<span data-ttu-id="27e8d-102">Representa uma coleção de elementos de configuração que identificam o tipo de um transporte específico.</span><span class="sxs-lookup"><span data-stu-id="27e8d-102">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="27e8d-103">Isso pode ser usado para adicionar protocolos WAS personalizados.</span><span class="sxs-lookup"><span data-stu-id="27e8d-103">This can be used to add custom WAS protocols.</span></span>  
  
<span data-ttu-id="27e8d-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="27e8d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="27e8d-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="27e8d-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="27e8d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de ServiceHostingEnvironment**](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="27e8d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="27e8d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> transportConfigurationTypes**</span><span class="sxs-lookup"><span data-stu-id="27e8d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transportConfigurationTypes>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27e8d-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="27e8d-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27e8d-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="27e8d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="27e8d-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="27e8d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27e8d-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="27e8d-111">Attributes</span></span>  
  
|<span data-ttu-id="27e8d-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="27e8d-112">Attribute</span></span>|<span data-ttu-id="27e8d-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="27e8d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="27e8d-114">name</span><span class="sxs-lookup"><span data-stu-id="27e8d-114">name</span></span>|<span data-ttu-id="27e8d-115">O nome do transporte</span><span class="sxs-lookup"><span data-stu-id="27e8d-115">The name of the transport</span></span>|  
|<span data-ttu-id="27e8d-116">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="27e8d-116">transportConfigurationType</span></span>|<span data-ttu-id="27e8d-117">O tipo que implementa o transporte</span><span class="sxs-lookup"><span data-stu-id="27e8d-117">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="27e8d-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="27e8d-118">Child Elements</span></span>  
  
|<span data-ttu-id="27e8d-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="27e8d-119">Element</span></span>|<span data-ttu-id="27e8d-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="27e8d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27e8d-121">\<add></span><span class="sxs-lookup"><span data-stu-id="27e8d-121">\<add></span></span>](add-of-transportconfigurationtype.md)|<span data-ttu-id="27e8d-122">Adiciona um elemento de configuração que identifica o tipo de um transporte específico.</span><span class="sxs-lookup"><span data-stu-id="27e8d-122">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="27e8d-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="27e8d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="27e8d-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="27e8d-124">Element</span></span>|<span data-ttu-id="27e8d-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="27e8d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27e8d-126">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="27e8d-126">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="27e8d-127">Define o tipo que o ambiente de Hospedagem de serviço instancia para um transporte específico.</span><span class="sxs-lookup"><span data-stu-id="27e8d-127">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="27e8d-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27e8d-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="27e8d-129">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="27e8d-129">Hosting</span></span>](../../../wcf/feature-details/hosting.md)

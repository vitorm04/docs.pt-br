---
title: '&lt;transportConfigurationTypes&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b048b160f337897765fa4fcff73a4906534ab08b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportconfigurationtypesgt"></a><span data-ttu-id="13f16-102">&lt;transportConfigurationTypes&gt;</span><span class="sxs-lookup"><span data-stu-id="13f16-102">&lt;transportConfigurationTypes&gt;</span></span>
<span data-ttu-id="13f16-103">Representa uma coleção de elementos de configuração que identificam o tipo de um transporte particular.</span><span class="sxs-lookup"><span data-stu-id="13f16-103">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="13f16-104">Isso pode ser usado para adicionar protocolos personalizados do WAS.</span><span class="sxs-lookup"><span data-stu-id="13f16-104">This can be used to add custom WAS protocols.</span></span>  
  
 <span data-ttu-id="13f16-105">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="13f16-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="13f16-106">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="13f16-106">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="13f16-107">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="13f16-107">\<transportConfigurationTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13f16-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13f16-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="String"  
               transportConfigurationType="String"/>   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13f16-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="13f16-109">Attributes and Elements</span></span>  
 <span data-ttu-id="13f16-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="13f16-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13f16-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="13f16-111">Attributes</span></span>  
  
|<span data-ttu-id="13f16-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="13f16-112">Attribute</span></span>|<span data-ttu-id="13f16-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="13f16-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="13f16-114">name</span><span class="sxs-lookup"><span data-stu-id="13f16-114">name</span></span>|<span data-ttu-id="13f16-115">O nome do transporte</span><span class="sxs-lookup"><span data-stu-id="13f16-115">The name of the transport</span></span>|  
|<span data-ttu-id="13f16-116">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="13f16-116">transportConfigurationType</span></span>|<span data-ttu-id="13f16-117">O tipo que implementa o transporte</span><span class="sxs-lookup"><span data-stu-id="13f16-117">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13f16-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="13f16-118">Child Elements</span></span>  
  
|<span data-ttu-id="13f16-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="13f16-119">Element</span></span>|<span data-ttu-id="13f16-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="13f16-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13f16-121">\<add></span><span class="sxs-lookup"><span data-stu-id="13f16-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-transportconfigurationtype.md)|<span data-ttu-id="13f16-122">Adiciona um elemento de configuração que identifica o tipo de um transporte particular.</span><span class="sxs-lookup"><span data-stu-id="13f16-122">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="13f16-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="13f16-123">Parent Elements</span></span>  
  
|<span data-ttu-id="13f16-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="13f16-124">Element</span></span>|<span data-ttu-id="13f16-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="13f16-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13f16-126">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="13f16-126">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="13f16-127">Define o tipo que o ambiente de hospedagem de serviço instancia para um transporte particular.</span><span class="sxs-lookup"><span data-stu-id="13f16-127">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="13f16-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13f16-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>  
 [<span data-ttu-id="13f16-129">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="13f16-129">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)

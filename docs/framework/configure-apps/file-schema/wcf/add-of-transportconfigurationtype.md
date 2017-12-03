---
title: '&lt;adicionar&gt; &lt;transportConfigurationType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b27994cae77ec012e0b432e702c9c2ccb1933b8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-lttransportconfigurationtypegt"></a><span data-ttu-id="ee801-102">&lt;adicionar&gt; &lt;transportConfigurationType&gt;</span><span class="sxs-lookup"><span data-stu-id="ee801-102">&lt;add&gt; of &lt;transportConfigurationType&gt;</span></span>
<span data-ttu-id="ee801-103">Esse elemento é um par chave/valor, que identifica o tipo de um transporte particular.</span><span class="sxs-lookup"><span data-stu-id="ee801-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
 <span data-ttu-id="ee801-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ee801-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ee801-105">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="ee801-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="ee801-106">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="ee801-106">\<transportConfigurationTypes></span></span>  
<span data-ttu-id="ee801-107">\<add></span><span class="sxs-lookup"><span data-stu-id="ee801-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee801-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ee801-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="String"  
               transportConfigurationType="String"/>   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee801-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ee801-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ee801-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ee801-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee801-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="ee801-111">Attributes</span></span>  
  
|<span data-ttu-id="ee801-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="ee801-112">Attribute</span></span>|<span data-ttu-id="ee801-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="ee801-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ee801-114">name</span><span class="sxs-lookup"><span data-stu-id="ee801-114">name</span></span>|<span data-ttu-id="ee801-115">Atributo de cadeia de caracteres obrigatório.</span><span class="sxs-lookup"><span data-stu-id="ee801-115">Required String attribute.</span></span><br /><br /> <span data-ttu-id="ee801-116">Contém uma chave definida pelo usuário que identifica exclusivamente o tipo de transporte.</span><span class="sxs-lookup"><span data-stu-id="ee801-116">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="ee801-117">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="ee801-117">transportConfigurationType</span></span>|<span data-ttu-id="ee801-118">Uma cadeia de caracteres que contém o tipo que implementa o transporte específico.</span><span class="sxs-lookup"><span data-stu-id="ee801-118">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ee801-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ee801-119">Child Elements</span></span>  
 <span data-ttu-id="ee801-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="ee801-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ee801-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ee801-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ee801-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="ee801-122">Element</span></span>|<span data-ttu-id="ee801-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="ee801-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee801-124">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="ee801-124">\<transportConfigurationTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|<span data-ttu-id="ee801-125">Uma coleção de tipos que implementam o transporte específico.</span><span class="sxs-lookup"><span data-stu-id="ee801-125">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ee801-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ee801-126">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="net.udp"  
      transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ee801-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee801-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="ee801-128">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="ee801-128">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)

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
ms.workload: dotnet
ms.openlocfilehash: 2b52345ae30ab56a6f34d2aa46f9836d67555b15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-lttransportconfigurationtypegt"></a><span data-ttu-id="29bf2-102">&lt;adicionar&gt; &lt;transportConfigurationType&gt;</span><span class="sxs-lookup"><span data-stu-id="29bf2-102">&lt;add&gt; of &lt;transportConfigurationType&gt;</span></span>
<span data-ttu-id="29bf2-103">Esse elemento é um par chave/valor, que identifica o tipo de um transporte particular.</span><span class="sxs-lookup"><span data-stu-id="29bf2-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
 <span data-ttu-id="29bf2-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="29bf2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="29bf2-105">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="29bf2-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="29bf2-106">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="29bf2-106">\<transportConfigurationTypes></span></span>  
<span data-ttu-id="29bf2-107">\<add></span><span class="sxs-lookup"><span data-stu-id="29bf2-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29bf2-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29bf2-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="String"  
               transportConfigurationType="String"/>   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29bf2-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="29bf2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="29bf2-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="29bf2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29bf2-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="29bf2-111">Attributes</span></span>  
  
|<span data-ttu-id="29bf2-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="29bf2-112">Attribute</span></span>|<span data-ttu-id="29bf2-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="29bf2-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="29bf2-114">name</span><span class="sxs-lookup"><span data-stu-id="29bf2-114">name</span></span>|<span data-ttu-id="29bf2-115">Atributo de cadeia de caracteres obrigatório.</span><span class="sxs-lookup"><span data-stu-id="29bf2-115">Required String attribute.</span></span><br /><br /> <span data-ttu-id="29bf2-116">Contém uma chave definida pelo usuário que identifica exclusivamente o tipo de transporte.</span><span class="sxs-lookup"><span data-stu-id="29bf2-116">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="29bf2-117">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="29bf2-117">transportConfigurationType</span></span>|<span data-ttu-id="29bf2-118">Uma cadeia de caracteres que contém o tipo que implementa o transporte específico.</span><span class="sxs-lookup"><span data-stu-id="29bf2-118">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29bf2-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="29bf2-119">Child Elements</span></span>  
 <span data-ttu-id="29bf2-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="29bf2-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="29bf2-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="29bf2-121">Parent Elements</span></span>  
  
|<span data-ttu-id="29bf2-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="29bf2-122">Element</span></span>|<span data-ttu-id="29bf2-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="29bf2-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29bf2-124">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="29bf2-124">\<transportConfigurationTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|<span data-ttu-id="29bf2-125">Uma coleção de tipos que implementam o transporte específico.</span><span class="sxs-lookup"><span data-stu-id="29bf2-125">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="29bf2-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="29bf2-126">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="net.udp"  
      transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="see-also"></a><span data-ttu-id="29bf2-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29bf2-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="29bf2-128">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="29bf2-128">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)

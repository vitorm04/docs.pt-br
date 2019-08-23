---
title: <add> de <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: 483ede53df13c896b88171910031dbe9793d66dc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920043"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="c150a-102">\<Adicionar > de \<transportConfigurationType ></span><span class="sxs-lookup"><span data-stu-id="c150a-102">\<add> of \<transportConfigurationType></span></span>
<span data-ttu-id="c150a-103">Esse elemento é um par chave/valor, que identifica o tipo de um transporte específico.</span><span class="sxs-lookup"><span data-stu-id="c150a-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
 <span data-ttu-id="c150a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c150a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c150a-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="c150a-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="c150a-106">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="c150a-106">\<transportConfigurationTypes></span></span>  
<span data-ttu-id="c150a-107">\<add></span><span class="sxs-lookup"><span data-stu-id="c150a-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c150a-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c150a-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c150a-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c150a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c150a-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c150a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c150a-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="c150a-111">Attributes</span></span>  
  
|<span data-ttu-id="c150a-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="c150a-112">Attribute</span></span>|<span data-ttu-id="c150a-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="c150a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c150a-114">name</span><span class="sxs-lookup"><span data-stu-id="c150a-114">name</span></span>|<span data-ttu-id="c150a-115">Atributo de cadeia de caracteres necessário.</span><span class="sxs-lookup"><span data-stu-id="c150a-115">Required String attribute.</span></span><br /><br /> <span data-ttu-id="c150a-116">Contém uma chave definida pelo usuário que identifica exclusivamente o tipo de transporte.</span><span class="sxs-lookup"><span data-stu-id="c150a-116">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="c150a-117">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="c150a-117">transportConfigurationType</span></span>|<span data-ttu-id="c150a-118">Uma cadeia de caracteres que contém o tipo que implementa o transporte específico.</span><span class="sxs-lookup"><span data-stu-id="c150a-118">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c150a-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c150a-119">Child Elements</span></span>  
 <span data-ttu-id="c150a-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c150a-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c150a-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c150a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c150a-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="c150a-122">Element</span></span>|<span data-ttu-id="c150a-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="c150a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c150a-124">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="c150a-124">\<transportConfigurationTypes></span></span>](transportconfigurationtypes.md)|<span data-ttu-id="c150a-125">Uma coleção de tipos que implementam o transporte específico.</span><span class="sxs-lookup"><span data-stu-id="c150a-125">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c150a-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c150a-126">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="c150a-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c150a-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="c150a-128">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="c150a-128">Hosting</span></span>](../../../wcf/feature-details/hosting.md)

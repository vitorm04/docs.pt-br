---
title: '&lt;adicionar&gt; &lt;transportConfigurationType&gt;'
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: 1079b25ce137dc89fc31f46a11f3720486462021
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149131"
---
# <a name="ltaddgt-of-lttransportconfigurationtypegt"></a><span data-ttu-id="de9b9-102">&lt;adicionar&gt; &lt;transportConfigurationType&gt;</span><span class="sxs-lookup"><span data-stu-id="de9b9-102">&lt;add&gt; of &lt;transportConfigurationType&gt;</span></span>
<span data-ttu-id="de9b9-103">Esse elemento é um par chave/valor, que identifica o tipo de um transporte particular.</span><span class="sxs-lookup"><span data-stu-id="de9b9-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
 <span data-ttu-id="de9b9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="de9b9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="de9b9-105">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="de9b9-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="de9b9-106">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="de9b9-106">\<transportConfigurationTypes></span></span>  
<span data-ttu-id="de9b9-107">\<add></span><span class="sxs-lookup"><span data-stu-id="de9b9-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de9b9-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="de9b9-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de9b9-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="de9b9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="de9b9-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="de9b9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de9b9-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="de9b9-111">Attributes</span></span>  
  
|<span data-ttu-id="de9b9-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="de9b9-112">Attribute</span></span>|<span data-ttu-id="de9b9-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="de9b9-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="de9b9-114">name</span><span class="sxs-lookup"><span data-stu-id="de9b9-114">name</span></span>|<span data-ttu-id="de9b9-115">Atributo de cadeia de caracteres obrigatório.</span><span class="sxs-lookup"><span data-stu-id="de9b9-115">Required String attribute.</span></span><br /><br /> <span data-ttu-id="de9b9-116">Contém uma chave definida pelo usuário que identifica exclusivamente o tipo de transporte.</span><span class="sxs-lookup"><span data-stu-id="de9b9-116">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="de9b9-117">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="de9b9-117">transportConfigurationType</span></span>|<span data-ttu-id="de9b9-118">Uma cadeia de caracteres que contém o tipo que implementa o transporte específico.</span><span class="sxs-lookup"><span data-stu-id="de9b9-118">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de9b9-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="de9b9-119">Child Elements</span></span>  
 <span data-ttu-id="de9b9-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="de9b9-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de9b9-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="de9b9-121">Parent Elements</span></span>  
  
|<span data-ttu-id="de9b9-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="de9b9-122">Element</span></span>|<span data-ttu-id="de9b9-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="de9b9-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de9b9-124">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="de9b9-124">\<transportConfigurationTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|<span data-ttu-id="de9b9-125">Uma coleção de tipos que implementam o transporte específico.</span><span class="sxs-lookup"><span data-stu-id="de9b9-125">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="de9b9-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="de9b9-126">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="de9b9-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de9b9-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="de9b9-128">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="de9b9-128">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)

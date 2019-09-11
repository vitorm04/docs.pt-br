---
title: <add> de <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: adf4cd7f02db6535c5950443d09476a9a5ff63fb
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850312"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="4e039-102">\<Adicionar > de \<transportConfigurationType ></span><span class="sxs-lookup"><span data-stu-id="4e039-102">\<add> of \<transportConfigurationType></span></span>
<span data-ttu-id="4e039-103">Esse elemento é um par chave/valor, que identifica o tipo de um transporte específico.</span><span class="sxs-lookup"><span data-stu-id="4e039-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
<span data-ttu-id="4e039-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4e039-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4e039-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4e039-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4e039-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de ServiceHostingEnvironment**](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="4e039-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="4e039-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> transportConfigurationTypes**](transportconfigurationtypes.md)</span><span class="sxs-lookup"><span data-stu-id="4e039-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<transportConfigurationTypes>**](transportconfigurationtypes.md)</span></span>\
<span data-ttu-id="4e039-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adicionar >**</span><span class="sxs-lookup"><span data-stu-id="4e039-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e039-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4e039-109">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e039-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4e039-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4e039-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4e039-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e039-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="4e039-112">Attributes</span></span>  
  
|<span data-ttu-id="4e039-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="4e039-113">Attribute</span></span>|<span data-ttu-id="4e039-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="4e039-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4e039-115">name</span><span class="sxs-lookup"><span data-stu-id="4e039-115">name</span></span>|<span data-ttu-id="4e039-116">Atributo de cadeia de caracteres necessário.</span><span class="sxs-lookup"><span data-stu-id="4e039-116">Required String attribute.</span></span><br /><br /> <span data-ttu-id="4e039-117">Contém uma chave definida pelo usuário que identifica exclusivamente o tipo de transporte.</span><span class="sxs-lookup"><span data-stu-id="4e039-117">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="4e039-118">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="4e039-118">transportConfigurationType</span></span>|<span data-ttu-id="4e039-119">Uma cadeia de caracteres que contém o tipo que implementa o transporte específico.</span><span class="sxs-lookup"><span data-stu-id="4e039-119">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4e039-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4e039-120">Child Elements</span></span>  
 <span data-ttu-id="4e039-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="4e039-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4e039-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4e039-122">Parent Elements</span></span>  
  
|<span data-ttu-id="4e039-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="4e039-123">Element</span></span>|<span data-ttu-id="4e039-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="4e039-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4e039-125">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="4e039-125">\<transportConfigurationTypes></span></span>](transportconfigurationtypes.md)|<span data-ttu-id="4e039-126">Uma coleção de tipos que implementam o transporte específico.</span><span class="sxs-lookup"><span data-stu-id="4e039-126">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4e039-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4e039-127">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="4e039-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4e039-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="4e039-129">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="4e039-129">Hosting</span></span>](../../../wcf/feature-details/hosting.md)

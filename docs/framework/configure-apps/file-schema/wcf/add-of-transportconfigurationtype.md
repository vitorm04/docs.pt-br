---
title: <add> de <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: 9bef44ed39ee892080342058206f779b38fb460d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151149"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="7cfbb-102">\<add> de \<transportConfigurationType></span><span class="sxs-lookup"><span data-stu-id="7cfbb-102">\<add> of \<transportConfigurationType></span></span>

<span data-ttu-id="7cfbb-103">Esse elemento é um par chave/valor, que identifica o tipo de um transporte específico.</span><span class="sxs-lookup"><span data-stu-id="7cfbb-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<transportConfigurationTypes>**](transportconfigurationtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="7cfbb-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="7cfbb-104">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7cfbb-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7cfbb-105">Attributes and Elements</span></span>  

 <span data-ttu-id="7cfbb-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7cfbb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7cfbb-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="7cfbb-107">Attributes</span></span>  
  
|<span data-ttu-id="7cfbb-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="7cfbb-108">Attribute</span></span>|<span data-ttu-id="7cfbb-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="7cfbb-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7cfbb-110">name</span><span class="sxs-lookup"><span data-stu-id="7cfbb-110">name</span></span>|<span data-ttu-id="7cfbb-111">Atributo String obrigatório.</span><span class="sxs-lookup"><span data-stu-id="7cfbb-111">Required String attribute.</span></span><br /><br /> <span data-ttu-id="7cfbb-112">Contém uma chave definida pelo usuário que identifica exclusivamente o tipo de transporte.</span><span class="sxs-lookup"><span data-stu-id="7cfbb-112">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="7cfbb-113">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="7cfbb-113">transportConfigurationType</span></span>|<span data-ttu-id="7cfbb-114">Uma cadeia de caracteres que contém o tipo que implementa o transporte específico.</span><span class="sxs-lookup"><span data-stu-id="7cfbb-114">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7cfbb-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7cfbb-115">Child Elements</span></span>  

 <span data-ttu-id="7cfbb-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="7cfbb-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7cfbb-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7cfbb-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7cfbb-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="7cfbb-118">Element</span></span>|<span data-ttu-id="7cfbb-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="7cfbb-119">Description</span></span>|  
|-------------|-----------------|  
|[\<transportConfigurationTypes>](transportconfigurationtypes.md)|<span data-ttu-id="7cfbb-120">Uma coleção de tipos que implementam o transporte específico.</span><span class="sxs-lookup"><span data-stu-id="7cfbb-120">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7cfbb-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7cfbb-121">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="7cfbb-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="7cfbb-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="7cfbb-123">Hosting</span><span class="sxs-lookup"><span data-stu-id="7cfbb-123">Hosting</span></span>](../../../wcf/feature-details/hosting.md)

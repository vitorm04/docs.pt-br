---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 7760ee4d3b118e339944317e8ec8d8217b5d909d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855115"
---
# \<mexEndpoint>
<span data-ttu-id="0c5cf-101">Este elemento de configuração define um ponto de extremidade padrão com um contrato IMetadataExchange fixo.</span><span class="sxs-lookup"><span data-stu-id="0c5cf-101">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="0c5cf-102">Como todos os pontos de extremidade de troca de metadados especificam IMetadataExchange como seu contrato, você pode usar esse ponto padrão em vez de definir um para você mesmo.</span><span class="sxs-lookup"><span data-stu-id="0c5cf-102">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="0c5cf-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0c5cf-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c5cf-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0c5cf-104">Attributes and Elements</span></span>  
 <span data-ttu-id="0c5cf-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0c5cf-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c5cf-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="0c5cf-106">Attributes</span></span>  
  
|<span data-ttu-id="0c5cf-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="0c5cf-107">Attribute</span></span>|<span data-ttu-id="0c5cf-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c5cf-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0c5cf-109">name</span><span class="sxs-lookup"><span data-stu-id="0c5cf-109">name</span></span>|<span data-ttu-id="0c5cf-110">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="0c5cf-110">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="0c5cf-111">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular um ponto de extremidade padrão à sua configuração.</span><span class="sxs-lookup"><span data-stu-id="0c5cf-111">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c5cf-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0c5cf-112">Child Elements</span></span>  
 <span data-ttu-id="0c5cf-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0c5cf-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c5cf-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0c5cf-114">Parent Elements</span></span>  
  
|<span data-ttu-id="0c5cf-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="0c5cf-115">Element</span></span>|<span data-ttu-id="0c5cf-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c5cf-116">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="0c5cf-117">Uma coleção de pontos de extremidade padrão que são pontos de extremidade predefinidos com uma ou mais de suas propriedades (endereço, associação, contrato) fixa.</span><span class="sxs-lookup"><span data-stu-id="0c5cf-117">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|

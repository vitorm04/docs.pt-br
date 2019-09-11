---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 7760ee4d3b118e339944317e8ec8d8217b5d909d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855115"
---
# <a name="mexendpoint"></a><span data-ttu-id="b1b08-101">\<mexEndpoint></span><span class="sxs-lookup"><span data-stu-id="b1b08-101">\<mexEndpoint></span></span>
<span data-ttu-id="b1b08-102">Este elemento de configuração define um ponto de extremidade padrão com um contrato IMetadataExchange fixo.</span><span class="sxs-lookup"><span data-stu-id="b1b08-102">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="b1b08-103">Como todos os pontos de extremidade de troca de metadados especificam IMetadataExchange como seu contrato, você pode usar esse ponto padrão em vez de definir um para você mesmo.</span><span class="sxs-lookup"><span data-stu-id="b1b08-103">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
<span data-ttu-id="b1b08-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b1b08-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b1b08-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b1b08-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b1b08-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> standardEndpoints**](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="b1b08-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="b1b08-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> mexEndpoint**</span><span class="sxs-lookup"><span data-stu-id="b1b08-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1b08-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1b08-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1b08-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b1b08-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b1b08-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b1b08-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1b08-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="b1b08-111">Attributes</span></span>  
  
|<span data-ttu-id="b1b08-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="b1b08-112">Attribute</span></span>|<span data-ttu-id="b1b08-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1b08-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b1b08-114">name</span><span class="sxs-lookup"><span data-stu-id="b1b08-114">name</span></span>|<span data-ttu-id="b1b08-115">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="b1b08-115">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="b1b08-116">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular um ponto de extremidade padrão à sua configuração.</span><span class="sxs-lookup"><span data-stu-id="b1b08-116">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1b08-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b1b08-117">Child Elements</span></span>  
 <span data-ttu-id="b1b08-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b1b08-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b1b08-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b1b08-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b1b08-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="b1b08-120">Element</span></span>|<span data-ttu-id="b1b08-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1b08-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1b08-122">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="b1b08-122">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="b1b08-123">Uma coleção de pontos de extremidade padrão que são pontos de extremidade predefinidos com uma ou mais de suas propriedades (endereço, associação, contrato) fixa.</span><span class="sxs-lookup"><span data-stu-id="b1b08-123">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|

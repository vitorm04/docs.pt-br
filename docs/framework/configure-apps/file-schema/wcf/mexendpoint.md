---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: e8f0e0fa2ea1606bf980fd6fa1fcd47f12c3b540
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204743"
---
# \<mexEndpoint>

<span data-ttu-id="0d9c5-101">Este elemento de configuração define um ponto de extremidade padrão com um contrato IMetadataExchange fixo.</span><span class="sxs-lookup"><span data-stu-id="0d9c5-101">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="0d9c5-102">Como todos os pontos de extremidade de troca de metadados especificam IMetadataExchange como seu contrato, você pode usar esse ponto padrão em vez de definir um para você mesmo.</span><span class="sxs-lookup"><span data-stu-id="0d9c5-102">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="0d9c5-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d9c5-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d9c5-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0d9c5-104">Attributes and Elements</span></span>  

 <span data-ttu-id="0d9c5-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0d9c5-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d9c5-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="0d9c5-106">Attributes</span></span>  
  
|<span data-ttu-id="0d9c5-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="0d9c5-107">Attribute</span></span>|<span data-ttu-id="0d9c5-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d9c5-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0d9c5-109">name</span><span class="sxs-lookup"><span data-stu-id="0d9c5-109">name</span></span>|<span data-ttu-id="0d9c5-110">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="0d9c5-110">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="0d9c5-111">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular um ponto de extremidade padrão à sua configuração.</span><span class="sxs-lookup"><span data-stu-id="0d9c5-111">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d9c5-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0d9c5-112">Child Elements</span></span>  

 <span data-ttu-id="0d9c5-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0d9c5-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0d9c5-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0d9c5-114">Parent Elements</span></span>  
  
|<span data-ttu-id="0d9c5-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="0d9c5-115">Element</span></span>|<span data-ttu-id="0d9c5-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d9c5-116">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="0d9c5-117">Uma coleção de pontos de extremidade padrão que são pontos de extremidade predefinidos com uma ou mais de suas propriedades (endereço, associação, contrato) fixa.</span><span class="sxs-lookup"><span data-stu-id="0d9c5-117">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|

---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 8814a48df8933cf08db78e397c24d42f2da26026
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919226"
---
# <a name="datacontractserializer"></a><span data-ttu-id="f3b5a-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="f3b5a-102">dataContractSerializer</span></span>
<span data-ttu-id="f3b5a-103">Contém dados de configuração para <xref:System.Runtime.Serialization.DataContractSerializer>o.</span><span class="sxs-lookup"><span data-stu-id="f3b5a-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="f3b5a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f3b5a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f3b5a-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="f3b5a-105">\<behaviors></span></span>  
<span data-ttu-id="f3b5a-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="f3b5a-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="f3b5a-107">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="f3b5a-107">\<behavior></span></span>  
<span data-ttu-id="f3b5a-108">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="f3b5a-108">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3b5a-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f3b5a-109">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3b5a-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f3b5a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f3b5a-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f3b5a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3b5a-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="f3b5a-112">Attributes</span></span>  
  
|<span data-ttu-id="f3b5a-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="f3b5a-113">Element</span></span>|<span data-ttu-id="f3b5a-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="f3b5a-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f3b5a-115">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="f3b5a-115">ignoreExtensionDataObject</span></span>|<span data-ttu-id="f3b5a-116">Um valor booliano que especifica se os dados fornecidos pelo ponto de extremidade devem ser ignorados, quando ele está sendo serializado ou desserializado.</span><span class="sxs-lookup"><span data-stu-id="f3b5a-116">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="f3b5a-117">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="f3b5a-117">maxItemsInObjectGraph</span></span>|<span data-ttu-id="f3b5a-118">Um inteiro que especifica o número máximo de itens a serem serializados ou desserializados.</span><span class="sxs-lookup"><span data-stu-id="f3b5a-118">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3b5a-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f3b5a-119">Child Elements</span></span>  
 <span data-ttu-id="f3b5a-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f3b5a-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3b5a-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f3b5a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f3b5a-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="f3b5a-122">Element</span></span>|<span data-ttu-id="f3b5a-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="f3b5a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3b5a-124">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="f3b5a-124">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="f3b5a-125">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="f3b5a-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3b5a-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="f3b5a-126">Remarks</span></span>  
 <span data-ttu-id="f3b5a-127">Consulte a <xref:System.Runtime.Serialization.DataContractSerializer> documentação para obter mais informações sobre tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="f3b5a-127">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="f3b5a-128">O `<dataContractSerializer>` elemento Behavior (se presente) sempre deve aparecer antes do `<enableWebScript>` elemento Behavior no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="f3b5a-128">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="f3b5a-129">Caso contrário, o comportamento resultante será indefinido.</span><span class="sxs-lookup"><span data-stu-id="f3b5a-129">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3b5a-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3b5a-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="f3b5a-131">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="f3b5a-131">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="f3b5a-132">Serialização e transferência de dados</span><span class="sxs-lookup"><span data-stu-id="f3b5a-132">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)

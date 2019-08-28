---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 7952e6cc4d2fe7eaa77e297a650f7ffbd7aec785
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040936"
---
# <a name="datacontractserializer"></a><span data-ttu-id="5203e-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="5203e-102">dataContractSerializer</span></span>
<span data-ttu-id="5203e-103">Contém dados de configuração para <xref:System.Runtime.Serialization.DataContractSerializer>o.</span><span class="sxs-lookup"><span data-stu-id="5203e-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="5203e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5203e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5203e-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="5203e-105">\<behaviors></span></span>  
<span data-ttu-id="5203e-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="5203e-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="5203e-107">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="5203e-107">\<behavior></span></span>  
<span data-ttu-id="5203e-108">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="5203e-108">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5203e-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5203e-109">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5203e-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5203e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5203e-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5203e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5203e-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="5203e-112">Attributes</span></span>  
  
|<span data-ttu-id="5203e-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="5203e-113">Element</span></span>|<span data-ttu-id="5203e-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="5203e-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5203e-115">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="5203e-115">ignoreExtensionDataObject</span></span>|<span data-ttu-id="5203e-116">Um valor booliano que especifica se os dados fornecidos pelo ponto de extremidade devem ser ignorados, quando ele está sendo serializado ou desserializado.</span><span class="sxs-lookup"><span data-stu-id="5203e-116">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="5203e-117">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="5203e-117">maxItemsInObjectGraph</span></span>|<span data-ttu-id="5203e-118">Um inteiro que especifica o número máximo de itens a serem serializados ou desserializados.</span><span class="sxs-lookup"><span data-stu-id="5203e-118">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5203e-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5203e-119">Child Elements</span></span>  
 <span data-ttu-id="5203e-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5203e-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5203e-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5203e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5203e-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="5203e-122">Element</span></span>|<span data-ttu-id="5203e-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="5203e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5203e-124">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="5203e-124">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="5203e-125">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="5203e-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5203e-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="5203e-126">Remarks</span></span>  
 <span data-ttu-id="5203e-127">Consulte a <xref:System.Runtime.Serialization.DataContractSerializer> documentação para obter mais informações sobre tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="5203e-127">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="5203e-128">O `<dataContractSerializer>` elemento Behavior (se presente) sempre deve aparecer antes do `<enableWebScript>` elemento Behavior no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="5203e-128">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="5203e-129">Caso contrário, o comportamento resultante será indefinido.</span><span class="sxs-lookup"><span data-stu-id="5203e-129">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5203e-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5203e-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="5203e-131">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="5203e-131">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="5203e-132">Serialização e transferência de dados</span><span class="sxs-lookup"><span data-stu-id="5203e-132">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)

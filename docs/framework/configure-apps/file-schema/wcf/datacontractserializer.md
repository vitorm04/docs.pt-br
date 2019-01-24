---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 933d49092c392fa293468d546e521bf7ed858376
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539838"
---
# <a name="datacontractserializer"></a><span data-ttu-id="1875f-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="1875f-102">dataContractSerializer</span></span>
<span data-ttu-id="1875f-103">Contém dados de configuração para o <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="1875f-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="1875f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1875f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1875f-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="1875f-105">\<behaviors></span></span>  
<span data-ttu-id="1875f-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="1875f-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="1875f-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="1875f-107">\<behavior></span></span>  
<span data-ttu-id="1875f-108">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="1875f-108">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1875f-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1875f-109">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1875f-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1875f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1875f-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1875f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1875f-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="1875f-112">Attributes</span></span>  
  
|<span data-ttu-id="1875f-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="1875f-113">Element</span></span>|<span data-ttu-id="1875f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="1875f-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1875f-115">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="1875f-115">ignoreExtensionDataObject</span></span>|<span data-ttu-id="1875f-116">Um valor booliano que especifica se deve ignorar os dados fornecidos pelo ponto de extremidade, quando ele está sendo serializado ou desserializado.</span><span class="sxs-lookup"><span data-stu-id="1875f-116">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="1875f-117">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="1875f-117">maxItemsInObjectGraph</span></span>|<span data-ttu-id="1875f-118">Um inteiro que especifica o número máximo de itens para serializar ou desserializar.</span><span class="sxs-lookup"><span data-stu-id="1875f-118">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1875f-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1875f-119">Child Elements</span></span>  
 <span data-ttu-id="1875f-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="1875f-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1875f-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1875f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="1875f-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="1875f-122">Element</span></span>|<span data-ttu-id="1875f-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="1875f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1875f-124">\<behavior></span><span class="sxs-lookup"><span data-stu-id="1875f-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="1875f-125">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="1875f-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1875f-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="1875f-126">Remarks</span></span>  
 <span data-ttu-id="1875f-127">Consulte o <xref:System.Runtime.Serialization.DataContractSerializer> documentação para obter mais informações sobre tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="1875f-127">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="1875f-128">O `<dataContractSerializer>` elemento de comportamento (se houver) sempre deverá aparecer antes do `<enableWebScript>` elemento de comportamento no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="1875f-128">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="1875f-129">Caso contrário, o comportamento resultante será indefinido.</span><span class="sxs-lookup"><span data-stu-id="1875f-129">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1875f-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1875f-130">See also</span></span>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="1875f-131">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="1875f-131">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="1875f-132">Serialização e transferência de dados</span><span class="sxs-lookup"><span data-stu-id="1875f-132">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)

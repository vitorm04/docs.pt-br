---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 8ba16d9cc30b07d3e6b0924e6013ec01443867d4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59139042"
---
# <a name="datacontractserializer"></a><span data-ttu-id="60ad0-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="60ad0-102">dataContractSerializer</span></span>
<span data-ttu-id="60ad0-103">Contém dados de configuração para o <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="60ad0-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="60ad0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="60ad0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="60ad0-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="60ad0-105">\<behaviors></span></span>  
<span data-ttu-id="60ad0-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="60ad0-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="60ad0-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="60ad0-107">\<behavior></span></span>  
<span data-ttu-id="60ad0-108">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="60ad0-108">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60ad0-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="60ad0-109">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60ad0-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="60ad0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="60ad0-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="60ad0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60ad0-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="60ad0-112">Attributes</span></span>  
  
|<span data-ttu-id="60ad0-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="60ad0-113">Element</span></span>|<span data-ttu-id="60ad0-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="60ad0-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="60ad0-115">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="60ad0-115">ignoreExtensionDataObject</span></span>|<span data-ttu-id="60ad0-116">Um valor booliano que especifica se deve ignorar os dados fornecidos pelo ponto de extremidade, quando ele está sendo serializado ou desserializado.</span><span class="sxs-lookup"><span data-stu-id="60ad0-116">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="60ad0-117">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="60ad0-117">maxItemsInObjectGraph</span></span>|<span data-ttu-id="60ad0-118">Um inteiro que especifica o número máximo de itens para serializar ou desserializar.</span><span class="sxs-lookup"><span data-stu-id="60ad0-118">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="60ad0-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="60ad0-119">Child Elements</span></span>  
 <span data-ttu-id="60ad0-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="60ad0-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="60ad0-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="60ad0-121">Parent Elements</span></span>  
  
|<span data-ttu-id="60ad0-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="60ad0-122">Element</span></span>|<span data-ttu-id="60ad0-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="60ad0-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60ad0-124">\<behavior></span><span class="sxs-lookup"><span data-stu-id="60ad0-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="60ad0-125">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="60ad0-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60ad0-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="60ad0-126">Remarks</span></span>  
 <span data-ttu-id="60ad0-127">Consulte o <xref:System.Runtime.Serialization.DataContractSerializer> documentação para obter mais informações sobre tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="60ad0-127">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="60ad0-128">O `<dataContractSerializer>` elemento de comportamento (se houver) sempre deverá aparecer antes do `<enableWebScript>` elemento de comportamento no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="60ad0-128">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="60ad0-129">Caso contrário, o comportamento resultante será indefinido.</span><span class="sxs-lookup"><span data-stu-id="60ad0-129">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60ad0-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60ad0-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="60ad0-131">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="60ad0-131">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="60ad0-132">Serialização e transferência de dados</span><span class="sxs-lookup"><span data-stu-id="60ad0-132">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)

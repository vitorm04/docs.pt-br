---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: a024ca89bd766681f25b992f1d2c66a92e3b31b7
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150195"
---
# <a name="datacontractserializer"></a><span data-ttu-id="88ed4-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="88ed4-102">dataContractSerializer</span></span>
<span data-ttu-id="88ed4-103">Contém dados de configuração para o <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="88ed4-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="88ed4-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="88ed4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="88ed4-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="88ed4-105">\<behaviors></span></span>  
<span data-ttu-id="88ed4-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="88ed4-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="88ed4-107">\<comportamento de ></span><span class="sxs-lookup"><span data-stu-id="88ed4-107">\<behavior></span></span>  
<span data-ttu-id="88ed4-108">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="88ed4-108">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88ed4-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="88ed4-109">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88ed4-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="88ed4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="88ed4-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="88ed4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88ed4-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="88ed4-112">Attributes</span></span>  
  
|<span data-ttu-id="88ed4-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="88ed4-113">Element</span></span>|<span data-ttu-id="88ed4-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="88ed4-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="88ed4-115">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="88ed4-115">ignoreExtensionDataObject</span></span>|<span data-ttu-id="88ed4-116">Um valor booliano que especifica se deve ignorar os dados fornecidos pelo ponto de extremidade, quando ele está sendo serializado ou desserializado.</span><span class="sxs-lookup"><span data-stu-id="88ed4-116">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="88ed4-117">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="88ed4-117">maxItemsInObjectGraph</span></span>|<span data-ttu-id="88ed4-118">Um inteiro que especifica o número máximo de itens para serializar ou desserializar.</span><span class="sxs-lookup"><span data-stu-id="88ed4-118">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="88ed4-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="88ed4-119">Child Elements</span></span>  
 <span data-ttu-id="88ed4-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="88ed4-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="88ed4-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="88ed4-121">Parent Elements</span></span>  
  
|<span data-ttu-id="88ed4-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="88ed4-122">Element</span></span>|<span data-ttu-id="88ed4-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="88ed4-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="88ed4-124">\<comportamento de ></span><span class="sxs-lookup"><span data-stu-id="88ed4-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="88ed4-125">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="88ed4-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88ed4-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="88ed4-126">Remarks</span></span>  
 <span data-ttu-id="88ed4-127">Consulte o <xref:System.Runtime.Serialization.DataContractSerializer> documentação para obter mais informações sobre tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="88ed4-127">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="88ed4-128">O `<dataContractSerializer>` elemento de comportamento (se houver) sempre deverá aparecer antes do `<enableWebScript>` elemento de comportamento no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="88ed4-128">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="88ed4-129">Caso contrário, o comportamento resultante será indefinido.</span><span class="sxs-lookup"><span data-stu-id="88ed4-129">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88ed4-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88ed4-130">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.ServiceModel.Configuration.DataContractSerializerElement>  
 [<span data-ttu-id="88ed4-131">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="88ed4-131">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="88ed4-132">Serialização e transferência de dados</span><span class="sxs-lookup"><span data-stu-id="88ed4-132">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)

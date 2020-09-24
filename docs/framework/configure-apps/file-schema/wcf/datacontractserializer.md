---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 0e4cbc50c25d4fa1f67f283f2b52d4b174428cd3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153918"
---
# <a name="datacontractserializer"></a><span data-ttu-id="796a9-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="796a9-102">dataContractSerializer</span></span>

<span data-ttu-id="796a9-103">Contém dados de configuração para o <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="796a9-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="796a9-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="796a9-104">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="796a9-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="796a9-105">Attributes and Elements</span></span>  

 <span data-ttu-id="796a9-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="796a9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="796a9-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="796a9-107">Attributes</span></span>  
  
|<span data-ttu-id="796a9-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="796a9-108">Element</span></span>|<span data-ttu-id="796a9-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="796a9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="796a9-110">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="796a9-110">ignoreExtensionDataObject</span></span>|<span data-ttu-id="796a9-111">Um valor booliano que especifica se os dados fornecidos pelo ponto de extremidade devem ser ignorados, quando ele está sendo serializado ou desserializado.</span><span class="sxs-lookup"><span data-stu-id="796a9-111">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="796a9-112">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="796a9-112">maxItemsInObjectGraph</span></span>|<span data-ttu-id="796a9-113">Um inteiro que especifica o número máximo de itens a serem serializados ou desserializados.</span><span class="sxs-lookup"><span data-stu-id="796a9-113">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="796a9-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="796a9-114">Child Elements</span></span>  

 <span data-ttu-id="796a9-115">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="796a9-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="796a9-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="796a9-116">Parent Elements</span></span>  
  
|<span data-ttu-id="796a9-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="796a9-117">Element</span></span>|<span data-ttu-id="796a9-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="796a9-118">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="796a9-119">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="796a9-119">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="796a9-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="796a9-120">Remarks</span></span>  

 <span data-ttu-id="796a9-121">Consulte a <xref:System.Runtime.Serialization.DataContractSerializer> documentação para obter mais informações sobre tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="796a9-121">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="796a9-122">O `<dataContractSerializer>` elemento Behavior (se presente) sempre deve aparecer antes do `<enableWebScript>` elemento Behavior no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="796a9-122">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="796a9-123">Caso contrário, o comportamento resultante será indefinido.</span><span class="sxs-lookup"><span data-stu-id="796a9-123">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="796a9-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="796a9-124">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="796a9-125">Tipos de contratos de dados conhecidos</span><span class="sxs-lookup"><span data-stu-id="796a9-125">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="796a9-126">Serialização e transferência de dados</span><span class="sxs-lookup"><span data-stu-id="796a9-126">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)

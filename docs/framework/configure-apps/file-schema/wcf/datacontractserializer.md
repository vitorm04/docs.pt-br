---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: e6524c18780c062c3b5b7dfc2509449cb208e270
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400440"
---
# <a name="datacontractserializer"></a><span data-ttu-id="64afa-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="64afa-102">dataContractSerializer</span></span>
<span data-ttu-id="64afa-103">Contém dados de configuração para o <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="64afa-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="64afa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="64afa-104">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64afa-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="64afa-105">Attributes and Elements</span></span>  
 <span data-ttu-id="64afa-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="64afa-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64afa-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="64afa-107">Attributes</span></span>  
  
|<span data-ttu-id="64afa-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="64afa-108">Element</span></span>|<span data-ttu-id="64afa-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="64afa-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="64afa-110">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="64afa-110">ignoreExtensionDataObject</span></span>|<span data-ttu-id="64afa-111">Um valor booliano que especifica se os dados fornecidos pelo ponto de extremidade devem ser ignorados, quando ele está sendo serializado ou desserializado.</span><span class="sxs-lookup"><span data-stu-id="64afa-111">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="64afa-112">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="64afa-112">maxItemsInObjectGraph</span></span>|<span data-ttu-id="64afa-113">Um inteiro que especifica o número máximo de itens a serem serializados ou desserializados.</span><span class="sxs-lookup"><span data-stu-id="64afa-113">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="64afa-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="64afa-114">Child Elements</span></span>  
 <span data-ttu-id="64afa-115">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="64afa-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="64afa-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="64afa-116">Parent Elements</span></span>  
  
|<span data-ttu-id="64afa-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="64afa-117">Element</span></span>|<span data-ttu-id="64afa-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="64afa-118">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="64afa-119">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="64afa-119">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64afa-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="64afa-120">Remarks</span></span>  
 <span data-ttu-id="64afa-121">Consulte a <xref:System.Runtime.Serialization.DataContractSerializer> documentação para obter mais informações sobre tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="64afa-121">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="64afa-122">O `<dataContractSerializer>` elemento Behavior (se presente) sempre deve aparecer antes do `<enableWebScript>` elemento Behavior no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="64afa-122">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="64afa-123">Caso contrário, o comportamento resultante será indefinido.</span><span class="sxs-lookup"><span data-stu-id="64afa-123">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64afa-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="64afa-124">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="64afa-125">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="64afa-125">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="64afa-126">Serialização e transferência de dados</span><span class="sxs-lookup"><span data-stu-id="64afa-126">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)

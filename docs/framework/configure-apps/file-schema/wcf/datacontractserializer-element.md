---
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: 2a994a8ba97d4c65fdaba5a85e779dd9935e3074
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195020"
---
# \<dataContractSerializer>

<span data-ttu-id="06e06-101">Contém dados de configuração para o <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="06e06-101">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="06e06-102">Esse elemento ocorre em duas hierarquias diferentes.</span><span class="sxs-lookup"><span data-stu-id="06e06-102">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="06e06-103">Uma é listada na seção hierarquia de esquema a seguir e a outra é listada na seção comentários.</span><span class="sxs-lookup"><span data-stu-id="06e06-103">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="06e06-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="06e06-104">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06e06-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="06e06-105">Attributes and Elements</span></span>  

 <span data-ttu-id="06e06-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="06e06-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06e06-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="06e06-107">Attributes</span></span>  
  
|<span data-ttu-id="06e06-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="06e06-108">Element</span></span>|<span data-ttu-id="06e06-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="06e06-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="06e06-110">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="06e06-110">ignoreExtensionDataObject</span></span>|<span data-ttu-id="06e06-111">Um valor booliano que especifica se é para ignorar os dados fornecidos pelo ponto de extremidade quando ele está sendo serializado ou desserializado.</span><span class="sxs-lookup"><span data-stu-id="06e06-111">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="06e06-112">Esse atributo é configurável somente no `<dataContractSerializer>` `<behavior>` elemento abaixo.</span><span class="sxs-lookup"><span data-stu-id="06e06-112">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="06e06-113">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="06e06-113">maxItemsInObjectGraph</span></span>|<span data-ttu-id="06e06-114">Um inteiro que especifica o número máximo de itens a serem serializados ou desserializados.</span><span class="sxs-lookup"><span data-stu-id="06e06-114">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="06e06-115">Esse atributo é 65536.</span><span class="sxs-lookup"><span data-stu-id="06e06-115">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="06e06-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="06e06-116">Child Elements</span></span>  

 <span data-ttu-id="06e06-117">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="06e06-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="06e06-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="06e06-118">Parent Elements</span></span>  
  
|<span data-ttu-id="06e06-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="06e06-119">Element</span></span>|<span data-ttu-id="06e06-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="06e06-120">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-servicebehaviors.md)|<span data-ttu-id="06e06-121">Uma coleção de configurações para o comportamento de um serviço.</span><span class="sxs-lookup"><span data-stu-id="06e06-121">A collection of settings for the behavior of a service.</span></span>|  
|[\<system.runtime.serialization>](system-runtime-serialization.md)|<span data-ttu-id="06e06-122">Representa o elemento raiz da <xref:System.Runtime.Serialization> seção namespace e contém elementos para definir as opções do <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="06e06-122">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06e06-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="06e06-123">Remarks</span></span>  

 <span data-ttu-id="06e06-124">Conforme indicado na introdução deste tópico, esta é a segunda hierarquia na qual o \<X509Extension> elemento ocorre.</span><span class="sxs-lookup"><span data-stu-id="06e06-124">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [\<system.runtime.serialization>](system-runtime-serialization.md)  
  
 [\<dataContractSerializer>](datacontractserializer-element.md)  
  
 <span data-ttu-id="06e06-125">Para obter mais informações sobre tipos conhecidos, consulte <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="06e06-125">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06e06-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="06e06-126">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="06e06-127">Tipos de contratos de dados conhecidos</span><span class="sxs-lookup"><span data-stu-id="06e06-127">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="06e06-128">Serialização e transferência de dados</span><span class="sxs-lookup"><span data-stu-id="06e06-128">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)

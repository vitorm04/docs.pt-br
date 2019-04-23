---
title: <AttributeImplies> (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d59f1f48be19a21ccc7ee5bb73cebfffc387fec2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59165055"
---
# <a name="attributeimplies-element-net-native"></a><span data-ttu-id="30b16-102">\<AttributeImplies > (.NET nativo)</span><span class="sxs-lookup"><span data-stu-id="30b16-102">\<AttributeImplies> Element (.NET Native)</span></span>
<span data-ttu-id="30b16-103">Define a política para os elementos de código ao qual o atributo recipiente é aplicado.</span><span class="sxs-lookup"><span data-stu-id="30b16-103">Defines policy for code elements the containing attribute is applied to.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30b16-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30b16-104">Syntax</span></span>  
  
```xml  
<AttributeImplies Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type"   
                  DataContractSerializer="policy_setting"  
                  DataContractJsonSerializer="policy_setting"  
                  XmlSerializer="policy_setting"  
                  MarshalObject="policy_setting"  
                  MarshalDelegate="policy_setting"  
                  MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30b16-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="30b16-105">Attributes and Elements</span></span>  
 <span data-ttu-id="30b16-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="30b16-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30b16-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="30b16-107">Attributes</span></span>  
  
|<span data-ttu-id="30b16-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="30b16-108">Attribute</span></span>|<span data-ttu-id="30b16-109">Tipo de atributo</span><span class="sxs-lookup"><span data-stu-id="30b16-109">Attribute type</span></span>|<span data-ttu-id="30b16-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="30b16-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="30b16-111">Reflexão</span><span class="sxs-lookup"><span data-stu-id="30b16-111">Reflection</span></span>|<span data-ttu-id="30b16-112">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="30b16-112">Optional attribute.</span></span> <span data-ttu-id="30b16-113">Controla o acesso de tempo de execução a construtores para habilitar a ativação de instâncias.</span><span class="sxs-lookup"><span data-stu-id="30b16-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="30b16-114">Reflexão</span><span class="sxs-lookup"><span data-stu-id="30b16-114">Reflection</span></span>|<span data-ttu-id="30b16-115">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="30b16-115">Optional attribute.</span></span> <span data-ttu-id="30b16-116">Controla a consulta para obter informações sobre elementos do programa, mas não permite qualquer acesso de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="30b16-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="30b16-117">Reflexão</span><span class="sxs-lookup"><span data-stu-id="30b16-117">Reflection</span></span>|<span data-ttu-id="30b16-118">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="30b16-118">Optional attribute.</span></span> <span data-ttu-id="30b16-119">Controla o acesso a todos os tipos de membro ao tempo de execução, incluindo construtores, métodos, campos, propriedades e eventos, habilitando a programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="30b16-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="30b16-120">Serialização</span><span class="sxs-lookup"><span data-stu-id="30b16-120">Serialization</span></span>|<span data-ttu-id="30b16-121">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="30b16-121">Optional attribute.</span></span> <span data-ttu-id="30b16-122">Controla o acesso ao tempo de execução para construtores, campos e propriedades para habilitar a serialização e desserialização das instâncias por bibliotecas como o serializador Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="30b16-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="30b16-123">Serialização</span><span class="sxs-lookup"><span data-stu-id="30b16-123">Serialization</span></span>|<span data-ttu-id="30b16-124">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="30b16-124">Optional attribute.</span></span> <span data-ttu-id="30b16-125">Controla a política de serialização que usa a classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="30b16-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="30b16-126">Serialização</span><span class="sxs-lookup"><span data-stu-id="30b16-126">Serialization</span></span>|<span data-ttu-id="30b16-127">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="30b16-127">Optional attribute.</span></span> <span data-ttu-id="30b16-128">Controla a política de serialização JSON que usa a classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="30b16-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="30b16-129">Serialização</span><span class="sxs-lookup"><span data-stu-id="30b16-129">Serialization</span></span>|<span data-ttu-id="30b16-130">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="30b16-130">Optional attribute.</span></span> <span data-ttu-id="30b16-131">Controla a política de serialização XML que usa a classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="30b16-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="30b16-132">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="30b16-132">Interop</span></span>|<span data-ttu-id="30b16-133">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="30b16-133">Optional attribute.</span></span> <span data-ttu-id="30b16-134">Política de controles de marshaling de tipos de referência para o Tempo de Execução do Windows e COM.</span><span class="sxs-lookup"><span data-stu-id="30b16-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="30b16-135">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="30b16-135">Interop</span></span>|<span data-ttu-id="30b16-136">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="30b16-136">Optional attribute.</span></span> <span data-ttu-id="30b16-137">Controla a diretiva de marshaling de tipos delegados como ponteiros de função para código nativo.</span><span class="sxs-lookup"><span data-stu-id="30b16-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="30b16-138">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="30b16-138">Interop</span></span>|<span data-ttu-id="30b16-139">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="30b16-139">Optional attribute.</span></span> <span data-ttu-id="30b16-140">Controla a política de marshaling de tipos de valor para código nativo.</span><span class="sxs-lookup"><span data-stu-id="30b16-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="30b16-141">Todos os atributos</span><span class="sxs-lookup"><span data-stu-id="30b16-141">All attributes</span></span>  
  
|<span data-ttu-id="30b16-142">Valor</span><span class="sxs-lookup"><span data-stu-id="30b16-142">Value</span></span>|<span data-ttu-id="30b16-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="30b16-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="30b16-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="30b16-144">*policy_setting*</span></span>|<span data-ttu-id="30b16-145">A configuração a ser aplicada a este tipo de política.</span><span class="sxs-lookup"><span data-stu-id="30b16-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="30b16-146">Os valores possíveis são `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` e `Required All`.</span><span class="sxs-lookup"><span data-stu-id="30b16-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="30b16-147">Para obter mais informações, consulte [Configurações da política da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="30b16-147">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30b16-148">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="30b16-148">Child Elements</span></span>  
 <span data-ttu-id="30b16-149">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="30b16-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="30b16-150">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="30b16-150">Parent Elements</span></span>  
  
|<span data-ttu-id="30b16-151">Elemento</span><span class="sxs-lookup"><span data-stu-id="30b16-151">Element</span></span>|<span data-ttu-id="30b16-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="30b16-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30b16-153">\<Type></span><span class="sxs-lookup"><span data-stu-id="30b16-153">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="30b16-154">Aplica a política de reflexão a um tipo e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="30b16-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30b16-155">Comentários</span><span class="sxs-lookup"><span data-stu-id="30b16-155">Remarks</span></span>  
 <span data-ttu-id="30b16-156">O elemento `<AttributeImplies>` é usado se o seu tipo recipiente for um atributo (isto é, uma classe derivada de <xref:System.Attribute?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="30b16-156">The `<AttributeImplies>` element is used if its containing type is an attribute (that is, a class derived from <xref:System.Attribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="30b16-157">Se o atributo for aplicado a um elemento de programa específico, a política definida pelo elemento `<AttributeImplies>` aplica-se a esse elemento de programa.</span><span class="sxs-lookup"><span data-stu-id="30b16-157">If the attribute is applied to a particular program element, the policy defined by the `<AttributeImplies>` element applies to that program element.</span></span>  
  
 <span data-ttu-id="30b16-158">Os atributos de reflexão, serialização e interoperabilidade são todos opcionais, embora pelo menos um deve estar presente.</span><span class="sxs-lookup"><span data-stu-id="30b16-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30b16-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30b16-159">See also</span></span>

- [<span data-ttu-id="30b16-160">\<Tipo > elemento</span><span class="sxs-lookup"><span data-stu-id="30b16-160">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)
- [<span data-ttu-id="30b16-161">Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="30b16-161">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="30b16-162">Elementos da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="30b16-162">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="30b16-163">Configurações da política da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="30b16-163">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)

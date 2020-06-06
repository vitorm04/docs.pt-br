---
title: <AttributeImplies> (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
ms.openlocfilehash: 2ab1fdc71bc43f61f69a0d9b7bea7acb35e14ea5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79181058"
---
# <a name="attributeimplies-element-net-native"></a><span data-ttu-id="4530c-102">\<AttributeImplies> (.NET Nativo)</span><span class="sxs-lookup"><span data-stu-id="4530c-102">\<AttributeImplies> Element (.NET Native)</span></span>
<span data-ttu-id="4530c-103">Define a política para os elementos de código ao qual o atributo recipiente é aplicado.</span><span class="sxs-lookup"><span data-stu-id="4530c-103">Defines policy for code elements the containing attribute is applied to.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4530c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4530c-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4530c-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4530c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="4530c-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4530c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4530c-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="4530c-107">Attributes</span></span>  
  
|<span data-ttu-id="4530c-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="4530c-108">Attribute</span></span>|<span data-ttu-id="4530c-109">Tipo de atributo</span><span class="sxs-lookup"><span data-stu-id="4530c-109">Attribute type</span></span>|<span data-ttu-id="4530c-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="4530c-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="4530c-111">Reflexão</span><span class="sxs-lookup"><span data-stu-id="4530c-111">Reflection</span></span>|<span data-ttu-id="4530c-112">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="4530c-112">Optional attribute.</span></span> <span data-ttu-id="4530c-113">Controla o acesso de runtime a construtores para habilitar a ativação de instâncias.</span><span class="sxs-lookup"><span data-stu-id="4530c-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="4530c-114">Reflexão</span><span class="sxs-lookup"><span data-stu-id="4530c-114">Reflection</span></span>|<span data-ttu-id="4530c-115">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="4530c-115">Optional attribute.</span></span> <span data-ttu-id="4530c-116">Controla a consulta para obter informações sobre elementos do programa, mas não permite qualquer acesso de runtime.</span><span class="sxs-lookup"><span data-stu-id="4530c-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="4530c-117">Reflexão</span><span class="sxs-lookup"><span data-stu-id="4530c-117">Reflection</span></span>|<span data-ttu-id="4530c-118">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="4530c-118">Optional attribute.</span></span> <span data-ttu-id="4530c-119">Controla o acesso a todos os tipos de membro ao runtime, incluindo construtores, métodos, campos, propriedades e eventos, habilitando a programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="4530c-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="4530c-120">Serialização</span><span class="sxs-lookup"><span data-stu-id="4530c-120">Serialization</span></span>|<span data-ttu-id="4530c-121">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="4530c-121">Optional attribute.</span></span> <span data-ttu-id="4530c-122">Controla o acesso ao runtime para construtores, campos e propriedades para habilitar a serialização e desserialização das instâncias por bibliotecas como o serializador Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="4530c-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="4530c-123">Serialização</span><span class="sxs-lookup"><span data-stu-id="4530c-123">Serialization</span></span>|<span data-ttu-id="4530c-124">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="4530c-124">Optional attribute.</span></span> <span data-ttu-id="4530c-125">Controla a política de serialização que usa a classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4530c-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="4530c-126">Serialização</span><span class="sxs-lookup"><span data-stu-id="4530c-126">Serialization</span></span>|<span data-ttu-id="4530c-127">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="4530c-127">Optional attribute.</span></span> <span data-ttu-id="4530c-128">Controla a política de serialização JSON que usa a classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4530c-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="4530c-129">Serialização</span><span class="sxs-lookup"><span data-stu-id="4530c-129">Serialization</span></span>|<span data-ttu-id="4530c-130">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="4530c-130">Optional attribute.</span></span> <span data-ttu-id="4530c-131">Controla a política de serialização XML que usa a classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4530c-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="4530c-132">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="4530c-132">Interop</span></span>|<span data-ttu-id="4530c-133">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="4530c-133">Optional attribute.</span></span> <span data-ttu-id="4530c-134">Política de controles de marshaling de tipos de referência para o Windows Runtime e COM.</span><span class="sxs-lookup"><span data-stu-id="4530c-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="4530c-135">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="4530c-135">Interop</span></span>|<span data-ttu-id="4530c-136">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="4530c-136">Optional attribute.</span></span> <span data-ttu-id="4530c-137">Controla a diretiva de marshaling de tipos delegados como ponteiros de função para código nativo.</span><span class="sxs-lookup"><span data-stu-id="4530c-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="4530c-138">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="4530c-138">Interop</span></span>|<span data-ttu-id="4530c-139">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="4530c-139">Optional attribute.</span></span> <span data-ttu-id="4530c-140">Controla a política de marshaling de tipos de valor para código nativo.</span><span class="sxs-lookup"><span data-stu-id="4530c-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="4530c-141">Todos os atributos</span><span class="sxs-lookup"><span data-stu-id="4530c-141">All attributes</span></span>  
  
|<span data-ttu-id="4530c-142">Valor</span><span class="sxs-lookup"><span data-stu-id="4530c-142">Value</span></span>|<span data-ttu-id="4530c-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="4530c-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4530c-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="4530c-144">*policy_setting*</span></span>|<span data-ttu-id="4530c-145">A configuração a ser aplicada a este tipo de política.</span><span class="sxs-lookup"><span data-stu-id="4530c-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="4530c-146">Os valores possíveis são `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` e `Required All`.</span><span class="sxs-lookup"><span data-stu-id="4530c-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="4530c-147">Para obter mais informações, consulte [Configurações da política da diretiva de runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="4530c-147">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4530c-148">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4530c-148">Child Elements</span></span>  
 <span data-ttu-id="4530c-149">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="4530c-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4530c-150">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4530c-150">Parent Elements</span></span>  
  
|<span data-ttu-id="4530c-151">Elemento</span><span class="sxs-lookup"><span data-stu-id="4530c-151">Element</span></span>|<span data-ttu-id="4530c-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="4530c-152">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="4530c-153">Aplica a política de reflexão a um tipo e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="4530c-153">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4530c-154">Comentários</span><span class="sxs-lookup"><span data-stu-id="4530c-154">Remarks</span></span>  
 <span data-ttu-id="4530c-155">O elemento `<AttributeImplies>` é usado se o seu tipo recipiente for um atributo (isto é, uma classe derivada de <xref:System.Attribute?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="4530c-155">The `<AttributeImplies>` element is used if its containing type is an attribute (that is, a class derived from <xref:System.Attribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="4530c-156">Se o atributo for aplicado a um elemento de programa específico, a política definida pelo elemento `<AttributeImplies>` aplica-se a esse elemento de programa.</span><span class="sxs-lookup"><span data-stu-id="4530c-156">If the attribute is applied to a particular program element, the policy defined by the `<AttributeImplies>` element applies to that program element.</span></span>  
  
 <span data-ttu-id="4530c-157">Os atributos de reflexão, serialização e interoperabilidade são todos opcionais, embora pelo menos um deve estar presente.</span><span class="sxs-lookup"><span data-stu-id="4530c-157">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4530c-158">Confira também</span><span class="sxs-lookup"><span data-stu-id="4530c-158">See also</span></span>

- [<span data-ttu-id="4530c-159">\<Type>Elementos</span><span class="sxs-lookup"><span data-stu-id="4530c-159">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="4530c-160">Referência do arquivo de configuração de diretivas do runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="4530c-160">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="4530c-161">Elementos da diretiva de runtime</span><span class="sxs-lookup"><span data-stu-id="4530c-161">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="4530c-162">Configurações da política da diretiva de runtime</span><span class="sxs-lookup"><span data-stu-id="4530c-162">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)

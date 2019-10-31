---
title: <Parameter> (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: 22aaa1f3-596f-4733-93db-f4bcabcb5240
ms.openlocfilehash: c6dfc347d44a794ee8496c45ca879f9daab12b22
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128194"
---
# <a name="parameter-element-net-native"></a><span data-ttu-id="d687a-102">Elemento de > de parâmetro de \<(.NET Native)</span><span class="sxs-lookup"><span data-stu-id="d687a-102">\<Parameter> Element (.NET Native)</span></span>
<span data-ttu-id="d687a-103">Aplica a política de tempo de reflexão ao tipo do argumento passado para um método.</span><span class="sxs-lookup"><span data-stu-id="d687a-103">Applies reflection policy to the type of the argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d687a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d687a-104">Syntax</span></span>  
  
```xml  
<Parameter Name="parameter_name"  
           Activate="policy_type"  
           Browse="policy_type"  
           Dynamic="policy_type"  
           Serialize="policy_type"  
           DataContractSerializer="policy_type"  
           DataContractJsonSerializer="policy_type"  
           XmlSerializer="policy_type"  
           MarshalObject="policy_type"  
           MarshalDelegate="policy_type"  
           MarshalStructure="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d687a-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d687a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d687a-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d687a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d687a-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="d687a-107">Attributes</span></span>  
  
|<span data-ttu-id="d687a-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="d687a-108">Attribute</span></span>|<span data-ttu-id="d687a-109">Tipo de atributo</span><span class="sxs-lookup"><span data-stu-id="d687a-109">Attribute type</span></span>|<span data-ttu-id="d687a-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="d687a-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="d687a-111">Geral</span><span class="sxs-lookup"><span data-stu-id="d687a-111">General</span></span>|<span data-ttu-id="d687a-112">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="d687a-112">Required attribute.</span></span> <span data-ttu-id="d687a-113">O nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d687a-113">The parameter name.</span></span> <span data-ttu-id="d687a-114">Por exemplo, para a assinatura do método `String.CompareTo(Object value)`, o valor do atributo `Name` é "value".</span><span class="sxs-lookup"><span data-stu-id="d687a-114">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
|`Activate`|<span data-ttu-id="d687a-115">Reflexão</span><span class="sxs-lookup"><span data-stu-id="d687a-115">Reflection</span></span>|<span data-ttu-id="d687a-116">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="d687a-116">Optional attribute.</span></span> <span data-ttu-id="d687a-117">Controla o acesso de tempo de execução a construtores para habilitar a ativação de instâncias.</span><span class="sxs-lookup"><span data-stu-id="d687a-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="d687a-118">Reflexão</span><span class="sxs-lookup"><span data-stu-id="d687a-118">Reflection</span></span>|<span data-ttu-id="d687a-119">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="d687a-119">Optional attribute.</span></span> <span data-ttu-id="d687a-120">Controla a consulta para obter informações sobre elementos do programa, mas não permite qualquer acesso de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d687a-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="d687a-121">Reflexão</span><span class="sxs-lookup"><span data-stu-id="d687a-121">Reflection</span></span>|<span data-ttu-id="d687a-122">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="d687a-122">Optional attribute.</span></span> <span data-ttu-id="d687a-123">Controla o acesso a todos os tipos de membro ao tempo de execução, incluindo construtores, métodos, campos, propriedades e eventos, habilitando a programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="d687a-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="d687a-124">Serialização</span><span class="sxs-lookup"><span data-stu-id="d687a-124">Serialization</span></span>|<span data-ttu-id="d687a-125">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="d687a-125">Optional attribute.</span></span> <span data-ttu-id="d687a-126">Controla o acesso ao tempo de execução para construtores, campos e propriedades para habilitar a serialização e desserialização das instâncias por bibliotecas como o serializador Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="d687a-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="d687a-127">Serialização</span><span class="sxs-lookup"><span data-stu-id="d687a-127">Serialization</span></span>|<span data-ttu-id="d687a-128">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="d687a-128">Optional attribute.</span></span> <span data-ttu-id="d687a-129">Controla a política de serialização que usa a classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d687a-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="d687a-130">Serialização</span><span class="sxs-lookup"><span data-stu-id="d687a-130">Serialization</span></span>|<span data-ttu-id="d687a-131">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="d687a-131">Optional attribute.</span></span> <span data-ttu-id="d687a-132">Controla a política de serialização JSON que usa a classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d687a-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="d687a-133">Serialização</span><span class="sxs-lookup"><span data-stu-id="d687a-133">Serialization</span></span>|<span data-ttu-id="d687a-134">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="d687a-134">Optional attribute.</span></span> <span data-ttu-id="d687a-135">Controla a política de serialização XML que usa a classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d687a-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="d687a-136">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="d687a-136">Interop</span></span>|<span data-ttu-id="d687a-137">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="d687a-137">Optional attribute.</span></span> <span data-ttu-id="d687a-138">Controla a política de marshaling de tipos de referência do WinRT e COM.</span><span class="sxs-lookup"><span data-stu-id="d687a-138">Controls policy for marshaling reference types to WinRT and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="d687a-139">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="d687a-139">Interop</span></span>|<span data-ttu-id="d687a-140">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="d687a-140">Optional attribute.</span></span> <span data-ttu-id="d687a-141">Controla a diretiva de marshaling de tipos delegados como ponteiros de função para código nativo.</span><span class="sxs-lookup"><span data-stu-id="d687a-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="d687a-142">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="d687a-142">Interop</span></span>|<span data-ttu-id="d687a-143">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="d687a-143">Optional attribute.</span></span> <span data-ttu-id="d687a-144">Controla a política de marshaling de tipos de valor para código nativo.</span><span class="sxs-lookup"><span data-stu-id="d687a-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="d687a-145">Atributo de nome</span><span class="sxs-lookup"><span data-stu-id="d687a-145">Name attribute</span></span>  
  
|<span data-ttu-id="d687a-146">Valor</span><span class="sxs-lookup"><span data-stu-id="d687a-146">Value</span></span>|<span data-ttu-id="d687a-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="d687a-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d687a-148">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="d687a-148">*parameter_name*</span></span>|<span data-ttu-id="d687a-149">O nome do parâmetro de método aos quais a política é aplicada.</span><span class="sxs-lookup"><span data-stu-id="d687a-149">The name of the method parameter to which policy is applied.</span></span> <span data-ttu-id="d687a-150">Por exemplo, para a assinatura do método `String.CompareTo(Object value)`, o valor do atributo `Name` é "value".</span><span class="sxs-lookup"><span data-stu-id="d687a-150">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="d687a-151">Todos os outros atributos</span><span class="sxs-lookup"><span data-stu-id="d687a-151">All other attributes</span></span>  
  
|<span data-ttu-id="d687a-152">Valor</span><span class="sxs-lookup"><span data-stu-id="d687a-152">Value</span></span>|<span data-ttu-id="d687a-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="d687a-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d687a-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="d687a-154">*policy_setting*</span></span>|<span data-ttu-id="d687a-155">A configuração a ser aplicada a este tipo de política.</span><span class="sxs-lookup"><span data-stu-id="d687a-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="d687a-156">Os valores possíveis são `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` e `Required All`.</span><span class="sxs-lookup"><span data-stu-id="d687a-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="d687a-157">Para obter mais informações, consulte [Configurações da política da diretiva de tempo de execução](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="d687a-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d687a-158">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d687a-158">Child Elements</span></span>  
 <span data-ttu-id="d687a-159">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d687a-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d687a-160">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d687a-160">Parent Elements</span></span>  
  
|<span data-ttu-id="d687a-161">Elemento</span><span class="sxs-lookup"><span data-stu-id="d687a-161">Element</span></span>|<span data-ttu-id="d687a-162">Descrição</span><span class="sxs-lookup"><span data-stu-id="d687a-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d687a-163">\<Method></span><span class="sxs-lookup"><span data-stu-id="d687a-163">\<Method></span></span>](method-element-net-native.md)|<span data-ttu-id="d687a-164">Aplica a política de reflexão de tempo de execução a um construtor ou método.</span><span class="sxs-lookup"><span data-stu-id="d687a-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d687a-165">Comentários</span><span class="sxs-lookup"><span data-stu-id="d687a-165">Remarks</span></span>  
 <span data-ttu-id="d687a-166">O elemento `<Parameter>` é filho do elemento [\<Method>](method-element-net-native.md) e é usado para aplicar a política a um parâmetro de método específico.</span><span class="sxs-lookup"><span data-stu-id="d687a-166">The `<Parameter>` element is a child of the [\<Method>](method-element-net-native.md) element and is used to apply policy to a particular method parameter.</span></span> <span data-ttu-id="d687a-167">O parâmetro de método específico é especificado pelo nome em vez de por tipo.</span><span class="sxs-lookup"><span data-stu-id="d687a-167">The specific method parameter is specified by name rather than by type.</span></span> <span data-ttu-id="d687a-168">Pelo menos um atributo que representa um tipo de política, como `Activate` ou `Dynamic`, deve estar presente.</span><span class="sxs-lookup"><span data-stu-id="d687a-168">At least one attribute that represents a policy type, such as `Activate` or `Dynamic`, must be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d687a-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d687a-169">See also</span></span>

- [<span data-ttu-id="d687a-170">Elemento \<Method></span><span class="sxs-lookup"><span data-stu-id="d687a-170">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="d687a-171">Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="d687a-171">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="d687a-172">Configurações da política da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="d687a-172">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="d687a-173">Elementos da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="d687a-173">Runtime Directive Elements</span></span>](runtime-directive-elements.md)

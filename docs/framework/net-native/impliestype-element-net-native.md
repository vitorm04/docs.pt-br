---
title: <ImpliesType> (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
ms.openlocfilehash: 2f0ce1a1587e190627212cba07db298c12f4b30e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128385"
---
# <a name="impliestype-element-net-native"></a><span data-ttu-id="db816-102">\<implica > elemento (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="db816-102">\<ImpliesType> Element (.NET Native)</span></span>
<span data-ttu-id="db816-103">Aplica a política a um tipo, se ela foi aplicada ao tipo recipiente ou do método.</span><span class="sxs-lookup"><span data-stu-id="db816-103">Applies policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db816-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="db816-104">Syntax</span></span>  
  
```xml
<ImpliesType Name="type_name"  
             Activate="policy_type"  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db816-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="db816-105">Attributes and Elements</span></span>  
 <span data-ttu-id="db816-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="db816-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db816-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="db816-107">Attributes</span></span>  
  
|<span data-ttu-id="db816-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="db816-108">Attribute</span></span>|<span data-ttu-id="db816-109">Tipo de atributo</span><span class="sxs-lookup"><span data-stu-id="db816-109">Attribute type</span></span>|<span data-ttu-id="db816-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="db816-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="db816-111">Geral</span><span class="sxs-lookup"><span data-stu-id="db816-111">General</span></span>|<span data-ttu-id="db816-112">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="db816-112">Required attribute.</span></span> <span data-ttu-id="db816-113">Especifica o nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="db816-113">Specifies the type name.</span></span>|  
|`Activate`|<span data-ttu-id="db816-114">Reflexão</span><span class="sxs-lookup"><span data-stu-id="db816-114">Reflection</span></span>|<span data-ttu-id="db816-115">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="db816-115">Optional attribute.</span></span> <span data-ttu-id="db816-116">Controla o acesso de tempo de execução a construtores para habilitar a ativação de instâncias.</span><span class="sxs-lookup"><span data-stu-id="db816-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="db816-117">Reflexão</span><span class="sxs-lookup"><span data-stu-id="db816-117">Reflection</span></span>|<span data-ttu-id="db816-118">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="db816-118">Optional attribute.</span></span> <span data-ttu-id="db816-119">Controla a consulta para obter informações sobre elementos do programa, mas não permite qualquer acesso de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="db816-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="db816-120">Reflexão</span><span class="sxs-lookup"><span data-stu-id="db816-120">Reflection</span></span>|<span data-ttu-id="db816-121">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="db816-121">Optional attribute.</span></span> <span data-ttu-id="db816-122">Controla o acesso a todos os tipos de membro ao tempo de execução, incluindo construtores, métodos, campos, propriedades e eventos, habilitando a programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="db816-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="db816-123">Serialização</span><span class="sxs-lookup"><span data-stu-id="db816-123">Serialization</span></span>|<span data-ttu-id="db816-124">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="db816-124">Optional attribute.</span></span> <span data-ttu-id="db816-125">Controla o acesso ao tempo de execução para construtores, campos e propriedades para habilitar a serialização e desserialização das instâncias por bibliotecas como o serializador Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="db816-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="db816-126">Serialização</span><span class="sxs-lookup"><span data-stu-id="db816-126">Serialization</span></span>|<span data-ttu-id="db816-127">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="db816-127">Optional attribute.</span></span> <span data-ttu-id="db816-128">Controla a política de serialização que usa a classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="db816-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="db816-129">Serialização</span><span class="sxs-lookup"><span data-stu-id="db816-129">Serialization</span></span>|<span data-ttu-id="db816-130">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="db816-130">Optional attribute.</span></span> <span data-ttu-id="db816-131">Controla a política de serialização JSON que usa a classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="db816-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="db816-132">Serialização</span><span class="sxs-lookup"><span data-stu-id="db816-132">Serialization</span></span>|<span data-ttu-id="db816-133">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="db816-133">Optional attribute.</span></span> <span data-ttu-id="db816-134">Controla a política de serialização XML que usa a classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="db816-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="db816-135">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="db816-135">Interop</span></span>|<span data-ttu-id="db816-136">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="db816-136">Optional attribute.</span></span> <span data-ttu-id="db816-137">Política de controles de marshaling de tipos de referência para o Tempo de Execução do Windows e COM.</span><span class="sxs-lookup"><span data-stu-id="db816-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="db816-138">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="db816-138">Interop</span></span>|<span data-ttu-id="db816-139">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="db816-139">Optional attribute.</span></span> <span data-ttu-id="db816-140">Controla a diretiva de marshaling de tipos delegados como ponteiros de função para código nativo.</span><span class="sxs-lookup"><span data-stu-id="db816-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="db816-141">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="db816-141">Interop</span></span>|<span data-ttu-id="db816-142">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="db816-142">Optional attribute.</span></span> <span data-ttu-id="db816-143">Controla a política de marshaling de tipos de valor para código nativo.</span><span class="sxs-lookup"><span data-stu-id="db816-143">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="db816-144">Atributo de nome</span><span class="sxs-lookup"><span data-stu-id="db816-144">Name attribute</span></span>  
  
|<span data-ttu-id="db816-145">Valor</span><span class="sxs-lookup"><span data-stu-id="db816-145">Value</span></span>|<span data-ttu-id="db816-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="db816-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="db816-147">*type_name*</span><span class="sxs-lookup"><span data-stu-id="db816-147">*type_name*</span></span>|<span data-ttu-id="db816-148">O nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="db816-148">The type name.</span></span> <span data-ttu-id="db816-149">Se o tipo representado por este elemento `<ImpliesType>` estiver localizado no mesmo namespace contendo seu elemento `<Type>`, o *type_name* poderá incluir o nome do tipo sem o respectivo namespace.</span><span class="sxs-lookup"><span data-stu-id="db816-149">If the type represented by this `<ImpliesType>` element is located in the same namespace as its containing `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="db816-150">Caso contrário, o *type_name* deverá incluir o nome do tipo totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="db816-150">Otherwise, *type_name* must include the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="db816-151">Todos os outros atributos</span><span class="sxs-lookup"><span data-stu-id="db816-151">All other attributes</span></span>  
  
|<span data-ttu-id="db816-152">Valor</span><span class="sxs-lookup"><span data-stu-id="db816-152">Value</span></span>|<span data-ttu-id="db816-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="db816-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="db816-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="db816-154">*policy_setting*</span></span>|<span data-ttu-id="db816-155">A configuração a ser aplicada a este tipo de política.</span><span class="sxs-lookup"><span data-stu-id="db816-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="db816-156">Os valores possíveis são `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` e `Required All`.</span><span class="sxs-lookup"><span data-stu-id="db816-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="db816-157">Para obter mais informações, consulte [Configurações da política da diretiva de tempo de execução](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="db816-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db816-158">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="db816-158">Child Elements</span></span>  
 <span data-ttu-id="db816-159">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="db816-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="db816-160">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="db816-160">Parent Elements</span></span>  
  
|<span data-ttu-id="db816-161">Elemento</span><span class="sxs-lookup"><span data-stu-id="db816-161">Element</span></span>|<span data-ttu-id="db816-162">Descrição</span><span class="sxs-lookup"><span data-stu-id="db816-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="db816-163">\<Type></span><span class="sxs-lookup"><span data-stu-id="db816-163">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="db816-164">Aplica a política de reflexão a um tipo e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="db816-164">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="db816-165">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="db816-165">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="db816-166">Aplica a política de reflexão a um tipo genérico construído e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="db816-166">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
|[<span data-ttu-id="db816-167">\<Method></span><span class="sxs-lookup"><span data-stu-id="db816-167">\<Method></span></span>](method-element-net-native.md)|<span data-ttu-id="db816-168">Aplica a política de reflexão a um método.</span><span class="sxs-lookup"><span data-stu-id="db816-168">Applies reflection policy to a method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db816-169">Comentários</span><span class="sxs-lookup"><span data-stu-id="db816-169">Remarks</span></span>  
 <span data-ttu-id="db816-170">O elemento `<ImpliesType>` destina-se principalmente para uso por bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="db816-170">The `<ImpliesType>` element is primarily intended for use by libraries.</span></span> <span data-ttu-id="db816-171">Ele aborda o cenário a seguir:</span><span class="sxs-lookup"><span data-stu-id="db816-171">It addresses the following scenario:</span></span>  
  
- <span data-ttu-id="db816-172">Se uma rotina precisa refletir em um tipo, ela necessariamente precisa refletir no segundo tipo.</span><span class="sxs-lookup"><span data-stu-id="db816-172">If a routine needs to reflect on one type, it necessarily needs to reflect on a second type.</span></span>  
  
- <span data-ttu-id="db816-173">Os metadados para a instanciação implícita do segundo tipo não estão disponíveis, pois a análise estática não indica que é necessário.</span><span class="sxs-lookup"><span data-stu-id="db816-173">The metadata for the implied instantiation of the second type is otherwise unavailable, because static analysis doesn't indicate that it's necessary.</span></span>  
  
 <span data-ttu-id="db816-174">Geralmente, os dois tipos são instanciações genéricas com argumentos de tipo compartilhados.</span><span class="sxs-lookup"><span data-stu-id="db816-174">Most commonly, the two types are generic instantiations with shared type arguments.</span></span>  
  
 <span data-ttu-id="db816-175">O elemento `<ImpliesType>` foi definido presumindo que a necessidade de reflexão no tipo especificado pelo seu elemento pai implica a necessidade de reflexão no tipo especificado pelo elemento `<ImpliesType>`.</span><span class="sxs-lookup"><span data-stu-id="db816-175">The `<ImpliesType>` element was defined with the assumption that a need for reflection on the type specified by its parent element implies a need for reflection on the type specified by the `<ImpliesType>` element.</span></span> <span data-ttu-id="db816-176">Por exemplo, as seguintes diretivas de reflexão aplicam-se a dois tipos, `Explicit<T>` e `Implicit<T>`.</span><span class="sxs-lookup"><span data-stu-id="db816-176">For example, the following reflection directives apply to two types, `Explicit<T>` and `Implicit<T>`.</span></span>  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 <span data-ttu-id="db816-177">Essa diretiva não tem efeito, a menos que uma instanciação de `Explicit` tenha uma configuração de política `Dynamic` definida.</span><span class="sxs-lookup"><span data-stu-id="db816-177">This directive has no effect unless an instantiation of `Explicit` has a defined `Dynamic` policy setting.</span></span> <span data-ttu-id="db816-178">Por exemplo, se for o caso de `Explicit<Int32>`, `Implicit<Int32>` é instanciado com seu membros públicos enraizados e seus metadados são disponibilizados por programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="db816-178">For example, if that's the case for `Explicit<Int32>`, `Implicit<Int32>` is instantiated with its public members rooted, and their metadata is made accessible for dynamic programming.</span></span>  
  
 <span data-ttu-id="db816-179">Veja a seguir um exemplo real que se aplica a pelo menos um serializador.</span><span class="sxs-lookup"><span data-stu-id="db816-179">The following is a real-world example that applies to at least one serializer.</span></span> <span data-ttu-id="db816-180">As diretivas capturam o requisito de que a reflexão sobre algo digitado como `IList<`*algo*`>` também envolve reflexão sobre o tipo `List<`*algo*`>` correspondente sem exigir nenhuma anotação por aplicativo.</span><span class="sxs-lookup"><span data-stu-id="db816-180">The directives capture the requirement that reflecting on something typed as `IList<`*something*`>` also involves reflecting on the corresponding `List<`*something*`>` type without requiring any per-application annotation.</span></span>  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 <span data-ttu-id="db816-181">O elemento `<ImpliesType>` também pode aparecer em um elemento `<Method>`, pois em alguns casos instanciar um método genérico implica refletir em uma instanciação de um tipo.</span><span class="sxs-lookup"><span data-stu-id="db816-181">The `<ImpliesType>` element can also appear within a `<Method>` element, because in some cases instantiating a generic method implies reflecting on a type instantiation.</span></span> <span data-ttu-id="db816-182">Por exemplo, imagine um método genérico `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` que uma determinada biblioteca acessará dinamicamente, juntamente com os tipos associados <xref:System.Collections.Generic.List%601> e <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="db816-182">For example, imagine a generic method `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` that a given library will access dynamically along with the associated <xref:System.Collections.Generic.List%601> and <xref:System.Array> types.</span></span> <span data-ttu-id="db816-183">Isso pode ser expressado como:</span><span class="sxs-lookup"><span data-stu-id="db816-183">This can be expressed as:</span></span>  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public" />  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a><span data-ttu-id="db816-184">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db816-184">See also</span></span>

- [<span data-ttu-id="db816-185">Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="db816-185">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="db816-186">Elementos da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="db816-186">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="db816-187">Configurações da política da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="db816-187">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)

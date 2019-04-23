---
title: <ImpliesType> (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ef238a2cb852ecd7fa3f0e2dbe4048ff03a4139
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080872"
---
# <a name="impliestype-element-net-native"></a><span data-ttu-id="502f5-102">\<ImpliesType > (.NET nativo)</span><span class="sxs-lookup"><span data-stu-id="502f5-102">\<ImpliesType> Element (.NET Native)</span></span>
<span data-ttu-id="502f5-103">Aplica a política a um tipo, se ela foi aplicada ao tipo recipiente ou do método.</span><span class="sxs-lookup"><span data-stu-id="502f5-103">Applies policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="502f5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="502f5-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="502f5-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="502f5-105">Attributes and Elements</span></span>  
 <span data-ttu-id="502f5-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="502f5-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="502f5-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="502f5-107">Attributes</span></span>  
  
|<span data-ttu-id="502f5-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="502f5-108">Attribute</span></span>|<span data-ttu-id="502f5-109">Tipo de atributo</span><span class="sxs-lookup"><span data-stu-id="502f5-109">Attribute type</span></span>|<span data-ttu-id="502f5-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="502f5-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="502f5-111">Geral</span><span class="sxs-lookup"><span data-stu-id="502f5-111">General</span></span>|<span data-ttu-id="502f5-112">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="502f5-112">Required attribute.</span></span> <span data-ttu-id="502f5-113">Especifica o nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="502f5-113">Specifies the type name.</span></span>|  
|`Activate`|<span data-ttu-id="502f5-114">Reflexão</span><span class="sxs-lookup"><span data-stu-id="502f5-114">Reflection</span></span>|<span data-ttu-id="502f5-115">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="502f5-115">Optional attribute.</span></span> <span data-ttu-id="502f5-116">Controla o acesso de tempo de execução a construtores para habilitar a ativação de instâncias.</span><span class="sxs-lookup"><span data-stu-id="502f5-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="502f5-117">Reflexão</span><span class="sxs-lookup"><span data-stu-id="502f5-117">Reflection</span></span>|<span data-ttu-id="502f5-118">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="502f5-118">Optional attribute.</span></span> <span data-ttu-id="502f5-119">Controla a consulta para obter informações sobre elementos do programa, mas não permite qualquer acesso de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="502f5-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="502f5-120">Reflexão</span><span class="sxs-lookup"><span data-stu-id="502f5-120">Reflection</span></span>|<span data-ttu-id="502f5-121">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="502f5-121">Optional attribute.</span></span> <span data-ttu-id="502f5-122">Controla o acesso a todos os tipos de membro ao tempo de execução, incluindo construtores, métodos, campos, propriedades e eventos, habilitando a programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="502f5-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="502f5-123">Serialização</span><span class="sxs-lookup"><span data-stu-id="502f5-123">Serialization</span></span>|<span data-ttu-id="502f5-124">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="502f5-124">Optional attribute.</span></span> <span data-ttu-id="502f5-125">Controla o acesso ao tempo de execução para construtores, campos e propriedades para habilitar a serialização e desserialização das instâncias por bibliotecas como o serializador Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="502f5-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="502f5-126">Serialização</span><span class="sxs-lookup"><span data-stu-id="502f5-126">Serialization</span></span>|<span data-ttu-id="502f5-127">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="502f5-127">Optional attribute.</span></span> <span data-ttu-id="502f5-128">Controla a política de serialização que usa a classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="502f5-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="502f5-129">Serialização</span><span class="sxs-lookup"><span data-stu-id="502f5-129">Serialization</span></span>|<span data-ttu-id="502f5-130">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="502f5-130">Optional attribute.</span></span> <span data-ttu-id="502f5-131">Controla a política de serialização JSON que usa a classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="502f5-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="502f5-132">Serialização</span><span class="sxs-lookup"><span data-stu-id="502f5-132">Serialization</span></span>|<span data-ttu-id="502f5-133">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="502f5-133">Optional attribute.</span></span> <span data-ttu-id="502f5-134">Controla a política de serialização XML que usa a classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="502f5-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="502f5-135">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="502f5-135">Interop</span></span>|<span data-ttu-id="502f5-136">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="502f5-136">Optional attribute.</span></span> <span data-ttu-id="502f5-137">Política de controles de marshaling de tipos de referência para o Tempo de Execução do Windows e COM.</span><span class="sxs-lookup"><span data-stu-id="502f5-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="502f5-138">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="502f5-138">Interop</span></span>|<span data-ttu-id="502f5-139">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="502f5-139">Optional attribute.</span></span> <span data-ttu-id="502f5-140">Controla a diretiva de marshaling de tipos delegados como ponteiros de função para código nativo.</span><span class="sxs-lookup"><span data-stu-id="502f5-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="502f5-141">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="502f5-141">Interop</span></span>|<span data-ttu-id="502f5-142">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="502f5-142">Optional attribute.</span></span> <span data-ttu-id="502f5-143">Controla a política de marshaling de tipos de valor para código nativo.</span><span class="sxs-lookup"><span data-stu-id="502f5-143">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="502f5-144">Atributo de nome</span><span class="sxs-lookup"><span data-stu-id="502f5-144">Name attribute</span></span>  
  
|<span data-ttu-id="502f5-145">Valor</span><span class="sxs-lookup"><span data-stu-id="502f5-145">Value</span></span>|<span data-ttu-id="502f5-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="502f5-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="502f5-147">*type_name*</span><span class="sxs-lookup"><span data-stu-id="502f5-147">*type_name*</span></span>|<span data-ttu-id="502f5-148">O nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="502f5-148">The type name.</span></span> <span data-ttu-id="502f5-149">Se o tipo representado por este elemento `<ImpliesType>` estiver localizado no mesmo namespace contendo seu elemento `<Type>`, o *type_name* poderá incluir o nome do tipo sem o respectivo namespace.</span><span class="sxs-lookup"><span data-stu-id="502f5-149">If the type represented by this `<ImpliesType>` element is located in the same namespace as its containing `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="502f5-150">Caso contrário, o *type_name* deverá incluir o nome do tipo totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="502f5-150">Otherwise, *type_name* must include the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="502f5-151">Todos os outros atributos</span><span class="sxs-lookup"><span data-stu-id="502f5-151">All other attributes</span></span>  
  
|<span data-ttu-id="502f5-152">Valor</span><span class="sxs-lookup"><span data-stu-id="502f5-152">Value</span></span>|<span data-ttu-id="502f5-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="502f5-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="502f5-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="502f5-154">*policy_setting*</span></span>|<span data-ttu-id="502f5-155">A configuração a ser aplicada a este tipo de política.</span><span class="sxs-lookup"><span data-stu-id="502f5-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="502f5-156">Os valores possíveis são `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` e `Required All`.</span><span class="sxs-lookup"><span data-stu-id="502f5-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="502f5-157">Para obter mais informações, consulte [Configurações da política da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="502f5-157">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="502f5-158">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="502f5-158">Child Elements</span></span>  
 <span data-ttu-id="502f5-159">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="502f5-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="502f5-160">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="502f5-160">Parent Elements</span></span>  
  
|<span data-ttu-id="502f5-161">Elemento</span><span class="sxs-lookup"><span data-stu-id="502f5-161">Element</span></span>|<span data-ttu-id="502f5-162">Descrição</span><span class="sxs-lookup"><span data-stu-id="502f5-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="502f5-163">\<Type></span><span class="sxs-lookup"><span data-stu-id="502f5-163">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="502f5-164">Aplica a política de reflexão a um tipo e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="502f5-164">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="502f5-165">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="502f5-165">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="502f5-166">Aplica a política de reflexão a um tipo genérico construído e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="502f5-166">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
|[<span data-ttu-id="502f5-167">\<Method></span><span class="sxs-lookup"><span data-stu-id="502f5-167">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="502f5-168">Aplica a política de reflexão a um método.</span><span class="sxs-lookup"><span data-stu-id="502f5-168">Applies reflection policy to a method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="502f5-169">Comentários</span><span class="sxs-lookup"><span data-stu-id="502f5-169">Remarks</span></span>  
 <span data-ttu-id="502f5-170">O elemento `<ImpliesType>` destina-se principalmente para uso por bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="502f5-170">The `<ImpliesType>` element is primarily intended for use by libraries.</span></span> <span data-ttu-id="502f5-171">Ele aborda o cenário a seguir:</span><span class="sxs-lookup"><span data-stu-id="502f5-171">It addresses the following scenario:</span></span>  
  
-   <span data-ttu-id="502f5-172">Se uma rotina precisa refletir em um tipo, ela necessariamente precisa refletir no segundo tipo.</span><span class="sxs-lookup"><span data-stu-id="502f5-172">If a routine needs to reflect on one type, it necessarily needs to reflect on a second type.</span></span>  
  
-   <span data-ttu-id="502f5-173">Os metadados para a instanciação implícita do segundo tipo não estão disponíveis, pois a análise estática não indica que é necessário.</span><span class="sxs-lookup"><span data-stu-id="502f5-173">The metadata for the implied instantiation of the second type is otherwise unavailable, because static analysis doesn't indicate that it's necessary.</span></span>  
  
 <span data-ttu-id="502f5-174">Geralmente, os dois tipos são instanciações genéricas com argumentos de tipo compartilhados.</span><span class="sxs-lookup"><span data-stu-id="502f5-174">Most commonly, the two types are generic instantiations with shared type arguments.</span></span>  
  
 <span data-ttu-id="502f5-175">O elemento `<ImpliesType>` foi definido presumindo que a necessidade de reflexão no tipo especificado pelo seu elemento pai implica a necessidade de reflexão no tipo especificado pelo elemento `<ImpliesType>`.</span><span class="sxs-lookup"><span data-stu-id="502f5-175">The `<ImpliesType>` element was defined with the assumption that a need for reflection on the type specified by its parent element implies a need for reflection on the type specified by the `<ImpliesType>` element.</span></span> <span data-ttu-id="502f5-176">Por exemplo, as seguintes diretivas de reflexão aplicam-se a dois tipos, `Explicit<T>` e `Implicit<T>`.</span><span class="sxs-lookup"><span data-stu-id="502f5-176">For example, the following reflection directives apply to two types, `Explicit<T>` and `Implicit<T>`.</span></span>  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 <span data-ttu-id="502f5-177">Essa diretiva não tem efeito, a menos que uma instanciação de `Explicit` tenha uma configuração de política `Dynamic` definida.</span><span class="sxs-lookup"><span data-stu-id="502f5-177">This directive has no effect unless an instantiation of `Explicit` has a defined `Dynamic` policy setting.</span></span> <span data-ttu-id="502f5-178">Por exemplo, se for o caso de `Explicit<Int32>`, `Implicit<Int32>` é instanciado com seu membros públicos enraizados e seus metadados são disponibilizados por programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="502f5-178">For example, if that's the case for `Explicit<Int32>`, `Implicit<Int32>` is instantiated with its public members rooted, and their metadata is made accessible for dynamic programming.</span></span>  
  
 <span data-ttu-id="502f5-179">Veja a seguir um exemplo real que se aplica a pelo menos um serializador.</span><span class="sxs-lookup"><span data-stu-id="502f5-179">The following is a real-world example that applies to at least one serializer.</span></span> <span data-ttu-id="502f5-180">As diretivas capturam o requisito de que a reflexão sobre algo digitado como `IList<`*algo*`>` também envolve reflexão sobre o tipo `List<`*algo*`>` correspondente sem exigir nenhuma anotação por aplicativo.</span><span class="sxs-lookup"><span data-stu-id="502f5-180">The directives capture the requirement that reflecting on something typed as `IList<`*something*`>` also involves reflecting on the corresponding `List<`*something*`>` type without requiring any per-application annotation.</span></span>  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 <span data-ttu-id="502f5-181">O elemento `<ImpliesType>` também pode aparecer em um elemento `<Method>`, pois em alguns casos instanciar um método genérico implica refletir em uma instanciação de um tipo.</span><span class="sxs-lookup"><span data-stu-id="502f5-181">The `<ImpliesType>` element can also appear within a `<Method>` element, because in some cases instantiating a generic method implies reflecting on a type instantiation.</span></span> <span data-ttu-id="502f5-182">Por exemplo, imagine um método genérico `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` que uma determinada biblioteca acessará dinamicamente juntamente com o associado <xref:System.Collections.Generic.List%601> e <xref:System.Array> tipos.</span><span class="sxs-lookup"><span data-stu-id="502f5-182">For example, imagine a generic method `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` that a given library will access dynamically along with the associated <xref:System.Collections.Generic.List%601> and <xref:System.Array> types.</span></span> <span data-ttu-id="502f5-183">Isso pode ser expressado como:</span><span class="sxs-lookup"><span data-stu-id="502f5-183">This can be expressed as:</span></span>  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public">  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a><span data-ttu-id="502f5-184">Consulte também</span><span class="sxs-lookup"><span data-stu-id="502f5-184">See also</span></span>

- [<span data-ttu-id="502f5-185">Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="502f5-185">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="502f5-186">Elementos da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="502f5-186">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="502f5-187">Configurações da política da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="502f5-187">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)

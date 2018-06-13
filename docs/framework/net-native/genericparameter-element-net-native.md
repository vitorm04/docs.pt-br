---
title: Elemento &lt;GenericParameter&gt; (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c0bf4aff9d7cc657b3005f0a19b09f3df10957c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393088"
---
# <a name="ltgenericparametergt-element-net-native"></a><span data-ttu-id="0daec-102">Elemento &lt;GenericParameter&gt; (.NET Nativo)</span><span class="sxs-lookup"><span data-stu-id="0daec-102">&lt;GenericParameter&gt; Element (.NET Native)</span></span>
<span data-ttu-id="0daec-103">Aplica a política ao tipo de parâmetro de um tipo ou método genérico.</span><span class="sxs-lookup"><span data-stu-id="0daec-103">Applies policy to the parameter type of a generic type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0daec-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0daec-104">Syntax</span></span>  
  
```xml  
<GenericParameter Name="generic_parameter_name"  
                  Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type" />  
                  DataContractSerializer="policy_type"  
                  DataContractJsonSerializer="policy_type"  
                  XmlSerializer="policy_type"  
                  MarshalObject="policy_type"  
                  MarshalDelegate="policy_type"  
                  MarshalStructure="policy_type"  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0daec-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0daec-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0daec-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0daec-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0daec-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="0daec-107">Attributes</span></span>  
  
|<span data-ttu-id="0daec-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="0daec-108">Attribute</span></span>|<span data-ttu-id="0daec-109">Tipo de atributo</span><span class="sxs-lookup"><span data-stu-id="0daec-109">Attribute type</span></span>|<span data-ttu-id="0daec-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="0daec-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="0daec-111">Geral</span><span class="sxs-lookup"><span data-stu-id="0daec-111">General</span></span>|<span data-ttu-id="0daec-112">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="0daec-112">Required attribute.</span></span> <span data-ttu-id="0daec-113">O nome do parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="0daec-113">The name of the generic parameter.</span></span> <span data-ttu-id="0daec-114">Por exemplo, para o delegado genérico <xref:System.Func%603>, o valor do atributo `Name` é "TResult" para aplicar a política de tempo de execução ao valor de retorno do delegado.</span><span class="sxs-lookup"><span data-stu-id="0daec-114">For example, for the generic delegate <xref:System.Func%603>, the value of the `Name` attribute is "TResult" to apply runtime policy to the delegate's return value.</span></span>|  
|`Activate`|<span data-ttu-id="0daec-115">Reflexão</span><span class="sxs-lookup"><span data-stu-id="0daec-115">Reflection</span></span>|<span data-ttu-id="0daec-116">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="0daec-116">Optional attribute.</span></span> <span data-ttu-id="0daec-117">Controla o acesso de tempo de execução a construtores para habilitar a ativação de instâncias.</span><span class="sxs-lookup"><span data-stu-id="0daec-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="0daec-118">Reflexão</span><span class="sxs-lookup"><span data-stu-id="0daec-118">Reflection</span></span>|<span data-ttu-id="0daec-119">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="0daec-119">Optional attribute.</span></span> <span data-ttu-id="0daec-120">Controla a consulta para obter informações sobre elementos do programa, mas não permite qualquer acesso de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0daec-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="0daec-121">Reflexão</span><span class="sxs-lookup"><span data-stu-id="0daec-121">Reflection</span></span>|<span data-ttu-id="0daec-122">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="0daec-122">Optional attribute.</span></span> <span data-ttu-id="0daec-123">Controla o acesso a todos os tipos de membro ao tempo de execução, incluindo construtores, métodos, campos, propriedades e eventos, habilitando a programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="0daec-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="0daec-124">Serialização</span><span class="sxs-lookup"><span data-stu-id="0daec-124">Serialization</span></span>|<span data-ttu-id="0daec-125">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="0daec-125">Optional attribute.</span></span> <span data-ttu-id="0daec-126">Controla o acesso ao tempo de execução para construtores, campos e propriedades para habilitar a serialização e desserialização das instâncias por bibliotecas como o serializador Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="0daec-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="0daec-127">Serialização</span><span class="sxs-lookup"><span data-stu-id="0daec-127">Serialization</span></span>|<span data-ttu-id="0daec-128">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="0daec-128">Optional attribute.</span></span> <span data-ttu-id="0daec-129">Controla a política de serialização que usa a classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0daec-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="0daec-130">Serialização</span><span class="sxs-lookup"><span data-stu-id="0daec-130">Serialization</span></span>|<span data-ttu-id="0daec-131">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="0daec-131">Optional attribute.</span></span> <span data-ttu-id="0daec-132">Controla a política de serialização JSON que usa a classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0daec-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="0daec-133">Serialização</span><span class="sxs-lookup"><span data-stu-id="0daec-133">Serialization</span></span>|<span data-ttu-id="0daec-134">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="0daec-134">Optional attribute.</span></span> <span data-ttu-id="0daec-135">Controla a política de serialização XML que usa a classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0daec-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="0daec-136">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="0daec-136">Interop</span></span>|<span data-ttu-id="0daec-137">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="0daec-137">Optional attribute.</span></span> <span data-ttu-id="0daec-138">Política de controles de marshaling de tipos de referência para o Tempo de Execução do Windows e COM.</span><span class="sxs-lookup"><span data-stu-id="0daec-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="0daec-139">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="0daec-139">Interop</span></span>|<span data-ttu-id="0daec-140">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="0daec-140">Optional attribute.</span></span> <span data-ttu-id="0daec-141">Controla a diretiva de marshaling de tipos delegados como ponteiros de função para código nativo.</span><span class="sxs-lookup"><span data-stu-id="0daec-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="0daec-142">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="0daec-142">Interop</span></span>|<span data-ttu-id="0daec-143">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="0daec-143">Optional attribute.</span></span> <span data-ttu-id="0daec-144">Controla a política de marshaling de tipos de valor para código nativo.</span><span class="sxs-lookup"><span data-stu-id="0daec-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="0daec-145">Atributo de nome</span><span class="sxs-lookup"><span data-stu-id="0daec-145">Name attribute</span></span>  
  
|<span data-ttu-id="0daec-146">Valor</span><span class="sxs-lookup"><span data-stu-id="0daec-146">Value</span></span>|<span data-ttu-id="0daec-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="0daec-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0daec-148">*generic_parameter_name*</span><span class="sxs-lookup"><span data-stu-id="0daec-148">*generic_parameter_name*</span></span>|<span data-ttu-id="0daec-149">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="0daec-149">Required attribute.</span></span> <span data-ttu-id="0daec-150">O nome do parâmetro de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="0daec-150">The name of the generic type parameter.</span></span> <span data-ttu-id="0daec-151">Por exemplo, para o delegado genérico <xref:System.Func%603>, um valor igual a “TResult” para *generic_parameter_name* aplica a política de tempo de execução ao valor retornado do representante.</span><span class="sxs-lookup"><span data-stu-id="0daec-151">For example, for the generic delegate <xref:System.Func%603>, a *generic_parameter_name* value of "TResult" applies runtime policy to the delegate's return value.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="0daec-152">Todos os outros atributos</span><span class="sxs-lookup"><span data-stu-id="0daec-152">All other attributes</span></span>  
  
|<span data-ttu-id="0daec-153">Valor</span><span class="sxs-lookup"><span data-stu-id="0daec-153">Value</span></span>|<span data-ttu-id="0daec-154">Descrição</span><span class="sxs-lookup"><span data-stu-id="0daec-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0daec-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="0daec-155">*policy_setting*</span></span>|<span data-ttu-id="0daec-156">A configuração a ser aplicada a este tipo de política.</span><span class="sxs-lookup"><span data-stu-id="0daec-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="0daec-157">Os valores possíveis são `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` e `Required All`.</span><span class="sxs-lookup"><span data-stu-id="0daec-157">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="0daec-158">Para obter mais informações, consulte [Configurações da política da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="0daec-158">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0daec-159">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0daec-159">Child Elements</span></span>  
 <span data-ttu-id="0daec-160">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0daec-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0daec-161">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0daec-161">Parent Elements</span></span>  
  
|<span data-ttu-id="0daec-162">Elemento</span><span class="sxs-lookup"><span data-stu-id="0daec-162">Element</span></span>|<span data-ttu-id="0daec-163">Descrição</span><span class="sxs-lookup"><span data-stu-id="0daec-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0daec-164">\<Method></span><span class="sxs-lookup"><span data-stu-id="0daec-164">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="0daec-165">Aplica a política de reflexão de tempo de execução a um construtor ou método.</span><span class="sxs-lookup"><span data-stu-id="0daec-165">Applies runtime reflection policy to a constructor or method.</span></span>|  
|[<span data-ttu-id="0daec-166">\<Type></span><span class="sxs-lookup"><span data-stu-id="0daec-166">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="0daec-167">Aplica a política de tempo reflexão de execução a um tipo específico, como uma classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="0daec-167">Applies runtime reflection policy to a particular type, such as a class or structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0daec-168">Comentários</span><span class="sxs-lookup"><span data-stu-id="0daec-168">Remarks</span></span>  
 <span data-ttu-id="0daec-169">O elemento `<GenericParameter>` é filho do elemento [\<Method>](../../../docs/framework/net-native/method-element-net-native.md) ou [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) e é usado para aplicar a política a um parâmetro de tipo genérico específico, que é especificado pelo seu nome no tipo genérico ou na assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="0daec-169">The `<GenericParameter>` element is a child of either the [\<Method>](../../../docs/framework/net-native/method-element-net-native.md) or [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) element and is used to apply policy to a particular generic type parameter, which is specified by its name in the generic type or method signature.</span></span>  
  
 <span data-ttu-id="0daec-170">O elemento `<GenericParameter>` é mais útil quando usado com serializadores.</span><span class="sxs-lookup"><span data-stu-id="0daec-170">The `<GenericParameter>` element is most useful when used with serializers.</span></span> <span data-ttu-id="0daec-171">O exemplo a seguir usa o elemento `<GenericParameter>` para aplicar a política ao tipo `T` em chamadas a sobrecargas do método [JsonConvert.DeserializeObject\<T>(String)](http://james.newtonking.com/json/help/index.html?topic=html/T_Newtonsoft_Json_JsonConvert.htm) do serializador JSON da NewtonSoft.</span><span class="sxs-lookup"><span data-stu-id="0daec-171">The following example uses the `<GenericParameter>` element to apply policy to the type `T` in calls to the NewtonSoft JSON serializer's [JsonConvert.DeserializeObject\<T>(String)](http://james.newtonking.com/json/help/index.html?topic=html/T_Newtonsoft_Json_JsonConvert.htm) method overloads.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0daec-172">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0daec-172">See Also</span></span>  
 [<span data-ttu-id="0daec-173">Elemento \<Method></span><span class="sxs-lookup"><span data-stu-id="0daec-173">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)  
 [<span data-ttu-id="0daec-174">\<Tipo > elemento</span><span class="sxs-lookup"><span data-stu-id="0daec-174">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)  
 [<span data-ttu-id="0daec-175">Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="0daec-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="0daec-176">Configurações da política da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="0daec-176">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="0daec-177">Elementos da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="0daec-177">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)

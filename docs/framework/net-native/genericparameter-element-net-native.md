---
title: <GenericParameter> (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
ms.openlocfilehash: d0b18211206a8f9d4365ab3affe6d1c376003348
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128429"
---
# <a name="genericparameter-element-net-native"></a><span data-ttu-id="8f48a-102">\<GenericParameter> (.NET Nativo)</span><span class="sxs-lookup"><span data-stu-id="8f48a-102">\<GenericParameter> Element (.NET Native)</span></span>
<span data-ttu-id="8f48a-103">Aplica a política ao tipo de parâmetro de um tipo ou método genérico.</span><span class="sxs-lookup"><span data-stu-id="8f48a-103">Applies policy to the parameter type of a generic type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f48a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f48a-104">Syntax</span></span>  
  
```xml  
<GenericParameter Name="generic_parameter_name"  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f48a-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8f48a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8f48a-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8f48a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f48a-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="8f48a-107">Attributes</span></span>  
  
|<span data-ttu-id="8f48a-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="8f48a-108">Attribute</span></span>|<span data-ttu-id="8f48a-109">Tipo de atributo</span><span class="sxs-lookup"><span data-stu-id="8f48a-109">Attribute type</span></span>|<span data-ttu-id="8f48a-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f48a-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="8f48a-111">Geral</span><span class="sxs-lookup"><span data-stu-id="8f48a-111">General</span></span>|<span data-ttu-id="8f48a-112">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="8f48a-112">Required attribute.</span></span> <span data-ttu-id="8f48a-113">O nome do parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="8f48a-113">The name of the generic parameter.</span></span> <span data-ttu-id="8f48a-114">Por exemplo, para o delegado genérico <xref:System.Func%603>, o valor do atributo `Name` é "TResult" para aplicar a política de runtime ao valor de retorno do delegado.</span><span class="sxs-lookup"><span data-stu-id="8f48a-114">For example, for the generic delegate <xref:System.Func%603>, the value of the `Name` attribute is "TResult" to apply runtime policy to the delegate's return value.</span></span>|  
|`Activate`|<span data-ttu-id="8f48a-115">Reflexão</span><span class="sxs-lookup"><span data-stu-id="8f48a-115">Reflection</span></span>|<span data-ttu-id="8f48a-116">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="8f48a-116">Optional attribute.</span></span> <span data-ttu-id="8f48a-117">Controla o acesso de runtime a construtores para habilitar a ativação de instâncias.</span><span class="sxs-lookup"><span data-stu-id="8f48a-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="8f48a-118">Reflexão</span><span class="sxs-lookup"><span data-stu-id="8f48a-118">Reflection</span></span>|<span data-ttu-id="8f48a-119">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="8f48a-119">Optional attribute.</span></span> <span data-ttu-id="8f48a-120">Controla a consulta para obter informações sobre elementos do programa, mas não permite qualquer acesso de runtime.</span><span class="sxs-lookup"><span data-stu-id="8f48a-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="8f48a-121">Reflexão</span><span class="sxs-lookup"><span data-stu-id="8f48a-121">Reflection</span></span>|<span data-ttu-id="8f48a-122">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="8f48a-122">Optional attribute.</span></span> <span data-ttu-id="8f48a-123">Controla o acesso a todos os tipos de membro ao runtime, incluindo construtores, métodos, campos, propriedades e eventos, habilitando a programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="8f48a-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="8f48a-124">Serialização</span><span class="sxs-lookup"><span data-stu-id="8f48a-124">Serialization</span></span>|<span data-ttu-id="8f48a-125">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="8f48a-125">Optional attribute.</span></span> <span data-ttu-id="8f48a-126">Controla o acesso ao runtime para construtores, campos e propriedades para habilitar a serialização e desserialização das instâncias por bibliotecas como o serializador Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="8f48a-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="8f48a-127">Serialização</span><span class="sxs-lookup"><span data-stu-id="8f48a-127">Serialization</span></span>|<span data-ttu-id="8f48a-128">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="8f48a-128">Optional attribute.</span></span> <span data-ttu-id="8f48a-129">Controla a política de serialização que usa a classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8f48a-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="8f48a-130">Serialização</span><span class="sxs-lookup"><span data-stu-id="8f48a-130">Serialization</span></span>|<span data-ttu-id="8f48a-131">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="8f48a-131">Optional attribute.</span></span> <span data-ttu-id="8f48a-132">Controla a política de serialização JSON que usa a classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8f48a-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="8f48a-133">Serialização</span><span class="sxs-lookup"><span data-stu-id="8f48a-133">Serialization</span></span>|<span data-ttu-id="8f48a-134">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="8f48a-134">Optional attribute.</span></span> <span data-ttu-id="8f48a-135">Controla a política de serialização XML que usa a classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8f48a-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="8f48a-136">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="8f48a-136">Interop</span></span>|<span data-ttu-id="8f48a-137">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="8f48a-137">Optional attribute.</span></span> <span data-ttu-id="8f48a-138">Política de controles de marshaling de tipos de referência para o Windows Runtime e COM.</span><span class="sxs-lookup"><span data-stu-id="8f48a-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="8f48a-139">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="8f48a-139">Interop</span></span>|<span data-ttu-id="8f48a-140">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="8f48a-140">Optional attribute.</span></span> <span data-ttu-id="8f48a-141">Controla a diretiva de marshaling de tipos delegados como ponteiros de função para código nativo.</span><span class="sxs-lookup"><span data-stu-id="8f48a-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="8f48a-142">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="8f48a-142">Interop</span></span>|<span data-ttu-id="8f48a-143">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="8f48a-143">Optional attribute.</span></span> <span data-ttu-id="8f48a-144">Controla a política de marshaling de tipos de valor para código nativo.</span><span class="sxs-lookup"><span data-stu-id="8f48a-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="8f48a-145">Atributo de nome</span><span class="sxs-lookup"><span data-stu-id="8f48a-145">Name attribute</span></span>  
  
|<span data-ttu-id="8f48a-146">Valor</span><span class="sxs-lookup"><span data-stu-id="8f48a-146">Value</span></span>|<span data-ttu-id="8f48a-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f48a-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8f48a-148">*generic_parameter_name*</span><span class="sxs-lookup"><span data-stu-id="8f48a-148">*generic_parameter_name*</span></span>|<span data-ttu-id="8f48a-149">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="8f48a-149">Required attribute.</span></span> <span data-ttu-id="8f48a-150">O nome do parâmetro de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="8f48a-150">The name of the generic type parameter.</span></span> <span data-ttu-id="8f48a-151">Por exemplo, para o delegado genérico <xref:System.Func%603>, um valor igual a “TResult” para *generic_parameter_name* aplica a política de runtime ao valor retornado do representante.</span><span class="sxs-lookup"><span data-stu-id="8f48a-151">For example, for the generic delegate <xref:System.Func%603>, a *generic_parameter_name* value of "TResult" applies runtime policy to the delegate's return value.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="8f48a-152">Todos os outros atributos</span><span class="sxs-lookup"><span data-stu-id="8f48a-152">All other attributes</span></span>  
  
|<span data-ttu-id="8f48a-153">Valor</span><span class="sxs-lookup"><span data-stu-id="8f48a-153">Value</span></span>|<span data-ttu-id="8f48a-154">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f48a-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8f48a-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="8f48a-155">*policy_setting*</span></span>|<span data-ttu-id="8f48a-156">A configuração a ser aplicada a este tipo de política.</span><span class="sxs-lookup"><span data-stu-id="8f48a-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="8f48a-157">Os valores possíveis são `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` e `Required All`.</span><span class="sxs-lookup"><span data-stu-id="8f48a-157">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="8f48a-158">Para obter mais informações, consulte [Configurações da política da diretiva de runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="8f48a-158">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8f48a-159">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8f48a-159">Child Elements</span></span>  
 <span data-ttu-id="8f48a-160">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="8f48a-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8f48a-161">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8f48a-161">Parent Elements</span></span>  
  
|<span data-ttu-id="8f48a-162">Elemento</span><span class="sxs-lookup"><span data-stu-id="8f48a-162">Element</span></span>|<span data-ttu-id="8f48a-163">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f48a-163">Description</span></span>|  
|-------------|-----------------|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="8f48a-164">Aplica a política de reflexão de runtime a um construtor ou método.</span><span class="sxs-lookup"><span data-stu-id="8f48a-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="8f48a-165">Aplica a política de tempo reflexão de runtime a um tipo específico, como uma classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="8f48a-165">Applies runtime reflection policy to a particular type, such as a class or structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f48a-166">Comentários</span><span class="sxs-lookup"><span data-stu-id="8f48a-166">Remarks</span></span>  
 <span data-ttu-id="8f48a-167">O `<GenericParameter>` elemento é um filho do [\<Method>](method-element-net-native.md) [\<Type>](type-element-net-native.md) elemento ou e é usado para aplicar a política a um parâmetro de tipo genérico específico, que é especificado por seu nome na assinatura de método ou tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="8f48a-167">The `<GenericParameter>` element is a child of either the [\<Method>](method-element-net-native.md) or [\<Type>](type-element-net-native.md) element and is used to apply policy to a particular generic type parameter, which is specified by its name in the generic type or method signature.</span></span>  
  
 <span data-ttu-id="8f48a-168">O elemento `<GenericParameter>` é mais útil quando usado com serializadores.</span><span class="sxs-lookup"><span data-stu-id="8f48a-168">The `<GenericParameter>` element is most useful when used with serializers.</span></span> <span data-ttu-id="8f48a-169">O exemplo a seguir usa o `<GenericParameter>` elemento para aplicar a política ao tipo `T` em chamadas para as sobrecargas do método [JsonConvert. deserializaobject \<T> (String)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) do serializador JSON NewtonSoft.</span><span class="sxs-lookup"><span data-stu-id="8f48a-169">The following example uses the `<GenericParameter>` element to apply policy to the type `T` in calls to the NewtonSoft JSON serializer's [JsonConvert.DeserializeObject\<T>(String)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) method overloads.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8f48a-170">Confira também</span><span class="sxs-lookup"><span data-stu-id="8f48a-170">See also</span></span>

- [<span data-ttu-id="8f48a-171">\<Method>Elementos</span><span class="sxs-lookup"><span data-stu-id="8f48a-171">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="8f48a-172">\<Type>Elementos</span><span class="sxs-lookup"><span data-stu-id="8f48a-172">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="8f48a-173">Referência do arquivo de configuração de diretivas do runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="8f48a-173">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="8f48a-174">Configurações da política da diretiva de runtime</span><span class="sxs-lookup"><span data-stu-id="8f48a-174">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="8f48a-175">Elementos da diretiva de runtime</span><span class="sxs-lookup"><span data-stu-id="8f48a-175">Runtime Directive Elements</span></span>](runtime-directive-elements.md)

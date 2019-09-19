---
title: <TypeParameter> (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: d37bb1b7-1ddc-4c6d-8ecf-583f804a2479
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0de00b9313b60b3a527dd0380ae90d82731a8c02
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049058"
---
# <a name="typeparameter-element-net-native"></a><span data-ttu-id="b9990-102">\<Elemento de > TypeParameter (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="b9990-102">\<TypeParameter> Element (.NET Native)</span></span>
<span data-ttu-id="b9990-103">Aplica a política ao tipo representado por um argumento Type passado para um método.</span><span class="sxs-lookup"><span data-stu-id="b9990-103">Applies policy to the type represented by a Type argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9990-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b9990-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9990-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b9990-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b9990-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b9990-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9990-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="b9990-107">Attributes</span></span>  
  
|<span data-ttu-id="b9990-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="b9990-108">Attribute</span></span>|<span data-ttu-id="b9990-109">Tipo de atributo</span><span class="sxs-lookup"><span data-stu-id="b9990-109">Attribute type</span></span>|<span data-ttu-id="b9990-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9990-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="b9990-111">Geral</span><span class="sxs-lookup"><span data-stu-id="b9990-111">General</span></span>|<span data-ttu-id="b9990-112">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="b9990-112">Required attribute.</span></span> <span data-ttu-id="b9990-113">O nome do parâmetro do tipo <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="b9990-113">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="b9990-114">Por exemplo, para a assinatura do método `Type.GetInterfaceMap(Type interfaceType)`, o valor do atributo `Name` é "interfaceType".</span><span class="sxs-lookup"><span data-stu-id="b9990-114">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
|`Activate`|<span data-ttu-id="b9990-115">Reflexão</span><span class="sxs-lookup"><span data-stu-id="b9990-115">Reflection</span></span>|<span data-ttu-id="b9990-116">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="b9990-116">Optional attribute.</span></span> <span data-ttu-id="b9990-117">Controla o acesso de tempo de execução a construtores para habilitar a ativação de instâncias.</span><span class="sxs-lookup"><span data-stu-id="b9990-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="b9990-118">Reflexão</span><span class="sxs-lookup"><span data-stu-id="b9990-118">Reflection</span></span>|<span data-ttu-id="b9990-119">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="b9990-119">Optional attribute.</span></span> <span data-ttu-id="b9990-120">Controla a consulta para obter informações sobre elementos do programa, mas não permite qualquer acesso de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b9990-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="b9990-121">Reflexão</span><span class="sxs-lookup"><span data-stu-id="b9990-121">Reflection</span></span>|<span data-ttu-id="b9990-122">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="b9990-122">Optional attribute.</span></span> <span data-ttu-id="b9990-123">Controla o acesso a todos os tipos de membro ao tempo de execução, incluindo construtores, métodos, campos, propriedades e eventos, habilitando a programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="b9990-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="b9990-124">Serialização</span><span class="sxs-lookup"><span data-stu-id="b9990-124">Serialization</span></span>|<span data-ttu-id="b9990-125">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="b9990-125">Optional attribute.</span></span> <span data-ttu-id="b9990-126">Controla o acesso ao tempo de execução para construtores, campos e propriedades para habilitar a serialização e desserialização das instâncias por bibliotecas como o serializador Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="b9990-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="b9990-127">Serialização</span><span class="sxs-lookup"><span data-stu-id="b9990-127">Serialization</span></span>|<span data-ttu-id="b9990-128">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="b9990-128">Optional attribute.</span></span> <span data-ttu-id="b9990-129">Controla a política de serialização que usa a classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b9990-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="b9990-130">Serialização</span><span class="sxs-lookup"><span data-stu-id="b9990-130">Serialization</span></span>|<span data-ttu-id="b9990-131">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="b9990-131">Optional attribute.</span></span> <span data-ttu-id="b9990-132">Controla a política de serialização JSON que usa a classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b9990-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="b9990-133">Serialização</span><span class="sxs-lookup"><span data-stu-id="b9990-133">Serialization</span></span>|<span data-ttu-id="b9990-134">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="b9990-134">Optional attribute.</span></span> <span data-ttu-id="b9990-135">Controla a política de serialização XML que usa a classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b9990-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="b9990-136">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="b9990-136">Interop</span></span>|<span data-ttu-id="b9990-137">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="b9990-137">Optional attribute.</span></span> <span data-ttu-id="b9990-138">Política de controles de marshaling de tipos de referência para o Tempo de Execução do Windows e COM.</span><span class="sxs-lookup"><span data-stu-id="b9990-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="b9990-139">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="b9990-139">Interop</span></span>|<span data-ttu-id="b9990-140">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="b9990-140">Optional attribute.</span></span> <span data-ttu-id="b9990-141">Controla a diretiva de marshaling de tipos delegados como ponteiros de função para código nativo.</span><span class="sxs-lookup"><span data-stu-id="b9990-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="b9990-142">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="b9990-142">Interop</span></span>|<span data-ttu-id="b9990-143">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="b9990-143">Optional attribute.</span></span> <span data-ttu-id="b9990-144">Controla a política de marshaling de tipos de valor para código nativo.</span><span class="sxs-lookup"><span data-stu-id="b9990-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="b9990-145">Atributo de nome</span><span class="sxs-lookup"><span data-stu-id="b9990-145">Name attribute</span></span>  
  
|<span data-ttu-id="b9990-146">Valor</span><span class="sxs-lookup"><span data-stu-id="b9990-146">Value</span></span>|<span data-ttu-id="b9990-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9990-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b9990-148">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="b9990-148">*parameter_name*</span></span>|<span data-ttu-id="b9990-149">O nome do parâmetro do tipo <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="b9990-149">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="b9990-150">Por exemplo, para a assinatura do método `Type.GetInterfaceMap(Type interfaceType)`, o valor do atributo `Name` é "interfaceType".</span><span class="sxs-lookup"><span data-stu-id="b9990-150">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="b9990-151">Todos os outros atributos</span><span class="sxs-lookup"><span data-stu-id="b9990-151">All other attributes</span></span>  
  
|<span data-ttu-id="b9990-152">Valor</span><span class="sxs-lookup"><span data-stu-id="b9990-152">Value</span></span>|<span data-ttu-id="b9990-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9990-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b9990-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="b9990-154">*policy_setting*</span></span>|<span data-ttu-id="b9990-155">A configuração a ser aplicada a este tipo de política.</span><span class="sxs-lookup"><span data-stu-id="b9990-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="b9990-156">Os valores possíveis são `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` e `Required All`.</span><span class="sxs-lookup"><span data-stu-id="b9990-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="b9990-157">Para obter mais informações, consulte [Configurações da política da diretiva de tempo de execução](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="b9990-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b9990-158">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b9990-158">Child Elements</span></span>  
 <span data-ttu-id="b9990-159">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b9990-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b9990-160">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b9990-160">Parent Elements</span></span>  
  
|<span data-ttu-id="b9990-161">Elemento</span><span class="sxs-lookup"><span data-stu-id="b9990-161">Element</span></span>|<span data-ttu-id="b9990-162">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9990-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9990-163">\<Method></span><span class="sxs-lookup"><span data-stu-id="b9990-163">\<Method></span></span>](method-element-net-native.md)|<span data-ttu-id="b9990-164">Aplica a política de reflexão de tempo de execução a um construtor ou método.</span><span class="sxs-lookup"><span data-stu-id="b9990-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9990-165">Comentários</span><span class="sxs-lookup"><span data-stu-id="b9990-165">Remarks</span></span>  
 <span data-ttu-id="b9990-166">O elemento `<TypeParameter>` é semelhante ao elemento [\<Parameter>](parameter-element-net-native.md), exceto pelo fato que ele pode ser aplicado somente aos parâmetros do tipo <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="b9990-166">The `<TypeParameter>` element is similar to the [\<Parameter>](parameter-element-net-native.md) element, except that it can be applied only to parameters of type <xref:System.Type>.</span></span> <span data-ttu-id="b9990-167">Ele aplica a política a qualquer tipo que é representado no tempo de execução pelo argumento do tipo especificado pelo atributo `Name`.</span><span class="sxs-lookup"><span data-stu-id="b9990-167">It applies policy to whatever type is represented at run time by the type argument specified by the `Name` attribute.</span></span>  
  
 <span data-ttu-id="b9990-168">Por exemplo, o serializador NewtonSoft JSON inclui um método `JsonConvert.DeserializeObject(String value, Type type)` estático.</span><span class="sxs-lookup"><span data-stu-id="b9990-168">For example, the NewtonSoft JSON serializer includes a static `JsonConvert.DeserializeObject(String value, Type type)` method.</span></span> <span data-ttu-id="b9990-169">As seguintes diretivas de reflexão:</span><span class="sxs-lookup"><span data-stu-id="b9990-169">The following reflection directives:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject">  
         <GenericParameter Name="type" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
 <span data-ttu-id="b9990-170">especificam que os metadados para o tipo de tempo de execução representado pelo argumento `type` deve ser disponibilizado para serialização.</span><span class="sxs-lookup"><span data-stu-id="b9990-170">specify that metadata for the runtime type represented by the `type` argument should be made available for serialization.</span></span> <span data-ttu-id="b9990-171">Se essas diretivas de tempo de execução para um projeto que inclui o seguinte código-fonte:</span><span class="sxs-lookup"><span data-stu-id="b9990-171">If these runtime directives apply to a project that includes the following source code:</span></span>  
  
```csharp  
Type t = typeof(StockQuote);  
Object obj = JsonConvert.DeserializeObject(data, t);  
```  
  
 <span data-ttu-id="b9990-172">as diretivas de reflexão disponibilizam os metadados para o tipo `StockQuote` disponível para o serializador NewtonSoft JSON no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b9990-172">the reflection directives make metadata for the `StockQuote` type available for the NewtonSoft JSON serializer at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9990-173">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9990-173">See also</span></span>

- [<span data-ttu-id="b9990-174">Elemento \<Method></span><span class="sxs-lookup"><span data-stu-id="b9990-174">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="b9990-175">Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="b9990-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="b9990-176">Configurações da política da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="b9990-176">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="b9990-177">Elementos da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="b9990-177">Runtime Directive Elements</span></span>](runtime-directive-elements.md)

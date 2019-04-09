---
title: <Subtypes> (.NET nativo)
ms.date: 03/30/2017
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e0ec1ed73148b319217a70cc3be99b486be2f8e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208287"
---
# <a name="subtypes-element-net-native"></a><span data-ttu-id="13ce4-102">\<Subtipos > (.NET nativo)</span><span class="sxs-lookup"><span data-stu-id="13ce4-102">\<Subtypes> Element (.NET Native)</span></span>
<span data-ttu-id="13ce4-103">Aplica a política de tempo de execução a todas as classes herdadas do tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="13ce4-103">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13ce4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13ce4-104">Syntax</span></span>  
  
```xml  
<Subtypes Activate="policy_type"  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13ce4-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="13ce4-105">Attributes and Elements</span></span>  
 <span data-ttu-id="13ce4-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="13ce4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13ce4-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="13ce4-107">Attributes</span></span>  
  
|<span data-ttu-id="13ce4-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="13ce4-108">Attribute</span></span>|<span data-ttu-id="13ce4-109">Tipo de atributo</span><span class="sxs-lookup"><span data-stu-id="13ce4-109">Attribute type</span></span>|<span data-ttu-id="13ce4-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="13ce4-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="13ce4-111">Reflexão</span><span class="sxs-lookup"><span data-stu-id="13ce4-111">Reflection</span></span>|<span data-ttu-id="13ce4-112">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="13ce4-112">Optional attribute.</span></span> <span data-ttu-id="13ce4-113">Controla o acesso de tempo de execução a construtores para habilitar a ativação de instâncias.</span><span class="sxs-lookup"><span data-stu-id="13ce4-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="13ce4-114">Reflexão</span><span class="sxs-lookup"><span data-stu-id="13ce4-114">Reflection</span></span>|<span data-ttu-id="13ce4-115">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="13ce4-115">Optional attribute.</span></span> <span data-ttu-id="13ce4-116">Controla a consulta para obter informações sobre elementos do programa, mas não permite qualquer acesso de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="13ce4-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="13ce4-117">Reflexão</span><span class="sxs-lookup"><span data-stu-id="13ce4-117">Reflection</span></span>|<span data-ttu-id="13ce4-118">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="13ce4-118">Optional attribute.</span></span> <span data-ttu-id="13ce4-119">Controla o acesso a todos os tipos de membro ao tempo de execução, incluindo construtores, métodos, campos, propriedades e eventos, habilitando a programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="13ce4-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="13ce4-120">Serialização</span><span class="sxs-lookup"><span data-stu-id="13ce4-120">Serialization</span></span>|<span data-ttu-id="13ce4-121">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="13ce4-121">Optional attribute.</span></span> <span data-ttu-id="13ce4-122">Controla o acesso ao tempo de execução para construtores, campos e propriedades para habilitar a serialização e desserialização das instâncias por bibliotecas como o serializador Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="13ce4-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="13ce4-123">Serialização</span><span class="sxs-lookup"><span data-stu-id="13ce4-123">Serialization</span></span>|<span data-ttu-id="13ce4-124">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="13ce4-124">Optional attribute.</span></span> <span data-ttu-id="13ce4-125">Controla a política de serialização que usa a classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="13ce4-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="13ce4-126">Serialização</span><span class="sxs-lookup"><span data-stu-id="13ce4-126">Serialization</span></span>|<span data-ttu-id="13ce4-127">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="13ce4-127">Optional attribute.</span></span> <span data-ttu-id="13ce4-128">Controla a política de serialização JSON que usa a classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="13ce4-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="13ce4-129">Serialização</span><span class="sxs-lookup"><span data-stu-id="13ce4-129">Serialization</span></span>|<span data-ttu-id="13ce4-130">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="13ce4-130">Optional attribute.</span></span> <span data-ttu-id="13ce4-131">Controla a política de serialização XML que usa a classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="13ce4-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="13ce4-132">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="13ce4-132">Interop</span></span>|<span data-ttu-id="13ce4-133">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="13ce4-133">Optional attribute.</span></span> <span data-ttu-id="13ce4-134">Política de controles de marshaling de tipos de referência para o Tempo de Execução do Windows e COM.</span><span class="sxs-lookup"><span data-stu-id="13ce4-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="13ce4-135">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="13ce4-135">Interop</span></span>|<span data-ttu-id="13ce4-136">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="13ce4-136">Optional attribute.</span></span> <span data-ttu-id="13ce4-137">Controla a diretiva de marshaling de tipos delegados como ponteiros de função para código nativo.</span><span class="sxs-lookup"><span data-stu-id="13ce4-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="13ce4-138">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="13ce4-138">Interop</span></span>|<span data-ttu-id="13ce4-139">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="13ce4-139">Optional attribute.</span></span> <span data-ttu-id="13ce4-140">Controla a política de marshaling de tipos de valor para código nativo.</span><span class="sxs-lookup"><span data-stu-id="13ce4-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="13ce4-141">Todos os atributos</span><span class="sxs-lookup"><span data-stu-id="13ce4-141">All attributes</span></span>  
  
|<span data-ttu-id="13ce4-142">Valor</span><span class="sxs-lookup"><span data-stu-id="13ce4-142">Value</span></span>|<span data-ttu-id="13ce4-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="13ce4-143">Description</span></span>|  
|-----------|-----------------|  
|*<span data-ttu-id="13ce4-144">policy_setting</span><span class="sxs-lookup"><span data-stu-id="13ce4-144">policy_setting</span></span>*|<span data-ttu-id="13ce4-145">A configuração a ser aplicada a este tipo de política.</span><span class="sxs-lookup"><span data-stu-id="13ce4-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="13ce4-146">Os valores possíveis são `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` e `Required All`.</span><span class="sxs-lookup"><span data-stu-id="13ce4-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="13ce4-147">Para obter mais informações, consulte [Configurações da política da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="13ce4-147">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13ce4-148">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="13ce4-148">Child Elements</span></span>  
 <span data-ttu-id="13ce4-149">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="13ce4-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="13ce4-150">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="13ce4-150">Parent Elements</span></span>  
  
|<span data-ttu-id="13ce4-151">Elemento</span><span class="sxs-lookup"><span data-stu-id="13ce4-151">Element</span></span>|<span data-ttu-id="13ce4-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="13ce4-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13ce4-153">\<tipo ></span><span class="sxs-lookup"><span data-stu-id="13ce4-153">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="13ce4-154">Aplica a política de reflexão a um tipo e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="13ce4-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13ce4-155">Comentários</span><span class="sxs-lookup"><span data-stu-id="13ce4-155">Remarks</span></span>  
 <span data-ttu-id="13ce4-156">O elemento `<Subtypes>` aplica a política a todos os subtipos de seu tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="13ce4-156">The `<Subtypes>` element applies policy to all the subtypes of its containing type.</span></span> <span data-ttu-id="13ce4-157">Use-o quando desejar aplicar políticas diferentes a tipos derivados e suas classes base.</span><span class="sxs-lookup"><span data-stu-id="13ce4-157">You use it when you want to apply different policies to derived types and their base classes.</span></span>  
  
 <span data-ttu-id="13ce4-158">Os atributos de reflexão, serialização e interoperabilidade são todos opcionais, embora pelo menos um deve estar presente.</span><span class="sxs-lookup"><span data-stu-id="13ce4-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13ce4-159">Exemplo</span><span class="sxs-lookup"><span data-stu-id="13ce4-159">Example</span></span>  
 <span data-ttu-id="13ce4-160">O exemplo a seguir define uma classe chamada `BaseClass` e uma subclasse denominada `Derived1`.</span><span class="sxs-lookup"><span data-stu-id="13ce4-160">The following example defines a class named `BaseClass` and a subclass named `Derived1`.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 <span data-ttu-id="13ce4-161">Conforme mostrado no código a seguir, o arquivo de diretivas de tempo de execução define explicitamente o `Dynamic` e `Activate` políticas para `BaseClass` para `Excluded`.</span><span class="sxs-lookup"><span data-stu-id="13ce4-161">As shown in the following code, the runtime directives file explicitly sets the `Dynamic` and `Activate` policies for `BaseClass` to `Excluded`.</span></span> <span data-ttu-id="13ce4-162">Devido a isso, objetos do tipo `BaseClass` não pode ser instanciada dinamicamente ou por chamadas para o construtor da classe `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="13ce4-162">Because of this, objects of type `BaseClass` cannot be instantiated dynamically or by calls to the `BaseClass` class constructor.</span></span> <span data-ttu-id="13ce4-163">No entanto, o elemento `<Subtypes>` permite que classes derivadas de `BaseClass` sejam instanciadas dinamicamente e por meio de chamadas para seus construtores de classe.</span><span class="sxs-lookup"><span data-stu-id="13ce4-163">However, the `<Subtypes>` element allows classes derived from `BaseClass` to be instantiated dynamically and through calls to their class constructors.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
   <Assembly Name="*Application*" Dynamic="Required All" />  
     <Type Name="Examples.Libraries.BaseClass" Activate ="Excluded" Dynamic="Excluded" >  
        <Subtypes Activate="Public" Dynamic ="Public"/>  
     </Type>  
  </Application>  
</Directives>  
```  
  
 <span data-ttu-id="13ce4-164">Devido à diretiva `<Subtypes>`, o seguinte código instancia uma instância `Derived1` dinamicamente chamando o método <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType>, que é executado com êxito.</span><span class="sxs-lookup"><span data-stu-id="13ce4-164">Because of the `<Subtypes>` directive, the following code that instantiates a `Derived1` instance dynamically by calling the <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> method executes successfully.</span></span>  <span data-ttu-id="13ce4-165">A variável de bloco aqui é um objeto <xref:System.Windows.Controls.TextBlock> em um aplicativo da Windows Store em branco.</span><span class="sxs-lookup"><span data-stu-id="13ce4-165">The block variable here is a <xref:System.Windows.Controls.TextBlock> object in a blank Windows Store app.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="13ce4-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13ce4-166">See also</span></span>

- [<span data-ttu-id="13ce4-167">\<Tipo > elemento</span><span class="sxs-lookup"><span data-stu-id="13ce4-167">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)
- [<span data-ttu-id="13ce4-168">Referência do arquivo de configuração de diretivas do tempo de execução (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="13ce4-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="13ce4-169">Elementos da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="13ce4-169">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="13ce4-170">Configurações da política da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="13ce4-170">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)

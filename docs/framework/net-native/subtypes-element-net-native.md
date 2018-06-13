---
title: Elemento &lt;Subtypes&gt; (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f850ec24530dd9a7d80f826461cacd9c249dd0de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397982"
---
# <a name="ltsubtypesgt-element-net-native"></a><span data-ttu-id="05757-102">Elemento &lt;Subtypes&gt; (.NET Nativo)</span><span class="sxs-lookup"><span data-stu-id="05757-102">&lt;Subtypes&gt; Element (.NET Native)</span></span>
<span data-ttu-id="05757-103">Aplica a política de tempo de execução a todas as classes herdadas do tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="05757-103">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05757-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="05757-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05757-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="05757-105">Attributes and Elements</span></span>  
 <span data-ttu-id="05757-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="05757-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05757-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="05757-107">Attributes</span></span>  
  
|<span data-ttu-id="05757-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="05757-108">Attribute</span></span>|<span data-ttu-id="05757-109">Tipo de atributo</span><span class="sxs-lookup"><span data-stu-id="05757-109">Attribute type</span></span>|<span data-ttu-id="05757-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="05757-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="05757-111">Reflexão</span><span class="sxs-lookup"><span data-stu-id="05757-111">Reflection</span></span>|<span data-ttu-id="05757-112">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="05757-112">Optional attribute.</span></span> <span data-ttu-id="05757-113">Controla o acesso de tempo de execução a construtores para habilitar a ativação de instâncias.</span><span class="sxs-lookup"><span data-stu-id="05757-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="05757-114">Reflexão</span><span class="sxs-lookup"><span data-stu-id="05757-114">Reflection</span></span>|<span data-ttu-id="05757-115">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="05757-115">Optional attribute.</span></span> <span data-ttu-id="05757-116">Controla a consulta para obter informações sobre elementos do programa, mas não permite qualquer acesso de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="05757-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="05757-117">Reflexão</span><span class="sxs-lookup"><span data-stu-id="05757-117">Reflection</span></span>|<span data-ttu-id="05757-118">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="05757-118">Optional attribute.</span></span> <span data-ttu-id="05757-119">Controla o acesso a todos os tipos de membro ao tempo de execução, incluindo construtores, métodos, campos, propriedades e eventos, habilitando a programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="05757-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="05757-120">Serialização</span><span class="sxs-lookup"><span data-stu-id="05757-120">Serialization</span></span>|<span data-ttu-id="05757-121">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="05757-121">Optional attribute.</span></span> <span data-ttu-id="05757-122">Controla o acesso ao tempo de execução para construtores, campos e propriedades para habilitar a serialização e desserialização das instâncias por bibliotecas como o serializador Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="05757-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="05757-123">Serialização</span><span class="sxs-lookup"><span data-stu-id="05757-123">Serialization</span></span>|<span data-ttu-id="05757-124">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="05757-124">Optional attribute.</span></span> <span data-ttu-id="05757-125">Controla a política de serialização que usa a classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="05757-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="05757-126">Serialização</span><span class="sxs-lookup"><span data-stu-id="05757-126">Serialization</span></span>|<span data-ttu-id="05757-127">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="05757-127">Optional attribute.</span></span> <span data-ttu-id="05757-128">Controla a política de serialização JSON que usa a classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="05757-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="05757-129">Serialização</span><span class="sxs-lookup"><span data-stu-id="05757-129">Serialization</span></span>|<span data-ttu-id="05757-130">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="05757-130">Optional attribute.</span></span> <span data-ttu-id="05757-131">Controla a política de serialização XML que usa a classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="05757-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="05757-132">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="05757-132">Interop</span></span>|<span data-ttu-id="05757-133">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="05757-133">Optional attribute.</span></span> <span data-ttu-id="05757-134">Política de controles de marshaling de tipos de referência para o Tempo de Execução do Windows e COM.</span><span class="sxs-lookup"><span data-stu-id="05757-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="05757-135">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="05757-135">Interop</span></span>|<span data-ttu-id="05757-136">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="05757-136">Optional attribute.</span></span> <span data-ttu-id="05757-137">Controla a diretiva de marshaling de tipos delegados como ponteiros de função para código nativo.</span><span class="sxs-lookup"><span data-stu-id="05757-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="05757-138">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="05757-138">Interop</span></span>|<span data-ttu-id="05757-139">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="05757-139">Optional attribute.</span></span> <span data-ttu-id="05757-140">Controla a política de marshaling de tipos de valor para código nativo.</span><span class="sxs-lookup"><span data-stu-id="05757-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="05757-141">Todos os atributos</span><span class="sxs-lookup"><span data-stu-id="05757-141">All attributes</span></span>  
  
|<span data-ttu-id="05757-142">Valor</span><span class="sxs-lookup"><span data-stu-id="05757-142">Value</span></span>|<span data-ttu-id="05757-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="05757-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="05757-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="05757-144">*policy_setting*</span></span>|<span data-ttu-id="05757-145">A configuração a ser aplicada a este tipo de política.</span><span class="sxs-lookup"><span data-stu-id="05757-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="05757-146">Os valores possíveis são `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` e `Required All`.</span><span class="sxs-lookup"><span data-stu-id="05757-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="05757-147">Para obter mais informações, consulte [Configurações da política da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="05757-147">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="05757-148">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="05757-148">Child Elements</span></span>  
 <span data-ttu-id="05757-149">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="05757-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="05757-150">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="05757-150">Parent Elements</span></span>  
  
|<span data-ttu-id="05757-151">Elemento</span><span class="sxs-lookup"><span data-stu-id="05757-151">Element</span></span>|<span data-ttu-id="05757-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="05757-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05757-153">\<Type></span><span class="sxs-lookup"><span data-stu-id="05757-153">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="05757-154">Aplica a política de reflexão a um tipo e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="05757-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05757-155">Comentários</span><span class="sxs-lookup"><span data-stu-id="05757-155">Remarks</span></span>  
 <span data-ttu-id="05757-156">O elemento `<Subtypes>` aplica a política a todos os subtipos de seu tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="05757-156">The `<Subtypes>` element applies policy to all the subtypes of its containing type.</span></span> <span data-ttu-id="05757-157">Use-o quando desejar aplicar políticas diferentes a tipos derivados e suas classes base.</span><span class="sxs-lookup"><span data-stu-id="05757-157">You use it when you want to apply different policies to derived types and their base classes.</span></span>  
  
 <span data-ttu-id="05757-158">Os atributos de reflexão, serialização e interoperabilidade são todos opcionais, embora pelo menos um deve estar presente.</span><span class="sxs-lookup"><span data-stu-id="05757-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05757-159">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05757-159">Example</span></span>  
 <span data-ttu-id="05757-160">O exemplo a seguir define uma classe chamada `BaseClass` e uma subclasse denominada `Derived1`.</span><span class="sxs-lookup"><span data-stu-id="05757-160">The following example defines a class named `BaseClass` and a subclass named `Derived1`.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 <span data-ttu-id="05757-161">Conforme mostrado no código a seguir, o arquivo de diretivas de tempo de execução define explicitamente o `Dynamic` e `Activate` políticas para `BaseClass` para `Excluded`.</span><span class="sxs-lookup"><span data-stu-id="05757-161">As shown in the following code, the runtime directives file explicitly sets the `Dynamic` and `Activate` policies for `BaseClass` to `Excluded`.</span></span> <span data-ttu-id="05757-162">Devido a isso, objetos do tipo `BaseClass` não pode ser instanciada dinamicamente ou por chamadas para o construtor da classe `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="05757-162">Because of this, objects of type `BaseClass` cannot be instantiated dynamically or by calls to the `BaseClass` class constructor.</span></span> <span data-ttu-id="05757-163">No entanto, o elemento `<Subtypes>` permite que classes derivadas de `BaseClass` sejam instanciadas dinamicamente e por meio de chamadas para seus construtores de classe.</span><span class="sxs-lookup"><span data-stu-id="05757-163">However, the `<Subtypes>` element allows classes derived from `BaseClass` to be instantiated dynamically and through calls to their class constructors.</span></span>  
  
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
  
 <span data-ttu-id="05757-164">Devido à diretiva `<Subtypes>`, o seguinte código instancia uma instância `Derived1` dinamicamente chamando o método <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType>, que é executado com êxito.</span><span class="sxs-lookup"><span data-stu-id="05757-164">Because of the `<Subtypes>` directive, the following code that instantiates a `Derived1` instance dynamically by calling the <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> method executes successfully.</span></span>  <span data-ttu-id="05757-165">A variável de bloco aqui é um objeto <xref:System.Windows.Controls.TextBlock> em um aplicativo da Windows Store em branco.</span><span class="sxs-lookup"><span data-stu-id="05757-165">The block variable here is a <xref:System.Windows.Controls.TextBlock> object in a blank Windows Store app.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="05757-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05757-166">See Also</span></span>  
 [<span data-ttu-id="05757-167">\<Tipo > elemento</span><span class="sxs-lookup"><span data-stu-id="05757-167">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)  
 [<span data-ttu-id="05757-168">Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="05757-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="05757-169">Elementos da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="05757-169">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="05757-170">Configurações da política da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="05757-170">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)

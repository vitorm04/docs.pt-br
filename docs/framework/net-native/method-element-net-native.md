---
title: Elemento &lt;Method&gt; (.NET Nativo)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c6d70fd560cb7b164460eb3882cac88ed733d788
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmethodgt-element-net-native"></a><span data-ttu-id="90030-102">Elemento &lt;Method&gt; (.NET Nativo)</span><span class="sxs-lookup"><span data-stu-id="90030-102">&lt;Method&gt; Element (.NET Native)</span></span>
<span data-ttu-id="90030-103">Aplica a política de reflexão de tempo de execução a um construtor ou método.</span><span class="sxs-lookup"><span data-stu-id="90030-103">Applies runtime reflection policy to a constructor or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90030-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90030-104">Syntax</span></span>  
  
```xml  
<Method Name="method_name"  
        Signature="method_signature"  
        Browse="policy_type"  
        Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90030-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="90030-105">Attributes and Elements</span></span>  
 <span data-ttu-id="90030-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="90030-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90030-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="90030-107">Attributes</span></span>  
  
|<span data-ttu-id="90030-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="90030-108">Attribute</span></span>|<span data-ttu-id="90030-109">Tipo de atributo</span><span class="sxs-lookup"><span data-stu-id="90030-109">Attribute type</span></span>|<span data-ttu-id="90030-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="90030-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="90030-111">Geral</span><span class="sxs-lookup"><span data-stu-id="90030-111">General</span></span>|<span data-ttu-id="90030-112">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="90030-112">Required attribute.</span></span> <span data-ttu-id="90030-113">Especifica o nome do método.</span><span class="sxs-lookup"><span data-stu-id="90030-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="90030-114">Geral</span><span class="sxs-lookup"><span data-stu-id="90030-114">General</span></span>|<span data-ttu-id="90030-115">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="90030-115">Optional attribute.</span></span> <span data-ttu-id="90030-116">Especifica a assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="90030-116">Specifies the method signature.</span></span> <span data-ttu-id="90030-117">Se vários parâmetros estiverem presentes, eles são separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="90030-117">If multiple parameters are present, they are separated by commas.</span></span> <span data-ttu-id="90030-118">Por exemplo, o elemento `<Method>` a seguir define a política para o método <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29>.</span><span class="sxs-lookup"><span data-stu-id="90030-118">For example, the following `<Method>` element defines policy for the <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> method.</span></span><br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> <span data-ttu-id="90030-119">Se o atributo estiver ausente, a diretiva de tempo de execução se aplica a todas as sobrecargas do método.</span><span class="sxs-lookup"><span data-stu-id="90030-119">If the attribute is absent, the runtime directive applies to all overloads of the method.</span></span>|  
|`Browse`|<span data-ttu-id="90030-120">Reflexão</span><span class="sxs-lookup"><span data-stu-id="90030-120">Reflection</span></span>|<span data-ttu-id="90030-121">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="90030-121">Optional attribute.</span></span> <span data-ttu-id="90030-122">Controla consultas para obter informações sobre o método ou para enumerá-lo, mas não permite qualquer invocação dinâmica no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="90030-122">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="90030-123">Reflexão</span><span class="sxs-lookup"><span data-stu-id="90030-123">Reflection</span></span>|<span data-ttu-id="90030-124">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="90030-124">Optional attribute.</span></span> <span data-ttu-id="90030-125">Controla o acesso do tempo de execução a um construtor ou método para habilitar a programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="90030-125">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="90030-126">Essa política garante que um membro pode ser invocado dinamicamente no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="90030-126">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="90030-127">Atributo de nome</span><span class="sxs-lookup"><span data-stu-id="90030-127">Name attribute</span></span>  
  
|<span data-ttu-id="90030-128">Valor</span><span class="sxs-lookup"><span data-stu-id="90030-128">Value</span></span>|<span data-ttu-id="90030-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="90030-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="90030-130">*method_name*</span><span class="sxs-lookup"><span data-stu-id="90030-130">*method_name*</span></span>|<span data-ttu-id="90030-131">O nome do método.</span><span class="sxs-lookup"><span data-stu-id="90030-131">The method name.</span></span> <span data-ttu-id="90030-132">O tipo do método é definido pelo elemento pai [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) ou [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="90030-132">The type of the method is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="90030-133">Atributo de assinatura</span><span class="sxs-lookup"><span data-stu-id="90030-133">Signature attribute</span></span>  
  
|<span data-ttu-id="90030-134">Valor</span><span class="sxs-lookup"><span data-stu-id="90030-134">Value</span></span>|<span data-ttu-id="90030-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="90030-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="90030-136">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="90030-136">*method_signature*</span></span>|<span data-ttu-id="90030-137">Os tipos de parâmetros que formam a assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="90030-137">The parameter types that form the method signature.</span></span> <span data-ttu-id="90030-138">Vários parâmetros são separados por vírgulas, por exemplo, `"System.String,System.Int32,System.Int32)"`.</span><span class="sxs-lookup"><span data-stu-id="90030-138">Multiple parameters are separated by commas, for example, `"System.String,System.Int32,System.Int32)"`.</span></span> <span data-ttu-id="90030-139">Nomes de tipo de parâmetro devem ser totalmente qualificados.</span><span class="sxs-lookup"><span data-stu-id="90030-139">Parameter type names should be fully qualified.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="90030-140">Todos os outros atributos</span><span class="sxs-lookup"><span data-stu-id="90030-140">All other attributes</span></span>  
  
|<span data-ttu-id="90030-141">Valor</span><span class="sxs-lookup"><span data-stu-id="90030-141">Value</span></span>|<span data-ttu-id="90030-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="90030-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="90030-143">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="90030-143">*policy_setting*</span></span>|<span data-ttu-id="90030-144">A configuração a ser aplicada a este tipo de política.</span><span class="sxs-lookup"><span data-stu-id="90030-144">The setting to apply to this policy type.</span></span> <span data-ttu-id="90030-145">Os valores possíveis são `Auto`, `Excluded`, `Included` e `Required`.</span><span class="sxs-lookup"><span data-stu-id="90030-145">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="90030-146">Para obter mais informações, consulte [Configurações da política da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="90030-146">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90030-147">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="90030-147">Child Elements</span></span>  
  
|<span data-ttu-id="90030-148">Elemento</span><span class="sxs-lookup"><span data-stu-id="90030-148">Element</span></span>|<span data-ttu-id="90030-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="90030-149">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90030-150">\<Parameter></span><span class="sxs-lookup"><span data-stu-id="90030-150">\<Parameter></span></span>](../../../docs/framework/net-native/parameter-element-net-native.md)|<span data-ttu-id="90030-151">Aplica a política ao tipo do argumento passado para um método.</span><span class="sxs-lookup"><span data-stu-id="90030-151">Applies policy to the type of the argument passed to a method.</span></span>|  
|[<span data-ttu-id="90030-152">\<GenericParameter></span><span class="sxs-lookup"><span data-stu-id="90030-152">\<GenericParameter></span></span>](../../../docs/framework/net-native/genericparameter-element-net-native.md)|<span data-ttu-id="90030-153">Aplica a política ao tipo de parâmetro de um tipo ou método genérico.</span><span class="sxs-lookup"><span data-stu-id="90030-153">Applies policy to the parameter type of a generic type or method.</span></span>|  
|[<span data-ttu-id="90030-154">\<ImpliesType></span><span class="sxs-lookup"><span data-stu-id="90030-154">\<ImpliesType></span></span>](../../../docs/framework/net-native/impliestype-element-net-native.md)|<span data-ttu-id="90030-155">Aplica a política a um tipo, se esta política tiver sido aplicada ao método representado pelo elemento `<Method>` recipiente.</span><span class="sxs-lookup"><span data-stu-id="90030-155">Applies policy to a type, if that policy has been applied to the method represented by the containing `<Method>` element.</span></span>|  
|[<span data-ttu-id="90030-156">\<TypeParameter></span><span class="sxs-lookup"><span data-stu-id="90030-156">\<TypeParameter></span></span>](../../../docs/framework/net-native/typeparameter-element-net-native.md)|<span data-ttu-id="90030-157">Aplica a política ao tipo representado por um argumento <xref:System.Type> passado para um método.</span><span class="sxs-lookup"><span data-stu-id="90030-157">Applies policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="90030-158">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="90030-158">Parent Elements</span></span>  
  
|<span data-ttu-id="90030-159">Elemento</span><span class="sxs-lookup"><span data-stu-id="90030-159">Element</span></span>|<span data-ttu-id="90030-160">Descrição</span><span class="sxs-lookup"><span data-stu-id="90030-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90030-161">\<Type></span><span class="sxs-lookup"><span data-stu-id="90030-161">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="90030-162">Aplica a política de reflexão a um tipo e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="90030-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="90030-163">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="90030-163">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="90030-164">Aplica a política de reflexão a um tipo genérico construído e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="90030-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90030-165">Comentários</span><span class="sxs-lookup"><span data-stu-id="90030-165">Remarks</span></span>  
 <span data-ttu-id="90030-166">Um elemento `<Method>` de um método genérico aplica sua política a todas as instanciações que não possuem sua própria política.</span><span class="sxs-lookup"><span data-stu-id="90030-166">A `<Method>` element of a generic method applies its policy to all instantiations that do not have their own policy.</span></span>  
  
 <span data-ttu-id="90030-167">Você pode usar o atributo `Signature` para especificar uma política para uma sobrecarga de método específico.</span><span class="sxs-lookup"><span data-stu-id="90030-167">You can use the `Signature` attribute to specify policy for a particular method overload.</span></span> <span data-ttu-id="90030-168">Caso contrário, se o atributo `Signature` estiver ausente, a diretiva de tempo de execução se aplicará a todas as sobrecargas do método.</span><span class="sxs-lookup"><span data-stu-id="90030-168">Otherwise, if the `Signature` attribute is absent, the runtime directive applies to all overloads of the method.</span></span>  
  
 <span data-ttu-id="90030-169">Não é possível definir a política de reflexão de tempo de execução de um construtor usando o `<Method>` elemento.</span><span class="sxs-lookup"><span data-stu-id="90030-169">You cannot define the runtime reflection policy for a constructor by using the `<Method>` element.</span></span> <span data-ttu-id="90030-170">Em vez disso, use o atributo `Activate` do elemento [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md), [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md), [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) ou [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="90030-170">Instead, use the `Activate` attribute of the  [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md), [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md), [\<Type>](../../../docs/framework/net-native/type-element-net-native.md), or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90030-171">Exemplo</span><span class="sxs-lookup"><span data-stu-id="90030-171">Example</span></span>  
 <span data-ttu-id="90030-172">O método `Stringify` no exemplo a seguir é um método de formatação para fins gerais que usa reflexão para converter um objeto em sua representação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="90030-172">The `Stringify` method in the following example is a general-purpose formatting method that uses reflection to convert an object to its string representation.</span></span> <span data-ttu-id="90030-173">Além de chamar o método `ToString` padrão do objeto, o método pode produzir uma cadeia de caracteres de resultados formatada passando um método `ToString` do objeto método em uma cadeia de caracteres, uma implementação de <xref:System.IFormatProvider> ou ambos.</span><span class="sxs-lookup"><span data-stu-id="90030-173">In addition to calling the object's default `ToString` method, the method can produce a formatted result string by passing an object's `ToString` method a format string, an <xref:System.IFormatProvider> implementation, or both.</span></span> <span data-ttu-id="90030-174">Ele também pode chamar uma das sobrecargas de <xref:System.Convert.ToString%2A?displayProperty=nameWithType> que converte um número em sua representação octal, hexadecimal ou binária.</span><span class="sxs-lookup"><span data-stu-id="90030-174">It can also call one of the <xref:System.Convert.ToString%2A?displayProperty=nameWithType> overloads that converts a number to its binary, hexadecimal, or octal representation.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="90030-175">O método `Stringify` pode ser chamado pelo código da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="90030-175">The `Stringify` method can be called by code like the following:</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="90030-176">No entanto, quando compilado com .NET Native, o exemplo pode acionar diversas exceções no tempo de execução, incluindo as exceções <xref:System.NullReferenceException> e [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md). Isso ocorre porque o método `Stringify` destina-se principalmente a oferecer suporte à formatação dinâmica dos tipos primitivos na Biblioteca de Classes do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="90030-176">However, when compiled with .NET Native, the example can throw an number of exceptions at runtime, including <xref:System.NullReferenceException> and [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exceptions, This occurs because the `Stringify` method is intended primarily to support dynamically formatting the primitive types in the .NET Framework Class Library.</span></span> <span data-ttu-id="90030-177">No entanto, seus metadados não são disponibilizados pelo arquivo de diretivas padrão.</span><span class="sxs-lookup"><span data-stu-id="90030-177">However, their metadata is not made available by the default directives file.</span></span> <span data-ttu-id="90030-178">Mesmo quando seus metadados são disponibilizados, o exemplo aciona exceções [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) porque as devidas implementações `ToString` não foram incluídas no código nativo.</span><span class="sxs-lookup"><span data-stu-id="90030-178">Even when their metadata is made available, however, the example throws [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exceptions because the appropriate `ToString` implementations have not been include in the native code.</span></span>  
  
 <span data-ttu-id="90030-179">Essas exceções podem ser eliminadas usando o elemento [Type>\<](../../../docs/framework/net-native/type-element-net-native.md) para definir os tipos cujos metadados devem estar presentes e adicionando elementos `<Method>` para garantir que a implementação das sobrecargas de método que podem ser chamadas dinamicamente também estejam presentes.</span><span class="sxs-lookup"><span data-stu-id="90030-179">These exceptions can all be eliminated by using the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) element to define the types whose metadata must be present, and by adding `<Method>` elements to ensure that the implementation of method overloads that can be called dynamically is also present.</span></span> <span data-ttu-id="90030-180">Veja a seguir o arquivo default.rd.xml que elimina essas exceções e permite que o exemplo seja executado sem erros.</span><span class="sxs-lookup"><span data-stu-id="90030-180">The following is the default.rd.xml file that eliminates these exceptions and allows the example to execute without error.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
     <Assembly Name="*Application*" Dynamic="Required All" />  
  
     <Type Name = "System.Convert" Browse="Required Public" Dynamic="Required Public" >  
        <Method Name="ToString"    Dynamic ="Required" />  
     </Type>  
     <Type Name="System.Double" Browse="Required Public">  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int32" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int64" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Namespace Name="System" >  
        <Type Name="Byte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="DateTime" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Decimal" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Guid" Browse ="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Int16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="SByte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Single" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />           
        </Type>  
        <Type Name="TimeSpan" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />           
        </Type>  
        <Type Name="UInt16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt32" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt64" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
     </Namespace>  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="90030-181">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90030-181">See Also</span></span>  
 [<span data-ttu-id="90030-182">Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="90030-182">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="90030-183">Elementos da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="90030-183">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="90030-184">Configurações da política da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="90030-184">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="90030-185">Elemento \<MethodInstantiation></span><span class="sxs-lookup"><span data-stu-id="90030-185">\<MethodInstantiation> Element</span></span>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)

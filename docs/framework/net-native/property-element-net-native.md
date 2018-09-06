---
title: Elemento &lt;Property&gt; (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47ed75d377814a740edece2b6a69e44acbd8ef0c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43883955"
---
# <a name="ltpropertygt-element-net-native"></a><span data-ttu-id="361fa-102">Elemento &lt;Property&gt; (.NET Nativo)</span><span class="sxs-lookup"><span data-stu-id="361fa-102">&lt;Property&gt; Element (.NET Native)</span></span>
<span data-ttu-id="361fa-103">Aplica a política de reflexão de tempo de execução a uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="361fa-103">Applies runtime reflection policy to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="361fa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="361fa-104">Syntax</span></span>  
  
```xml  
<Property Name="property_name"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="361fa-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="361fa-105">Attributes and Elements</span></span>  
 <span data-ttu-id="361fa-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="361fa-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="361fa-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="361fa-107">Attributes</span></span>  
  
|<span data-ttu-id="361fa-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="361fa-108">Attribute</span></span>|<span data-ttu-id="361fa-109">Tipo de atributo</span><span class="sxs-lookup"><span data-stu-id="361fa-109">Attribute type</span></span>|<span data-ttu-id="361fa-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="361fa-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="361fa-111">Geral</span><span class="sxs-lookup"><span data-stu-id="361fa-111">General</span></span>|<span data-ttu-id="361fa-112">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="361fa-112">Required attribute.</span></span> <span data-ttu-id="361fa-113">Especifica o nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="361fa-113">Specifies the property name.</span></span>|  
|`Browse`|<span data-ttu-id="361fa-114">Reflexão</span><span class="sxs-lookup"><span data-stu-id="361fa-114">Reflection</span></span>|<span data-ttu-id="361fa-115">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="361fa-115">Optional attribute.</span></span> <span data-ttu-id="361fa-116">Controla consultas para obter informações sobre a propriedade ou para enumerá-la, mas não permite qualquer acesso dinâmico no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="361fa-116">Controls querying for information about or enumerating the property but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="361fa-117">Reflexão</span><span class="sxs-lookup"><span data-stu-id="361fa-117">Reflection</span></span>|<span data-ttu-id="361fa-118">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="361fa-118">Optional attribute.</span></span> <span data-ttu-id="361fa-119">Controla o acesso do tempo de execução à propriedade para habilitar programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="361fa-119">Controls runtime access to the property to enable dynamic programming.</span></span> <span data-ttu-id="361fa-120">Essa política garante que uma propriedade pode ser definida ou recuperada dinamicamente no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="361fa-120">This policy ensures that a property can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="361fa-121">Serialização</span><span class="sxs-lookup"><span data-stu-id="361fa-121">Serialization</span></span>|<span data-ttu-id="361fa-122">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="361fa-122">Optional attribute.</span></span> <span data-ttu-id="361fa-123">Controla o acesso do tempo de execução a uma propriedade para habilitar as instâncias de tipo a serem serializadas por bibliotecas como o serializador Newtonsoft JSON ou a ser usado para a associação de dados.</span><span class="sxs-lookup"><span data-stu-id="361fa-123">Controls runtime access to a property to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="361fa-124">Atributo de nome</span><span class="sxs-lookup"><span data-stu-id="361fa-124">Name attribute</span></span>  
  
|<span data-ttu-id="361fa-125">Valor</span><span class="sxs-lookup"><span data-stu-id="361fa-125">Value</span></span>|<span data-ttu-id="361fa-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="361fa-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="361fa-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="361fa-127">*method_name*</span></span>|<span data-ttu-id="361fa-128">O nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="361fa-128">The property name.</span></span> <span data-ttu-id="361fa-129">O tipo da propriedade é definido pelo elemento pai [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) ou [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="361fa-129">The type of the property is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="361fa-130">Todos os outros atributos</span><span class="sxs-lookup"><span data-stu-id="361fa-130">All other attributes</span></span>  
  
|<span data-ttu-id="361fa-131">Valor</span><span class="sxs-lookup"><span data-stu-id="361fa-131">Value</span></span>|<span data-ttu-id="361fa-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="361fa-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="361fa-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="361fa-133">*policy_setting*</span></span>|<span data-ttu-id="361fa-134">A configuração a ser aplicada a este tipo de política para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="361fa-134">The setting to apply to this policy type for the property.</span></span> <span data-ttu-id="361fa-135">Os valores possíveis são `Auto`, `Excluded`, `Included` e `Required`.</span><span class="sxs-lookup"><span data-stu-id="361fa-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="361fa-136">Para obter mais informações, consulte [Configurações da política da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="361fa-136">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="361fa-137">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="361fa-137">Child Elements</span></span>  
 <span data-ttu-id="361fa-138">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="361fa-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="361fa-139">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="361fa-139">Parent Elements</span></span>  
  
|<span data-ttu-id="361fa-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="361fa-140">Element</span></span>|<span data-ttu-id="361fa-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="361fa-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="361fa-142">\<Type></span><span class="sxs-lookup"><span data-stu-id="361fa-142">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="361fa-143">Aplica a política de reflexão a um tipo e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="361fa-143">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="361fa-144">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="361fa-144">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="361fa-145">Aplica a política de reflexão a um tipo genérico construído e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="361fa-145">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="361fa-146">Comentários</span><span class="sxs-lookup"><span data-stu-id="361fa-146">Remarks</span></span>  
 <span data-ttu-id="361fa-147">Se a política da propriedade não for definida explicitamente, ela herdará a política de tempo de execução do seu elemento pai.</span><span class="sxs-lookup"><span data-stu-id="361fa-147">If a property's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="361fa-148">Exemplo</span><span class="sxs-lookup"><span data-stu-id="361fa-148">Example</span></span>  
 <span data-ttu-id="361fa-149">O exemplo a seguir usa reflexão para instanciar um objeto `Book` e exibir seus valores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="361fa-149">The following example uses reflection to instantiate a `Book` object and display its property values.</span></span> <span data-ttu-id="361fa-150">O arquivo default.rd.xml original para o projeto aparece da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="361fa-150">The original default.rd.xml file for the project appears as follows:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 <span data-ttu-id="361fa-151">O arquivo se aplica ao valor `All` para a política `Activate` da classe `Book`, que permite acesso aos construtores de classe por meio de reflexão.</span><span class="sxs-lookup"><span data-stu-id="361fa-151">The file applies the `All` value to the `Activate` policy for the `Book` class, which allows access to class constructors through reflection.</span></span> <span data-ttu-id="361fa-152">A política `Browse` para a classe `Book` é herdada do seu namespace pai.</span><span class="sxs-lookup"><span data-stu-id="361fa-152">The `Browse` policy for the `Book` class is inherited from its parent namespace.</span></span> <span data-ttu-id="361fa-153">Isso é definido para `Required Public`, que disponibiliza metadados no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="361fa-153">This is set to `Required Public`, which makes metadata available at runtime.</span></span>  
  
 <span data-ttu-id="361fa-154">Este é o código-fonte para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="361fa-154">The following is the source code for the example.</span></span> <span data-ttu-id="361fa-155">A variável `outputBlock` representa um controle [TextBlock](https://msdn.microsoft.com/library/windows.ui.xaml.controls.textblock.aspx).</span><span class="sxs-lookup"><span data-stu-id="361fa-155">The `outputBlock` variable represents a [TextBlock](https://msdn.microsoft.com/library/windows.ui.xaml.controls.textblock.aspx) control.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 <span data-ttu-id="361fa-156">No entanto, compilar e executar este exemplo gera uma exceção [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="361fa-156">However, compiling and executing this example throws a [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exception.</span></span> <span data-ttu-id="361fa-157">Embora tenhamos disponibilizados metadados para o tipo `Book` disponível, não realizamos implementações de getters de propriedades disponíveis dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="361fa-157">Although we've made metadata for the `Book` type available, we've failed to make the implementations of the property getters available dynamically.</span></span> <span data-ttu-id="361fa-158">Podemos corrigir esse erro de uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="361fa-158">We can correct this error by either in one of two ways:</span></span>  
  
-   <span data-ttu-id="361fa-159">definindo a política `Dynamic` para o tipo `Book` no seu elemento [\<Type>](../../../docs/framework/net-native/type-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="361fa-159">by defining the `Dynamic` policy for the `Book` type in its [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) element.</span></span>  
  
-   <span data-ttu-id="361fa-160">Adicionando um elemento [\<Property>](../../../docs/framework/net-native/property-element-net-native.md) aninhado para cada propriedade cujo getter gostaríamos de invocar, como faz o arquivo default.rd.xml a seguir.</span><span class="sxs-lookup"><span data-stu-id="361fa-160">By adding a nested [\<Property>](../../../docs/framework/net-native/property-element-net-native.md) element for each property whose getter we'd like to invoke, as the following default.rd.xml file does.</span></span>  
  
    ```xml  
    <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
       <Application>  
          <Namespace Name="LibraryApplications"  Browse="Required Public" >  
             <Type Name="Book"   Activate="All" >  
                <Property Name="Title" Dynamic="Required" />  
                <Property Name="Author" Dynamic="Required" />  
                  <Property Name="ISBN" Dynamic="Required" />  
             </Type>  
          </Namespace>  
       </Application>  
    </Directives>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="361fa-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="361fa-161">See Also</span></span>  
 [<span data-ttu-id="361fa-162">Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="361fa-162">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="361fa-163">Elementos da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="361fa-163">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="361fa-164">Configurações da política da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="361fa-164">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)

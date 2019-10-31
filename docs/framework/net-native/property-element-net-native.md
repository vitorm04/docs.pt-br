---
title: <Property> (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
ms.openlocfilehash: b9bc89804a872dddf1a56c2a3dadc9c3df4f5fd1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128204"
---
# <a name="property-element-net-native"></a><span data-ttu-id="794a9-102">Elemento de > de propriedade \<(.NET Native)</span><span class="sxs-lookup"><span data-stu-id="794a9-102">\<Property> Element (.NET Native)</span></span>
<span data-ttu-id="794a9-103">Aplica a política de reflexão de tempo de execução a uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="794a9-103">Applies runtime reflection policy to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="794a9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="794a9-104">Syntax</span></span>  
  
```xml  
<Property Name="property_name"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="794a9-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="794a9-105">Attributes and Elements</span></span>  
 <span data-ttu-id="794a9-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="794a9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="794a9-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="794a9-107">Attributes</span></span>  
  
|<span data-ttu-id="794a9-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="794a9-108">Attribute</span></span>|<span data-ttu-id="794a9-109">Tipo de atributo</span><span class="sxs-lookup"><span data-stu-id="794a9-109">Attribute type</span></span>|<span data-ttu-id="794a9-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="794a9-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="794a9-111">Geral</span><span class="sxs-lookup"><span data-stu-id="794a9-111">General</span></span>|<span data-ttu-id="794a9-112">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="794a9-112">Required attribute.</span></span> <span data-ttu-id="794a9-113">Especifica o nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="794a9-113">Specifies the property name.</span></span>|  
|`Browse`|<span data-ttu-id="794a9-114">Reflexão</span><span class="sxs-lookup"><span data-stu-id="794a9-114">Reflection</span></span>|<span data-ttu-id="794a9-115">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="794a9-115">Optional attribute.</span></span> <span data-ttu-id="794a9-116">Controla consultas para obter informações sobre a propriedade ou para enumerá-la, mas não permite qualquer acesso dinâmico no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="794a9-116">Controls querying for information about or enumerating the property but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="794a9-117">Reflexão</span><span class="sxs-lookup"><span data-stu-id="794a9-117">Reflection</span></span>|<span data-ttu-id="794a9-118">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="794a9-118">Optional attribute.</span></span> <span data-ttu-id="794a9-119">Controla o acesso do tempo de execução à propriedade para habilitar programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="794a9-119">Controls runtime access to the property to enable dynamic programming.</span></span> <span data-ttu-id="794a9-120">Essa política garante que uma propriedade pode ser definida ou recuperada dinamicamente no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="794a9-120">This policy ensures that a property can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="794a9-121">Serialização</span><span class="sxs-lookup"><span data-stu-id="794a9-121">Serialization</span></span>|<span data-ttu-id="794a9-122">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="794a9-122">Optional attribute.</span></span> <span data-ttu-id="794a9-123">Controla o acesso do tempo de execução a uma propriedade para habilitar as instâncias de tipo a serem serializadas por bibliotecas como o serializador Newtonsoft JSON ou a ser usado para a associação de dados.</span><span class="sxs-lookup"><span data-stu-id="794a9-123">Controls runtime access to a property to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="794a9-124">Atributo de nome</span><span class="sxs-lookup"><span data-stu-id="794a9-124">Name attribute</span></span>  
  
|<span data-ttu-id="794a9-125">Valor</span><span class="sxs-lookup"><span data-stu-id="794a9-125">Value</span></span>|<span data-ttu-id="794a9-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="794a9-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="794a9-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="794a9-127">*method_name*</span></span>|<span data-ttu-id="794a9-128">O nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="794a9-128">The property name.</span></span> <span data-ttu-id="794a9-129">O tipo da propriedade é definido pelo elemento pai [\<Type>](type-element-net-native.md) ou [\<TypeInstantiation>](typeinstantiation-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="794a9-129">The type of the property is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="794a9-130">Todos os outros atributos</span><span class="sxs-lookup"><span data-stu-id="794a9-130">All other attributes</span></span>  
  
|<span data-ttu-id="794a9-131">Valor</span><span class="sxs-lookup"><span data-stu-id="794a9-131">Value</span></span>|<span data-ttu-id="794a9-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="794a9-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="794a9-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="794a9-133">*policy_setting*</span></span>|<span data-ttu-id="794a9-134">A configuração a ser aplicada a este tipo de política para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="794a9-134">The setting to apply to this policy type for the property.</span></span> <span data-ttu-id="794a9-135">Os valores possíveis são `Auto`, `Excluded`, `Included` e `Required`.</span><span class="sxs-lookup"><span data-stu-id="794a9-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="794a9-136">Para obter mais informações, consulte [Configurações da política da diretiva de tempo de execução](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="794a9-136">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="794a9-137">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="794a9-137">Child Elements</span></span>  
 <span data-ttu-id="794a9-138">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="794a9-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="794a9-139">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="794a9-139">Parent Elements</span></span>  
  
|<span data-ttu-id="794a9-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="794a9-140">Element</span></span>|<span data-ttu-id="794a9-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="794a9-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="794a9-142">\<Type></span><span class="sxs-lookup"><span data-stu-id="794a9-142">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="794a9-143">Aplica a política de reflexão a um tipo e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="794a9-143">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="794a9-144">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="794a9-144">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="794a9-145">Aplica a política de reflexão a um tipo genérico construído e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="794a9-145">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="794a9-146">Comentários</span><span class="sxs-lookup"><span data-stu-id="794a9-146">Remarks</span></span>  
 <span data-ttu-id="794a9-147">Se a política da propriedade não for definida explicitamente, ela herdará a política de tempo de execução do seu elemento pai.</span><span class="sxs-lookup"><span data-stu-id="794a9-147">If a property's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="794a9-148">Exemplo</span><span class="sxs-lookup"><span data-stu-id="794a9-148">Example</span></span>  
 <span data-ttu-id="794a9-149">O exemplo a seguir usa reflexão para instanciar um objeto `Book` e exibir seus valores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="794a9-149">The following example uses reflection to instantiate a `Book` object and display its property values.</span></span> <span data-ttu-id="794a9-150">O arquivo default.rd.xml original para o projeto aparece da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="794a9-150">The original default.rd.xml file for the project appears as follows:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 <span data-ttu-id="794a9-151">O arquivo se aplica ao valor `All` para a política `Activate` da classe `Book`, que permite acesso aos construtores de classe por meio de reflexão.</span><span class="sxs-lookup"><span data-stu-id="794a9-151">The file applies the `All` value to the `Activate` policy for the `Book` class, which allows access to class constructors through reflection.</span></span> <span data-ttu-id="794a9-152">A política `Browse` para a classe `Book` é herdada do seu namespace pai.</span><span class="sxs-lookup"><span data-stu-id="794a9-152">The `Browse` policy for the `Book` class is inherited from its parent namespace.</span></span> <span data-ttu-id="794a9-153">Isso é definido para `Required Public`, que disponibiliza metadados no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="794a9-153">This is set to `Required Public`, which makes metadata available at runtime.</span></span>  
  
 <span data-ttu-id="794a9-154">Este é o código-fonte para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="794a9-154">The following is the source code for the example.</span></span> <span data-ttu-id="794a9-155">A variável `outputBlock` representa um controle de <xref:Windows.UI.Xaml.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="794a9-155">The `outputBlock` variable represents a <xref:Windows.UI.Xaml.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 <span data-ttu-id="794a9-156">No entanto, compilar e executar este exemplo gera uma exceção [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="794a9-156">However, compiling and executing this example throws a [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exception.</span></span> <span data-ttu-id="794a9-157">Embora tenhamos disponibilizados metadados para o tipo `Book` disponível, não realizamos implementações de getters de propriedades disponíveis dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="794a9-157">Although we've made metadata for the `Book` type available, we've failed to make the implementations of the property getters available dynamically.</span></span> <span data-ttu-id="794a9-158">Podemos corrigir esse erro de uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="794a9-158">We can correct this error by either in one of two ways:</span></span>  
  
- <span data-ttu-id="794a9-159">definindo a política `Dynamic` para o tipo `Book` no seu elemento [\<Type>](type-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="794a9-159">by defining the `Dynamic` policy for the `Book` type in its [\<Type>](type-element-net-native.md) element.</span></span>  
  
- <span data-ttu-id="794a9-160">Adicionando um elemento [\<Property>](property-element-net-native.md) aninhado para cada propriedade cujo getter gostaríamos de invocar, como faz o arquivo default.rd.xml a seguir.</span><span class="sxs-lookup"><span data-stu-id="794a9-160">By adding a nested [\<Property>](property-element-net-native.md) element for each property whose getter we'd like to invoke, as the following default.rd.xml file does.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="794a9-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="794a9-161">See also</span></span>

- [<span data-ttu-id="794a9-162">Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="794a9-162">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="794a9-163">Elementos da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="794a9-163">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="794a9-164">Configurações da política da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="794a9-164">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)

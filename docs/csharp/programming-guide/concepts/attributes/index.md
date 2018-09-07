---
title: Atributos (C#)
ms.date: 04/26/2018
ms.openlocfilehash: c33d93a4af91e0c61546e8d51ab470f2889c095c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43892380"
---
# <a name="attributes-c"></a><span data-ttu-id="49c08-102">Atributos (C#)</span><span class="sxs-lookup"><span data-stu-id="49c08-102">Attributes (C#)</span></span>

<span data-ttu-id="49c08-103">Os atributos fornecem um método eficiente de associação de metadados, ou informações declarativas, ao código (assemblies, tipos, métodos, propriedades e etc.).</span><span class="sxs-lookup"><span data-stu-id="49c08-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="49c08-104">Após um atributo ser associado a uma entidade de programa, o atributo poderá ser consultado no tempo de execução usando uma técnica chamada *reflexão*.</span><span class="sxs-lookup"><span data-stu-id="49c08-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="49c08-105">Para obter mais informações, consulte [Reflexão (C#)](../reflection.md).</span><span class="sxs-lookup"><span data-stu-id="49c08-105">For more information, see [Reflection (C#)](../reflection.md).</span></span>

<span data-ttu-id="49c08-106">Os atributos têm as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="49c08-106">Attributes have the following properties:</span></span>

- <span data-ttu-id="49c08-107">Os atributos adicionam metadados ao seu programa.</span><span class="sxs-lookup"><span data-stu-id="49c08-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="49c08-108">Os *metadados* são informações sobre os tipos definidos em um programa.</span><span class="sxs-lookup"><span data-stu-id="49c08-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="49c08-109">Todos os assemblies .NET contêm um conjunto de metadados especificado que descreve os tipos e os membros de tipo definidos no assembly.</span><span class="sxs-lookup"><span data-stu-id="49c08-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="49c08-110">Você pode adicionar atributos personalizados para especificar qualquer informação adicional necessária.</span><span class="sxs-lookup"><span data-stu-id="49c08-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="49c08-111">Para obter mais informações, consulte [Criando atributos personalizados (C#)](creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="49c08-111">For more information, see, [Creating Custom Attributes (C#)](creating-custom-attributes.md).</span></span>
- <span data-ttu-id="49c08-112">Você pode aplicar um ou mais atributos a assemblies completos, módulos ou elementos de programas menores, como classes e propriedades.</span><span class="sxs-lookup"><span data-stu-id="49c08-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>
- <span data-ttu-id="49c08-113">Os atributos podem aceitar argumentos da mesma forma que métodos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="49c08-113">Attributes can accept arguments in the same way as methods and properties.</span></span>
- <span data-ttu-id="49c08-114">Seu programa pode examinar seus próprios metadados ou os metadados em outros programas usando reflexão.</span><span class="sxs-lookup"><span data-stu-id="49c08-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="49c08-115">Para obter mais informações, consulte [Acessando atributos usando reflexão (C#)](accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="49c08-115">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="using-attributes"></a><span data-ttu-id="49c08-116">Usando atributos</span><span class="sxs-lookup"><span data-stu-id="49c08-116">Using attributes</span></span>

<span data-ttu-id="49c08-117">Os atributos podem ser colocados em quase qualquer declaração, embora um atributo específico possa restringir os tipos de declarações nas quais ele é válido.</span><span class="sxs-lookup"><span data-stu-id="49c08-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="49c08-118">No C#, você especifica um atributo colocando o nome do atributo entre colchetes ([]) acima da declaração da entidade à qual ele se aplica.</span><span class="sxs-lookup"><span data-stu-id="49c08-118">In C#, you specify an attribute by placing the name of the attribute enclosed in square brackets ([]) above the declaration of the entity to which it applies.</span></span>

<span data-ttu-id="49c08-119">Neste exemplo, o atributo <xref:System.SerializableAttribute> é usado para aplicar uma característica específica a uma classe:</span><span class="sxs-lookup"><span data-stu-id="49c08-119">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>

[!code-csharp[Using the serializable attribute](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

<span data-ttu-id="49c08-120">Um método com o atributo <xref:System.Runtime.InteropServices.DllImportAttribute> é declarado como este exemplo:</span><span class="sxs-lookup"><span data-stu-id="49c08-120">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like the following example:</span></span>

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

<span data-ttu-id="49c08-121">Mais de um atributo pode ser colocado em uma declaração como o seguinte exemplo mostra:</span><span class="sxs-lookup"><span data-stu-id="49c08-121">More than one attribute can be placed on a declaration as the following example shows:</span></span>

[!code-csharp[Including the interop namespace](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

<span data-ttu-id="49c08-122">Alguns atributos podem ser especificados mais de uma vez para uma determinada entidade.</span><span class="sxs-lookup"><span data-stu-id="49c08-122">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="49c08-123">Um exemplo de um atributo multiuso é <xref:System.Diagnostics.ConditionalAttribute>:</span><span class="sxs-lookup"><span data-stu-id="49c08-123">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>

[!code-csharp[Using the conditional attribute](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> <span data-ttu-id="49c08-124">Por convenção, todos os nomes de atributo terminam com a palavra "Atributo" para distingui-los de outros itens nas bibliotecas do .NET.</span><span class="sxs-lookup"><span data-stu-id="49c08-124">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET libraries.</span></span> <span data-ttu-id="49c08-125">No entanto, você não precisa especificar o sufixo de atributo ao usar atributos no código.</span><span class="sxs-lookup"><span data-stu-id="49c08-125">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="49c08-126">Por exemplo, `[DllImport]` é equivalente a `[DllImportAttribute]`, mas `DllImportAttribute` é o nome real do atributo na Biblioteca de Classes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="49c08-126">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework Class Library.</span></span>

### <a name="attribute-parameters"></a><span data-ttu-id="49c08-127">Parâmetros de atributo</span><span class="sxs-lookup"><span data-stu-id="49c08-127">Attribute parameters</span></span>

<span data-ttu-id="49c08-128">Muitos atributos têm parâmetros, que podem ser nomeados, sem nome ou posicionais.</span><span class="sxs-lookup"><span data-stu-id="49c08-128">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="49c08-129">Quaisquer parâmetros de posição devem ser especificados em uma determinada ordem e não podem ser omitidos.</span><span class="sxs-lookup"><span data-stu-id="49c08-129">Any positional parameters must be specified in a certain order and cannot be omitted.</span></span> <span data-ttu-id="49c08-130">Parâmetros nomeados são opcionais e podem ser especificados em qualquer ordem.</span><span class="sxs-lookup"><span data-stu-id="49c08-130">Named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="49c08-131">Os parâmetros posicionais são especificados primeiro.</span><span class="sxs-lookup"><span data-stu-id="49c08-131">Positional parameters are specified first.</span></span> <span data-ttu-id="49c08-132">Por exemplo, esses três atributos são equivalentes:</span><span class="sxs-lookup"><span data-stu-id="49c08-132">For example, these three attributes are equivalent:</span></span>

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

<span data-ttu-id="49c08-133">O primeiro parâmetro, o nome da DLL, é posicional e sempre vir em primeiro lugar; os outros são nomeados.</span><span class="sxs-lookup"><span data-stu-id="49c08-133">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="49c08-134">Nesse caso, ambos os parâmetros nomeados são padronizados como false e, portanto, podem ser omitidos.</span><span class="sxs-lookup"><span data-stu-id="49c08-134">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="49c08-135">Parâmetros de posição correspondem aos parâmetros do construtor de atributo.</span><span class="sxs-lookup"><span data-stu-id="49c08-135">Positional parameters correspond to the parameters of the attribute constructor.</span></span> <span data-ttu-id="49c08-136">Parâmetros nomeados ou opcionais correspondem a propriedades ou a campos do atributo.</span><span class="sxs-lookup"><span data-stu-id="49c08-136">Named or optional parameters correspond to either properties or fields of the attribute.</span></span> <span data-ttu-id="49c08-137">Consulte a documentação do atributo individual para obter informações sobre valores de parâmetro padrão.</span><span class="sxs-lookup"><span data-stu-id="49c08-137">Refer to the individual attribute's documentation for information on default parameter values.</span></span>

### <a name="attribute-targets"></a><span data-ttu-id="49c08-138">Destinos do atributo</span><span class="sxs-lookup"><span data-stu-id="49c08-138">Attribute targets</span></span>

<span data-ttu-id="49c08-139">O *destino* de um atributo é a entidade à qual o atributo se aplica.</span><span class="sxs-lookup"><span data-stu-id="49c08-139">The *target* of an attribute is the entity to which the attribute applies.</span></span> <span data-ttu-id="49c08-140">Por exemplo, um atributo pode ser aplicado a uma classe, um método específico ou um assembly inteiro.</span><span class="sxs-lookup"><span data-stu-id="49c08-140">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="49c08-141">Por padrão, um atributo aplica-se ao elemento que ele precede.</span><span class="sxs-lookup"><span data-stu-id="49c08-141">By default, an attribute applies to the element that it precedes.</span></span> <span data-ttu-id="49c08-142">Mas você pode identificar explicitamente, por exemplo, se um atributo é aplicado a um método, ou a seu parâmetro ou a seu valor retornado.</span><span class="sxs-lookup"><span data-stu-id="49c08-142">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>

<span data-ttu-id="49c08-143">Para identificar explicitamente um atributo de destino, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="49c08-143">To explicitly identify an attribute target, use the following syntax:</span></span>

```csharp
[target : attribute-list]
```

<span data-ttu-id="49c08-144">A lista de possíveis valores `target` é mostrada na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="49c08-144">The list of possible `target` values is shown in the following table.</span></span>

|<span data-ttu-id="49c08-145">Valor de destino</span><span class="sxs-lookup"><span data-stu-id="49c08-145">Target value</span></span>|<span data-ttu-id="49c08-146">Aplica-se a</span><span class="sxs-lookup"><span data-stu-id="49c08-146">Applies to</span></span>|
|------------------|----------------|
|`assembly`|<span data-ttu-id="49c08-147">Assembly inteiro</span><span class="sxs-lookup"><span data-stu-id="49c08-147">Entire assembly</span></span>|
|`module`|<span data-ttu-id="49c08-148">Módulo do assembly atual</span><span class="sxs-lookup"><span data-stu-id="49c08-148">Current assembly module</span></span>|
|`field`|<span data-ttu-id="49c08-149">Campo em uma classe ou um struct</span><span class="sxs-lookup"><span data-stu-id="49c08-149">Field in a class or a struct</span></span>|
|`event`|<span data-ttu-id="49c08-150">evento</span><span class="sxs-lookup"><span data-stu-id="49c08-150">Event</span></span>|
|`method`|<span data-ttu-id="49c08-151">Método ou acessadores de propriedade `get` e `set`</span><span class="sxs-lookup"><span data-stu-id="49c08-151">Method or `get` and `set` property accessors</span></span>|
|`param`|<span data-ttu-id="49c08-152">Parâmetros de método ou parâmetros de acessador de propriedade `set`</span><span class="sxs-lookup"><span data-stu-id="49c08-152">Method parameters or `set` property accessor parameters</span></span>|
|`property`|<span data-ttu-id="49c08-153">Propriedade</span><span class="sxs-lookup"><span data-stu-id="49c08-153">Property</span></span>|
|`return`|<span data-ttu-id="49c08-154">Valor retornado de um método, indexador de propriedade ou acessador de propriedade `get`</span><span class="sxs-lookup"><span data-stu-id="49c08-154">Return value of a method, property indexer, or `get` property accessor</span></span>|
|`type`|<span data-ttu-id="49c08-155">Struct, classe, interface, enum ou delegado</span><span class="sxs-lookup"><span data-stu-id="49c08-155">Struct, class, interface, enum, or delegate</span></span>|

<span data-ttu-id="49c08-156">Especifique o valor de destino `field` para aplicar um atributo ao campo de suporte criado para uma [propriedade autoimplementada](../../../properties.md).</span><span class="sxs-lookup"><span data-stu-id="49c08-156">You would specify the `field` target value to apply an attribute to the backing field created for an [auto-implemented property](../../../properties.md).</span></span>

<span data-ttu-id="49c08-157">O exemplo a seguir mostra como aplicar atributos a módulos e assemblies.</span><span class="sxs-lookup"><span data-stu-id="49c08-157">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="49c08-158">Para obter mais informações, consulte [Atributos comuns (C#)](common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="49c08-158">For more information, see [Common Attributes (C#)](common-attributes.md).</span></span>

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

<span data-ttu-id="49c08-159">O exemplo a seguir mostra como aplicar atributos a métodos, parâmetros de método e valores de retorno de método em C#.</span><span class="sxs-lookup"><span data-stu-id="49c08-159">The following example shows how to apply attributes to methods, method parameters, and method return values in C#.</span></span>

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> <span data-ttu-id="49c08-160">Independentemente dos destinos nos quais `ValidatedContract` é definido como válido, o destino `return` deve ser especificado, mesmo se `ValidatedContract` forem definidos para serem aplicados somente a valores de retorno.</span><span class="sxs-lookup"><span data-stu-id="49c08-160">Regardless of the targets on which `ValidatedContract` is defined to be valid, the `return` target has to be specified, even if `ValidatedContract` were defined to apply only to return values.</span></span> <span data-ttu-id="49c08-161">Em outras palavras, o compilador não usará as informações de `AttributeUsage` para resolver os destinos de atributos ambíguos.</span><span class="sxs-lookup"><span data-stu-id="49c08-161">In other words, the compiler will not use `AttributeUsage` information to resolve ambiguous attribute targets.</span></span> <span data-ttu-id="49c08-162">Para obter mais informações, consulte [AttributeUsage (C#)](attributeusage.md).</span><span class="sxs-lookup"><span data-stu-id="49c08-162">For more information, see [AttributeUsage (C#)](attributeusage.md).</span></span>

## <a name="common-uses-for-attributes"></a><span data-ttu-id="49c08-163">Usos comuns para atributos</span><span class="sxs-lookup"><span data-stu-id="49c08-163">Common uses for attributes</span></span>

<span data-ttu-id="49c08-164">A lista a seguir inclui alguns dos usos comuns de atributos no código:</span><span class="sxs-lookup"><span data-stu-id="49c08-164">The following list includes a few of the common uses of attributes in code:</span></span>

- <span data-ttu-id="49c08-165">Marcar métodos usando o atributo `WebMethod` nos serviços Web para indicar que o método deve ser chamado por meio do protocolo SOAP.</span><span class="sxs-lookup"><span data-stu-id="49c08-165">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="49c08-166">Para obter mais informações, consulte <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="49c08-166">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>
- <span data-ttu-id="49c08-167">Descrever como realizar marshaling de parâmetros de método ao interoperar com código nativo.</span><span class="sxs-lookup"><span data-stu-id="49c08-167">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="49c08-168">Para obter mais informações, consulte <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="49c08-168">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>
- <span data-ttu-id="49c08-169">Descrever as propriedades COM para classes, métodos e interfaces.</span><span class="sxs-lookup"><span data-stu-id="49c08-169">Describing the COM properties for classes, methods, and interfaces.</span></span>
- <span data-ttu-id="49c08-170">Chamar o código não gerenciado usando a classe <xref:System.Runtime.InteropServices.DllImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="49c08-170">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>
- <span data-ttu-id="49c08-171">Descrever o assembly em termos de versão, título, descrição ou marca.</span><span class="sxs-lookup"><span data-stu-id="49c08-171">Describing your assembly in terms of title, version, description, or trademark.</span></span>
- <span data-ttu-id="49c08-172">Descrever quais membros de uma classe serializar para persistência.</span><span class="sxs-lookup"><span data-stu-id="49c08-172">Describing which members of a class to serialize for persistence.</span></span>
- <span data-ttu-id="49c08-173">Descrever como fazer mapeamento entre nós XML e membros de classe para serialização de XML.</span><span class="sxs-lookup"><span data-stu-id="49c08-173">Describing how to map between class members and XML nodes for XML serialization.</span></span>
- <span data-ttu-id="49c08-174">Descrever os requisitos de segurança para métodos.</span><span class="sxs-lookup"><span data-stu-id="49c08-174">Describing the security requirements for methods.</span></span>
- <span data-ttu-id="49c08-175">Especificar as características usadas para impor a segurança.</span><span class="sxs-lookup"><span data-stu-id="49c08-175">Specifying characteristics used to enforce security.</span></span>
- <span data-ttu-id="49c08-176">Controlar otimizações pelo compilador JIT (Just-In-Time) para que o código permaneça fácil de depurar.</span><span class="sxs-lookup"><span data-stu-id="49c08-176">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>
- <span data-ttu-id="49c08-177">Obter informações sobre o chamador de um método.</span><span class="sxs-lookup"><span data-stu-id="49c08-177">Obtaining information about the caller to a method.</span></span>

## <a name="related-sections"></a><span data-ttu-id="49c08-178">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="49c08-178">Related sections</span></span>

<span data-ttu-id="49c08-179">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="49c08-179">For more information, see:</span></span>

- [<span data-ttu-id="49c08-180">Criando atributos personalizados (C#)</span><span class="sxs-lookup"><span data-stu-id="49c08-180">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)  
- [<span data-ttu-id="49c08-181">Acessando atributos usando reflexão (C#)</span><span class="sxs-lookup"><span data-stu-id="49c08-181">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)  
- [<span data-ttu-id="49c08-182">Como criar uma união do C/C++ usando atributos (C#)</span><span class="sxs-lookup"><span data-stu-id="49c08-182">How to: Create a C/C++ Union by Using Attributes (C#)</span></span>](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [<span data-ttu-id="49c08-183">Atributos comuns (C#)</span><span class="sxs-lookup"><span data-stu-id="49c08-183">Common Attributes (C#)</span></span>](common-attributes.md)  
- [<span data-ttu-id="49c08-184">Informações do chamador (C#)</span><span class="sxs-lookup"><span data-stu-id="49c08-184">Caller Information (C#)</span></span>](../caller-information.md)  

## <a name="see-also"></a><span data-ttu-id="49c08-185">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49c08-185">See Also</span></span>

- [<span data-ttu-id="49c08-186">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="49c08-186">C# Programming Guide</span></span>](../../index.md)  
- [<span data-ttu-id="49c08-187">Reflexão (C#)</span><span class="sxs-lookup"><span data-stu-id="49c08-187">Reflection (C#)</span></span>](../reflection.md)  
- [<span data-ttu-id="49c08-188">Atributos</span><span class="sxs-lookup"><span data-stu-id="49c08-188">Attributes</span></span>](../../../../standard/attributes/index.md)  
- [<span data-ttu-id="49c08-189">Usando atributos em C#</span><span class="sxs-lookup"><span data-stu-id="49c08-189">Using Attributes in C#</span></span>](../../../tutorials/attributes.md)  

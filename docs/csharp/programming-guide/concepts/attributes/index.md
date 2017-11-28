---
title: Atributos (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: f148f13f-a0d5-4f22-9c87-4b73d5dde270
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2993ef3f424aa6487681e194f21e0f82193342ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="attributes-c"></a><span data-ttu-id="e7756-102">Atributos (C#)</span><span class="sxs-lookup"><span data-stu-id="e7756-102">Attributes (C#)</span></span>
<span data-ttu-id="e7756-103">Os atributos fornecem um método eficiente de associação de metadados, ou informações declarativas, ao código (assemblies, tipos, métodos, propriedades e etc.).</span><span class="sxs-lookup"><span data-stu-id="e7756-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="e7756-104">Após um atributo ser associado a uma entidade de programa, o atributo poderá ser consultado no tempo de execução usando uma técnica chamada *reflexão*.</span><span class="sxs-lookup"><span data-stu-id="e7756-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="e7756-105">Para obter mais informações, consulte [Reflexão (C#)](../../../../csharp/programming-guide/concepts/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="e7756-105">For more information, see [Reflection (C#)](../../../../csharp/programming-guide/concepts/reflection.md).</span></span>  
  
 <span data-ttu-id="e7756-106">Os atributos têm as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="e7756-106">Attributes have the following properties:</span></span>  
  
-   <span data-ttu-id="e7756-107">Os atributos adicionam metadados ao seu programa.</span><span class="sxs-lookup"><span data-stu-id="e7756-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="e7756-108">Os *metadados* são informações sobre os tipos definidos em um programa.</span><span class="sxs-lookup"><span data-stu-id="e7756-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="e7756-109">Todos os assemblies .NET contêm um conjunto de metadados especificado que descreve os tipos e os membros de tipo definidos no assembly.</span><span class="sxs-lookup"><span data-stu-id="e7756-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="e7756-110">Você pode adicionar atributos personalizados para especificar qualquer informação adicional necessária.</span><span class="sxs-lookup"><span data-stu-id="e7756-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="e7756-111">Para obter mais informações, consulte [Criando atributos personalizados (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="e7756-111">For more information, see, [Creating Custom Attributes (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md).</span></span>  
  
-   <span data-ttu-id="e7756-112">Você pode aplicar um ou mais atributos a assemblies completos, módulos ou elementos de programas menores, como classes e propriedades.</span><span class="sxs-lookup"><span data-stu-id="e7756-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>  
  
-   <span data-ttu-id="e7756-113">Os atributos podem aceitar argumentos da mesma forma que métodos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="e7756-113">Attributes can accept arguments in the same way as methods and properties.</span></span>  
  
-   <span data-ttu-id="e7756-114">Seu programa pode examinar seus próprios metadados ou os metadados em outros programas usando reflexão.</span><span class="sxs-lookup"><span data-stu-id="e7756-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="e7756-115">Para obter mais informações, consulte [Acessando atributos usando reflexão (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="e7756-115">For more information, see [Accessing Attributes by Using Reflection (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="using-attributes"></a><span data-ttu-id="e7756-116">Usando atributos</span><span class="sxs-lookup"><span data-stu-id="e7756-116">Using Attributes</span></span>  
 <span data-ttu-id="e7756-117">Os atributos podem ser colocados em quase qualquer declaração, embora um atributo específico possa restringir os tipos de declarações nas quais ele é válido.</span><span class="sxs-lookup"><span data-stu-id="e7756-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="e7756-118">No C#, você especifica um atributo colocando o nome do atributo entre colchetes ([]) acima da declaração da entidade à qual ele se aplica.</span><span class="sxs-lookup"><span data-stu-id="e7756-118">In C#, you specify an attribute by placing the name of the attribute, enclosed in square brackets ([]), above the declaration of the entity to which it applies.</span></span>  
  
 <span data-ttu-id="e7756-119">Neste exemplo, o atributo <xref:System.SerializableAttribute> é usado para aplicar uma característica específica a uma classe:</span><span class="sxs-lookup"><span data-stu-id="e7756-119">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>  
  
```csharp  
[System.Serializable]  
public class SampleClass  
{  
    // Objects of this type can be serialized.  
}  
```  
  
 <span data-ttu-id="e7756-120">Um método com o atributo <xref:System.Runtime.InteropServices.DllImportAttribute> é declarado como este:</span><span class="sxs-lookup"><span data-stu-id="e7756-120">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like this:</span></span>  
  
```csharp  
using System.Runtime.InteropServices;  
```  
  
```csharp  
[System.Runtime.InteropServices.DllImport("user32.dll")]  
extern static void SampleMethod();  
```  
  
 <span data-ttu-id="e7756-121">Mais de um atributo pode ser colocado em uma declaração:</span><span class="sxs-lookup"><span data-stu-id="e7756-121">More than one attribute can be placed on a declaration:</span></span>  
  
```csharp  
using System.Runtime.InteropServices;  
```  
  
```csharp  
void MethodA([In][Out] ref double x) { }  
void MethodB([Out][In] ref double x) { }  
void MethodC([In, Out] ref double x) { }  
```  
  
 <span data-ttu-id="e7756-122">Alguns atributos podem ser especificados mais de uma vez para uma determinada entidade.</span><span class="sxs-lookup"><span data-stu-id="e7756-122">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="e7756-123">Um exemplo de um atributo multiuso é <xref:System.Diagnostics.ConditionalAttribute>:</span><span class="sxs-lookup"><span data-stu-id="e7756-123">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>  
  
```csharp  
[Conditional("DEBUG"), Conditional("TEST1")]  
void TraceMethod()  
{  
    // ...  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="e7756-124">Por convenção, todos os nomes de atributo terminam com a palavra "Atributo" para distingui-los de outros itens no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e7756-124">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET Framework.</span></span> <span data-ttu-id="e7756-125">No entanto, você não precisa especificar o sufixo de atributo ao usar atributos no código.</span><span class="sxs-lookup"><span data-stu-id="e7756-125">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="e7756-126">Por exemplo, `[DllImport]` é equivalente a `[DllImportAttribute]`, mas `DllImportAttribute` é o nome do atributo real no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e7756-126">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework.</span></span>  
  
### <a name="attribute-parameters"></a><span data-ttu-id="e7756-127">Parâmetros de atributo</span><span class="sxs-lookup"><span data-stu-id="e7756-127">Attribute Parameters</span></span>  
 <span data-ttu-id="e7756-128">Muitos atributos têm parâmetros, que podem ser nomeados, sem nome ou posicionais.</span><span class="sxs-lookup"><span data-stu-id="e7756-128">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="e7756-129">Quaisquer parâmetros posicionais devem ser especificados em uma determinada ordem e não podem ser omitidos. Os parâmetros nomeados são opcionais e podem ser especificados em qualquer ordem.</span><span class="sxs-lookup"><span data-stu-id="e7756-129">Any positional parameters must be specified in a certain order and cannot be omitted; named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="e7756-130">Os parâmetros posicionais são especificados primeiro.</span><span class="sxs-lookup"><span data-stu-id="e7756-130">Positional parameters are specified first.</span></span> <span data-ttu-id="e7756-131">Por exemplo, esses três atributos são equivalentes:</span><span class="sxs-lookup"><span data-stu-id="e7756-131">For example, these three attributes are equivalent:</span></span>  
  
```csharp  
[DllImport("user32.dll")]  
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]  
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]  
```  
  
 <span data-ttu-id="e7756-132">O primeiro parâmetro, o nome da DLL, é posicional e sempre vir em primeiro lugar; os outros são nomeados.</span><span class="sxs-lookup"><span data-stu-id="e7756-132">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="e7756-133">Nesse caso, ambos os parâmetros nomeados são padronizados como false e, portanto, podem ser omitidos.</span><span class="sxs-lookup"><span data-stu-id="e7756-133">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="e7756-134">Consulte a documentação do atributo individual para obter informações sobre valores de parâmetro padrão.</span><span class="sxs-lookup"><span data-stu-id="e7756-134">Refer to the individual attribute's documentation for information on default parameter values.</span></span>  
  
### <a name="attribute-targets"></a><span data-ttu-id="e7756-135">Destinos de Atributos</span><span class="sxs-lookup"><span data-stu-id="e7756-135">Attribute Targets</span></span>  
 <span data-ttu-id="e7756-136">O *destino* de um atributo é a entidade à qual o atributo se aplica.</span><span class="sxs-lookup"><span data-stu-id="e7756-136">The *target* of an attribute is the entity to which the attribute applies.</span></span> <span data-ttu-id="e7756-137">Por exemplo, um atributo pode ser aplicado a uma classe, um método específico ou um assembly inteiro.</span><span class="sxs-lookup"><span data-stu-id="e7756-137">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="e7756-138">Por padrão, um atributo aplica-se ao elemento que ele precede.</span><span class="sxs-lookup"><span data-stu-id="e7756-138">By default, an attribute applies to the element that it precedes.</span></span> <span data-ttu-id="e7756-139">Mas você pode identificar explicitamente, por exemplo, se um atributo é aplicado a um método, ou a seu parâmetro ou a seu valor retornado.</span><span class="sxs-lookup"><span data-stu-id="e7756-139">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>  
  
 <span data-ttu-id="e7756-140">Para identificar explicitamente um atributo de destino, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="e7756-140">To explicitly identify an attribute target, use the following syntax:</span></span>  
  
```csharp  
[target : attribute-list]  
```  
  
 <span data-ttu-id="e7756-141">A lista de possíveis valores `target` é mostrada na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="e7756-141">The list of possible `target` values is shown in the following table.</span></span>  
  
|<span data-ttu-id="e7756-142">Valor de destino</span><span class="sxs-lookup"><span data-stu-id="e7756-142">Target value</span></span>|<span data-ttu-id="e7756-143">Aplica-se a</span><span class="sxs-lookup"><span data-stu-id="e7756-143">Applies to</span></span>|  
|------------------|----------------|  
|`assembly`|<span data-ttu-id="e7756-144">Assembly inteiro</span><span class="sxs-lookup"><span data-stu-id="e7756-144">Entire assembly</span></span>|  
|`module`|<span data-ttu-id="e7756-145">Módulo do assembly atual</span><span class="sxs-lookup"><span data-stu-id="e7756-145">Current assembly module</span></span>|  
|`field`|<span data-ttu-id="e7756-146">Campo em uma classe ou um struct</span><span class="sxs-lookup"><span data-stu-id="e7756-146">Field in a class or a struct</span></span>|  
|`event`|<span data-ttu-id="e7756-147">Evento</span><span class="sxs-lookup"><span data-stu-id="e7756-147">Event</span></span>|  
|`method`|<span data-ttu-id="e7756-148">Método ou acessadores de propriedade `get` e `set`</span><span class="sxs-lookup"><span data-stu-id="e7756-148">Method or `get` and `set` property accessors</span></span>|  
|`param`|<span data-ttu-id="e7756-149">Parâmetros de método ou parâmetros de acessador de propriedade `set`</span><span class="sxs-lookup"><span data-stu-id="e7756-149">Method parameters or `set` property accessor parameters</span></span>|  
|`property`|<span data-ttu-id="e7756-150">Propriedade</span><span class="sxs-lookup"><span data-stu-id="e7756-150">Property</span></span>|  
|`return`|<span data-ttu-id="e7756-151">Valor retornado de um método, indexador de propriedade ou acessador de propriedade `get`</span><span class="sxs-lookup"><span data-stu-id="e7756-151">Return value of a method, property indexer, or `get` property accessor</span></span>|  
|`type`|<span data-ttu-id="e7756-152">Struct, classe, interface, enum ou delegado</span><span class="sxs-lookup"><span data-stu-id="e7756-152">Struct, class, interface, enum, or delegate</span></span>|  
  
 <span data-ttu-id="e7756-153">O exemplo a seguir mostra como aplicar atributos a módulos e assemblies.</span><span class="sxs-lookup"><span data-stu-id="e7756-153">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="e7756-154">Para obter mais informações, consulte [Atributos comuns (C#)](../../../../csharp/programming-guide/concepts/attributes/common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="e7756-154">For more information, see [Common Attributes (C#)](../../../../csharp/programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
```csharp  
using System;  
using System.Reflection;  
[assembly: AssemblyTitleAttribute("Production assembly 4")]  
[module: CLSCompliant(true)]  
```  
  
 <span data-ttu-id="e7756-155">O exemplo a seguir mostra como aplicar atributos a métodos, parâmetros de método e valores de retorno de método em C#.</span><span class="sxs-lookup"><span data-stu-id="e7756-155">The following example shows how to apply attributes to methods, method parameters, and method return values in C#.</span></span>  
  
```csharp  
// default: applies to method  
[SomeAttr]  
int Method1() { return 0; }  
  
// applies to method  
[method: SomeAttr]  
int Method2() { return 0; }  
  
// applies to return value  
[return: SomeAttr]  
int Method3() { return 0; }  
```  
  
> [!NOTE]
>  <span data-ttu-id="e7756-156">Independentemente dos destinos nos quais `SomeAttr` é definido como válido, o destino `return` deve ser especificado, mesmo se `SomeAttr` forem definidos para serem aplicados somente a valores de retorno.</span><span class="sxs-lookup"><span data-stu-id="e7756-156">Regardless of the targets on which `SomeAttr` is defined to be valid, the `return` target has to be specified, even if `SomeAttr` were defined to apply only to return values.</span></span> <span data-ttu-id="e7756-157">Em outras palavras, o compilador não usará as informações de `AttributeUsage` para resolver os destinos de atributos ambíguos.</span><span class="sxs-lookup"><span data-stu-id="e7756-157">In other words, the compiler will not use `AttributeUsage` information to resolve ambiguous attribute targets.</span></span> <span data-ttu-id="e7756-158">Para obter mais informações, consulte [AttributeUsage (C#)](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md).</span><span class="sxs-lookup"><span data-stu-id="e7756-158">For more information, see [AttributeUsage (C#)](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md).</span></span>  
  
## <a name="common-uses-for-attributes"></a><span data-ttu-id="e7756-159">Usos comuns para os atributos</span><span class="sxs-lookup"><span data-stu-id="e7756-159">Common Uses for Attributes</span></span>  
 <span data-ttu-id="e7756-160">A lista a seguir inclui alguns dos usos comuns de atributos no código:</span><span class="sxs-lookup"><span data-stu-id="e7756-160">The following list includes a few of the common uses of attributes in code:</span></span>  
  
-   <span data-ttu-id="e7756-161">Marcar métodos usando o atributo `WebMethod` nos serviços Web para indicar que o método deve ser chamado por meio do protocolo SOAP.</span><span class="sxs-lookup"><span data-stu-id="e7756-161">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="e7756-162">Para obter mais informações, consulte <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e7756-162">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
-   <span data-ttu-id="e7756-163">Descrever como realizar marshaling de parâmetros de método ao interoperar com código nativo.</span><span class="sxs-lookup"><span data-stu-id="e7756-163">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="e7756-164">Para obter mais informações, consulte <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e7756-164">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>  
  
-   <span data-ttu-id="e7756-165">Descrever as propriedades COM para classes, métodos e interfaces.</span><span class="sxs-lookup"><span data-stu-id="e7756-165">Describing the COM properties for classes, methods, and interfaces.</span></span>  
  
-   <span data-ttu-id="e7756-166">Chamar o código não gerenciado usando a classe <xref:System.Runtime.InteropServices.DllImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e7756-166">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>  
  
-   <span data-ttu-id="e7756-167">Descrever o assembly em termos de versão, título, descrição ou marca.</span><span class="sxs-lookup"><span data-stu-id="e7756-167">Describing your assembly in terms of title, version, description, or trademark.</span></span>  
  
-   <span data-ttu-id="e7756-168">Descrever quais membros de uma classe serializar para persistência.</span><span class="sxs-lookup"><span data-stu-id="e7756-168">Describing which members of a class to serialize for persistence.</span></span>  
  
-   <span data-ttu-id="e7756-169">Descrever como fazer mapeamento entre nós XML e membros de classe para serialização de XML.</span><span class="sxs-lookup"><span data-stu-id="e7756-169">Describing how to map between class members and XML nodes for XML serialization.</span></span>  
  
-   <span data-ttu-id="e7756-170">Descrever os requisitos de segurança para métodos.</span><span class="sxs-lookup"><span data-stu-id="e7756-170">Describing the security requirements for methods.</span></span>  
  
-   <span data-ttu-id="e7756-171">Especificar as características usadas para impor a segurança.</span><span class="sxs-lookup"><span data-stu-id="e7756-171">Specifying characteristics used to enforce security.</span></span>  
  
-   <span data-ttu-id="e7756-172">Controlar otimizações pelo compilador JIT (Just-In-Time) para que o código permaneça fácil de depurar.</span><span class="sxs-lookup"><span data-stu-id="e7756-172">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>  
  
-   <span data-ttu-id="e7756-173">Obter informações sobre o chamador de um método.</span><span class="sxs-lookup"><span data-stu-id="e7756-173">Obtaining information about the caller to a method.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e7756-174">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="e7756-174">Related Sections</span></span>  
 <span data-ttu-id="e7756-175">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="e7756-175">For more information, see:</span></span>  
  
-   [<span data-ttu-id="e7756-176">Criando atributos personalizados (C#)</span><span class="sxs-lookup"><span data-stu-id="e7756-176">Creating Custom Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
-   [<span data-ttu-id="e7756-177">Acessando atributos usando reflexão (C#)</span><span class="sxs-lookup"><span data-stu-id="e7756-177">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
-   [<span data-ttu-id="e7756-178">Como criar uma união do C/C++ usando atributos (C#)</span><span class="sxs-lookup"><span data-stu-id="e7756-178">How to: Create a C/C++ Union by Using Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
-   [<span data-ttu-id="e7756-179">Atributos comuns (C#)</span><span class="sxs-lookup"><span data-stu-id="e7756-179">Common Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/common-attributes.md)  
  
-   [<span data-ttu-id="e7756-180">Informações do chamador (C#)</span><span class="sxs-lookup"><span data-stu-id="e7756-180">Caller Information (C#)</span></span>](../../../../csharp/programming-guide/concepts/caller-information.md)  
  
## <a name="see-also"></a><span data-ttu-id="e7756-181">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7756-181">See Also</span></span>  
 [<span data-ttu-id="e7756-182">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e7756-182">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e7756-183">Reflexão (C#)</span><span class="sxs-lookup"><span data-stu-id="e7756-183">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="e7756-184">Atributos</span><span class="sxs-lookup"><span data-stu-id="e7756-184">Attributes</span></span>](https://msdn.microsoft.com/library/5x6cd29c)

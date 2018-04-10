---
title: Visão geral de atributos (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1449f69b-c063-41de-8d89-f0bbdcf96ac6
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2b78eb3e5ac52ec89e810fde682249c689ba304a
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="attributes-overview-visual-basic"></a><span data-ttu-id="38af7-102">Visão geral de atributos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38af7-102">Attributes overview (Visual Basic)</span></span>
<span data-ttu-id="38af7-103">Os atributos fornecem um método eficiente de associação de metadados, ou informações declarativas, ao código (assemblies, tipos, métodos, propriedades e etc.).</span><span class="sxs-lookup"><span data-stu-id="38af7-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="38af7-104">Após um atributo ser associado a uma entidade de programa, o atributo poderá ser consultado no tempo de execução usando uma técnica chamada *reflexão*.</span><span class="sxs-lookup"><span data-stu-id="38af7-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="38af7-105">Para obter mais informações, consulte [Reflexão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="38af7-105">For more information, see [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).</span></span>  
  
 <span data-ttu-id="38af7-106">Os atributos têm as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="38af7-106">Attributes have the following properties:</span></span>  
  
-   <span data-ttu-id="38af7-107">Os atributos adicionam metadados ao seu programa.</span><span class="sxs-lookup"><span data-stu-id="38af7-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="38af7-108">Os *metadados* são informações sobre os tipos definidos em um programa.</span><span class="sxs-lookup"><span data-stu-id="38af7-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="38af7-109">Todos os assemblies .NET contêm um conjunto de metadados especificado que descreve os tipos e os membros de tipo definidos no assembly.</span><span class="sxs-lookup"><span data-stu-id="38af7-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="38af7-110">Você pode adicionar atributos personalizados para especificar qualquer informação adicional necessária.</span><span class="sxs-lookup"><span data-stu-id="38af7-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="38af7-111">Para obter mais informações, consulte [Criando atributos personalizados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="38af7-111">For more information, see, [Creating Custom Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).</span></span>  
  
-   <span data-ttu-id="38af7-112">Você pode aplicar um ou mais atributos a assemblies completos, módulos ou elementos de programas menores, como classes e propriedades.</span><span class="sxs-lookup"><span data-stu-id="38af7-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>  
  
-   <span data-ttu-id="38af7-113">Os atributos podem aceitar argumentos da mesma forma que métodos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="38af7-113">Attributes can accept arguments in the same way as methods and properties.</span></span>  
  
-   <span data-ttu-id="38af7-114">Seu programa pode examinar seus próprios metadados ou os metadados em outros programas usando reflexão.</span><span class="sxs-lookup"><span data-stu-id="38af7-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="38af7-115">Para obter mais informações, consulte [Acessando atributos usando reflexão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="38af7-115">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="using-attributes"></a><span data-ttu-id="38af7-116">Usando atributos</span><span class="sxs-lookup"><span data-stu-id="38af7-116">Using Attributes</span></span>  
 <span data-ttu-id="38af7-117">Os atributos podem ser colocados em quase qualquer declaração, embora um atributo específico possa restringir os tipos de declarações nas quais ele é válido.</span><span class="sxs-lookup"><span data-stu-id="38af7-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="38af7-118">No Visual Basic, um atributo fica entre colchetes angulares(\< >).</span><span class="sxs-lookup"><span data-stu-id="38af7-118">In Visual Basic, an attribute is enclosed in angle brackets (\< >).</span></span> <span data-ttu-id="38af7-119">Ele deverá aparecer imediatamente antes do elemento ao qual ele é aplicado, na mesma linha.</span><span class="sxs-lookup"><span data-stu-id="38af7-119">It must appear immediately before the element to which it is applied, on the same line.</span></span>  
  
 <span data-ttu-id="38af7-120">Neste exemplo, o atributo <xref:System.SerializableAttribute> é usado para aplicar uma característica específica a uma classe:</span><span class="sxs-lookup"><span data-stu-id="38af7-120">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>  
  
```vb  
<System.Serializable()> Public Class SampleClass  
    ' Objects of this type can be serialized.  
End Class  
```  
  
 <span data-ttu-id="38af7-121">Um método com o atributo <xref:System.Runtime.InteropServices.DllImportAttribute> é declarado como este:</span><span class="sxs-lookup"><span data-stu-id="38af7-121">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like this:</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
<System.Runtime.InteropServices.DllImport("user32.dll")>   
Sub SampleMethod()  
End Sub  
```  
  
 <span data-ttu-id="38af7-122">Mais de um atributo pode ser colocado em uma declaração:</span><span class="sxs-lookup"><span data-stu-id="38af7-122">More than one attribute can be placed on a declaration:</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
Sub MethodA(<[In](), Out()> ByVal x As Double)  
End Sub  
Sub MethodB(<Out(), [In]()> ByVal x As Double)  
End Sub  
```  
  
 <span data-ttu-id="38af7-123">Alguns atributos podem ser especificados mais de uma vez para uma determinada entidade.</span><span class="sxs-lookup"><span data-stu-id="38af7-123">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="38af7-124">Um exemplo de um atributo multiuso é <xref:System.Diagnostics.ConditionalAttribute>:</span><span class="sxs-lookup"><span data-stu-id="38af7-124">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>  
  
```vb  
<Conditional("DEBUG"), Conditional("TEST1")>   
Sub TraceMethod()  
End Sub  
```  
  
> [!NOTE]
>  <span data-ttu-id="38af7-125">Por convenção, todos os nomes de atributo terminam com a palavra "Atributo" para distingui-los de outros itens no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="38af7-125">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET Framework.</span></span> <span data-ttu-id="38af7-126">No entanto, você não precisa especificar o sufixo de atributo ao usar atributos no código.</span><span class="sxs-lookup"><span data-stu-id="38af7-126">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="38af7-127">Por exemplo, `[DllImport]` é equivalente a `[DllImportAttribute]`, mas `DllImportAttribute` é o nome do atributo real no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="38af7-127">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework.</span></span>  
  
### <a name="attribute-parameters"></a><span data-ttu-id="38af7-128">Parâmetros de atributo</span><span class="sxs-lookup"><span data-stu-id="38af7-128">Attribute Parameters</span></span>  
 <span data-ttu-id="38af7-129">Muitos atributos têm parâmetros, que podem ser nomeados, sem nome ou posicionais.</span><span class="sxs-lookup"><span data-stu-id="38af7-129">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="38af7-130">Quaisquer parâmetros posicionais devem ser especificados em uma determinada ordem e não podem ser omitidos. Os parâmetros nomeados são opcionais e podem ser especificados em qualquer ordem.</span><span class="sxs-lookup"><span data-stu-id="38af7-130">Any positional parameters must be specified in a certain order and cannot be omitted; named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="38af7-131">Os parâmetros posicionais são especificados primeiro.</span><span class="sxs-lookup"><span data-stu-id="38af7-131">Positional parameters are specified first.</span></span> <span data-ttu-id="38af7-132">Por exemplo, esses três atributos são equivalentes:</span><span class="sxs-lookup"><span data-stu-id="38af7-132">For example, these three attributes are equivalent:</span></span>  
  
```vb  
<DllImport("user32.dll")>  
<DllImport("user32.dll", SetLastError:=False, ExactSpelling:=False)>  
<DllImport("user32.dll", ExactSpelling:=False, SetLastError:=False)>  
```  
  
 <span data-ttu-id="38af7-133">O primeiro parâmetro, o nome da DLL, é posicional e sempre vir em primeiro lugar; os outros são nomeados.</span><span class="sxs-lookup"><span data-stu-id="38af7-133">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="38af7-134">Nesse caso, ambos os parâmetros nomeados são padronizados como false e, portanto, podem ser omitidos.</span><span class="sxs-lookup"><span data-stu-id="38af7-134">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="38af7-135">Consulte a documentação do atributo individual para obter informações sobre valores de parâmetro padrão.</span><span class="sxs-lookup"><span data-stu-id="38af7-135">Refer to the individual attribute's documentation for information on default parameter values.</span></span>  
  
### <a name="attribute-targets"></a><span data-ttu-id="38af7-136">Destinos de Atributos</span><span class="sxs-lookup"><span data-stu-id="38af7-136">Attribute Targets</span></span>  
 <span data-ttu-id="38af7-137">O *destino* de um atributo é a entidade à qual o atributo se aplica.</span><span class="sxs-lookup"><span data-stu-id="38af7-137">The *target* of an attribute is the entity to which the attribute applies.</span></span> <span data-ttu-id="38af7-138">Por exemplo, um atributo pode ser aplicado a uma classe, um método específico ou um assembly inteiro.</span><span class="sxs-lookup"><span data-stu-id="38af7-138">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="38af7-139">Por padrão, um atributo aplica-se ao elemento que ele precede.</span><span class="sxs-lookup"><span data-stu-id="38af7-139">By default, an attribute applies to the element that it precedes.</span></span> <span data-ttu-id="38af7-140">Mas você pode identificar explicitamente, por exemplo, se um atributo é aplicado a um método, ou a seu parâmetro ou a seu valor retornado.</span><span class="sxs-lookup"><span data-stu-id="38af7-140">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>  
  
 <span data-ttu-id="38af7-141">Para identificar explicitamente um atributo de destino, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="38af7-141">To explicitly identify an attribute target, use the following syntax:</span></span>  
  
```vb  
<target : attribute-list>  
```  
  
 <span data-ttu-id="38af7-142">A lista de possíveis valores `target` é mostrada na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="38af7-142">The list of possible `target` values is shown in the following table.</span></span>  
  
|<span data-ttu-id="38af7-143">Valor de destino</span><span class="sxs-lookup"><span data-stu-id="38af7-143">Target value</span></span>|<span data-ttu-id="38af7-144">Aplica-se a</span><span class="sxs-lookup"><span data-stu-id="38af7-144">Applies to</span></span>|  
|------------------|----------------|  
|`assembly`|<span data-ttu-id="38af7-145">Assembly inteiro</span><span class="sxs-lookup"><span data-stu-id="38af7-145">Entire assembly</span></span>|  
|`module`|<span data-ttu-id="38af7-146">Módulo de assembly atual (que é diferente de um módulo do Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38af7-146">Current assembly module (which is different from a Visual Basic Module)</span></span>|  
  
 <span data-ttu-id="38af7-147">O exemplo a seguir mostra como aplicar atributos a módulos e assemblies.</span><span class="sxs-lookup"><span data-stu-id="38af7-147">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="38af7-148">Para obter mais informações, consulte [Atributos comuns (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="38af7-148">For more information, see [Common Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
```vb  
Imports System.Reflection  
<Assembly: AssemblyTitleAttribute("Production assembly 4"),   
Module: CLSCompliant(True)>   
```  
  
## <a name="common-uses-for-attributes"></a><span data-ttu-id="38af7-149">Usos comuns para os atributos</span><span class="sxs-lookup"><span data-stu-id="38af7-149">Common Uses for Attributes</span></span>  
 <span data-ttu-id="38af7-150">A lista a seguir inclui alguns dos usos comuns de atributos no código:</span><span class="sxs-lookup"><span data-stu-id="38af7-150">The following list includes a few of the common uses of attributes in code:</span></span>  
  
-   <span data-ttu-id="38af7-151">Marcar métodos usando o atributo `WebMethod` nos serviços Web para indicar que o método deve ser chamado por meio do protocolo SOAP.</span><span class="sxs-lookup"><span data-stu-id="38af7-151">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="38af7-152">Para obter mais informações, consulte <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="38af7-152">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
-   <span data-ttu-id="38af7-153">Descrever como realizar marshaling de parâmetros de método ao interoperar com código nativo.</span><span class="sxs-lookup"><span data-stu-id="38af7-153">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="38af7-154">Para obter mais informações, consulte <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="38af7-154">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>  
  
-   <span data-ttu-id="38af7-155">Descrever as propriedades COM para classes, métodos e interfaces.</span><span class="sxs-lookup"><span data-stu-id="38af7-155">Describing the COM properties for classes, methods, and interfaces.</span></span>  
  
-   <span data-ttu-id="38af7-156">Chamar o código não gerenciado usando a classe <xref:System.Runtime.InteropServices.DllImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="38af7-156">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>  
  
-   <span data-ttu-id="38af7-157">Descrever o assembly em termos de versão, título, descrição ou marca.</span><span class="sxs-lookup"><span data-stu-id="38af7-157">Describing your assembly in terms of title, version, description, or trademark.</span></span>  
  
-   <span data-ttu-id="38af7-158">Descrever quais membros de uma classe serializar para persistência.</span><span class="sxs-lookup"><span data-stu-id="38af7-158">Describing which members of a class to serialize for persistence.</span></span>  
  
-   <span data-ttu-id="38af7-159">Descrever como fazer mapeamento entre nós XML e membros de classe para serialização de XML.</span><span class="sxs-lookup"><span data-stu-id="38af7-159">Describing how to map between class members and XML nodes for XML serialization.</span></span>  
  
-   <span data-ttu-id="38af7-160">Descrever os requisitos de segurança para métodos.</span><span class="sxs-lookup"><span data-stu-id="38af7-160">Describing the security requirements for methods.</span></span>  
  
-   <span data-ttu-id="38af7-161">Especificar as características usadas para impor a segurança.</span><span class="sxs-lookup"><span data-stu-id="38af7-161">Specifying characteristics used to enforce security.</span></span>  
  
-   <span data-ttu-id="38af7-162">Controlar otimizações pelo compilador JIT (Just-In-Time) para que o código permaneça fácil de depurar.</span><span class="sxs-lookup"><span data-stu-id="38af7-162">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>  
  
-   <span data-ttu-id="38af7-163">Obter informações sobre o chamador de um método.</span><span class="sxs-lookup"><span data-stu-id="38af7-163">Obtaining information about the caller to a method.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="38af7-164">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="38af7-164">Related Sections</span></span>  
 <span data-ttu-id="38af7-165">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="38af7-165">For more information, see:</span></span>  
  
-   [<span data-ttu-id="38af7-166">Criando atributos personalizados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38af7-166">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
-   [<span data-ttu-id="38af7-167">Acessando atributos usando reflexão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38af7-167">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
-   [<span data-ttu-id="38af7-168">Como criar uma união do C/C++ usando atributos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38af7-168">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
-   [<span data-ttu-id="38af7-169">Atributos comuns (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38af7-169">Common Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)  
  
-   [<span data-ttu-id="38af7-170">Informações do chamador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38af7-170">Caller Information (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/caller-information.md)  
  
## <a name="see-also"></a><span data-ttu-id="38af7-171">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38af7-171">See Also</span></span>  
 [<span data-ttu-id="38af7-172">Guia de programação do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="38af7-172">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="38af7-173">Reflexão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38af7-173">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="38af7-174">Atributos</span><span class="sxs-lookup"><span data-stu-id="38af7-174">Attributes</span></span>](../../../../standard/attributes/index.md)

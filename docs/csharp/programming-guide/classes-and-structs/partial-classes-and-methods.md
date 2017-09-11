---
title: "Classes e métodos partial (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
caps.latest.revision: 35
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 41b07af83faa6af23695f3719aae29183c35a417
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="partial-classes-and-methods-c-programming-guide"></a><span data-ttu-id="9cf7e-102">Classes e métodos partial (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="9cf7e-102">Partial Classes and Methods (C# Programming Guide)</span></span>
<span data-ttu-id="9cf7e-103">É possível dividir a definição de uma [classe](../../../csharp/language-reference/keywords/class.md) ou [struct](../../../csharp/language-reference/keywords/struct.md), uma [interface](../../../csharp/language-reference/keywords/interface.md) ou um método em dois ou mais arquivos de origem.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-103">It is possible to split the definition of a [class](../../../csharp/language-reference/keywords/class.md) or a [struct](../../../csharp/language-reference/keywords/struct.md), an [interface](../../../csharp/language-reference/keywords/interface.md) or a method over two or more source files.</span></span> <span data-ttu-id="9cf7e-104">Cada arquivo de origem contém uma seção da definição de tipo ou método e todas as partes são combinadas quando o aplicativo é compilado.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-104">Each source file contains a section of the type or method definition, and all parts are combined when the application is compiled.</span></span>  
  
## <a name="partial-classes"></a><span data-ttu-id="9cf7e-105">Classes parciais</span><span class="sxs-lookup"><span data-stu-id="9cf7e-105">Partial Classes</span></span>  
 <span data-ttu-id="9cf7e-106">Há várias situações em que a divisão de uma definição de classe é desejável:</span><span class="sxs-lookup"><span data-stu-id="9cf7e-106">There are several situations when splitting a class definition is desirable:</span></span>  
  
-   <span data-ttu-id="9cf7e-107">Ao trabalhar em projetos grandes, dividir uma classe em arquivos separados permite que vários programadores trabalhem ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-107">When working on large projects, spreading a class over separate files enables multiple programmers to work on it at the same time.</span></span>  
  
-   <span data-ttu-id="9cf7e-108">Ao trabalhar com código-fonte gerado automaticamente, o código pode ser adicionado à classe sem precisar recriar o arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-108">When working with automatically generated source, code can be added to the class without having to recreate the source file.</span></span> <span data-ttu-id="9cf7e-109">O Visual Studio usa essa abordagem quando cria Windows Forms, código de wrapper de serviço Web e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-109">Visual Studio uses this approach when it creates Windows Forms, Web service wrapper code, and so on.</span></span> <span data-ttu-id="9cf7e-110">Você pode criar código que usa essas classes sem precisar modificar o arquivo que o Visual Studio cria.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-110">You can create code that uses these classes without having to modify the file created by Visual Studio.</span></span>  
  
-   <span data-ttu-id="9cf7e-111">Para dividir uma definição de classe, use o modificador de palavra-chave [partial](../../../csharp/language-reference/keywords/partial-type.md), como mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="9cf7e-111">To split a class definition, use the [partial](../../../csharp/language-reference/keywords/partial-type.md) keyword modifier, as shown here:</span></span>  
  
 <span data-ttu-id="9cf7e-112">[!code-cs[csProgGuideObjects#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="9cf7e-112">[!code-cs[csProgGuideObjects#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_1.cs)]</span></span>  
  
 <span data-ttu-id="9cf7e-113">A palavra-chave `partial` indica que outras partes da classe, struct ou interface podem ser definidas no namespace.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-113">The `partial` keyword indicates that other parts of the class, struct, or interface can be defined in the namespace.</span></span> <span data-ttu-id="9cf7e-114">Todas as partes devem usar a palavra-chave `partial`.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-114">All the parts must use the `partial` keyword.</span></span> <span data-ttu-id="9cf7e-115">Todas as partes devem estar disponíveis em tempo de compilação para formar o tipo final.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-115">All the parts must be available at compile time to form the final type.</span></span> <span data-ttu-id="9cf7e-116">Todas as partes devem ter a mesma acessibilidade, tais como `public`, `private` e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-116">All the parts must have the same accessibility, such as `public`, `private`, and so on.</span></span>  
  
 <span data-ttu-id="9cf7e-117">Se alguma parte for declarada como abstrata, o tipo inteiro será considerado abstrato.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-117">If any part is declared abstract, then the whole type is considered abstract.</span></span> <span data-ttu-id="9cf7e-118">Se alguma parte for declarada como lacrada, o tipo inteiro será considerado lacrado.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-118">If any part is declared sealed, then the whole type is considered sealed.</span></span> <span data-ttu-id="9cf7e-119">Se alguma parte declarar um tipo base, o tipo inteiro herda dessa classe.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-119">If any part declares a base type, then the whole type inherits that class.</span></span>  
  
 <span data-ttu-id="9cf7e-120">Todas as partes que especificam uma classe base devem concordar, mas partes que omitem uma classe base ainda herdam o tipo base.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-120">All the parts that specify a base class must agree, but parts that omit a base class still inherit the base type.</span></span> <span data-ttu-id="9cf7e-121">As partes podem especificar diferentes interfaces base e o tipo final implementa todas as interfaces listadas por todas as declarações parciais.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-121">Parts can specify different base interfaces, and the final type implements all the interfaces listed by all the partial declarations.</span></span> <span data-ttu-id="9cf7e-122">Qualquer membro de classe, struct ou interface declarado em uma definição parcial está disponível para todas as outras partes.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-122">Any class, struct, or interface members declared in a partial definition are available to all the other parts.</span></span> <span data-ttu-id="9cf7e-123">O tipo final é a combinação de todas as partes em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-123">The final type is the combination of all the parts at compile time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9cf7e-124">O modificador `partial` não está disponível em declarações de enumeração ou delegados.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-124">The `partial` modifier is not available on delegate or enumeration declarations.</span></span>  
  
 <span data-ttu-id="9cf7e-125">O exemplo a seguir mostra que tipos aninhados podem ser parciais, mesmo se o tipo no qual eles estão aninhados não for parcial.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-125">The following example shows that nested types can be partial, even if the type they are nested within is not partial itself.</span></span>  
  
 <span data-ttu-id="9cf7e-126">[!code-cs[csProgGuideObjects#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="9cf7e-126">[!code-cs[csProgGuideObjects#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_2.cs)]</span></span>  
  
 <span data-ttu-id="9cf7e-127">Em tempo de compilação, atributos de definições de tipo parcial são mesclados.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-127">At compile time, attributes of partial-type definitions are merged.</span></span> <span data-ttu-id="9cf7e-128">Por exemplo, considere as declarações a seguir:</span><span class="sxs-lookup"><span data-stu-id="9cf7e-128">For example, consider the following declarations:</span></span>  
  
 <span data-ttu-id="9cf7e-129">[!code-cs[csProgGuideObjects#23](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="9cf7e-129">[!code-cs[csProgGuideObjects#23](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_3.cs)]</span></span>  
  
 <span data-ttu-id="9cf7e-130">Elas são equivalentes às seguintes declarações:</span><span class="sxs-lookup"><span data-stu-id="9cf7e-130">They are equivalent to the following declarations:</span></span>  
  
 <span data-ttu-id="9cf7e-131">[!code-cs[csProgGuideObjects#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="9cf7e-131">[!code-cs[csProgGuideObjects#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_4.cs)]</span></span>  
  
 <span data-ttu-id="9cf7e-132">Os itens a seguir são mesclados de todas as definições de tipo parcial:</span><span class="sxs-lookup"><span data-stu-id="9cf7e-132">The following are merged from all the partial-type definitions:</span></span>  
  
-   <span data-ttu-id="9cf7e-133">comentários XML</span><span class="sxs-lookup"><span data-stu-id="9cf7e-133">XML comments</span></span>  
  
-   <span data-ttu-id="9cf7e-134">interfaces</span><span class="sxs-lookup"><span data-stu-id="9cf7e-134">interfaces</span></span>  
  
-   <span data-ttu-id="9cf7e-135">atributos de parâmetro de tipo genérico</span><span class="sxs-lookup"><span data-stu-id="9cf7e-135">generic-type parameter attributes</span></span>  
  
-   <span data-ttu-id="9cf7e-136">atributos class</span><span class="sxs-lookup"><span data-stu-id="9cf7e-136">class attributes</span></span>  
  
-   <span data-ttu-id="9cf7e-137">membros</span><span class="sxs-lookup"><span data-stu-id="9cf7e-137">members</span></span>  
  
 <span data-ttu-id="9cf7e-138">Por exemplo, considere as declarações a seguir:</span><span class="sxs-lookup"><span data-stu-id="9cf7e-138">For example, consider the following declarations:</span></span>  
  
 <span data-ttu-id="9cf7e-139">[!code-cs[csProgGuideObjects#21](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="9cf7e-139">[!code-cs[csProgGuideObjects#21](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_5.cs)]</span></span>  
  
 <span data-ttu-id="9cf7e-140">Elas são equivalentes às seguintes declarações:</span><span class="sxs-lookup"><span data-stu-id="9cf7e-140">They are equivalent to the following declarations:</span></span>  
  
 <span data-ttu-id="9cf7e-141">[!code-cs[csProgGuideObjects#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="9cf7e-141">[!code-cs[csProgGuideObjects#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_6.cs)]</span></span>  
  
### <a name="restrictions"></a><span data-ttu-id="9cf7e-142">Restrições</span><span class="sxs-lookup"><span data-stu-id="9cf7e-142">Restrictions</span></span>  
 <span data-ttu-id="9cf7e-143">Há várias regras para seguir quando você está trabalhando com definições de classes parciais:</span><span class="sxs-lookup"><span data-stu-id="9cf7e-143">There are several rules to follow when you are working with partial class definitions:</span></span>  
  
-   <span data-ttu-id="9cf7e-144">Todas as definições de tipo parcial que devem ser partes do mesmo tipo devem ser modificadas com `partial`.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-144">All partial-type definitions meant to be parts of the same type must be modified with `partial`.</span></span> <span data-ttu-id="9cf7e-145">Por exemplo, as seguintes declarações de classe geram um erro:</span><span class="sxs-lookup"><span data-stu-id="9cf7e-145">For example, the following class declarations generate an error:</span></span>  
  
     <span data-ttu-id="9cf7e-146">[!code-cs[csProgGuideObjects#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="9cf7e-146">[!code-cs[csProgGuideObjects#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_7.cs)]</span></span>  
  
-   <span data-ttu-id="9cf7e-147">O modificador `partial` só pode aparecer imediatamente antes das palavras-chave `class`, `struct` ou `interface`.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-147">The `partial` modifier can only appear immediately before the keywords `class`, `struct`, or `interface`.</span></span>  
  
-   <span data-ttu-id="9cf7e-148">Tipos parciais aninhados são permitidos em definições de tipo parcial, conforme ilustrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="9cf7e-148">Nested partial types are allowed in partial-type definitions as illustrated in the following example:</span></span>  
  
     <span data-ttu-id="9cf7e-149">[!code-cs[csProgGuideObjects#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="9cf7e-149">[!code-cs[csProgGuideObjects#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_8.cs)]</span></span>  
  
-   <span data-ttu-id="9cf7e-150">Todas as definições de tipo parcial que devem ser partes do mesmo tipo devem ser definidas no mesmo assembly e no mesmo módulo (arquivo .dll ou .exe).</span><span class="sxs-lookup"><span data-stu-id="9cf7e-150">All partial-type definitions meant to be parts of the same type must be defined in the same assembly and the same module (.exe or .dll file).</span></span> <span data-ttu-id="9cf7e-151">Definições parciais não podem abranger vários módulos.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-151">Partial definitions cannot span multiple modules.</span></span>  
  
-   <span data-ttu-id="9cf7e-152">O nome de classe e os parâmetros de tipo genérico devem corresponder em todas as definições de tipo parcial.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-152">The class name and generic-type parameters must match on all partial-type definitions.</span></span> <span data-ttu-id="9cf7e-153">Tipos genéricos podem ser parciais.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-153">Generic types can be partial.</span></span> <span data-ttu-id="9cf7e-154">Cada declaração parcial deve usar os mesmos nomes de parâmetro na mesma ordem.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-154">Each partial declaration must use the same parameter names in the same order.</span></span>  
  
-   <span data-ttu-id="9cf7e-155">As seguintes palavras-chave em uma definição de tipo parcial são opcionais, mas, se estiverem presentes em uma definição de tipo parcial, não podem entrar em conflito com as palavras-chave especificadas em outra definição parcial para o mesmo tipo:</span><span class="sxs-lookup"><span data-stu-id="9cf7e-155">The following keywords on a partial-type definition are optional, but if present on one partial-type definition, cannot conflict with the keywords specified on another partial definition for the same type:</span></span>  
  
    -   [<span data-ttu-id="9cf7e-156">public</span><span class="sxs-lookup"><span data-stu-id="9cf7e-156">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
  
    -   [<span data-ttu-id="9cf7e-157">private</span><span class="sxs-lookup"><span data-stu-id="9cf7e-157">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
  
    -   [<span data-ttu-id="9cf7e-158">protected</span><span class="sxs-lookup"><span data-stu-id="9cf7e-158">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
  
    -   [<span data-ttu-id="9cf7e-159">internal</span><span class="sxs-lookup"><span data-stu-id="9cf7e-159">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
  
    -   [<span data-ttu-id="9cf7e-160">abstract</span><span class="sxs-lookup"><span data-stu-id="9cf7e-160">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
  
    -   [<span data-ttu-id="9cf7e-161">sealed</span><span class="sxs-lookup"><span data-stu-id="9cf7e-161">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)  
  
    -   <span data-ttu-id="9cf7e-162">classe base</span><span class="sxs-lookup"><span data-stu-id="9cf7e-162">base class</span></span>  
  
    -   <span data-ttu-id="9cf7e-163">modificador [new](../../../csharp/language-reference/keywords/new.md) (partes aninhadas)</span><span class="sxs-lookup"><span data-stu-id="9cf7e-163">[new](../../../csharp/language-reference/keywords/new.md) modifier (nested parts)</span></span>  
  
    -   <span data-ttu-id="9cf7e-164">restrições genéricas</span><span class="sxs-lookup"><span data-stu-id="9cf7e-164">generic constraints</span></span>  
  
         <span data-ttu-id="9cf7e-165">Para obter mais informações, consulte [Restrições a parâmetros de tipo](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="9cf7e-165">For more information, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="9cf7e-166">Exemplo 1</span><span class="sxs-lookup"><span data-stu-id="9cf7e-166">Example 1</span></span>  
  
### <a name="description"></a><span data-ttu-id="9cf7e-167">Descrição</span><span class="sxs-lookup"><span data-stu-id="9cf7e-167">Description</span></span>  
 <span data-ttu-id="9cf7e-168">No exemplo a seguir, os campos e o construtor da classe, `CoOrds`, são declarados em uma definição de classe parcial e o membro, `PrintCoOrds`, é declarado em outra definição de classe parcial.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-168">In the following example, the fields and the constructor of the class, `CoOrds`, are declared in one partial class definition, and the member, `PrintCoOrds`, is declared in another partial class definition.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9cf7e-169">Código</span><span class="sxs-lookup"><span data-stu-id="9cf7e-169">Code</span></span>  
 <span data-ttu-id="9cf7e-170">[!code-cs[csProgGuideObjects#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_9.cs)]</span><span class="sxs-lookup"><span data-stu-id="9cf7e-170">[!code-cs[csProgGuideObjects#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_9.cs)]</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="9cf7e-171">Exemplo 2</span><span class="sxs-lookup"><span data-stu-id="9cf7e-171">Example 2</span></span>  
  
### <a name="description"></a><span data-ttu-id="9cf7e-172">Descrição</span><span class="sxs-lookup"><span data-stu-id="9cf7e-172">Description</span></span>  
 <span data-ttu-id="9cf7e-173">O exemplo a seguir mostra que você também pode desenvolver interfaces e structs parciais.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-173">The following example shows that you can also develop partial structs and interfaces.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9cf7e-174">Código</span><span class="sxs-lookup"><span data-stu-id="9cf7e-174">Code</span></span>  
 <span data-ttu-id="9cf7e-175">[!code-cs[csProgGuideObjects#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_10.cs)]</span><span class="sxs-lookup"><span data-stu-id="9cf7e-175">[!code-cs[csProgGuideObjects#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_10.cs)]</span></span>  
  
## <a name="partial-methods"></a><span data-ttu-id="9cf7e-176">Métodos parciais</span><span class="sxs-lookup"><span data-stu-id="9cf7e-176">Partial Methods</span></span>  
 <span data-ttu-id="9cf7e-177">Uma classe ou struct parcial pode conter um método parcial.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-177">A partial class or struct may contain a partial method.</span></span> <span data-ttu-id="9cf7e-178">Uma parte da classe contém a assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-178">One part of the class contains the signature of the method.</span></span> <span data-ttu-id="9cf7e-179">Uma implementação opcional pode ser definida na mesma parte ou em outra parte.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-179">An optional implementation may be defined in the same part or another part.</span></span> <span data-ttu-id="9cf7e-180">Se a implementação não for fornecida, o método e todas as chamadas para o método serão removidos em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-180">If the implementation is not supplied, then the method and all calls to the method are removed at compile time.</span></span>  
  
 <span data-ttu-id="9cf7e-181">Métodos parciais permitem que o implementador de uma parte de uma classe defina um método, semelhante a um evento.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-181">Partial methods enable the implementer of one part of a class to define a method, similar to an event.</span></span> <span data-ttu-id="9cf7e-182">O implementador da outra parte da classe pode decidir implementará o método ou não.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-182">The implementer of the other part of the class can decide whether to implement the method or not.</span></span> <span data-ttu-id="9cf7e-183">Se o método não for implementado, o compilador removerá a assinatura do método e todas as chamadas para o método.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-183">If the method is not implemented, then the compiler removes the method signature and all calls to the method.</span></span> <span data-ttu-id="9cf7e-184">As chamadas para o método, incluindo qualquer resultado que ocorreria da avaliação de argumentos nas chamadas, não têm efeito em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-184">The calls to the method, including any results that would occur from evaluation of arguments in the calls, have no effect at run time.</span></span> <span data-ttu-id="9cf7e-185">Portanto, qualquer código na classe parcial pode usar livremente um método parcial, mesmo que a implementação não seja fornecida.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-185">Therefore, any code in the partial class can freely use a partial method, even if the implementation is not supplied.</span></span> <span data-ttu-id="9cf7e-186">Nenhum erro de tempo de compilação ou tempo de execução ocorrerá se o método for chamado, mas não implementado.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-186">No compile-time or run-time errors will result if the method is called but not implemented.</span></span>  
  
 <span data-ttu-id="9cf7e-187">Métodos parciais são especialmente úteis como uma maneira de personalizar o código gerado.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-187">Partial methods are especially useful as a way to customize generated code.</span></span> <span data-ttu-id="9cf7e-188">Eles permitem que um nome e uma assinatura de método sejam reservados, para que o código gerado possa chamar o método, mas o desenvolvedor possa decidir se deve implementar o método.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-188">They allow for a method name and signature to be reserved, so that generated code can call the method but the developer can decide whether to implement the method.</span></span> <span data-ttu-id="9cf7e-189">Assim como as classes parciais, os métodos parciais habilitam o código criado por um gerador de código e o código criado por um desenvolvedor humano a funcionarem juntos sem custos de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-189">Much like partial classes, partial methods enable code created by a code generator and code created by a human developer to work together without run-time costs.</span></span>  
  
 <span data-ttu-id="9cf7e-190">Uma declaração de método parcial consiste em duas partes: a definição e a implementação.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-190">A partial method declaration consists of two parts: the definition, and the implementation.</span></span> <span data-ttu-id="9cf7e-191">Elas podem estar em partes separadas de uma classe parcial ou na mesma parte.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-191">These may be in separate parts of a partial class, or in the same part.</span></span> <span data-ttu-id="9cf7e-192">Se não houver nenhuma declaração de implementação, o compilador otimizará a declaração de definição e todas as chamadas para o método.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-192">If there is no implementation declaration, then the compiler optimizes away both the defining declaration and all calls to the method.</span></span>  
  
```  
// Definition in file1.cs  
partial void onNameChanged();  
  
// Implementation in file2.cs  
partial void onNameChanged()  
{  
  // method body  
}  
```  
  
-   <span data-ttu-id="9cf7e-193">Declarações de métodos parcial devem começar com a palavra-chave contextual [partial](../../../csharp/language-reference/keywords/partial-type.md) e o método deve retornar [void](../../../csharp/language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="9cf7e-193">Partial method declarations must begin with the contextual keyword [partial](../../../csharp/language-reference/keywords/partial-type.md) and the method must return [void](../../../csharp/language-reference/keywords/void.md).</span></span>  
  
-   <span data-ttu-id="9cf7e-194">Métodos parciais podem ter parâmetros [ref](../../../csharp/language-reference/keywords/ref.md), mas não [out](../../../csharp/language-reference/keywords/out.md).</span><span class="sxs-lookup"><span data-stu-id="9cf7e-194">Partial methods can have [ref](../../../csharp/language-reference/keywords/ref.md) but not [out](../../../csharp/language-reference/keywords/out.md) parameters.</span></span>  
  
-   <span data-ttu-id="9cf7e-195">Métodos parciais são implicitamente [private](../../../csharp/language-reference/keywords/private.md) e portanto não podem ser [virtual](../../../csharp/language-reference/keywords/virtual.md).</span><span class="sxs-lookup"><span data-stu-id="9cf7e-195">Partial methods are implicitly [private](../../../csharp/language-reference/keywords/private.md), and therefore they cannot be [virtual](../../../csharp/language-reference/keywords/virtual.md).</span></span>  
  
-   <span data-ttu-id="9cf7e-196">Métodos parciais não podem ser [extern](../../../csharp/language-reference/keywords/extern.md), pois a presença do corpo determina se eles estão sendo definidos ou implementados.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-196">Partial methods cannot be [extern](../../../csharp/language-reference/keywords/extern.md), because the presence of the body determines whether they are defining or implementing.</span></span>  
  
-   <span data-ttu-id="9cf7e-197">Métodos parciais podem ter modificadores [static](../../../csharp/language-reference/keywords/static.md) e [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="9cf7e-197">Partial methods can have [static](../../../csharp/language-reference/keywords/static.md) and [unsafe](../../../csharp/language-reference/keywords/unsafe.md) modifiers.</span></span>  
  
-   <span data-ttu-id="9cf7e-198">Métodos parciais podem ser genéricos.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-198">Partial methods can be generic.</span></span> <span data-ttu-id="9cf7e-199">Restrições são colocadas quanto à declaração de método parcial de definição e, opcionalmente, podem ser repetidas na de implementação.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-199">Constraints are put on the defining partial method declaration, and may optionally be repeated on the implementing one.</span></span> <span data-ttu-id="9cf7e-200">Nomes de parâmetro e de tipo de parâmetro não precisam ser iguais na declaração de implementação e na de definição.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-200">Parameter and type parameter names do not have to be the same in the implementing declaration as in the defining one.</span></span>  
  
-   <span data-ttu-id="9cf7e-201">Você pode fazer um [delegado](../../../csharp/language-reference/keywords/delegate.md) para um método parcial que foi definido e implementado, mas não para um método parcial que só foi definido.</span><span class="sxs-lookup"><span data-stu-id="9cf7e-201">You can make a [delegate](../../../csharp/language-reference/keywords/delegate.md) to a partial method that has been defined and implemented, but not to a partial method that has only been defined.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="9cf7e-202">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="9cf7e-202">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9cf7e-203">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9cf7e-203">See Also</span></span>  
 <span data-ttu-id="9cf7e-204">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9cf7e-204">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="9cf7e-205">[Classes](../../../csharp/programming-guide/classes-and-structs/classes.md) </span><span class="sxs-lookup"><span data-stu-id="9cf7e-205">[Classes](../../../csharp/programming-guide/classes-and-structs/classes.md) </span></span>  
 <span data-ttu-id="9cf7e-206">[Structs](../../../csharp/programming-guide/classes-and-structs/structs.md) </span><span class="sxs-lookup"><span data-stu-id="9cf7e-206">[Structs](../../../csharp/programming-guide/classes-and-structs/structs.md) </span></span>  
 <span data-ttu-id="9cf7e-207">[Interfaces](../../../csharp/programming-guide/interfaces/index.md) </span><span class="sxs-lookup"><span data-stu-id="9cf7e-207">[Interfaces](../../../csharp/programming-guide/interfaces/index.md) </span></span>  
 [<span data-ttu-id="9cf7e-208">(partial (tipo)</span><span class="sxs-lookup"><span data-stu-id="9cf7e-208">partial (Type)</span></span>](../../../csharp/language-reference/keywords/partial-type.md)


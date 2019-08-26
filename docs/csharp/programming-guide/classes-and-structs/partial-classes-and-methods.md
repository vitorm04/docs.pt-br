---
title: Classes e métodos partial – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: 53c3ac6e4fa6313488c47d851e0897bd512521b7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596280"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a><span data-ttu-id="89d70-102">Classes e métodos partial (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="89d70-102">Partial Classes and Methods (C# Programming Guide)</span></span>

<span data-ttu-id="89d70-103">É possível dividir a definição de uma [classe](../../language-reference/keywords/class.md) ou [struct](../../language-reference/keywords/struct.md), uma [interface](../../language-reference/keywords/interface.md) ou um método em dois ou mais arquivos de origem.</span><span class="sxs-lookup"><span data-stu-id="89d70-103">It is possible to split the definition of a [class](../../language-reference/keywords/class.md), a [struct](../../language-reference/keywords/struct.md), an [interface](../../language-reference/keywords/interface.md) or a method over two or more source files.</span></span> <span data-ttu-id="89d70-104">Cada arquivo de origem contém uma seção da definição de tipo ou método e todas as partes são combinadas quando o aplicativo é compilado.</span><span class="sxs-lookup"><span data-stu-id="89d70-104">Each source file contains a section of the type or method definition, and all parts are combined when the application is compiled.</span></span>

## <a name="partial-classes"></a><span data-ttu-id="89d70-105">Classes parciais</span><span class="sxs-lookup"><span data-stu-id="89d70-105">Partial Classes</span></span>

<span data-ttu-id="89d70-106">Há várias situações em que a divisão de uma definição de classe é desejável:</span><span class="sxs-lookup"><span data-stu-id="89d70-106">There are several situations when splitting a class definition is desirable:</span></span>

- <span data-ttu-id="89d70-107">Ao trabalhar em projetos grandes, dividir uma classe em arquivos separados permite que vários programadores trabalhem ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="89d70-107">When working on large projects, spreading a class over separate files enables multiple programmers to work on it at the same time.</span></span>

- <span data-ttu-id="89d70-108">Ao trabalhar com código-fonte gerado automaticamente, o código pode ser adicionado à classe sem precisar recriar o arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="89d70-108">When working with automatically generated source, code can be added to the class without having to recreate the source file.</span></span> <span data-ttu-id="89d70-109">O Visual Studio usa essa abordagem quando cria Windows Forms, código de wrapper de serviço Web e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="89d70-109">Visual Studio uses this approach when it creates Windows Forms, Web service wrapper code, and so on.</span></span> <span data-ttu-id="89d70-110">Você pode criar código que usa essas classes sem precisar modificar o arquivo que o Visual Studio cria.</span><span class="sxs-lookup"><span data-stu-id="89d70-110">You can create code that uses these classes without having to modify the file created by Visual Studio.</span></span>

- <span data-ttu-id="89d70-111">Para dividir uma definição de classe, use o modificador de palavra-chave [partial](../../language-reference/keywords/partial-type.md), como mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="89d70-111">To split a class definition, use the [partial](../../language-reference/keywords/partial-type.md) keyword modifier, as shown here:</span></span>

  [!code-csharp[csProgGuideObjects#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#26)]

<span data-ttu-id="89d70-112">A palavra-chave `partial` indica que outras partes da classe, struct ou interface podem ser definidas no namespace.</span><span class="sxs-lookup"><span data-stu-id="89d70-112">The `partial` keyword indicates that other parts of the class, struct, or interface can be defined in the namespace.</span></span> <span data-ttu-id="89d70-113">Todas as partes devem usar a palavra-chave `partial`.</span><span class="sxs-lookup"><span data-stu-id="89d70-113">All the parts must use the `partial` keyword.</span></span> <span data-ttu-id="89d70-114">Todas as partes devem estar disponíveis em tempo de compilação para formar o tipo final.</span><span class="sxs-lookup"><span data-stu-id="89d70-114">All the parts must be available at compile time to form the final type.</span></span> <span data-ttu-id="89d70-115">Todas as partes devem ter a mesma acessibilidade, tais como `public`, `private` e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="89d70-115">All the parts must have the same accessibility, such as `public`, `private`, and so on.</span></span>

<span data-ttu-id="89d70-116">Se alguma parte for declarada como abstrata, o tipo inteiro será considerado abstrato.</span><span class="sxs-lookup"><span data-stu-id="89d70-116">If any part is declared abstract, then the whole type is considered abstract.</span></span> <span data-ttu-id="89d70-117">Se alguma parte for declarada como lacrada, o tipo inteiro será considerado lacrado.</span><span class="sxs-lookup"><span data-stu-id="89d70-117">If any part is declared sealed, then the whole type is considered sealed.</span></span> <span data-ttu-id="89d70-118">Se alguma parte declarar um tipo base, o tipo inteiro herda dessa classe.</span><span class="sxs-lookup"><span data-stu-id="89d70-118">If any part declares a base type, then the whole type inherits that class.</span></span>

<span data-ttu-id="89d70-119">Todas as partes que especificam uma classe base devem concordar, mas partes que omitem uma classe base ainda herdam o tipo base.</span><span class="sxs-lookup"><span data-stu-id="89d70-119">All the parts that specify a base class must agree, but parts that omit a base class still inherit the base type.</span></span> <span data-ttu-id="89d70-120">As partes podem especificar diferentes interfaces base e o tipo final implementa todas as interfaces listadas por todas as declarações parciais.</span><span class="sxs-lookup"><span data-stu-id="89d70-120">Parts can specify different base interfaces, and the final type implements all the interfaces listed by all the partial declarations.</span></span> <span data-ttu-id="89d70-121">Qualquer membro de classe, struct ou interface declarado em uma definição parcial está disponível para todas as outras partes.</span><span class="sxs-lookup"><span data-stu-id="89d70-121">Any class, struct, or interface members declared in a partial definition are available to all the other parts.</span></span> <span data-ttu-id="89d70-122">O tipo final é a combinação de todas as partes em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="89d70-122">The final type is the combination of all the parts at compile time.</span></span>

> [!NOTE]
> <span data-ttu-id="89d70-123">O modificador `partial` não está disponível em declarações de enumeração ou delegados.</span><span class="sxs-lookup"><span data-stu-id="89d70-123">The `partial` modifier is not available on delegate or enumeration declarations.</span></span>

<span data-ttu-id="89d70-124">O exemplo a seguir mostra que tipos aninhados podem ser parciais, mesmo se o tipo no qual eles estão aninhados não for parcial.</span><span class="sxs-lookup"><span data-stu-id="89d70-124">The following example shows that nested types can be partial, even if the type they are nested within is not partial itself.</span></span>

[!code-csharp[csProgGuideObjects#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#25)]

<span data-ttu-id="89d70-125">Em tempo de compilação, atributos de definições de tipo parcial são mesclados.</span><span class="sxs-lookup"><span data-stu-id="89d70-125">At compile time, attributes of partial-type definitions are merged.</span></span> <span data-ttu-id="89d70-126">Por exemplo, considere as declarações a seguir:</span><span class="sxs-lookup"><span data-stu-id="89d70-126">For example, consider the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#23)]

<span data-ttu-id="89d70-127">Elas são equivalentes às seguintes declarações:</span><span class="sxs-lookup"><span data-stu-id="89d70-127">They are equivalent to the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#24)]

<span data-ttu-id="89d70-128">Os itens a seguir são mesclados de todas as definições de tipo parcial:</span><span class="sxs-lookup"><span data-stu-id="89d70-128">The following are merged from all the partial-type definitions:</span></span>

- <span data-ttu-id="89d70-129">comentários XML</span><span class="sxs-lookup"><span data-stu-id="89d70-129">XML comments</span></span>

- <span data-ttu-id="89d70-130">interfaces</span><span class="sxs-lookup"><span data-stu-id="89d70-130">interfaces</span></span>

- <span data-ttu-id="89d70-131">atributos de parâmetro de tipo genérico</span><span class="sxs-lookup"><span data-stu-id="89d70-131">generic-type parameter attributes</span></span>

- <span data-ttu-id="89d70-132">atributos class</span><span class="sxs-lookup"><span data-stu-id="89d70-132">class attributes</span></span>

- <span data-ttu-id="89d70-133">membros</span><span class="sxs-lookup"><span data-stu-id="89d70-133">members</span></span>

<span data-ttu-id="89d70-134">Por exemplo, considere as declarações a seguir:</span><span class="sxs-lookup"><span data-stu-id="89d70-134">For example, consider the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#21)]

<span data-ttu-id="89d70-135">Elas são equivalentes às seguintes declarações:</span><span class="sxs-lookup"><span data-stu-id="89d70-135">They are equivalent to the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#22)]

### <a name="restrictions"></a><span data-ttu-id="89d70-136">Restrições</span><span class="sxs-lookup"><span data-stu-id="89d70-136">Restrictions</span></span>

<span data-ttu-id="89d70-137">Há várias regras para seguir quando você está trabalhando com definições de classes parciais:</span><span class="sxs-lookup"><span data-stu-id="89d70-137">There are several rules to follow when you are working with partial class definitions:</span></span>

- <span data-ttu-id="89d70-138">Todas as definições de tipo parcial que devem ser partes do mesmo tipo devem ser modificadas com `partial`.</span><span class="sxs-lookup"><span data-stu-id="89d70-138">All partial-type definitions meant to be parts of the same type must be modified with `partial`.</span></span> <span data-ttu-id="89d70-139">Por exemplo, as seguintes declarações de classe geram um erro:</span><span class="sxs-lookup"><span data-stu-id="89d70-139">For example, the following class declarations generate an error:</span></span>

  [!code-csharp[csProgGuideObjects#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#20)]

- <span data-ttu-id="89d70-140">O modificador `partial` só pode aparecer imediatamente antes das palavras-chave `class`, `struct` ou `interface`.</span><span class="sxs-lookup"><span data-stu-id="89d70-140">The `partial` modifier can only appear immediately before the keywords `class`, `struct`, or `interface`.</span></span>

- <span data-ttu-id="89d70-141">Tipos parciais aninhados são permitidos em definições de tipo parcial, conforme ilustrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="89d70-141">Nested partial types are allowed in partial-type definitions as illustrated in the following example:</span></span>

  [!code-csharp[csProgGuideObjects#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#19)]

- <span data-ttu-id="89d70-142">Todas as definições de tipo parcial que devem ser partes do mesmo tipo devem ser definidas no mesmo assembly e no mesmo módulo (arquivo .dll ou .exe).</span><span class="sxs-lookup"><span data-stu-id="89d70-142">All partial-type definitions meant to be parts of the same type must be defined in the same assembly and the same module (.exe or .dll file).</span></span> <span data-ttu-id="89d70-143">Definições parciais não podem abranger vários módulos.</span><span class="sxs-lookup"><span data-stu-id="89d70-143">Partial definitions cannot span multiple modules.</span></span>

- <span data-ttu-id="89d70-144">O nome de classe e os parâmetros de tipo genérico devem corresponder em todas as definições de tipo parcial.</span><span class="sxs-lookup"><span data-stu-id="89d70-144">The class name and generic-type parameters must match on all partial-type definitions.</span></span> <span data-ttu-id="89d70-145">Tipos genéricos podem ser parciais.</span><span class="sxs-lookup"><span data-stu-id="89d70-145">Generic types can be partial.</span></span> <span data-ttu-id="89d70-146">Cada declaração parcial deve usar os mesmos nomes de parâmetro na mesma ordem.</span><span class="sxs-lookup"><span data-stu-id="89d70-146">Each partial declaration must use the same parameter names in the same order.</span></span>

- <span data-ttu-id="89d70-147">As seguintes palavras-chave em uma definição de tipo parcial são opcionais, mas, se estiverem presentes em uma definição de tipo parcial, não podem entrar em conflito com as palavras-chave especificadas em outra definição parcial para o mesmo tipo:</span><span class="sxs-lookup"><span data-stu-id="89d70-147">The following keywords on a partial-type definition are optional, but if present on one partial-type definition, cannot conflict with the keywords specified on another partial definition for the same type:</span></span>

  - [<span data-ttu-id="89d70-148">public</span><span class="sxs-lookup"><span data-stu-id="89d70-148">public</span></span>](../../language-reference/keywords/public.md)

  - [<span data-ttu-id="89d70-149">private</span><span class="sxs-lookup"><span data-stu-id="89d70-149">private</span></span>](../../language-reference/keywords/private.md)

  - [<span data-ttu-id="89d70-150">protected</span><span class="sxs-lookup"><span data-stu-id="89d70-150">protected</span></span>](../../language-reference/keywords/protected.md)

  - [<span data-ttu-id="89d70-151">internal</span><span class="sxs-lookup"><span data-stu-id="89d70-151">internal</span></span>](../../language-reference/keywords/internal.md)

  - [<span data-ttu-id="89d70-152">abstract</span><span class="sxs-lookup"><span data-stu-id="89d70-152">abstract</span></span>](../../language-reference/keywords/abstract.md)

  - [<span data-ttu-id="89d70-153">sealed</span><span class="sxs-lookup"><span data-stu-id="89d70-153">sealed</span></span>](../../language-reference/keywords/sealed.md)

  - <span data-ttu-id="89d70-154">classe base</span><span class="sxs-lookup"><span data-stu-id="89d70-154">base class</span></span>

  - <span data-ttu-id="89d70-155">modificador [new](../../language-reference/keywords/new-modifier.md) (partes aninhadas)</span><span class="sxs-lookup"><span data-stu-id="89d70-155">[new](../../language-reference/keywords/new-modifier.md) modifier (nested parts)</span></span>

  - <span data-ttu-id="89d70-156">restrições genéricas</span><span class="sxs-lookup"><span data-stu-id="89d70-156">generic constraints</span></span>

<span data-ttu-id="89d70-157">Para obter mais informações, consulte [Restrições a parâmetros de tipo](../generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="89d70-157">For more information, see [Constraints on Type Parameters](../generics/constraints-on-type-parameters.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="89d70-158">Exemplo 1</span><span class="sxs-lookup"><span data-stu-id="89d70-158">Example 1</span></span>

### <a name="description"></a><span data-ttu-id="89d70-159">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="89d70-159">Description</span></span>

<span data-ttu-id="89d70-160">No exemplo a seguir, os campos e o construtor da classe, `Coords`, são declarados em uma definição de classe parcial e o membro, `PrintCoords`, é declarado em outra definição de classe parcial.</span><span class="sxs-lookup"><span data-stu-id="89d70-160">In the following example, the fields and the constructor of the class, `Coords`, are declared in one partial class definition, and the member, `PrintCoords`, is declared in another partial class definition.</span></span>

### <a name="code"></a><span data-ttu-id="89d70-161">Código</span><span class="sxs-lookup"><span data-stu-id="89d70-161">Code</span></span>

[!code-csharp[csProgGuideObjects#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#17)]

## <a name="example-2"></a><span data-ttu-id="89d70-162">Exemplo 2</span><span class="sxs-lookup"><span data-stu-id="89d70-162">Example 2</span></span>

### <a name="description"></a><span data-ttu-id="89d70-163">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="89d70-163">Description</span></span>

<span data-ttu-id="89d70-164">O exemplo a seguir mostra que você também pode desenvolver interfaces e structs parciais.</span><span class="sxs-lookup"><span data-stu-id="89d70-164">The following example shows that you can also develop partial structs and interfaces.</span></span>

### <a name="code"></a><span data-ttu-id="89d70-165">Código</span><span class="sxs-lookup"><span data-stu-id="89d70-165">Code</span></span>

[!code-csharp[csProgGuideObjects#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#18)]

## <a name="partial-methods"></a><span data-ttu-id="89d70-166">Métodos parciais</span><span class="sxs-lookup"><span data-stu-id="89d70-166">Partial Methods</span></span>

<span data-ttu-id="89d70-167">Uma classe ou struct parcial pode conter um método parcial.</span><span class="sxs-lookup"><span data-stu-id="89d70-167">A partial class or struct may contain a partial method.</span></span> <span data-ttu-id="89d70-168">Uma parte da classe contém a assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="89d70-168">One part of the class contains the signature of the method.</span></span> <span data-ttu-id="89d70-169">Uma implementação opcional pode ser definida na mesma parte ou em outra parte.</span><span class="sxs-lookup"><span data-stu-id="89d70-169">An optional implementation may be defined in the same part or another part.</span></span> <span data-ttu-id="89d70-170">Se a implementação não for fornecida, o método e todas as chamadas para o método serão removidos em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="89d70-170">If the implementation is not supplied, then the method and all calls to the method are removed at compile time.</span></span>

<span data-ttu-id="89d70-171">Métodos parciais permitem que o implementador de uma parte de uma classe defina um método, semelhante a um evento.</span><span class="sxs-lookup"><span data-stu-id="89d70-171">Partial methods enable the implementer of one part of a class to define a method, similar to an event.</span></span> <span data-ttu-id="89d70-172">O implementador da outra parte da classe pode decidir implementará o método ou não.</span><span class="sxs-lookup"><span data-stu-id="89d70-172">The implementer of the other part of the class can decide whether to implement the method or not.</span></span> <span data-ttu-id="89d70-173">Se o método não for implementado, o compilador removerá a assinatura do método e todas as chamadas para o método.</span><span class="sxs-lookup"><span data-stu-id="89d70-173">If the method is not implemented, then the compiler removes the method signature and all calls to the method.</span></span> <span data-ttu-id="89d70-174">As chamadas para o método, incluindo qualquer resultado que ocorreria da avaliação de argumentos nas chamadas, não têm efeito em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="89d70-174">The calls to the method, including any results that would occur from evaluation of arguments in the calls, have no effect at run time.</span></span> <span data-ttu-id="89d70-175">Portanto, qualquer código na classe parcial pode usar livremente um método parcial, mesmo que a implementação não seja fornecida.</span><span class="sxs-lookup"><span data-stu-id="89d70-175">Therefore, any code in the partial class can freely use a partial method, even if the implementation is not supplied.</span></span> <span data-ttu-id="89d70-176">Nenhum erro de tempo de compilação ou tempo de execução ocorrerá se o método for chamado, mas não implementado.</span><span class="sxs-lookup"><span data-stu-id="89d70-176">No compile-time or run-time errors will result if the method is called but not implemented.</span></span>

<span data-ttu-id="89d70-177">Métodos parciais são especialmente úteis como uma maneira de personalizar o código gerado.</span><span class="sxs-lookup"><span data-stu-id="89d70-177">Partial methods are especially useful as a way to customize generated code.</span></span> <span data-ttu-id="89d70-178">Eles permitem que um nome e uma assinatura de método sejam reservados, para que o código gerado possa chamar o método, mas o desenvolvedor possa decidir se deve implementar o método.</span><span class="sxs-lookup"><span data-stu-id="89d70-178">They allow for a method name and signature to be reserved, so that generated code can call the method but the developer can decide whether to implement the method.</span></span> <span data-ttu-id="89d70-179">Assim como as classes parciais, os métodos parciais habilitam o código criado por um gerador de código e o código criado por um desenvolvedor humano a funcionarem juntos sem custos de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="89d70-179">Much like partial classes, partial methods enable code created by a code generator and code created by a human developer to work together without run-time costs.</span></span>

<span data-ttu-id="89d70-180">Uma declaração de método parcial consiste em duas partes: a definição e a implementação.</span><span class="sxs-lookup"><span data-stu-id="89d70-180">A partial method declaration consists of two parts: the definition, and the implementation.</span></span> <span data-ttu-id="89d70-181">Elas podem estar em partes separadas de uma classe parcial ou na mesma parte.</span><span class="sxs-lookup"><span data-stu-id="89d70-181">These may be in separate parts of a partial class, or in the same part.</span></span> <span data-ttu-id="89d70-182">Se não houver nenhuma declaração de implementação, o compilador otimizará a declaração de definição e todas as chamadas para o método.</span><span class="sxs-lookup"><span data-stu-id="89d70-182">If there is no implementation declaration, then the compiler optimizes away both the defining declaration and all calls to the method.</span></span>

```csharp
// Definition in file1.cs
partial void onNameChanged();

// Implementation in file2.cs
partial void onNameChanged()
{
  // method body
}
```

- <span data-ttu-id="89d70-183">Declarações de métodos parcial devem começar com a palavra-chave contextual [partial](../../language-reference/keywords/partial-type.md) e o método deve retornar [void](../../language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="89d70-183">Partial method declarations must begin with the contextual keyword [partial](../../language-reference/keywords/partial-type.md) and the method must return [void](../../language-reference/keywords/void.md).</span></span>

- <span data-ttu-id="89d70-184">Os métodos parciais podem ter os parâmetros [in](../../language-reference/keywords/in-parameter-modifier.md) ou [ref](../../language-reference/keywords/ref.md), mas não [out](../../language-reference/keywords/out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="89d70-184">Partial methods can have [in](../../language-reference/keywords/in-parameter-modifier.md) or [ref](../../language-reference/keywords/ref.md) but not [out](../../language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>

- <span data-ttu-id="89d70-185">Métodos parciais são implicitamente [private](../../language-reference/keywords/private.md) e portanto não podem ser [virtual](../../language-reference/keywords/virtual.md).</span><span class="sxs-lookup"><span data-stu-id="89d70-185">Partial methods are implicitly [private](../../language-reference/keywords/private.md), and therefore they cannot be [virtual](../../language-reference/keywords/virtual.md).</span></span>

- <span data-ttu-id="89d70-186">Métodos parciais não podem ser [extern](../../language-reference/keywords/extern.md), pois a presença do corpo determina se eles estão sendo definidos ou implementados.</span><span class="sxs-lookup"><span data-stu-id="89d70-186">Partial methods cannot be [extern](../../language-reference/keywords/extern.md), because the presence of the body determines whether they are defining or implementing.</span></span>

- <span data-ttu-id="89d70-187">Métodos parciais podem ter modificadores [static](../../language-reference/keywords/static.md) e [unsafe](../../language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="89d70-187">Partial methods can have [static](../../language-reference/keywords/static.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span>

- <span data-ttu-id="89d70-188">Métodos parciais podem ser genéricos.</span><span class="sxs-lookup"><span data-stu-id="89d70-188">Partial methods can be generic.</span></span> <span data-ttu-id="89d70-189">Restrições são colocadas quanto à declaração de método parcial de definição e, opcionalmente, podem ser repetidas na de implementação.</span><span class="sxs-lookup"><span data-stu-id="89d70-189">Constraints are put on the defining partial method declaration, and may optionally be repeated on the implementing one.</span></span> <span data-ttu-id="89d70-190">Nomes de parâmetro e de tipo de parâmetro não precisam ser iguais na declaração de implementação e na de definição.</span><span class="sxs-lookup"><span data-stu-id="89d70-190">Parameter and type parameter names do not have to be the same in the implementing declaration as in the defining one.</span></span>

- <span data-ttu-id="89d70-191">Você pode fazer um [delegado](../../language-reference/keywords/delegate.md) para um método parcial que foi definido e implementado, mas não para um método parcial que só foi definido.</span><span class="sxs-lookup"><span data-stu-id="89d70-191">You can make a [delegate](../../language-reference/keywords/delegate.md) to a partial method that has been defined and implemented, but not to a partial method that has only been defined.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="89d70-192">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="89d70-192">C# Language Specification</span></span>

<span data-ttu-id="89d70-193">Para obter mais informações, veja [Tipos parciais](~/_csharplang/spec/classes.md#partial-types) na [Especificação da Linguagem C#](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="89d70-193">For more information, see [Partial types](~/_csharplang/spec/classes.md#partial-types) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="89d70-194">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="89d70-194">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="89d70-195">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89d70-195">See also</span></span>

- [<span data-ttu-id="89d70-196">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="89d70-196">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="89d70-197">Classes</span><span class="sxs-lookup"><span data-stu-id="89d70-197">Classes</span></span>](./classes.md)
- [<span data-ttu-id="89d70-198">Estruturas</span><span class="sxs-lookup"><span data-stu-id="89d70-198">Structs</span></span>](./structs.md)
- [<span data-ttu-id="89d70-199">Interfaces</span><span class="sxs-lookup"><span data-stu-id="89d70-199">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="89d70-200">(partial (tipo)</span><span class="sxs-lookup"><span data-stu-id="89d70-200">partial (Type)</span></span>](../../language-reference/keywords/partial-type.md)

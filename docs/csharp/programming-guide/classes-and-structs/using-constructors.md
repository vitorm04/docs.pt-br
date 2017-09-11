---
title: "Usando construtores (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
caps.latest.revision: 26
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
ms.openlocfilehash: 75b55fde2fbd1697aed7eb0665a571c63b9b0b42
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="using-constructors-c-programming-guide"></a><span data-ttu-id="54e9c-102">Usando construtores (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="54e9c-102">Using Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="54e9c-103">Quando uma [classe](../../../csharp/language-reference/keywords/class.md) ou [struct](../../../csharp/language-reference/keywords/struct.md) é criado, seu construtor é chamado.</span><span class="sxs-lookup"><span data-stu-id="54e9c-103">When a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="54e9c-104">Os construtores têm o mesmo nome que a classe ou struct e eles geralmente inicializam os membros de dados do novo objeto.</span><span class="sxs-lookup"><span data-stu-id="54e9c-104">Constructors have the same name as the class or struct, and they usually initialize the data members of the new object.</span></span>  
  
 <span data-ttu-id="54e9c-105">No exemplo a seguir, uma classe chamada `Taxi` é definida usando um construtor simples.</span><span class="sxs-lookup"><span data-stu-id="54e9c-105">In the following example, a class named `Taxi` is defined by using a simple constructor.</span></span> <span data-ttu-id="54e9c-106">A classe é então instanciada com o operador [new](../../../csharp/language-reference/keywords/new.md).</span><span class="sxs-lookup"><span data-stu-id="54e9c-106">This class is then instantiated with the [new](../../../csharp/language-reference/keywords/new.md) operator.</span></span> <span data-ttu-id="54e9c-107">O construtor `Taxi` é invocado pelo operador `new` imediatamente após a memória ser alocada para o novo objeto.</span><span class="sxs-lookup"><span data-stu-id="54e9c-107">The `Taxi` constructor is invoked by the `new` operator immediately after memory is allocated for the new object.</span></span>  
  
 <span data-ttu-id="54e9c-108">[!code-cs[csProgGuideObjects#53](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="54e9c-108">[!code-cs[csProgGuideObjects#53](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_1.cs)]</span></span>  
  
 <span data-ttu-id="54e9c-109">Um construtor sem parâmetros é chamado de um *construtor padrão*.</span><span class="sxs-lookup"><span data-stu-id="54e9c-109">A constructor that takes no parameters is called a *default constructor*.</span></span> <span data-ttu-id="54e9c-110">Os construtores padrão são invocados sempre que um objeto é instanciado usando o operador `new` e nenhum argumento é fornecido para `new`.</span><span class="sxs-lookup"><span data-stu-id="54e9c-110">Default constructors are invoked whenever an object is instantiated by using the `new` operator and no arguments are provided to `new`.</span></span> <span data-ttu-id="54e9c-111">Para obter mais informações, consulte [Construtores de instâncias](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="54e9c-111">For more information, see [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  
  
 <span data-ttu-id="54e9c-112">A menos que a classe seja [static](../../../csharp/language-reference/keywords/static.md), as classes sem construtores recebem um construtor padrão público pelo compilador C# para habilitar a instanciação de classe.</span><span class="sxs-lookup"><span data-stu-id="54e9c-112">Unless the class is [static](../../../csharp/language-reference/keywords/static.md), classes without constructors are given a public default constructor by the C# compiler in order to enable class instantiation.</span></span> <span data-ttu-id="54e9c-113">Para obter mais informações, consulte [Classes Estáticas e Membros de Classes Estáticas](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="54e9c-113">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="54e9c-114">Você pode impedir que uma classe seja instanciada tornando o construtor privado, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="54e9c-114">You can prevent a class from being instantiated by making the constructor private, as follows:</span></span>  
  
 <span data-ttu-id="54e9c-115">[!code-cs[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="54e9c-115">[!code-cs[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_2.cs)]</span></span>  
  
 <span data-ttu-id="54e9c-116">Para obter mais informações, consulte [Construtores particulares](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="54e9c-116">For more information, see [Private Constructors](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).</span></span>  
  
 <span data-ttu-id="54e9c-117">Os construtores de tipos [struct](../../../csharp/language-reference/keywords/struct.md) são semelhantes aos construtores de classe, mas `structs` não podem conter um construtor padrão explícito porque um é fornecido automaticamente pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="54e9c-117">Constructors for [struct](../../../csharp/language-reference/keywords/struct.md) types resemble class constructors, but `structs` cannot contain an explicit default constructor because one is provided automatically by the compiler.</span></span> <span data-ttu-id="54e9c-118">Este construtor inicializa todos os campos no `struct` com os valores padrão.</span><span class="sxs-lookup"><span data-stu-id="54e9c-118">This constructor initializes each field in the `struct` to the default values.</span></span> <span data-ttu-id="54e9c-119">Para obter mais informações, consulte [Tabela de opções padrão](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="54e9c-119">For more information, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="54e9c-120">No entanto, esse construtor padrão é invocado apenas se o `struct` é instanciado com `new`.</span><span class="sxs-lookup"><span data-stu-id="54e9c-120">However, this default constructor is only invoked if the `struct` is instantiated with `new`.</span></span> <span data-ttu-id="54e9c-121">Por exemplo, esse código usa o construtor padrão para <xref:System.Int32>, de modo que você tenha certeza de que o inteiro é inicializado:</span><span class="sxs-lookup"><span data-stu-id="54e9c-121">For example, this code uses the default constructor for <xref:System.Int32>, so that you are assured that the integer is initialized:</span></span>  
  
```  
int i = new int();  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="54e9c-122">O código a seguir, no entanto, causa um erro do compilador porque ele não usa `new` e porque ele tenta usar um objeto que não foi inicializado:</span><span class="sxs-lookup"><span data-stu-id="54e9c-122">The following code, however, causes a compiler error because it does not use `new`, and because it tries to use an object that has not been initialized:</span></span>  
  
```  
int i;  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="54e9c-123">Como alternativa, os objetos com base em `structs` (incluindo todos os tipos numéricos internos) podem ser inicializados ou atribuídos e, em seguida, usados como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="54e9c-123">Alternatively, objects based on `structs` (including all built-in numeric types) can be initialized or assigned and then used as in the following example:</span></span>  
  
```  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 <span data-ttu-id="54e9c-124">Portanto, não é necessário chamar o construtor padrão para um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="54e9c-124">So calling the default constructor for a value type is not required.</span></span>  
  
 <span data-ttu-id="54e9c-125">Ambas as classes e `structs` podem definir construtores que usam parâmetros.</span><span class="sxs-lookup"><span data-stu-id="54e9c-125">Both classes and `structs` can define constructors that take parameters.</span></span> <span data-ttu-id="54e9c-126">Os construtores que usam parâmetros devem ser chamados por meio de uma instrução `new` ou uma instrução [base](../../../csharp/language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="54e9c-126">Constructors that take parameters must be called through a `new` statement or a [base](../../../csharp/language-reference/keywords/base.md) statement.</span></span> <span data-ttu-id="54e9c-127">As classes e `structs` também pode definem vários construtores e nenhum deles precisa definir um construtor padrão.</span><span class="sxs-lookup"><span data-stu-id="54e9c-127">Classes and `structs` can also define multiple constructors, and neither is required to define a default constructor.</span></span> <span data-ttu-id="54e9c-128">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="54e9c-128">For example:</span></span>  
  
 <span data-ttu-id="54e9c-129">[!code-cs[csProgGuideObjects#54](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="54e9c-129">[!code-cs[csProgGuideObjects#54](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_3.cs)]</span></span>  
  
 <span data-ttu-id="54e9c-130">Essa classe pode ser criada usando qualquer uma das instruções a seguir:</span><span class="sxs-lookup"><span data-stu-id="54e9c-130">This class can be created by using either of the following statements:</span></span>  
  
 <span data-ttu-id="54e9c-131">[!code-cs[csProgGuideObjects#55](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="54e9c-131">[!code-cs[csProgGuideObjects#55](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_4.cs)]</span></span>  
  
 <span data-ttu-id="54e9c-132">Um construtor pode usar a palavra-chave `base` para chamar o construtor de uma classe base.</span><span class="sxs-lookup"><span data-stu-id="54e9c-132">A constructor can use the `base` keyword to call the constructor of a base class.</span></span> <span data-ttu-id="54e9c-133">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="54e9c-133">For example:</span></span>  
  
 <span data-ttu-id="54e9c-134">[!code-cs[csProgGuideObjects#56](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="54e9c-134">[!code-cs[csProgGuideObjects#56](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_5.cs)]</span></span>  
  
 <span data-ttu-id="54e9c-135">Neste exemplo, o construtor da classe base é chamado antes de o bloco do construtor ser executado.</span><span class="sxs-lookup"><span data-stu-id="54e9c-135">In this example, the constructor for the base class is called before the block for the constructor is executed.</span></span> <span data-ttu-id="54e9c-136">A palavra-chave `base` pode ser usada com ou sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="54e9c-136">The `base` keyword can be used with or without parameters.</span></span> <span data-ttu-id="54e9c-137">Os parâmetros para o construtor podem ser usados como parâmetros para `base` ou como parte de uma expressão.</span><span class="sxs-lookup"><span data-stu-id="54e9c-137">Any parameters to the constructor can be used as parameters to `base`, or as part of an expression.</span></span> <span data-ttu-id="54e9c-138">Para obter mais informações, consulte [base](../../../csharp/language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="54e9c-138">For more information, see [base](../../../csharp/language-reference/keywords/base.md).</span></span>  
  
 <span data-ttu-id="54e9c-139">Em uma classe derivada, se um construtor de classe base não for chamado explicitamente usando a palavra-chave `base`, o construtor padrão, se houver, será chamado implicitamente.</span><span class="sxs-lookup"><span data-stu-id="54e9c-139">In a derived class, if a base-class constructor is not called explicitly by using the `base` keyword, the default constructor, if there is one, is called implicitly.</span></span> <span data-ttu-id="54e9c-140">Isso significa que as seguintes declarações de construtor são efetivamente iguais:</span><span class="sxs-lookup"><span data-stu-id="54e9c-140">This means that the following constructor declarations are effectively the same:</span></span>  
  
 <span data-ttu-id="54e9c-141">[!code-cs[csProgGuideObjects#58](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="54e9c-141">[!code-cs[csProgGuideObjects#58](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_6.cs)]</span></span>  
  
 <span data-ttu-id="54e9c-142">[!code-cs[csProgGuideObjects#57](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="54e9c-142">[!code-cs[csProgGuideObjects#57](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_7.cs)]</span></span>  
  
 <span data-ttu-id="54e9c-143">Se uma classe base não oferecer um construtor padrão, a classe derivada deverá fazer uma chamada explícita para um construtor base usando `base`.</span><span class="sxs-lookup"><span data-stu-id="54e9c-143">If a base class does not offer a default constructor, the derived class must make an explicit call to a base constructor by using `base`.</span></span>  
  
 <span data-ttu-id="54e9c-144">Um construtor pode invocar outro construtor no mesmo objeto usando a palavra-chave [this](../../../csharp/language-reference/keywords/this.md).</span><span class="sxs-lookup"><span data-stu-id="54e9c-144">A constructor can invoke another constructor in the same object by using the [this](../../../csharp/language-reference/keywords/this.md) keyword.</span></span> <span data-ttu-id="54e9c-145">Como `base`, `this` pode ser usado com ou sem parâmetros e todos os parâmetros no construtor estão disponíveis como parâmetros para `this` ou como parte de uma expressão.</span><span class="sxs-lookup"><span data-stu-id="54e9c-145">Like `base`, `this` can be used with or without parameters, and any parameters in the constructor are available as parameters to `this`, or as part of an expression.</span></span> <span data-ttu-id="54e9c-146">Por exemplo, o segundo construtor no exemplo anterior pode ser reescrito usando `this`:</span><span class="sxs-lookup"><span data-stu-id="54e9c-146">For example, the second constructor in the previous example can be rewritten using `this`:</span></span>  
  
 <span data-ttu-id="54e9c-147">[!code-cs[csProgGuideObjects#59](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="54e9c-147">[!code-cs[csProgGuideObjects#59](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_8.cs)]</span></span>  
  
 <span data-ttu-id="54e9c-148">O uso da palavra-chave `this` no exemplo anterior faz com que esse construtor seja chamado:</span><span class="sxs-lookup"><span data-stu-id="54e9c-148">The use of the `this` keyword in the previous example causes this constructor to be called:</span></span>  
  
 <span data-ttu-id="54e9c-149">[!code-cs[csProgGuideObjects#60](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_9.cs)]</span><span class="sxs-lookup"><span data-stu-id="54e9c-149">[!code-cs[csProgGuideObjects#60](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_9.cs)]</span></span>  
  
 <span data-ttu-id="54e9c-150">Os construtores podem ser marcados como [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md) ou `protected internal`.</span><span class="sxs-lookup"><span data-stu-id="54e9c-150">Constructors can be marked as [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), or `protected internal`.</span></span> <span data-ttu-id="54e9c-151">Esses modificadores de acesso definem como os usuários da classe podem construir a classe.</span><span class="sxs-lookup"><span data-stu-id="54e9c-151">These access modifiers define how users of the class can construct the class.</span></span> <span data-ttu-id="54e9c-152">Para obter mais informações, consulte [Modificadores de Acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="54e9c-152">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="54e9c-153">Um construtor pode ser declarado estático usando a palavra-chave [static](../../../csharp/language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="54e9c-153">A constructor can be declared static by using the [static](../../../csharp/language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="54e9c-154">Os construtores estáticos são chamados automaticamente, imediatamente antes de qualquer campo estático ser acessado e geralmente são usados para inicializar membros da classe estática.</span><span class="sxs-lookup"><span data-stu-id="54e9c-154">Static constructors are called automatically, immediately before any static fields are accessed, and are generally used to initialize static class members.</span></span> <span data-ttu-id="54e9c-155">Para obter mais informações, consulte [Construtores estáticos](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="54e9c-155">For more information, see [Static Constructors](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="54e9c-156">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="54e9c-156">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="54e9c-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54e9c-157">See Also</span></span>  
 <span data-ttu-id="54e9c-158">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="54e9c-158">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="54e9c-159">[Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="54e9c-159">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="54e9c-160">[Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md) </span><span class="sxs-lookup"><span data-stu-id="54e9c-160">[Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md) </span></span>  
 [<span data-ttu-id="54e9c-161">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="54e9c-161">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)


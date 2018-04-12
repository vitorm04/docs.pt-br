---
title: Usando namespaces (Guia de Programação em C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
caps.latest.revision: 26
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f485992f5d4b7bc16aaefeec8c7c76ce39f48ef0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="0e79a-102">Usando namespaces (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="0e79a-102">Using Namespaces (C# Programming Guide)</span></span>
<span data-ttu-id="0e79a-103">Os namespaces são usados intensamente em programas em C# de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="0e79a-103">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="0e79a-104">Em primeiro lugar, as classes do .NET Framework usam namespaces para organizar suas muitas classes.</span><span class="sxs-lookup"><span data-stu-id="0e79a-104">Firstly, the .NET Framework classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="0e79a-105">Em segundo lugar, declarar seus próprios namespaces pode ajudar a controlar o escopo dos nomes de classe e de método em projetos de programação maiores.</span><span class="sxs-lookup"><span data-stu-id="0e79a-105">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="0e79a-106">Acessando namespaces</span><span class="sxs-lookup"><span data-stu-id="0e79a-106">Accessing Namespaces</span></span>  
 <span data-ttu-id="0e79a-107">A maioria dos aplicativos do C# começam com uma seção de diretivas `using`.</span><span class="sxs-lookup"><span data-stu-id="0e79a-107">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="0e79a-108">Essa seção lista os namespaces que o aplicativo usará com frequência e evita que o programador tenha que especificar um nome totalmente qualificado sempre que um método que está contido é usado.</span><span class="sxs-lookup"><span data-stu-id="0e79a-108">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="0e79a-109">Por exemplo, ao incluir a linha:</span><span class="sxs-lookup"><span data-stu-id="0e79a-109">For example, by including the line:</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_1.cs)]  
  
 <span data-ttu-id="0e79a-110">No início de um programa, o programador pode usar o código:</span><span class="sxs-lookup"><span data-stu-id="0e79a-110">At the start of a program, the programmer can use the code:</span></span>  
  
 [!code-csharp[csProgGuide#31](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_2.cs)]  
  
 <span data-ttu-id="0e79a-111">Em vez de:</span><span class="sxs-lookup"><span data-stu-id="0e79a-111">Instead of:</span></span>  
  
 [!code-csharp[csProgGuide#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_3.cs)]  
  
## <a name="namespace-aliases"></a><span data-ttu-id="0e79a-112">Aliases de Namespace</span><span class="sxs-lookup"><span data-stu-id="0e79a-112">Namespace Aliases</span></span>  
 <span data-ttu-id="0e79a-113">A [diretiva using](../../../csharp/language-reference/keywords/using-directive.md) também pode ser usada para criar um alias para um [namespace](../../../csharp/language-reference/keywords/namespace.md).</span><span class="sxs-lookup"><span data-stu-id="0e79a-113">The [using Directive](../../../csharp/language-reference/keywords/using-directive.md) can also be used to create an alias for a [namespace](../../../csharp/language-reference/keywords/namespace.md).</span></span> <span data-ttu-id="0e79a-114">Por exemplo, se você estiver usando um namespace gravado anteriormente que contém namespaces aninhados, convém declarar um alias para fornecer uma forma abreviada de fazer referênia a um namespace em particular, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0e79a-114">For example, if you are using a previously written namespace that contains nested namespaces, you might want to declare an alias to provide a shorthand way of referencing one in particular, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#7](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_4.cs)]  
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="0e79a-115">Usando namespaces para controlar o escopo</span><span class="sxs-lookup"><span data-stu-id="0e79a-115">Using Namespaces to control scope</span></span>  
 <span data-ttu-id="0e79a-116">A palavra-chave `namespace` é usada para declarar um escopo.</span><span class="sxs-lookup"><span data-stu-id="0e79a-116">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="0e79a-117">A capacidade de criar escopos dentro de seu projeto ajuda a organizar o código e permite que você crie tipos globalmente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="0e79a-117">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="0e79a-118">No exemplo a seguir, uma classe denominada `SampleClass` é definida em dois namespaces, um aninhado no outro.</span><span class="sxs-lookup"><span data-stu-id="0e79a-118">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="0e79a-119">O [. Operador](../../../csharp/language-reference/operators/member-access-operator.md) é usado para diferenciar qual método será chamado.</span><span class="sxs-lookup"><span data-stu-id="0e79a-119">The [. Operator](../../../csharp/language-reference/operators/member-access-operator.md) is used to differentiate which method gets called.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#8](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_5.cs)]  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="0e79a-120">Nomes totalmente qualificados</span><span class="sxs-lookup"><span data-stu-id="0e79a-120">Fully Qualified Names</span></span>  
 <span data-ttu-id="0e79a-121">Os namespaces e os tipos têm títulos exclusivos descritos por nomes totalmente qualificados que indicam uma hierarquia lógica.</span><span class="sxs-lookup"><span data-stu-id="0e79a-121">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="0e79a-122">Por exemplo, a instrução `A.B` implica que `A` é o nome do namespace ou do tipo e `B` é aninhado dentro dele.</span><span class="sxs-lookup"><span data-stu-id="0e79a-122">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="0e79a-123">No exemplo a seguir, há namespaces e classes aninhadas.</span><span class="sxs-lookup"><span data-stu-id="0e79a-123">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="0e79a-124">O nome totalmente qualificado é indicado como um comentário após cada entidade.</span><span class="sxs-lookup"><span data-stu-id="0e79a-124">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#9](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_6.cs)]  
  
 <span data-ttu-id="0e79a-125">No segmento de código anterior:</span><span class="sxs-lookup"><span data-stu-id="0e79a-125">In the previous code segment:</span></span>  
  
-   <span data-ttu-id="0e79a-126">O namespace `N1` é um membro do namespace global.</span><span class="sxs-lookup"><span data-stu-id="0e79a-126">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="0e79a-127">Seu nome totalmente qualificado é `N1`.</span><span class="sxs-lookup"><span data-stu-id="0e79a-127">Its fully qualified name is `N1`.</span></span>  
  
-   <span data-ttu-id="0e79a-128">O namespace `N2` é um membro de `N1`.</span><span class="sxs-lookup"><span data-stu-id="0e79a-128">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="0e79a-129">Seu nome totalmente qualificado é `N1.N2`.</span><span class="sxs-lookup"><span data-stu-id="0e79a-129">Its fully qualified name is `N1.N2`.</span></span>  
  
-   <span data-ttu-id="0e79a-130">A classe `C1` é um membro de `N1`.</span><span class="sxs-lookup"><span data-stu-id="0e79a-130">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="0e79a-131">Seu nome totalmente qualificado é `N1.C1`.</span><span class="sxs-lookup"><span data-stu-id="0e79a-131">Its fully qualified name is `N1.C1`.</span></span>  
  
-   <span data-ttu-id="0e79a-132">O nome de classe `C2` é usado duas vezes nesse código.</span><span class="sxs-lookup"><span data-stu-id="0e79a-132">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="0e79a-133">No entanto, os nomes totalmente qualificados são exclusivos.</span><span class="sxs-lookup"><span data-stu-id="0e79a-133">However, the fully qualified names are unique.</span></span> <span data-ttu-id="0e79a-134">A primeira instância da `C2` é declarada dentro de `C1`, portanto, seu nome totalmente qualificado é: `N1.C1.C2`.</span><span class="sxs-lookup"><span data-stu-id="0e79a-134">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="0e79a-135">A segunda instância da `C2` é declarada dentro de um namespace `N2`, portanto, seu nome totalmente qualificado é: `N1.N2.C2`.</span><span class="sxs-lookup"><span data-stu-id="0e79a-135">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="0e79a-136">Usando o segmento de código anterior, você pode adicionar um novo membro de classe `C3` ao namespace `N1.N2`, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="0e79a-136">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#10](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_7.cs)]  
  
 <span data-ttu-id="0e79a-137">Em geral, use `::` para fazer referência a um alias de namespace ou `global::` para referenciar o namespace global e `.` para qualificar os tipos ou membros.</span><span class="sxs-lookup"><span data-stu-id="0e79a-137">In general, use `::` to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="0e79a-138">É um erro usar `::` com um alias que faz referência a um tipo em vez de um namespace.</span><span class="sxs-lookup"><span data-stu-id="0e79a-138">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="0e79a-139">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="0e79a-139">For example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#11](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_8.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#12](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_9.cs)]  
  
 <span data-ttu-id="0e79a-140">Lembre-se que a palavra `global` não é um alias predefinido, portanto, `global.X` não tem qualquer significado especial.</span><span class="sxs-lookup"><span data-stu-id="0e79a-140">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="0e79a-141">Ela só adquire um significado especial quando é usada com `::`.</span><span class="sxs-lookup"><span data-stu-id="0e79a-141">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="0e79a-142">O aviso do compilador CS0440 será gerado se você definir um alias chamado global porque `global::` sempre faz referência ao namespace global e não a um alias.</span><span class="sxs-lookup"><span data-stu-id="0e79a-142">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="0e79a-143">Por exemplo, a linha a seguir gera o aviso:</span><span class="sxs-lookup"><span data-stu-id="0e79a-143">For example, the following line generates the warning:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#13](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_10.cs)]  
  
 <span data-ttu-id="0e79a-144">Usar `::` com aliases é uma boa ideia e protege contra a introdução inesperada de tipos adicionais.</span><span class="sxs-lookup"><span data-stu-id="0e79a-144">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="0e79a-145">Considere este exemplo:</span><span class="sxs-lookup"><span data-stu-id="0e79a-145">For example, consider this example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#14](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_11.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#15](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_12.cs)]  
  
 <span data-ttu-id="0e79a-146">Isso funciona, mas se um tipo nomeado `Alias` fosse subsequentemente introduzido, `Alias.` se associaria a esse tipo.</span><span class="sxs-lookup"><span data-stu-id="0e79a-146">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="0e79a-147">Usar `Alias::Exception` assegura que `Alias` seja tratado como um alias de namespace e não seja confundido com um tipo.</span><span class="sxs-lookup"><span data-stu-id="0e79a-147">Using `Alias::Exception` insures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  
  
 <span data-ttu-id="0e79a-148">Consulte o tópico [Como usar o alias de namespace global](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) para obter mais informações sobre o alias `global`.</span><span class="sxs-lookup"><span data-stu-id="0e79a-148">See the topic [How to: Use the Global Namespace Alias](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) for more information regarding the `global` alias.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e79a-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0e79a-149">See Also</span></span>  
 [<span data-ttu-id="0e79a-150">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="0e79a-150">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0e79a-151">Namespaces</span><span class="sxs-lookup"><span data-stu-id="0e79a-151">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
 [<span data-ttu-id="0e79a-152">Palavras-chave de namespace</span><span class="sxs-lookup"><span data-stu-id="0e79a-152">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="0e79a-153">. Operador .</span><span class="sxs-lookup"><span data-stu-id="0e79a-153">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
 [<span data-ttu-id="0e79a-154">Operador ::</span><span class="sxs-lookup"><span data-stu-id="0e79a-154">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [<span data-ttu-id="0e79a-155">extern</span><span class="sxs-lookup"><span data-stu-id="0e79a-155">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)

---
title: Usando namespaces (Guia de Programação em C#)
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: 81876d1818a6e82764e4aea0ae2b6f9e091f0ba3
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123391"
---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="20f0d-102">Usando namespaces (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="20f0d-102">Using Namespaces (C# Programming Guide)</span></span>
<span data-ttu-id="20f0d-103">Os namespaces são usados intensamente em programas em C# de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="20f0d-103">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="20f0d-104">Em primeiro lugar, as classes do .NET Framework usam namespaces para organizar suas muitas classes.</span><span class="sxs-lookup"><span data-stu-id="20f0d-104">Firstly, the .NET Framework classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="20f0d-105">Em segundo lugar, declarar seus próprios namespaces pode ajudar a controlar o escopo dos nomes de classe e de método em projetos de programação maiores.</span><span class="sxs-lookup"><span data-stu-id="20f0d-105">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="20f0d-106">Acessando namespaces</span><span class="sxs-lookup"><span data-stu-id="20f0d-106">Accessing Namespaces</span></span>  
 <span data-ttu-id="20f0d-107">A maioria dos aplicativos do C# começam com uma seção de diretivas `using`.</span><span class="sxs-lookup"><span data-stu-id="20f0d-107">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="20f0d-108">Essa seção lista os namespaces que o aplicativo usará com frequência e evita que o programador tenha que especificar um nome totalmente qualificado sempre que um método que está contido é usado.</span><span class="sxs-lookup"><span data-stu-id="20f0d-108">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="20f0d-109">Por exemplo, ao incluir a linha:</span><span class="sxs-lookup"><span data-stu-id="20f0d-109">For example, by including the line:</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_1.cs)]  
  
 <span data-ttu-id="20f0d-110">No início de um programa, o programador pode usar o código:</span><span class="sxs-lookup"><span data-stu-id="20f0d-110">At the start of a program, the programmer can use the code:</span></span>  
  
 [!code-csharp[csProgGuide#31](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_2.cs)]  
  
 <span data-ttu-id="20f0d-111">Em vez de:</span><span class="sxs-lookup"><span data-stu-id="20f0d-111">Instead of:</span></span>  
  
 [!code-csharp[csProgGuide#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_3.cs)]  
  
## <a name="namespace-aliases"></a><span data-ttu-id="20f0d-112">Aliases de Namespace</span><span class="sxs-lookup"><span data-stu-id="20f0d-112">Namespace Aliases</span></span>  
 <span data-ttu-id="20f0d-113">A [diretiva using](../../../csharp/language-reference/keywords/using-directive.md) também pode ser usada para criar um alias para um [namespace](../../../csharp/language-reference/keywords/namespace.md).</span><span class="sxs-lookup"><span data-stu-id="20f0d-113">The [using Directive](../../../csharp/language-reference/keywords/using-directive.md) can also be used to create an alias for a [namespace](../../../csharp/language-reference/keywords/namespace.md).</span></span> <span data-ttu-id="20f0d-114">Por exemplo, se você estiver usando um namespace gravado anteriormente que contém namespaces aninhados, convém declarar um alias para fornecer uma forma abreviada de fazer referênia a um namespace em particular, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="20f0d-114">For example, if you are using a previously written namespace that contains nested namespaces, you might want to declare an alias to provide a shorthand way of referencing one in particular, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#7](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_4.cs)]  
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="20f0d-115">Usando namespaces para controlar o escopo</span><span class="sxs-lookup"><span data-stu-id="20f0d-115">Using Namespaces to control scope</span></span>  
 <span data-ttu-id="20f0d-116">A palavra-chave `namespace` é usada para declarar um escopo.</span><span class="sxs-lookup"><span data-stu-id="20f0d-116">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="20f0d-117">A capacidade de criar escopos dentro de seu projeto ajuda a organizar o código e permite que você crie tipos globalmente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="20f0d-117">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="20f0d-118">No exemplo a seguir, uma classe denominada `SampleClass` é definida em dois namespaces, um aninhado no outro.</span><span class="sxs-lookup"><span data-stu-id="20f0d-118">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="20f0d-119">O [. Operador](../../../csharp/language-reference/operators/member-access-operator.md) é usado para diferenciar qual método será chamado.</span><span class="sxs-lookup"><span data-stu-id="20f0d-119">The [. Operator](../../../csharp/language-reference/operators/member-access-operator.md) is used to differentiate which method gets called.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#8](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_5.cs)]  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="20f0d-120">Nomes totalmente qualificados</span><span class="sxs-lookup"><span data-stu-id="20f0d-120">Fully Qualified Names</span></span>  
 <span data-ttu-id="20f0d-121">Os namespaces e os tipos têm títulos exclusivos descritos por nomes totalmente qualificados que indicam uma hierarquia lógica.</span><span class="sxs-lookup"><span data-stu-id="20f0d-121">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="20f0d-122">Por exemplo, a instrução `A.B` implica que `A` é o nome do namespace ou do tipo e `B` é aninhado dentro dele.</span><span class="sxs-lookup"><span data-stu-id="20f0d-122">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="20f0d-123">No exemplo a seguir, há namespaces e classes aninhadas.</span><span class="sxs-lookup"><span data-stu-id="20f0d-123">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="20f0d-124">O nome totalmente qualificado é indicado como um comentário após cada entidade.</span><span class="sxs-lookup"><span data-stu-id="20f0d-124">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#9](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_6.cs)]  
  
 <span data-ttu-id="20f0d-125">No segmento de código anterior:</span><span class="sxs-lookup"><span data-stu-id="20f0d-125">In the previous code segment:</span></span>  
  
-   <span data-ttu-id="20f0d-126">O namespace `N1` é um membro do namespace global.</span><span class="sxs-lookup"><span data-stu-id="20f0d-126">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="20f0d-127">Seu nome totalmente qualificado é `N1`.</span><span class="sxs-lookup"><span data-stu-id="20f0d-127">Its fully qualified name is `N1`.</span></span>  
  
-   <span data-ttu-id="20f0d-128">O namespace `N2` é um membro de `N1`.</span><span class="sxs-lookup"><span data-stu-id="20f0d-128">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="20f0d-129">Seu nome totalmente qualificado é `N1.N2`.</span><span class="sxs-lookup"><span data-stu-id="20f0d-129">Its fully qualified name is `N1.N2`.</span></span>  
  
-   <span data-ttu-id="20f0d-130">A classe `C1` é um membro de `N1`.</span><span class="sxs-lookup"><span data-stu-id="20f0d-130">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="20f0d-131">Seu nome totalmente qualificado é `N1.C1`.</span><span class="sxs-lookup"><span data-stu-id="20f0d-131">Its fully qualified name is `N1.C1`.</span></span>  
  
-   <span data-ttu-id="20f0d-132">O nome de classe `C2` é usado duas vezes nesse código.</span><span class="sxs-lookup"><span data-stu-id="20f0d-132">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="20f0d-133">No entanto, os nomes totalmente qualificados são exclusivos.</span><span class="sxs-lookup"><span data-stu-id="20f0d-133">However, the fully qualified names are unique.</span></span> <span data-ttu-id="20f0d-134">A primeira instância da `C2` é declarada dentro de `C1`, portanto, seu nome totalmente qualificado é: `N1.C1.C2`.</span><span class="sxs-lookup"><span data-stu-id="20f0d-134">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="20f0d-135">A segunda instância da `C2` é declarada dentro de um namespace `N2`, portanto, seu nome totalmente qualificado é: `N1.N2.C2`.</span><span class="sxs-lookup"><span data-stu-id="20f0d-135">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="20f0d-136">Usando o segmento de código anterior, você pode adicionar um novo membro de classe `C3` ao namespace `N1.N2`, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="20f0d-136">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#10](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_7.cs)]  
  
 <span data-ttu-id="20f0d-137">Em geral, use `::` para fazer referência a um alias de namespace ou `global::` para referenciar o namespace global e `.` para qualificar os tipos ou membros.</span><span class="sxs-lookup"><span data-stu-id="20f0d-137">In general, use `::` to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="20f0d-138">É um erro usar `::` com um alias que faz referência a um tipo em vez de um namespace.</span><span class="sxs-lookup"><span data-stu-id="20f0d-138">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="20f0d-139">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="20f0d-139">For example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#11](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_8.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#12](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_9.cs)]  
  
 <span data-ttu-id="20f0d-140">Lembre-se que a palavra `global` não é um alias predefinido, portanto, `global.X` não tem qualquer significado especial.</span><span class="sxs-lookup"><span data-stu-id="20f0d-140">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="20f0d-141">Ela só adquire um significado especial quando é usada com `::`.</span><span class="sxs-lookup"><span data-stu-id="20f0d-141">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="20f0d-142">O aviso do compilador CS0440 será gerado se você definir um alias chamado global porque `global::` sempre faz referência ao namespace global e não a um alias.</span><span class="sxs-lookup"><span data-stu-id="20f0d-142">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="20f0d-143">Por exemplo, a linha a seguir gera o aviso:</span><span class="sxs-lookup"><span data-stu-id="20f0d-143">For example, the following line generates the warning:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#13](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_10.cs)]  
  
 <span data-ttu-id="20f0d-144">Usar `::` com aliases é uma boa ideia e protege contra a introdução inesperada de tipos adicionais.</span><span class="sxs-lookup"><span data-stu-id="20f0d-144">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="20f0d-145">Considere este exemplo:</span><span class="sxs-lookup"><span data-stu-id="20f0d-145">For example, consider this example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#14](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_11.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#15](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_12.cs)]  
  
 <span data-ttu-id="20f0d-146">Isso funciona, mas se um tipo nomeado `Alias` fosse subsequentemente introduzido, `Alias.` se associaria a esse tipo.</span><span class="sxs-lookup"><span data-stu-id="20f0d-146">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="20f0d-147">Usar `Alias::Exception` assegura que `Alias` seja tratado como um alias de namespace e não seja confundido com um tipo.</span><span class="sxs-lookup"><span data-stu-id="20f0d-147">Using `Alias::Exception` insures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  
  
 <span data-ttu-id="20f0d-148">Consulte o tópico [Como usar o alias de namespace global](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) para obter mais informações sobre o alias `global`.</span><span class="sxs-lookup"><span data-stu-id="20f0d-148">See the topic [How to: Use the Global Namespace Alias](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) for more information regarding the `global` alias.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20f0d-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="20f0d-149">See Also</span></span>

- [<span data-ttu-id="20f0d-150">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="20f0d-150">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="20f0d-151">Namespaces</span><span class="sxs-lookup"><span data-stu-id="20f0d-151">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
- [<span data-ttu-id="20f0d-152">Palavras-chave de namespace</span><span class="sxs-lookup"><span data-stu-id="20f0d-152">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
- [<span data-ttu-id="20f0d-153">. Operador .</span><span class="sxs-lookup"><span data-stu-id="20f0d-153">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
- [<span data-ttu-id="20f0d-154">Operador ::</span><span class="sxs-lookup"><span data-stu-id="20f0d-154">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
- [<span data-ttu-id="20f0d-155">extern</span><span class="sxs-lookup"><span data-stu-id="20f0d-155">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)

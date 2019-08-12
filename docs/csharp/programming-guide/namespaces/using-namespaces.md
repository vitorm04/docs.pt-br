---
title: Usando namespaces – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: 06ebb9edfaf4753b98c3305a90b52e93ee7b4486
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796642"
---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="b4d78-102">Usando namespaces (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="b4d78-102">Using namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="b4d78-103">Os namespaces são usados intensamente em programas em C# de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="b4d78-103">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="b4d78-104">Em primeiro lugar, as classes do .NET Framework usam namespaces para organizar suas muitas classes.</span><span class="sxs-lookup"><span data-stu-id="b4d78-104">Firstly, the .NET Framework classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="b4d78-105">Em segundo lugar, declarar seus próprios namespaces pode ajudar a controlar o escopo dos nomes de classe e de método em projetos de programação maiores.</span><span class="sxs-lookup"><span data-stu-id="b4d78-105">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="b4d78-106">Acessar namespaces</span><span class="sxs-lookup"><span data-stu-id="b4d78-106">Accessing namespaces</span></span>

 <span data-ttu-id="b4d78-107">A maioria dos aplicativos do C# começam com uma seção de diretivas `using`.</span><span class="sxs-lookup"><span data-stu-id="b4d78-107">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="b4d78-108">Essa seção lista os namespaces que o aplicativo usará com frequência e evita que o programador tenha que especificar um nome totalmente qualificado sempre que um método que está contido é usado.</span><span class="sxs-lookup"><span data-stu-id="b4d78-108">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="b4d78-109">Por exemplo, ao incluir a linha:</span><span class="sxs-lookup"><span data-stu-id="b4d78-109">For example, by including the line:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 <span data-ttu-id="b4d78-110">No início de um programa, o programador pode usar o código:</span><span class="sxs-lookup"><span data-stu-id="b4d78-110">At the start of a program, the programmer can use the code:</span></span>  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 <span data-ttu-id="b4d78-111">Em vez de:</span><span class="sxs-lookup"><span data-stu-id="b4d78-111">Instead of:</span></span>  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a><span data-ttu-id="b4d78-112">aliases de namespace</span><span class="sxs-lookup"><span data-stu-id="b4d78-112">Namespace aliases</span></span>

 <span data-ttu-id="b4d78-113">Você também pode usar a [diretiva `using`](../../language-reference/keywords/using-directive.md) para criar um alias para um namespace.</span><span class="sxs-lookup"><span data-stu-id="b4d78-113">You also can use the [`using` directive](../../language-reference/keywords/using-directive.md) to create an alias for a namespace.</span></span> <span data-ttu-id="b4d78-114">Use o [qualificador de alias de namespace `::`](../../language-reference/operators/namespace-alias-qualifier.md) para acessar os membros do namespace com alias.</span><span class="sxs-lookup"><span data-stu-id="b4d78-114">Use the [namespace alias qualifier `::`](../../language-reference/operators/namespace-alias-qualifier.md) to access the members of the aliased namespace.</span></span> <span data-ttu-id="b4d78-115">O exemplo a seguir mostra como criar e usar um alias de namespace:</span><span class="sxs-lookup"><span data-stu-id="b4d78-115">The following example shows how to create and use a namespace alias:</span></span>
  
[!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="b4d78-116">Usar namespaces para controlar o escopo</span><span class="sxs-lookup"><span data-stu-id="b4d78-116">Using namespaces to control scope</span></span>

 <span data-ttu-id="b4d78-117">A palavra-chave `namespace` é usada para declarar um escopo.</span><span class="sxs-lookup"><span data-stu-id="b4d78-117">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="b4d78-118">A capacidade de criar escopos dentro de seu projeto ajuda a organizar o código e permite que você crie tipos globalmente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="b4d78-118">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="b4d78-119">No exemplo a seguir, uma classe denominada `SampleClass` é definida em dois namespaces, um aninhado no outro.</span><span class="sxs-lookup"><span data-stu-id="b4d78-119">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="b4d78-120">O [operador `.` de acesso de membro](../../language-reference/operators/member-access-operators.md#member-access-operator-) é usado para diferenciar qual método é chamado.</span><span class="sxs-lookup"><span data-stu-id="b4d78-120">The [member access `.` operator](../../language-reference/operators/member-access-operators.md#member-access-operator-) is used to differentiate which method gets called.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="b4d78-121">Nomes totalmente qualificados</span><span class="sxs-lookup"><span data-stu-id="b4d78-121">Fully qualified names</span></span>

 <span data-ttu-id="b4d78-122">Os namespaces e os tipos têm títulos exclusivos descritos por nomes totalmente qualificados que indicam uma hierarquia lógica.</span><span class="sxs-lookup"><span data-stu-id="b4d78-122">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="b4d78-123">Por exemplo, a instrução `A.B` implica que `A` é o nome do namespace ou do tipo e `B` é aninhado dentro dele.</span><span class="sxs-lookup"><span data-stu-id="b4d78-123">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="b4d78-124">No exemplo a seguir, há namespaces e classes aninhadas.</span><span class="sxs-lookup"><span data-stu-id="b4d78-124">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="b4d78-125">O nome totalmente qualificado é indicado como um comentário após cada entidade.</span><span class="sxs-lookup"><span data-stu-id="b4d78-125">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 <span data-ttu-id="b4d78-126">No segmento de código anterior:</span><span class="sxs-lookup"><span data-stu-id="b4d78-126">In the previous code segment:</span></span>  
  
- <span data-ttu-id="b4d78-127">O namespace `N1` é um membro do namespace global.</span><span class="sxs-lookup"><span data-stu-id="b4d78-127">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="b4d78-128">Seu nome totalmente qualificado é `N1`.</span><span class="sxs-lookup"><span data-stu-id="b4d78-128">Its fully qualified name is `N1`.</span></span>  
  
- <span data-ttu-id="b4d78-129">O namespace `N2` é um membro de `N1`.</span><span class="sxs-lookup"><span data-stu-id="b4d78-129">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="b4d78-130">Seu nome totalmente qualificado é `N1.N2`.</span><span class="sxs-lookup"><span data-stu-id="b4d78-130">Its fully qualified name is `N1.N2`.</span></span>  
  
- <span data-ttu-id="b4d78-131">A classe `C1` é um membro de `N1`.</span><span class="sxs-lookup"><span data-stu-id="b4d78-131">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="b4d78-132">Seu nome totalmente qualificado é `N1.C1`.</span><span class="sxs-lookup"><span data-stu-id="b4d78-132">Its fully qualified name is `N1.C1`.</span></span>  
  
- <span data-ttu-id="b4d78-133">O nome de classe `C2` é usado duas vezes nesse código.</span><span class="sxs-lookup"><span data-stu-id="b4d78-133">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="b4d78-134">No entanto, os nomes totalmente qualificados são exclusivos.</span><span class="sxs-lookup"><span data-stu-id="b4d78-134">However, the fully qualified names are unique.</span></span> <span data-ttu-id="b4d78-135">A primeira instância da `C2` é declarada dentro de `C1`, portanto, seu nome totalmente qualificado é: `N1.C1.C2`.</span><span class="sxs-lookup"><span data-stu-id="b4d78-135">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="b4d78-136">A segunda instância da `C2` é declarada dentro de um namespace `N2`, portanto, seu nome totalmente qualificado é: `N1.N2.C2`.</span><span class="sxs-lookup"><span data-stu-id="b4d78-136">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="b4d78-137">Usando o segmento de código anterior, você pode adicionar um novo membro de classe `C3` ao namespace `N1.N2`, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b4d78-137">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 <span data-ttu-id="b4d78-138">Em geral, use `::` para fazer referência a um alias de namespace ou `global::` para referenciar o namespace global e `.` para qualificar os tipos ou membros.</span><span class="sxs-lookup"><span data-stu-id="b4d78-138">In general, use `::` to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="b4d78-139">É um erro usar `::` com um alias que faz referência a um tipo em vez de um namespace.</span><span class="sxs-lookup"><span data-stu-id="b4d78-139">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="b4d78-140">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="b4d78-140">For example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 <span data-ttu-id="b4d78-141">Lembre-se que a palavra `global` não é um alias predefinido, portanto, `global.X` não tem qualquer significado especial.</span><span class="sxs-lookup"><span data-stu-id="b4d78-141">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="b4d78-142">Ela só adquire um significado especial quando é usada com `::`.</span><span class="sxs-lookup"><span data-stu-id="b4d78-142">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="b4d78-143">O aviso do compilador CS0440 será gerado se você definir um alias chamado global porque `global::` sempre faz referência ao namespace global e não a um alias.</span><span class="sxs-lookup"><span data-stu-id="b4d78-143">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="b4d78-144">Por exemplo, a linha a seguir gera o aviso:</span><span class="sxs-lookup"><span data-stu-id="b4d78-144">For example, the following line generates the warning:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 <span data-ttu-id="b4d78-145">Usar `::` com aliases é uma boa ideia e protege contra a introdução inesperada de tipos adicionais.</span><span class="sxs-lookup"><span data-stu-id="b4d78-145">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="b4d78-146">Considere este exemplo:</span><span class="sxs-lookup"><span data-stu-id="b4d78-146">For example, consider this example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 <span data-ttu-id="b4d78-147">Isso funciona, mas se um tipo nomeado `Alias` fosse subsequentemente introduzido, `Alias.` se associaria a esse tipo.</span><span class="sxs-lookup"><span data-stu-id="b4d78-147">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="b4d78-148">O uso de `Alias::Exception` garante que `Alias` seja tratado como um alias de namespace e não seja confundido com um tipo.</span><span class="sxs-lookup"><span data-stu-id="b4d78-148">Using `Alias::Exception` ensures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  
  
 <span data-ttu-id="b4d78-149">Confira o tópico [Como usar o alias de namespace global](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) para obter mais informações sobre o alias `global`.</span><span class="sxs-lookup"><span data-stu-id="b4d78-149">See the topic [How to: Use the Global Namespace Alias](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) for more information regarding the `global` alias.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4d78-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4d78-150">See also</span></span>

- [<span data-ttu-id="b4d78-151">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="b4d78-151">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="b4d78-152">Namespaces</span><span class="sxs-lookup"><span data-stu-id="b4d78-152">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
- [<span data-ttu-id="b4d78-153">Operador .</span><span class="sxs-lookup"><span data-stu-id="b4d78-153">. operator</span></span>](../../../csharp/language-reference/operators/member-access-operators.md#member-access-operator-)
- [<span data-ttu-id="b4d78-154">Operador ::</span><span class="sxs-lookup"><span data-stu-id="b4d78-154">:: operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="b4d78-155">Alias extern</span><span class="sxs-lookup"><span data-stu-id="b4d78-155">extern alias</span></span>](../../../csharp/language-reference/keywords/extern-alias.md)

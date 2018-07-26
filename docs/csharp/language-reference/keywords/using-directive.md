---
title: Diretiva using (Referência de C#)
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: 180c038987e7de6b39a8eae0e86871eea41a40bb
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960034"
---
# <a name="using-directive-c-reference"></a><span data-ttu-id="b19de-102">Diretiva using (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="b19de-102">using Directive (C# Reference)</span></span>
<span data-ttu-id="b19de-103">A diretiva `using` tem três usos:</span><span class="sxs-lookup"><span data-stu-id="b19de-103">The `using` directive has three uses:</span></span>  
  
-   <span data-ttu-id="b19de-104">Para permitir o uso de tipos em um namespace para que você não precise qualificar o uso de um tipo nesse namespace:</span><span class="sxs-lookup"><span data-stu-id="b19de-104">To allow the use of types in a namespace so that you do not have to qualify the use of a type in that namespace:</span></span>  
  
    ```csharp  
    using System.Text;  
    ```  
  
-   <span data-ttu-id="b19de-105">Para permitir que você acesse membros estáticos de um tipo sem precisar qualificar o acesso com o nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="b19de-105">To allow you to access static members of a type without having to qualify the access with the type name.</span></span> 
  
    ```csharp  
    using static System.Math;  
    ```  
     
    <span data-ttu-id="b19de-106">Para obter mais informações, consulte a [diretiva using static](using-static.md).</span><span class="sxs-lookup"><span data-stu-id="b19de-106">For more information, see the [using static directive](using-static.md).</span></span>

-   <span data-ttu-id="b19de-107">Para criar um alias para um namespace ou um tipo.</span><span class="sxs-lookup"><span data-stu-id="b19de-107">To create an alias for a namespace or a type.</span></span> <span data-ttu-id="b19de-108">Isso é chamado de uma *diretiva alias de using*.</span><span class="sxs-lookup"><span data-stu-id="b19de-108">This is called a *using alias directive*.</span></span>  
  
    ```csharp  
    using Project = PC.MyCompany.Project;  
    ```  
  
 <span data-ttu-id="b19de-109">A palavra-chave `using` também é usada para criar *instruções using*, o que ajuda a garantir que objetos <xref:System.IDisposable>, tais como arquivos e fontes, sejam tratados corretamente.</span><span class="sxs-lookup"><span data-stu-id="b19de-109">The `using` keyword is also used to create *using statements*, which help ensure that <xref:System.IDisposable> objects such as files and fonts are handled correctly.</span></span> <span data-ttu-id="b19de-110">Consulte a [Instrução using](../../../csharp/language-reference/keywords/using-statement.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="b19de-110">See [using Statement](../../../csharp/language-reference/keywords/using-statement.md) for more information.</span></span>  
  
## <a name="using-static-type"></a><span data-ttu-id="b19de-111">Tipo using static</span><span class="sxs-lookup"><span data-stu-id="b19de-111">Using Static Type</span></span>  
 <span data-ttu-id="b19de-112">Você pode acessar os membros estáticos de um tipo sem precisar qualificar o acesso com o nome do tipo:</span><span class="sxs-lookup"><span data-stu-id="b19de-112">You can access static members of a type without having to qualify the access with the type name:</span></span>  
  
```csharp  
using static System.Console;   
using static System.Math;  
class Program   
{   
    static void Main()   
    {   
        WriteLine(Sqrt(3*3 + 4*4));   
    }   
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="b19de-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="b19de-113">Remarks</span></span>  
 <span data-ttu-id="b19de-114">O escopo de uma diretiva `using` é limitado ao arquivo em que ele aparece.</span><span class="sxs-lookup"><span data-stu-id="b19de-114">The scope of a `using` directive is limited to the file in which it appears.</span></span>  
  
 <span data-ttu-id="b19de-115">Crie um alias `using` para tornar mais fácil a qualificação de um identificador para um namespace ou tipo.</span><span class="sxs-lookup"><span data-stu-id="b19de-115">Create a `using` alias to make it easier to qualify an identifier to a namespace or type.</span></span> <span data-ttu-id="b19de-116">O lado direito de uma diretiva alias de using deve sempre ser um tipo totalmente qualificado, independentemente das diretivas using que vêm antes dele.</span><span class="sxs-lookup"><span data-stu-id="b19de-116">The right side of a using alias directive must always be a fully-qualified type regardless of the using directives that come before it.</span></span>  
  
 <span data-ttu-id="b19de-117">Crie uma diretiva `using` para usar os tipos em um namespace sem precisar especificar o namespace.</span><span class="sxs-lookup"><span data-stu-id="b19de-117">Create a `using` directive to use the types in a namespace without having to specify the namespace.</span></span> <span data-ttu-id="b19de-118">Uma diretiva `using` não fornece acesso a nenhum namespace aninhado no namespace especificado.</span><span class="sxs-lookup"><span data-stu-id="b19de-118">A `using` directive does not give you access to any namespaces that are nested in the namespace you specify.</span></span>  
  
 <span data-ttu-id="b19de-119">Os namespaces vêm em duas categorias: definidos pelo usuário e definidos pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="b19de-119">Namespaces come in two categories: user-defined and system-defined.</span></span> <span data-ttu-id="b19de-120">Os namespaces definidos pelo usuário são namespaces definidos em seu código.</span><span class="sxs-lookup"><span data-stu-id="b19de-120">User-defined namespaces are namespaces defined in your code.</span></span> <span data-ttu-id="b19de-121">Para obter uma lista dos namespaces definidos pelo sistema, confira [Visão geral da biblioteca de classes .NET Framework](../../../standard/class-library-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b19de-121">For a list of the system-defined namespaces, see [.NET Framework Class Library Overview](../../../standard/class-library-overview.md).</span></span>  
  
 <span data-ttu-id="b19de-122">Para obter exemplos sobre como referenciar métodos em outros assemblies, confira [Criar e usar assemblies usando a linha de comando](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="b19de-122">For examples on referencing methods in other assemblies, see [Create and Use Assemblies Using the Command Line](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="b19de-123">Exemplo 1</span><span class="sxs-lookup"><span data-stu-id="b19de-123">Example 1</span></span>  
  
 <span data-ttu-id="b19de-124">O exemplo a seguir mostra como definir e usar um alias de `using` para um namespace:</span><span class="sxs-lookup"><span data-stu-id="b19de-124">The following example shows how to define and use a `using` alias for a namespace:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_1.cs)]  
  
 <span data-ttu-id="b19de-125">Uma diretiva alias de using não pode ter um tipo genérico aberto no lado direito.</span><span class="sxs-lookup"><span data-stu-id="b19de-125">A using alias directive cannot have an open generic type on the right hand side.</span></span> <span data-ttu-id="b19de-126">Por exemplo, você não pode criar um alias de using para uma List\<T>, mas pode criar um para uma List\<int>.</span><span class="sxs-lookup"><span data-stu-id="b19de-126">For example, you cannot create a using alias for a List\<T>, but you can create one for a List\<int>.</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="b19de-127">Exemplo 2</span><span class="sxs-lookup"><span data-stu-id="b19de-127">Example 2</span></span>  
  
 <span data-ttu-id="b19de-128">O exemplo a seguir mostra como definir uma diretiva `using` e um alias `using` para uma classe:</span><span class="sxs-lookup"><span data-stu-id="b19de-128">The following example shows how to define a `using` directive and a `using` alias for a class:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="b19de-129">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="b19de-129">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b19de-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b19de-130">See Also</span></span>  
 [<span data-ttu-id="b19de-131">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="b19de-131">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b19de-132">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="b19de-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b19de-133">Usando namespaces</span><span class="sxs-lookup"><span data-stu-id="b19de-133">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
 [<span data-ttu-id="b19de-134">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="b19de-134">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="b19de-135">Palavras-chave de namespace</span><span class="sxs-lookup"><span data-stu-id="b19de-135">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="b19de-136">Namespaces</span><span class="sxs-lookup"><span data-stu-id="b19de-136">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
 [<span data-ttu-id="b19de-137">Instrução using</span><span class="sxs-lookup"><span data-stu-id="b19de-137">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)

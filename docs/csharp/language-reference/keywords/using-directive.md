---
title: Diretiva using – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: d6e3667861c2b1ac9a84ca7b4e2cabb5784d793d
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970052"
---
# <a name="using-directive-c-reference"></a><span data-ttu-id="dd194-102">Diretiva using (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="dd194-102">using directive (C# Reference)</span></span>

<span data-ttu-id="dd194-103">A diretiva `using` tem três usos:</span><span class="sxs-lookup"><span data-stu-id="dd194-103">The `using` directive has three uses:</span></span>

- <span data-ttu-id="dd194-104">Para permitir o uso de tipos em um namespace para que você não precise qualificar o uso de um tipo nesse namespace:</span><span class="sxs-lookup"><span data-stu-id="dd194-104">To allow the use of types in a namespace so that you do not have to qualify the use of a type in that namespace:</span></span>

    ```csharp
    using System.Text;
    ```

- <span data-ttu-id="dd194-105">Para permitir que você acesse membros estáticos e tipos aninhados de um tipo sem precisar qualificar o acesso com o nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="dd194-105">To allow you to access static members and nested types of a type without having to qualify the access with the type name.</span></span>

    ```csharp
    using static System.Math;
    ```

    <span data-ttu-id="dd194-106">Para obter mais informações, consulte a [diretiva using static](using-static.md).</span><span class="sxs-lookup"><span data-stu-id="dd194-106">For more information, see the [using static directive](using-static.md).</span></span>

- <span data-ttu-id="dd194-107">Para criar um alias para um namespace ou um tipo.</span><span class="sxs-lookup"><span data-stu-id="dd194-107">To create an alias for a namespace or a type.</span></span> <span data-ttu-id="dd194-108">Isso é chamado de uma *diretiva alias de using*.</span><span class="sxs-lookup"><span data-stu-id="dd194-108">This is called a *using alias directive*.</span></span>

    ```csharp
    using Project = PC.MyCompany.Project;
    ```

<span data-ttu-id="dd194-109">A palavra-chave `using` também é usada para criar *instruções using*, o que ajuda a garantir que objetos <xref:System.IDisposable>, tais como arquivos e fontes, sejam tratados corretamente.</span><span class="sxs-lookup"><span data-stu-id="dd194-109">The `using` keyword is also used to create *using statements*, which help ensure that <xref:System.IDisposable> objects such as files and fonts are handled correctly.</span></span> <span data-ttu-id="dd194-110">Consulte a [Instrução using](using-statement.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="dd194-110">See [using Statement](using-statement.md) for more information.</span></span>

## <a name="using-static-type"></a><span data-ttu-id="dd194-111">Tipo using static</span><span class="sxs-lookup"><span data-stu-id="dd194-111">Using static type</span></span>

<span data-ttu-id="dd194-112">Você pode acessar os membros estáticos de um tipo sem precisar qualificar o acesso com o nome do tipo:</span><span class="sxs-lookup"><span data-stu-id="dd194-112">You can access static members of a type without having to qualify the access with the type name:</span></span>

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

## <a name="remarks"></a><span data-ttu-id="dd194-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="dd194-113">Remarks</span></span>

<span data-ttu-id="dd194-114">O escopo de uma diretiva `using` é limitado ao arquivo em que ele aparece.</span><span class="sxs-lookup"><span data-stu-id="dd194-114">The scope of a `using` directive is limited to the file in which it appears.</span></span>

<span data-ttu-id="dd194-115">A diretiva `using` pode aparecer:</span><span class="sxs-lookup"><span data-stu-id="dd194-115">The `using` directive can appear:</span></span>

- <span data-ttu-id="dd194-116">No início de um arquivo de código-fonte, antes de quaisquer definições de namespace ou tipo.</span><span class="sxs-lookup"><span data-stu-id="dd194-116">At the beginning of a source code file, before any namespace or type definitions.</span></span>
- <span data-ttu-id="dd194-117">Em qualquer namespace, mas antes de qualquer namespace ou tipos declarados neste namespace.</span><span class="sxs-lookup"><span data-stu-id="dd194-117">In any namespace, but before any namespace or types declared in this namespace.</span></span>

<span data-ttu-id="dd194-118">Caso contrário, serão gerados erros do compilador [CS1529](../../misc/cs1529.md).</span><span class="sxs-lookup"><span data-stu-id="dd194-118">Otherwise, compiler error [CS1529](../../misc/cs1529.md) is generated.</span></span>

<span data-ttu-id="dd194-119">Crie uma diretiva de alias `using` para tornar mais fácil a qualificação de um identificador para um namespace ou tipo.</span><span class="sxs-lookup"><span data-stu-id="dd194-119">Create a `using` alias directive to make it easier to qualify an identifier to a namespace or type.</span></span> <span data-ttu-id="dd194-120">Em qualquer diretiva `using`, o namespace totalmente qualificado ou o tipo deve ser usado independentemente das diretivas `using` que vêm antes.</span><span class="sxs-lookup"><span data-stu-id="dd194-120">In any `using` directive, the fully-qualified namespace or type must be used regardless of the `using` directives that come before it.</span></span> <span data-ttu-id="dd194-121">Nenhum alias `using` pode ser usado na declaração de uma diretiva `using`.</span><span class="sxs-lookup"><span data-stu-id="dd194-121">No `using` alias can be used in the declaration of a `using` directive.</span></span> <span data-ttu-id="dd194-122">Por exemplo, o código a seguir gera um erro de compilador:</span><span class="sxs-lookup"><span data-stu-id="dd194-122">For example, the following generates a compiler error:</span></span>

```csharp
using s = System.Text;
using s.RegularExpressions;
```

<span data-ttu-id="dd194-123">Crie uma diretiva `using` para usar os tipos em um namespace sem precisar especificar o namespace.</span><span class="sxs-lookup"><span data-stu-id="dd194-123">Create a `using` directive to use the types in a namespace without having to specify the namespace.</span></span> <span data-ttu-id="dd194-124">Uma diretiva `using` não fornece acesso a nenhum namespace aninhado no namespace especificado.</span><span class="sxs-lookup"><span data-stu-id="dd194-124">A `using` directive does not give you access to any namespaces that are nested in the namespace you specify.</span></span>

<span data-ttu-id="dd194-125">Os namespaces vêm em duas categorias: definidos pelo usuário e definidos pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="dd194-125">Namespaces come in two categories: user-defined and system-defined.</span></span> <span data-ttu-id="dd194-126">Os namespaces definidos pelo usuário são namespaces definidos em seu código.</span><span class="sxs-lookup"><span data-stu-id="dd194-126">User-defined namespaces are namespaces defined in your code.</span></span> <span data-ttu-id="dd194-127">Para obter uma lista dos namespaces definidos pelo sistema, consulte [Navegador de API do .NET](../../../../api/index.md).</span><span class="sxs-lookup"><span data-stu-id="dd194-127">For a list of the system-defined namespaces, see [.NET API Browser](../../../../api/index.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="dd194-128">Exemplo 1</span><span class="sxs-lookup"><span data-stu-id="dd194-128">Example 1</span></span>

<span data-ttu-id="dd194-129">O exemplo a seguir mostra como definir e usar um alias de `using` para um namespace:</span><span class="sxs-lookup"><span data-stu-id="dd194-129">The following example shows how to define and use a `using` alias for a namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#8)]

<span data-ttu-id="dd194-130">Uma diretiva alias de using não pode ter um tipo genérico aberto no lado direito.</span><span class="sxs-lookup"><span data-stu-id="dd194-130">A using alias directive cannot have an open generic type on the right hand side.</span></span> <span data-ttu-id="dd194-131">Por exemplo, você não pode criar um alias de using para um `List<T>`, mas pode criar um para um `List<int>`.</span><span class="sxs-lookup"><span data-stu-id="dd194-131">For example, you cannot create a using alias for a `List<T>`, but you can create one for a `List<int>`.</span></span>

## <a name="example-2"></a><span data-ttu-id="dd194-132">Exemplo 2</span><span class="sxs-lookup"><span data-stu-id="dd194-132">Example 2</span></span>

<span data-ttu-id="dd194-133">O exemplo a seguir mostra como definir uma diretiva `using` e um alias `using` para uma classe:</span><span class="sxs-lookup"><span data-stu-id="dd194-133">The following example shows how to define a `using` directive and a `using` alias for a class:</span></span>

[!code-csharp[csrefKeywordsNamespace#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="dd194-134">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="dd194-134">C# language specification</span></span>

<span data-ttu-id="dd194-135">Para obter mais informações, consulte [Diretivas using](~/_csharplang/spec/namespaces.md#using-directives) na [Especificação da Linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="dd194-135">For more information, see [Using directives](~/_csharplang/spec/namespaces.md#using-directives) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="dd194-136">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="dd194-136">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="dd194-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd194-137">See also</span></span>

- [<span data-ttu-id="dd194-138">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="dd194-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dd194-139">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="dd194-139">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="dd194-140">Usando namespaces</span><span class="sxs-lookup"><span data-stu-id="dd194-140">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="dd194-141">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="dd194-141">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="dd194-142">Namespaces</span><span class="sxs-lookup"><span data-stu-id="dd194-142">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
- [<span data-ttu-id="dd194-143">Instrução using</span><span class="sxs-lookup"><span data-stu-id="dd194-143">using Statement</span></span>](using-statement.md)

---
title: Diretiva using static – Referência de C#
ms.custom: seodec18
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 29610a77eadf587162731b5bddbcc4bbe7fa0714
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610522"
---
# <a name="using-static-directive-c-reference"></a><span data-ttu-id="a7dd7-102">Diretiva using static (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="a7dd7-102">using static directive (C# Reference)</span></span>

<span data-ttu-id="a7dd7-103">A diretiva `using static` designa um tipo cujos membros estáticos e tipos aninhados você pode acessar sem especificar um nome de tipo.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-103">The `using static` directive designates a type whose static members and nested types you can access without specifying a type name.</span></span> <span data-ttu-id="a7dd7-104">A sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="a7dd7-104">Its syntax is:</span></span>

```csharp
using static <fully-qualified-type-name>;
```

<span data-ttu-id="a7dd7-105">em que *fully-qualified-type-name* é o nome do tipo cujos membros estáticos e tipos aninhados podem ser referenciados sem especificar um nome de tipo.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-105">where *fully-qualified-type-name* is the name of the type whose static members and nested types can be referenced without specifying a type name.</span></span> <span data-ttu-id="a7dd7-106">Se você não fornecer um nome de tipo totalmente qualificado (o nome do namespace completo juntamente com o nome de tipo), o C# gerará o erro de compilador [CS0246](../compiler-messages/cs0246.md): "O nome do tipo ou do namespace 'tipo/namespace' não pode ser encontrado (está faltando uma diretiva using ou uma referência de assembly?)".</span><span class="sxs-lookup"><span data-stu-id="a7dd7-106">If you do not provide a fully qualified type name (the full namespace name along with the type name), C# generates compiler error [CS0246](../compiler-messages/cs0246.md): "The type or namespace name 'type/namespace' could not be found (are you missing a using directive or an assembly reference?)".</span></span>

<span data-ttu-id="a7dd7-107">A diretiva `using static` aplica-se a qualquer tipo que tenha membros estático (ou tipos aninhados), mesmo que ele também tenha membros de instância.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-107">The `using static` directive applies to any type that has static members (or nested types), even if it also has instance members.</span></span> <span data-ttu-id="a7dd7-108">No entanto, os membros da instância podem ser invocados apenas por meio de instância de tipo.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-108">However, instance members can only be invoked through the type instance.</span></span>

<span data-ttu-id="a7dd7-109">A diretiva `using static` foi introduzida no C# 6.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-109">The `using static` directive was introduced in C# 6.</span></span>

## <a name="remarks"></a><span data-ttu-id="a7dd7-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="a7dd7-110">Remarks</span></span>

<span data-ttu-id="a7dd7-111">Normalmente, quando você chamar um membro estático, fornece o nome do tipo juntamente com o nome do membro.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-111">Ordinarily, when you call a static member, you provide the type name along with the member name.</span></span> <span data-ttu-id="a7dd7-112">Inserir repetidamente o mesmo nome de tipo para invocar os membros do tipo pode resultar em código obscuro detalhado.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-112">Repeatedly entering the same type name to invoke members of the type can result in verbose, obscure code.</span></span> <span data-ttu-id="a7dd7-113">Por exemplo, a seguinte definição de uma classe `Circle` faz referência a um número de membros da classe <xref:System.Math>.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-113">For example, the following definition of a `Circle` class references a number of members of the <xref:System.Math> class.</span></span>

[!code-csharp[using-static#1](~/samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

<span data-ttu-id="a7dd7-114">Eliminando a necessidade de fazer referência explícita à classe <xref:System.Math> sempre que um membro é referenciado, a diretiva `using static` produz um código muito mais limpo:</span><span class="sxs-lookup"><span data-stu-id="a7dd7-114">By eliminating the need to explicitly reference the <xref:System.Math> class each time a member is referenced, the `using static` directive produces much cleaner code:</span></span>

[!code-csharp[using-static#2](~/samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

<span data-ttu-id="a7dd7-115">`using static` importa somente os membros estáticos acessíveis e os tipos aninhados declarados no tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-115">`using static` imports only accessible static members and nested types declared in the specified type.</span></span>  <span data-ttu-id="a7dd7-116">Os membros herdados não são importados.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-116">Inherited members are not imported.</span></span>  <span data-ttu-id="a7dd7-117">Você pode importar de qualquer tipo nomeado com uma diretiva using static, incluindo módulos do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-117">You can import from any named type with a using static directive, including Visual Basic modules.</span></span>  <span data-ttu-id="a7dd7-118">Se funções de nível superior do F# aparecerem nos metadados como membros estáticos de um tipo nomeado cujo nome é um identificador válido do C#, as funções do F# poderão ser importadas.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-118">If F# top-level functions appear in metadata as static members of a named type whose name is a valid C# identifier, then the F# functions can be imported.</span></span>

 <span data-ttu-id="a7dd7-119">`using static` torna os métodos de extensão declarados no tipo especificado disponível para pesquisa de método de extensão.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-119">`using static` makes extension methods declared in the specified type available for extension method lookup.</span></span>  <span data-ttu-id="a7dd7-120">No entanto, os nomes dos métodos de extensão não são importados no escopo para a referência não qualificada no código.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-120">However, the names of the extension methods are not imported into scope for unqualified reference in code.</span></span>

 <span data-ttu-id="a7dd7-121">Métodos com o mesmo nome importados de diferentes tipos por diferentes diretivas `using static` na mesma unidade de compilação ou namespace formam um grupo de métodos.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-121">Methods with the same name imported from different types by different `using static` directives in the same compilation unit or namespace form a method group.</span></span>  <span data-ttu-id="a7dd7-122">A resolução de sobrecarga nesses grupos de métodos segue as regras normais de C#.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-122">Overload resolution within these method groups follows normal C# rules.</span></span>

## <a name="example"></a><span data-ttu-id="a7dd7-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a7dd7-123">Example</span></span>

<span data-ttu-id="a7dd7-124">O exemplo a seguir usa a diretiva `using static` para tornar os membros estáticos das classes <xref:System.Console>, <xref:System.Math> e <xref:System.String> disponíveis sem a necessidade de especificar seu nome de tipo.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-124">The following example uses the `using static` directive to make the static members of the <xref:System.Console>, <xref:System.Math>, and <xref:System.String> classes available without having to specify their type name.</span></span>

[!code-csharp[using-static#3](~/samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

<span data-ttu-id="a7dd7-125">No exemplo, a diretiva `using static` também poderia ter sido aplicada ao tipo <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-125">In the example, the `using static` directive could also have been applied to the <xref:System.Double> type.</span></span> <span data-ttu-id="a7dd7-126">Isso tornaria possível chamar o método <xref:System.Double.TryParse(System.String,System.Double@)> sem especificar um nome de tipo.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-126">This would have made it possible to call the <xref:System.Double.TryParse(System.String,System.Double@)> method without specifying a type name.</span></span> <span data-ttu-id="a7dd7-127">No entanto, isso cria código menos legível, uma vez que se torna necessário verificar as instruções `using static` para determinar qual método `TryParse` do tipo numérico é chamado.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-127">However, this creates less readable code, since it becomes necessary to check the `using static` statements to determine which numeric type's `TryParse` method is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7dd7-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7dd7-128">See also</span></span>

- [<span data-ttu-id="a7dd7-129">Diretiva using</span><span class="sxs-lookup"><span data-stu-id="a7dd7-129">using directive</span></span>](using-directive.md)
- [<span data-ttu-id="a7dd7-130">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="a7dd7-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a7dd7-131">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="a7dd7-131">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a7dd7-132">Usando namespaces</span><span class="sxs-lookup"><span data-stu-id="a7dd7-132">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="a7dd7-133">Palavras-chave de namespace</span><span class="sxs-lookup"><span data-stu-id="a7dd7-133">Namespace Keywords</span></span>](namespace-keywords.md)
- [<span data-ttu-id="a7dd7-134">Namespaces</span><span class="sxs-lookup"><span data-stu-id="a7dd7-134">Namespaces</span></span>](../../programming-guide/namespaces/index.md)

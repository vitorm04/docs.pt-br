---
title: Modificador new (Referência de C#)
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: b66cfacc2203e0e529c19b5c566abad6c676f149
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273962"
---
# <a name="new-modifier-c-reference"></a><span data-ttu-id="23a66-102">Modificador new (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="23a66-102">new Modifier (C# Reference)</span></span>
<span data-ttu-id="23a66-103">Quando usada como um modificador de declaração, a palavra-chave `new` oculta explicitamente um membro herdado de uma classe base.</span><span class="sxs-lookup"><span data-stu-id="23a66-103">When used as a declaration modifier, the `new` keyword explicitly hides a member that is inherited from a base class.</span></span> <span data-ttu-id="23a66-104">Quando você oculta um membro herdado, a versão derivada do membro substitui a versão da classe base.</span><span class="sxs-lookup"><span data-stu-id="23a66-104">When you hide an inherited member, the derived version of the member replaces the base class version.</span></span> <span data-ttu-id="23a66-105">Embora possa ocultar membros sem usar o modificador `new`, você obtém um aviso do compilador.</span><span class="sxs-lookup"><span data-stu-id="23a66-105">Although you can hide members without using the `new` modifier, you get a compiler warning.</span></span> <span data-ttu-id="23a66-106">Se você usar `new` para ocultar explicitamente um membro, ele suprime o aviso.</span><span class="sxs-lookup"><span data-stu-id="23a66-106">If you use `new` to explicitly hide a member, it suppresses this warning.</span></span>  
  
 <span data-ttu-id="23a66-107">Para ocultar um membro herdado, declare-o na classe derivada usando o mesmo nome de membro e modifique-o com a palavra-chave `new`.</span><span class="sxs-lookup"><span data-stu-id="23a66-107">To hide an inherited member, declare it in the derived class by using the same member name, and modify it with the `new` keyword.</span></span> <span data-ttu-id="23a66-108">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="23a66-108">For example:</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_1.cs)]  
  
 <span data-ttu-id="23a66-109">Neste exemplo, `BaseC.Invoke` é ocultado por `DerivedC.Invoke`.</span><span class="sxs-lookup"><span data-stu-id="23a66-109">In this example, `BaseC.Invoke` is hidden by `DerivedC.Invoke`.</span></span> <span data-ttu-id="23a66-110">O campo `x` não é afetado porque não é ocultado por um nome semelhante.</span><span class="sxs-lookup"><span data-stu-id="23a66-110">The field `x` is not affected because it is not hidden by a similar name.</span></span>  
  
 <span data-ttu-id="23a66-111">A ocultação de nome por meio da herança assume uma das seguintes formas:</span><span class="sxs-lookup"><span data-stu-id="23a66-111">Name hiding through inheritance takes one of the following forms:</span></span>  
  
-   <span data-ttu-id="23a66-112">Normalmente, uma constante, campo, propriedade ou tipo que é apresentado em uma classe ou struct oculta todos os membros da classe base que compartilham seu nome.</span><span class="sxs-lookup"><span data-stu-id="23a66-112">Generally, a constant, field, property, or type that is introduced in a class or struct hides all base class members that share its name.</span></span>  <span data-ttu-id="23a66-113">Há casos especiais.</span><span class="sxs-lookup"><span data-stu-id="23a66-113">There are special cases.</span></span>  <span data-ttu-id="23a66-114">Por exemplo, se você declarar que um novo campo com o nome `N` tem um tipo que não pode ser invocado e um tipo base declarar que `N` é um método, o novo campo não ocultará a declaração base na sintaxe de invocação.</span><span class="sxs-lookup"><span data-stu-id="23a66-114">For example, if you declare a new field with name `N` to have a type that is not invocable, and a base type declares `N` to be a method, the new field does not hide the base declaration in invocation syntax.</span></span>  <span data-ttu-id="23a66-115">Consulte a [Especificação da linguagem C# 5.0](https://www.microsoft.com/download/details.aspx?id=7029) para obter detalhes (consulte a seção "Pesquisa de membro" na seção "Expressões").</span><span class="sxs-lookup"><span data-stu-id="23a66-115">See the [C# 5.0 language specification](https://www.microsoft.com/download/details.aspx?id=7029) for details (see section "Member Lookup" in section "Expressions").</span></span>  
  
-   <span data-ttu-id="23a66-116">Um método introduzido em uma classe ou struct oculta propriedades, campos e tipos que compartilham esse nome na classe base.</span><span class="sxs-lookup"><span data-stu-id="23a66-116">A method introduced in a class or struct hides properties, fields, and types that share that name in the base class.</span></span> <span data-ttu-id="23a66-117">Ele também oculta todos os métodos da classe base que têm a mesma assinatura.</span><span class="sxs-lookup"><span data-stu-id="23a66-117">It also hides all base class methods that have the same signature.</span></span>  
  
-   <span data-ttu-id="23a66-118">Um indexador introduzido em uma classe ou struct oculta todos os indexadores de classe base que têm a mesma assinatura.</span><span class="sxs-lookup"><span data-stu-id="23a66-118">An indexer introduced in a class or struct hides all base class indexers that have the same signature.</span></span>  
  
 <span data-ttu-id="23a66-119">É um erro usar `new` e [override](../../../csharp/language-reference/keywords/override.md) no mesmo membro, porque os dois modificadores têm significados mutuamente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="23a66-119">It is an error to use both `new` and [override](../../../csharp/language-reference/keywords/override.md) on the same member, because the two modifiers have mutually exclusive meanings.</span></span> <span data-ttu-id="23a66-120">O modificador `new` cria um novo membro com o mesmo nome e faz com que o membro original seja ocultado.</span><span class="sxs-lookup"><span data-stu-id="23a66-120">The `new` modifier creates a new member with the same name and causes the original member to become hidden.</span></span> <span data-ttu-id="23a66-121">O modificador `override` estende a implementação de um membro herdado.</span><span class="sxs-lookup"><span data-stu-id="23a66-121">The `override` modifier extends the implementation for an inherited member.</span></span>  
  
 <span data-ttu-id="23a66-122">Usar o modificador `new` em uma declaração que não oculta um membro herdado gera um aviso.</span><span class="sxs-lookup"><span data-stu-id="23a66-122">Using the `new` modifier in a declaration that does not hide an inherited member generates a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23a66-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="23a66-123">Example</span></span>  
 <span data-ttu-id="23a66-124">Neste exemplo, uma classe base, `BaseC` e uma classe derivada, `DerivedC`, usam o mesmo nome do campo `x`, que oculta o valor do campo herdado.</span><span class="sxs-lookup"><span data-stu-id="23a66-124">In this example, a base class, `BaseC`, and a derived class, `DerivedC`, use the same field name `x`, which hides the value of the inherited field.</span></span> <span data-ttu-id="23a66-125">O exemplo demonstra o uso do modificador `new`.</span><span class="sxs-lookup"><span data-stu-id="23a66-125">The example demonstrates the use of the `new` modifier.</span></span> <span data-ttu-id="23a66-126">Ele também demonstra como acessar os membros ocultos da classe base usando seus nomes totalmente qualificados.</span><span class="sxs-lookup"><span data-stu-id="23a66-126">It also demonstrates how to access the hidden members of the base class by using their fully qualified names.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="23a66-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="23a66-127">Example</span></span>  
 <span data-ttu-id="23a66-128">Neste exemplo, uma classe aninhada oculta uma classe que tem o mesmo nome na classe base.</span><span class="sxs-lookup"><span data-stu-id="23a66-128">In this example, a nested class hides a class that has the same name in the base class.</span></span> <span data-ttu-id="23a66-129">O exemplo demonstra como usar o modificador `new` para eliminar a mensagem de aviso e como acessar os membros da classe oculta usando seus nomes totalmente qualificados.</span><span class="sxs-lookup"><span data-stu-id="23a66-129">The example demonstrates how to use the `new` modifier to eliminate the warning message and how to access the hidden class members by using their fully qualified names.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_3.cs)]  
  
 <span data-ttu-id="23a66-130">Se você remover o modificador `new`, o programa ainda será compilado e executado, mas você receberá o seguinte aviso:</span><span class="sxs-lookup"><span data-stu-id="23a66-130">If you remove the `new` modifier, the program will still compile and run, but you will get the following warning:</span></span>  
  
```  
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="23a66-131">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="23a66-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="23a66-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23a66-132">See Also</span></span>  
 [<span data-ttu-id="23a66-133">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="23a66-133">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="23a66-134">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="23a66-134">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="23a66-135">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="23a66-135">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="23a66-136">Palavras-chave do operador</span><span class="sxs-lookup"><span data-stu-id="23a66-136">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="23a66-137">Modificadores</span><span class="sxs-lookup"><span data-stu-id="23a66-137">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="23a66-138">Controle de versão com as palavras-chave override e new</span><span class="sxs-lookup"><span data-stu-id="23a66-138">Versioning with the Override and New Keywords</span></span>](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
 [<span data-ttu-id="23a66-139">Quando usar as palavras-chave override e new</span><span class="sxs-lookup"><span data-stu-id="23a66-139">Knowing When to Use Override and New Keywords</span></span>](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)

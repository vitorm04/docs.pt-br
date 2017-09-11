---
title: "Constantes (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
caps.latest.revision: 24
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
ms.openlocfilehash: 85273420e9e0dbf4b8f24568d97be127c85d5f42
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="constants-c-programming-guide"></a><span data-ttu-id="0453a-102">Constantes (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="0453a-102">Constants (C# Programming Guide)</span></span>
<span data-ttu-id="0453a-103">As constantes são valores imutáveis que são conhecidos no tempo de compilação e não são alterados durante a vida útil do programa.</span><span class="sxs-lookup"><span data-stu-id="0453a-103">Constants are immutable values which are known at compile time and do not change for the life of the program.</span></span> <span data-ttu-id="0453a-104">Constantes são declaradas com o modificador [const](../../../csharp/language-reference/keywords/const.md).</span><span class="sxs-lookup"><span data-stu-id="0453a-104">Constants are declared with the [const](../../../csharp/language-reference/keywords/const.md) modifier.</span></span> <span data-ttu-id="0453a-105">Apenas os tipos C# internos (excluindo <xref:System.Object?displayProperty=fullName>) podem ser declarados como `const`.</span><span class="sxs-lookup"><span data-stu-id="0453a-105">Only the C# built-in types (excluding <xref:System.Object?displayProperty=fullName>) may be declared as `const`.</span></span> <span data-ttu-id="0453a-106">Para obter uma lista dos tipos internos, consulte [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="0453a-106">For a list of the built-in types, see [Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md).</span></span> <span data-ttu-id="0453a-107">Tipos definidos pelo usuário, incluindo classes, struct e matrizes, não podem ser `const`.</span><span class="sxs-lookup"><span data-stu-id="0453a-107">User-defined types, including classes, structs, and arrays, cannot be `const`.</span></span> <span data-ttu-id="0453a-108">Use o modificador [readonly](../../../csharp/language-reference/keywords/readonly.md) para criar uma classe, struct ou matriz que é inicializada uma vez em tempo de execução (por exemplo, em um construtor) e, assim, não pode ser alterada.</span><span class="sxs-lookup"><span data-stu-id="0453a-108">Use the [readonly](../../../csharp/language-reference/keywords/readonly.md) modifier to create a class, struct, or array that is initialized one time at runtime (for example in a constructor) and thereafter cannot be changed.</span></span>  
  
 <span data-ttu-id="0453a-109">O C# não dá suporte aos métodos `const`, propriedades ou eventos.</span><span class="sxs-lookup"><span data-stu-id="0453a-109">C# does not support `const` methods, properties, or events.</span></span>  
  
 <span data-ttu-id="0453a-110">O tipo de enumeração permite que você defina constantes nomeadas para tipos internos integrais (por exemplo `int`, `uint`, `long` e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="0453a-110">The enum type enables you to define named constants for integral built-in types (for example `int`, `uint`, `long`, and so on).</span></span> <span data-ttu-id="0453a-111">Para obter mais informações, consulte [enum](../../../csharp/language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="0453a-111">For more information, see [enum](../../../csharp/language-reference/keywords/enum.md).</span></span>  
  
 <span data-ttu-id="0453a-112">As constantes devem ser inicializadas conforme elas são declaradas.</span><span class="sxs-lookup"><span data-stu-id="0453a-112">Constants must be initialized as they are declared.</span></span> <span data-ttu-id="0453a-113">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="0453a-113">For example:</span></span>  
  
 <span data-ttu-id="0453a-114">[!code-cs[csProgGuideObjects#64](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="0453a-114">[!code-cs[csProgGuideObjects#64](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_1.cs)]</span></span>  
  
 <span data-ttu-id="0453a-115">Neste exemplo, a constante `months` sempre é 12 e não pode ser alterada até mesmo pela própria classe.</span><span class="sxs-lookup"><span data-stu-id="0453a-115">In this example, the constant `months` is always 12, and it cannot be changed even by the class itself.</span></span> <span data-ttu-id="0453a-116">Na verdade, quando o compilador encontra um identificador constante no código-fonte C# (por exemplo, `months`), ele substitui o valor literal diretamente no código de IL (linguagem intermediária) que ele produz.</span><span class="sxs-lookup"><span data-stu-id="0453a-116">In fact, when the compiler encounters a constant identifier in C# source code (for example, `months`), it substitutes the literal value directly into the intermediate language (IL) code that it produces.</span></span> <span data-ttu-id="0453a-117">Como não há nenhum endereço variável associado a uma constante em tempo de execução, os campos `const` não podem ser passados por referência e não podem aparecer como um l-value em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="0453a-117">Because there is no variable address associated with a constant at run time, `const` fields cannot be passed by reference and cannot appear as an l-value in an expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0453a-118">Tenha cuidado ao fazer referência a valores constantes definidos em outro código como DLLs.</span><span class="sxs-lookup"><span data-stu-id="0453a-118">Use caution when you refer to constant values defined in other code such as DLLs.</span></span> <span data-ttu-id="0453a-119">Se uma nova versão da DLL definir um novo valor para a constante, seu programa ainda conterá o valor literal antigo até que ele seja recompilado com a nova versão.</span><span class="sxs-lookup"><span data-stu-id="0453a-119">If a new version of the DLL defines a new value for the constant, your program will still hold the old literal value until it is recompiled against the new version.</span></span>  
  
 <span data-ttu-id="0453a-120">Várias constantes do mesmo tipo podem ser declaradas ao mesmo tempo, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="0453a-120">Multiple constants of the same type can be declared at the same time, for example:</span></span>  
  
 <span data-ttu-id="0453a-121">[!code-cs[csProgGuideObjects#65](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="0453a-121">[!code-cs[csProgGuideObjects#65](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_2.cs)]</span></span>  
  
 <span data-ttu-id="0453a-122">A expressão que é usada para inicializar uma constante poderá fazer referência a outra constante se ela não criar uma referência circular.</span><span class="sxs-lookup"><span data-stu-id="0453a-122">The expression that is used to initialize a constant can refer to another constant if it does not create a circular reference.</span></span> <span data-ttu-id="0453a-123">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="0453a-123">For example:</span></span>  
  
 <span data-ttu-id="0453a-124">[!code-cs[csProgGuideObjects#66](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="0453a-124">[!code-cs[csProgGuideObjects#66](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_3.cs)]</span></span>  
  
 <span data-ttu-id="0453a-125">As constantes podem ser marcadas como [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md) ou `protected internal`.</span><span class="sxs-lookup"><span data-stu-id="0453a-125">Constants can be marked as [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), or `protected internal`.</span></span> <span data-ttu-id="0453a-126">Esses modificadores de acesso definem como os usuários da classe podem acessar a constante.</span><span class="sxs-lookup"><span data-stu-id="0453a-126">These access modifiers define how users of the class can access the constant.</span></span> <span data-ttu-id="0453a-127">Para obter mais informações, consulte [Modificadores de Acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="0453a-127">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="0453a-128">As constantes são acessadas como se fossem campos [static](../../../csharp/language-reference/keywords/static.md) porque o valor da constante é o mesmo para todas as instâncias do tipo.</span><span class="sxs-lookup"><span data-stu-id="0453a-128">Constants are accessed as if they were [static](../../../csharp/language-reference/keywords/static.md) fields because the value of the constant is the same for all instances of the type.</span></span> <span data-ttu-id="0453a-129">Você não usa a palavra-chave `static` para declará-las.</span><span class="sxs-lookup"><span data-stu-id="0453a-129">You do not use the `static` keyword to declare them.</span></span> <span data-ttu-id="0453a-130">As expressões que não estão na classe que define a constante devem usar o nome de classe, um período e o nome da constante para acessar a constante.</span><span class="sxs-lookup"><span data-stu-id="0453a-130">Expressions that are not in the class that defines the constant must use the class name, a period, and the name of the constant to access the constant.</span></span> <span data-ttu-id="0453a-131">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="0453a-131">For example:</span></span>  
  
 <span data-ttu-id="0453a-132">[!code-cs[csProgGuideObjects#67](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="0453a-132">[!code-cs[csProgGuideObjects#67](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_4.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="0453a-133">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="0453a-133">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0453a-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0453a-134">See Also</span></span>  
 <span data-ttu-id="0453a-135">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="0453a-135">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="0453a-136">[Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="0453a-136">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="0453a-137">[Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md) </span><span class="sxs-lookup"><span data-stu-id="0453a-137">[Properties](../../../csharp/programming-guide/classes-and-structs/properties.md) </span></span>  
 <span data-ttu-id="0453a-138">[Tipos](../../../csharp/programming-guide/types/index.md) </span><span class="sxs-lookup"><span data-stu-id="0453a-138">[Types](../../../csharp/programming-guide/types/index.md) </span></span>  
 <span data-ttu-id="0453a-139">[readonly](../../../csharp/language-reference/keywords/readonly.md) </span><span class="sxs-lookup"><span data-stu-id="0453a-139">[readonly](../../../csharp/language-reference/keywords/readonly.md) </span></span>  
 <span data-ttu-id="0453a-140">[Immutability in C# Part One: Kinds of Immutability](http://go.microsoft.com/fwlink/?LinkId=112379) (Imutabilidade no C#, parte um: tipos de imutabilidade)</span><span class="sxs-lookup"><span data-stu-id="0453a-140">[Immutability in C# Part One: Kinds of Immutability](http://go.microsoft.com/fwlink/?LinkId=112379)</span></span>


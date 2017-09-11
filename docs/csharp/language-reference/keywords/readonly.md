---
title: "readonly (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- readonly_CSharpKeyword
- readonly
dev_langs:
- CSharp
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
caps.latest.revision: 16
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
ms.openlocfilehash: 2660aa56721815cbbeb668328863956473cce8f1
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="readonly-c-reference"></a><span data-ttu-id="39a3b-102">readonly (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="39a3b-102">readonly (C# Reference)</span></span>
<span data-ttu-id="39a3b-103">A palavra-chave `readonly` é um modificador que pode ser usado nos campos.</span><span class="sxs-lookup"><span data-stu-id="39a3b-103">The `readonly` keyword is a modifier that you can use on fields.</span></span> <span data-ttu-id="39a3b-104">Quando uma declaração de campo incluir um modificador `readonly`, atribuições aos campos introduzidas pela declaração podem ocorrer apenas como parte da declaração ou em um construtor na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="39a3b-104">When a field declaration includes a `readonly` modifier, assignments to the fields introduced by the declaration can only occur as part of the declaration or in a constructor in the same class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39a3b-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="39a3b-105">Example</span></span>  
 <span data-ttu-id="39a3b-106">Neste exemplo, o valor do campo `year` não pode ser alterado no método `ChangeYear`, ainda que seja atribuído a ele um valor no construtor da classe:</span><span class="sxs-lookup"><span data-stu-id="39a3b-106">In this example, the value of the field `year` cannot be changed in the method `ChangeYear`, even though it is assigned a value in the class constructor:</span></span>  
  
 <span data-ttu-id="39a3b-107">[!code-cs[csrefKeywordsModifiers#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="39a3b-107">[!code-cs[csrefKeywordsModifiers#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_1.cs)]</span></span>  
  
 <span data-ttu-id="39a3b-108">Você pode atribuir um valor a um campo `readonly` apenas nos seguintes contextos:</span><span class="sxs-lookup"><span data-stu-id="39a3b-108">You can assign a value to a `readonly` field only in the following contexts:</span></span>  
  
-   <span data-ttu-id="39a3b-109">Quando a variável é inicializada na declaração, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="39a3b-109">When the variable is initialized in the declaration, for example:</span></span>  
  
    ```  
    public readonly int y = 5;  
    ```  
  
-   <span data-ttu-id="39a3b-110">Para um campo de instância, nos construtores de instância da classe que contém a declaração do campo ou para um campo estático, no construtor estático da classe que contém a declaração do campo.</span><span class="sxs-lookup"><span data-stu-id="39a3b-110">For an instance field, in the instance constructors of the class that contains the field declaration, or for a static field, in the static constructor of the class that contains the field declaration.</span></span> <span data-ttu-id="39a3b-111">Esses também são os únicos contextos em que é válido passar um campo `readonly` como um parâmetro [out](../../../csharp/language-reference/keywords/out.md) ou [ref](../../../csharp/language-reference/keywords/ref.md).</span><span class="sxs-lookup"><span data-stu-id="39a3b-111">These are also the only contexts in which it is valid to pass a `readonly` field as an [out](../../../csharp/language-reference/keywords/out.md) or [ref](../../../csharp/language-reference/keywords/ref.md) parameter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39a3b-112">A palavra-chave `readonly` é diferente da palavra-chave [const](../../../csharp/language-reference/keywords/const.md).</span><span class="sxs-lookup"><span data-stu-id="39a3b-112">The `readonly` keyword is different from the [const](../../../csharp/language-reference/keywords/const.md) keyword.</span></span> <span data-ttu-id="39a3b-113">O campo `const` pode ser inicializado apenas na declaração do campo.</span><span class="sxs-lookup"><span data-stu-id="39a3b-113">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="39a3b-114">Um campo `readonly` pode ser inicializado na declaração ou em um construtor.</span><span class="sxs-lookup"><span data-stu-id="39a3b-114">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="39a3b-115">Portanto, campos `readonly` podem ter valores diferentes dependendo do construtor usado.</span><span class="sxs-lookup"><span data-stu-id="39a3b-115">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="39a3b-116">Além disso, enquanto um campo `const` é uma constante em tempo de compilação, o campo `readonly` pode ser usado para constantes de tempo de execução, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="39a3b-116">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for runtime constants as in the following example:</span></span>  
  
```  
public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;  
```  
  
## <a name="example"></a><span data-ttu-id="39a3b-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="39a3b-117">Example</span></span>  
 <span data-ttu-id="39a3b-118">[!code-cs[csrefKeywordsModifiers#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="39a3b-118">[!code-cs[csrefKeywordsModifiers#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_2.cs)]</span></span>  
  
 <span data-ttu-id="39a3b-119">No exemplo anterior, se você usar uma instrução como esta:</span><span class="sxs-lookup"><span data-stu-id="39a3b-119">In the preceding example, if you use a statement like this:</span></span>  
  
 `p2.y = 66;        // Error`  
  
 <span data-ttu-id="39a3b-120">você receberá a mensagem de erro do compilador:</span><span class="sxs-lookup"><span data-stu-id="39a3b-120">you will get the compiler error message:</span></span>  
  
 `The left-hand side of an assignment must be an l-value`  
  
 <span data-ttu-id="39a3b-121">que é o mesmo erro que você recebe quando tenta atribuir um valor a uma constante.</span><span class="sxs-lookup"><span data-stu-id="39a3b-121">which is the same error you get when you attempt to assign a value to a constant.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="39a3b-122">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="39a3b-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="39a3b-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39a3b-123">See Also</span></span>  
 <span data-ttu-id="39a3b-124">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="39a3b-124">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="39a3b-125">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="39a3b-125">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="39a3b-126">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="39a3b-126">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="39a3b-127">[Modificadores](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="39a3b-127">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="39a3b-128">[const](../../../csharp/language-reference/keywords/const.md) </span><span class="sxs-lookup"><span data-stu-id="39a3b-128">[const](../../../csharp/language-reference/keywords/const.md) </span></span>  
 [<span data-ttu-id="39a3b-129">Campos</span><span class="sxs-lookup"><span data-stu-id="39a3b-129">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)


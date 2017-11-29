---
title: "readonly (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords: readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b499f9fc5121afe6c2e92bcf8c5d2ac593b4c06c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="readonly-c-reference"></a><span data-ttu-id="3d763-102">readonly (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="3d763-102">readonly (C# Reference)</span></span>
<span data-ttu-id="3d763-103">A palavra-chave `readonly` é um modificador que pode ser usado nos campos.</span><span class="sxs-lookup"><span data-stu-id="3d763-103">The `readonly` keyword is a modifier that you can use on fields.</span></span> <span data-ttu-id="3d763-104">Quando uma declaração de campo incluir um modificador `readonly`, atribuições aos campos introduzidas pela declaração podem ocorrer apenas como parte da declaração ou em um construtor na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="3d763-104">When a field declaration includes a `readonly` modifier, assignments to the fields introduced by the declaration can only occur as part of the declaration or in a constructor in the same class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d763-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3d763-105">Example</span></span>  
 <span data-ttu-id="3d763-106">Neste exemplo, o valor do campo `year` não pode ser alterado no método `ChangeYear`, ainda que seja atribuído a ele um valor no construtor da classe:</span><span class="sxs-lookup"><span data-stu-id="3d763-106">In this example, the value of the field `year` cannot be changed in the method `ChangeYear`, even though it is assigned a value in the class constructor:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_1.cs)]  
  
 <span data-ttu-id="3d763-107">Você pode atribuir um valor a um campo `readonly` apenas nos seguintes contextos:</span><span class="sxs-lookup"><span data-stu-id="3d763-107">You can assign a value to a `readonly` field only in the following contexts:</span></span>  
  
-   <span data-ttu-id="3d763-108">Quando a variável é inicializada na declaração, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="3d763-108">When the variable is initialized in the declaration, for example:</span></span>  
  
    ```  
    public readonly int y = 5;  
    ```  
  
-   <span data-ttu-id="3d763-109">Para um campo de instância, nos construtores de instância da classe que contém a declaração do campo ou para um campo estático, no construtor estático da classe que contém a declaração do campo.</span><span class="sxs-lookup"><span data-stu-id="3d763-109">For an instance field, in the instance constructors of the class that contains the field declaration, or for a static field, in the static constructor of the class that contains the field declaration.</span></span> <span data-ttu-id="3d763-110">Esses também são os únicos contextos em que é válido passar um campo `readonly` como um parâmetro [out](../../../csharp/language-reference/keywords/out.md) ou [ref](../../../csharp/language-reference/keywords/ref.md).</span><span class="sxs-lookup"><span data-stu-id="3d763-110">These are also the only contexts in which it is valid to pass a `readonly` field as an [out](../../../csharp/language-reference/keywords/out.md) or [ref](../../../csharp/language-reference/keywords/ref.md) parameter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d763-111">A palavra-chave `readonly` é diferente da palavra-chave [const](../../../csharp/language-reference/keywords/const.md).</span><span class="sxs-lookup"><span data-stu-id="3d763-111">The `readonly` keyword is different from the [const](../../../csharp/language-reference/keywords/const.md) keyword.</span></span> <span data-ttu-id="3d763-112">O campo `const` pode ser inicializado apenas na declaração do campo.</span><span class="sxs-lookup"><span data-stu-id="3d763-112">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="3d763-113">Um campo `readonly` pode ser inicializado na declaração ou em um construtor.</span><span class="sxs-lookup"><span data-stu-id="3d763-113">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="3d763-114">Portanto, campos `readonly` podem ter valores diferentes dependendo do construtor usado.</span><span class="sxs-lookup"><span data-stu-id="3d763-114">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="3d763-115">Além disso, enquanto um campo `const` é uma constante em tempo de compilação, o campo `readonly` pode ser usado para constantes de tempo de execução, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="3d763-115">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for runtime constants as in the following example:</span></span>  
  
```  
public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;  
```  
  
## <a name="example"></a><span data-ttu-id="3d763-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3d763-116">Example</span></span>  
 [!code-csharp[csrefKeywordsModifiers#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_2.cs)]  
  
 <span data-ttu-id="3d763-117">No exemplo anterior, se você usar uma instrução como esta:</span><span class="sxs-lookup"><span data-stu-id="3d763-117">In the preceding example, if you use a statement like this:</span></span>  
  
 `p2.y = 66;        // Error`  
  
 <span data-ttu-id="3d763-118">você receberá a mensagem de erro do compilador:</span><span class="sxs-lookup"><span data-stu-id="3d763-118">you will get the compiler error message:</span></span>  
  
 `The left-hand side of an assignment must be an l-value`  
  
 <span data-ttu-id="3d763-119">que é o mesmo erro que você recebe quando tenta atribuir um valor a uma constante.</span><span class="sxs-lookup"><span data-stu-id="3d763-119">which is the same error you get when you attempt to assign a value to a constant.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="3d763-120">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="3d763-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3d763-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d763-121">See Also</span></span>  
 [<span data-ttu-id="3d763-122">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="3d763-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3d763-123">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="3d763-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3d763-124">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="3d763-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="3d763-125">Modificadores</span><span class="sxs-lookup"><span data-stu-id="3d763-125">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="3d763-126">const</span><span class="sxs-lookup"><span data-stu-id="3d763-126">const</span></span>](../../../csharp/language-reference/keywords/const.md)  
 [<span data-ttu-id="3d763-127">Campos</span><span class="sxs-lookup"><span data-stu-id="3d763-127">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)

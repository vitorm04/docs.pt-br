---
title: private (Referência de C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d9cc8f86166888b47a758e200182d319c68ca6d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="private-c-reference"></a><span data-ttu-id="c2f9d-102">private (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="c2f9d-102">private (C# Reference)</span></span>
<span data-ttu-id="c2f9d-103">A palavra-chave `private` é um modificador de acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="c2f9d-103">The `private` keyword is a member access modifier.</span></span> 
   
 > <span data-ttu-id="c2f9d-104">Esta página aborda `private` acesso.</span><span class="sxs-lookup"><span data-stu-id="c2f9d-104">This page covers `private` access.</span></span> <span data-ttu-id="c2f9d-105">O `private` palavra-chave também é parte do [ `private protected` ](./private-protected.md) modificador de acesso.</span><span class="sxs-lookup"><span data-stu-id="c2f9d-105">The `private` keyword is also part of the [`private protected`](./private-protected.md) access modifier.</span></span>
  
<span data-ttu-id="c2f9d-106">Acesso particular é o nível de acesso menos permissivo.</span><span class="sxs-lookup"><span data-stu-id="c2f9d-106">Private access is the least permissive access level.</span></span> <span data-ttu-id="c2f9d-107">Membros particulares são acessíveis somente dentro do corpo da classe ou do struct em que são declarados, como neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="c2f9d-107">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>  
  
```  
class Employee  
{  
    private int i;  
    double d;   // private access by default  
}  
```  

 <span data-ttu-id="c2f9d-108">Tipos aninhados no mesmo corpo também podem acessar os membros particulares.</span><span class="sxs-lookup"><span data-stu-id="c2f9d-108">Nested types in the same body can also access those private members.</span></span>  
  
 <span data-ttu-id="c2f9d-109">É um erro em tempo de compilação fazer referência a um membro particular fora da classe ou do struct em que ele é declarado.</span><span class="sxs-lookup"><span data-stu-id="c2f9d-109">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>  
  
 <span data-ttu-id="c2f9d-110">Para obter uma comparação de `private` com os outros modificadores de acesso, consulte [Níveis de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md) e [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="c2f9d-110">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) and [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2f9d-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c2f9d-111">Example</span></span>  
 <span data-ttu-id="c2f9d-112">Neste exemplo, a classe `Employee` contém dois membros de dados particulares, `name` e `salary`.</span><span class="sxs-lookup"><span data-stu-id="c2f9d-112">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="c2f9d-113">Como membros particulares, eles não podem ser acessados, exceto por métodos de membro.</span><span class="sxs-lookup"><span data-stu-id="c2f9d-113">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="c2f9d-114">Métodos públicos chamados `GetName` e `Salary` foram adicionados para permitir acesso controlado aos membros particulares.</span><span class="sxs-lookup"><span data-stu-id="c2f9d-114">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="c2f9d-115">O membro `name` é acessado por meio de um método público e o membro `salary` é acessado por meio de uma propriedade somente leitura pública.</span><span class="sxs-lookup"><span data-stu-id="c2f9d-115">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="c2f9d-116">(Consulte [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md) para obter mais informações.)</span><span class="sxs-lookup"><span data-stu-id="c2f9d-116">(See [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md) for more information.)</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/private_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="c2f9d-117">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="c2f9d-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c2f9d-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2f9d-118">See Also</span></span>  
 [<span data-ttu-id="c2f9d-119">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="c2f9d-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c2f9d-120">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="c2f9d-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c2f9d-121">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="c2f9d-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="c2f9d-122">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="c2f9d-122">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="c2f9d-123">Níveis de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="c2f9d-123">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="c2f9d-124">Modificadores</span><span class="sxs-lookup"><span data-stu-id="c2f9d-124">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="c2f9d-125">public</span><span class="sxs-lookup"><span data-stu-id="c2f9d-125">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="c2f9d-126">protected</span><span class="sxs-lookup"><span data-stu-id="c2f9d-126">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="c2f9d-127">internal</span><span class="sxs-lookup"><span data-stu-id="c2f9d-127">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)

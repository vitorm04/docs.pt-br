---
title: ". Operador (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ._CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
caps.latest.revision: 21
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
ms.openlocfilehash: fdc7c1821548509f3a3750aef2836c034f7aa53b
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="73d9c-103">.</span><span class="sxs-lookup"><span data-stu-id="73d9c-103">.</span></span> <span data-ttu-id="73d9c-104">Operador (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="73d9c-104">Operator (C# Reference)</span></span>
<span data-ttu-id="73d9c-105">O operador ponto (`.`) é usado para o acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="73d9c-105">The dot operator (`.`) is used for member access.</span></span> <span data-ttu-id="73d9c-106">O operador ponto especifica um membro de um tipo ou namespace.</span><span class="sxs-lookup"><span data-stu-id="73d9c-106">The dot operator specifies a member of a type or namespace.</span></span> <span data-ttu-id="73d9c-107">Por exemplo, o operador ponto é usado para acessar métodos específicos dentro das bibliotecas de classes do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="73d9c-107">For example, the dot operator is used to access specific methods within the .NET Framework class libraries:</span></span>  
  
 <span data-ttu-id="73d9c-108">[!code-cs[csRefOperators#16](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="73d9c-108">[!code-cs[csRefOperators#16](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_1.cs)]</span></span>  
  
 <span data-ttu-id="73d9c-109">Por exemplo, considere a seguinte classe:</span><span class="sxs-lookup"><span data-stu-id="73d9c-109">For example, consider the following class:</span></span>  
  
 <span data-ttu-id="73d9c-110">[!code-cs[csRefOperators#17](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="73d9c-110">[!code-cs[csRefOperators#17](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_2.cs)]</span></span>  
  
 <span data-ttu-id="73d9c-111">[!code-cs[csRefOperators#18](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="73d9c-111">[!code-cs[csRefOperators#18](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_3.cs)]</span></span>  
  
 <span data-ttu-id="73d9c-112">A variável `s` tem dois membros, `a` e `b`. Para acessá-los, use o operador ponto:</span><span class="sxs-lookup"><span data-stu-id="73d9c-112">The variable `s` has two members, `a` and `b`; to access them, use the dot operator:</span></span>  
  
 <span data-ttu-id="73d9c-113">[!code-cs[csRefOperators#19](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="73d9c-113">[!code-cs[csRefOperators#19](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_4.cs)]</span></span>  
  
 <span data-ttu-id="73d9c-114">O ponto é usado também para formar nomes qualificados, que são nomes que especificam o namespace ou interface, por exemplo, à qual eles pertencem.</span><span class="sxs-lookup"><span data-stu-id="73d9c-114">The dot is also used to form qualified names, which are names that specify the namespace or interface, for example, to which they belong.</span></span>  
  
 <span data-ttu-id="73d9c-115">[!code-cs[csRefOperators#20](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="73d9c-115">[!code-cs[csRefOperators#20](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_5.cs)]</span></span>  
  
 <span data-ttu-id="73d9c-116">A diretiva using torna algumas qualificações de nome opcionais:</span><span class="sxs-lookup"><span data-stu-id="73d9c-116">The using directive makes some name qualification optional:</span></span>  
  
 <span data-ttu-id="73d9c-117">[!code-cs[csRefOperators#21](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="73d9c-117">[!code-cs[csRefOperators#21](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_6.cs)]</span></span>  
  
 <span data-ttu-id="73d9c-118">Mas quando um identificador é ambíguo, ele deve ser qualificado:</span><span class="sxs-lookup"><span data-stu-id="73d9c-118">But when an identifier is ambiguous, it must be qualified:</span></span>  
  
 <span data-ttu-id="73d9c-119">[!code-cs[csRefOperators#22](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="73d9c-119">[!code-cs[csRefOperators#22](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_7.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="73d9c-120">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="73d9c-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="73d9c-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73d9c-121">See Also</span></span>  
 <span data-ttu-id="73d9c-122">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="73d9c-122">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="73d9c-123">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="73d9c-123">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="73d9c-124">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="73d9c-124">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)


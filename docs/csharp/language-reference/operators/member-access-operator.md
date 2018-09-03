---
title: . Operador (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
ms.openlocfilehash: a092c1a916e3dc4bf6d96660c532540945e57554
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43408001"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="c2f1b-103">.</span><span class="sxs-lookup"><span data-stu-id="c2f1b-103">.</span></span> <span data-ttu-id="c2f1b-104">Operador (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="c2f1b-104">Operator (C# Reference)</span></span>
<span data-ttu-id="c2f1b-105">O operador ponto (`.`) é usado para o acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="c2f1b-105">The dot operator (`.`) is used for member access.</span></span> <span data-ttu-id="c2f1b-106">O operador ponto especifica um membro de um tipo ou namespace.</span><span class="sxs-lookup"><span data-stu-id="c2f1b-106">The dot operator specifies a member of a type or namespace.</span></span> <span data-ttu-id="c2f1b-107">Por exemplo, o operador ponto é usado para acessar métodos específicos dentro das bibliotecas de classes do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="c2f1b-107">For example, the dot operator is used to access specific methods within the .NET Framework class libraries:</span></span>  
  
 [!code-csharp[csRefOperators#16](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_1.cs)]  
  
 <span data-ttu-id="c2f1b-108">Por exemplo, considere a seguinte classe:</span><span class="sxs-lookup"><span data-stu-id="c2f1b-108">For example, consider the following class:</span></span>  
  
 [!code-csharp[csRefOperators#17](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_2.cs)]  
  
 [!code-csharp[csRefOperators#18](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_3.cs)]  
  
 <span data-ttu-id="c2f1b-109">A variável `s` tem dois membros, `a` e `b`. Para acessá-los, use o operador ponto:</span><span class="sxs-lookup"><span data-stu-id="c2f1b-109">The variable `s` has two members, `a` and `b`; to access them, use the dot operator:</span></span>  
  
 [!code-csharp[csRefOperators#19](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_4.cs)]  
  
 <span data-ttu-id="c2f1b-110">O ponto é usado também para formar nomes qualificados, que são nomes que especificam o namespace ou interface, por exemplo, à qual eles pertencem.</span><span class="sxs-lookup"><span data-stu-id="c2f1b-110">The dot is also used to form qualified names, which are names that specify the namespace or interface, for example, to which they belong.</span></span>  
  
 [!code-csharp[csRefOperators#20](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_5.cs)]  
  
 <span data-ttu-id="c2f1b-111">A diretiva using torna algumas qualificações de nome opcionais:</span><span class="sxs-lookup"><span data-stu-id="c2f1b-111">The using directive makes some name qualification optional:</span></span>  
  
 [!code-csharp[csRefOperators#21](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_6.cs)]  
  
 <span data-ttu-id="c2f1b-112">Mas quando um identificador é ambíguo, ele deve ser qualificado:</span><span class="sxs-lookup"><span data-stu-id="c2f1b-112">But when an identifier is ambiguous, it must be qualified:</span></span>  
  
 [!code-csharp[csRefOperators#22](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_7.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="c2f1b-113">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="c2f1b-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c2f1b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2f1b-114">See Also</span></span>

- [<span data-ttu-id="c2f1b-115">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="c2f1b-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="c2f1b-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="c2f1b-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="c2f1b-117">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="c2f1b-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

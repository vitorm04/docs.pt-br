---
title: . Operador – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
ms.openlocfilehash: f5048761973e10bec9650469383e2f52cee74da4
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235040"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="dd857-103">.</span><span class="sxs-lookup"><span data-stu-id="dd857-103">.</span></span> <span data-ttu-id="dd857-104">Operador (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="dd857-104">Operator (C# Reference)</span></span>
<span data-ttu-id="dd857-105">O operador ponto (`.`) é usado para o acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="dd857-105">The dot operator (`.`) is used for member access.</span></span> <span data-ttu-id="dd857-106">O operador ponto especifica um membro de um tipo ou namespace.</span><span class="sxs-lookup"><span data-stu-id="dd857-106">The dot operator specifies a member of a type or namespace.</span></span> <span data-ttu-id="dd857-107">Por exemplo, o operador ponto é usado para acessar métodos específicos dentro das bibliotecas de classes do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="dd857-107">For example, the dot operator is used to access specific methods within the .NET Framework class libraries:</span></span>  
  
 [!code-csharp[csRefOperators#16](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_1.cs)]  
  
 <span data-ttu-id="dd857-108">Por exemplo, considere a seguinte classe:</span><span class="sxs-lookup"><span data-stu-id="dd857-108">For example, consider the following class:</span></span>  
  
 [!code-csharp[csRefOperators#17](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_2.cs)]  
  
 [!code-csharp[csRefOperators#18](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_3.cs)]  
  
 <span data-ttu-id="dd857-109">A variável `s` tem dois membros, `a` e `b`. Para acessá-los, use o operador ponto:</span><span class="sxs-lookup"><span data-stu-id="dd857-109">The variable `s` has two members, `a` and `b`; to access them, use the dot operator:</span></span>  
  
 [!code-csharp[csRefOperators#19](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_4.cs)]  
  
 <span data-ttu-id="dd857-110">O ponto é usado também para formar nomes qualificados, que são nomes que especificam o namespace ou interface, por exemplo, à qual eles pertencem.</span><span class="sxs-lookup"><span data-stu-id="dd857-110">The dot is also used to form qualified names, which are names that specify the namespace or interface, for example, to which they belong.</span></span>  
  
 [!code-csharp[csRefOperators#20](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_5.cs)]  
  
 <span data-ttu-id="dd857-111">A diretiva using torna algumas qualificações de nome opcionais:</span><span class="sxs-lookup"><span data-stu-id="dd857-111">The using directive makes some name qualification optional:</span></span>  
  
 [!code-csharp[csRefOperators#21](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_6.cs)]  
  
 <span data-ttu-id="dd857-112">Mas quando um identificador é ambíguo, ele deve ser qualificado:</span><span class="sxs-lookup"><span data-stu-id="dd857-112">But when an identifier is ambiguous, it must be qualified:</span></span>  
  
 [!code-csharp[csRefOperators#22](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_7.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="dd857-113">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="dd857-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dd857-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd857-114">See Also</span></span>

- [<span data-ttu-id="dd857-115">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="dd857-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="dd857-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="dd857-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="dd857-117">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="dd857-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

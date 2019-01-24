---
title: . Operador – referência do C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
ms.openlocfilehash: a59f69d0349a054c8c2a5b701b8f63df113a6580
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333714"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="aacb9-103">.</span><span class="sxs-lookup"><span data-stu-id="aacb9-103">.</span></span> <span data-ttu-id="aacb9-104">operator (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="aacb9-104">operator (C# Reference)</span></span>

<span data-ttu-id="aacb9-105">O operador ponto (`.`) é usado para o acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="aacb9-105">The dot operator (`.`) is used for member access.</span></span> <span data-ttu-id="aacb9-106">O operador ponto especifica um membro de um tipo ou namespace.</span><span class="sxs-lookup"><span data-stu-id="aacb9-106">The dot operator specifies a member of a type or namespace.</span></span> <span data-ttu-id="aacb9-107">Por exemplo, o operador ponto é usado para acessar métodos específicos dentro das bibliotecas de classes do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="aacb9-107">For example, the dot operator is used to access specific methods within the .NET Framework class libraries:</span></span>

[!code-csharp[csRefOperators#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#16)]

<span data-ttu-id="aacb9-108">Por exemplo, considere a seguinte classe:</span><span class="sxs-lookup"><span data-stu-id="aacb9-108">For example, consider the following class:</span></span>

[!code-csharp[csRefOperators#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#17)]

[!code-csharp[csRefOperators#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#18)]

<span data-ttu-id="aacb9-109">A variável `s` tem dois membros, `a` e `b`. Para acessá-los, use o operador ponto:</span><span class="sxs-lookup"><span data-stu-id="aacb9-109">The variable `s` has two members, `a` and `b`; to access them, use the dot operator:</span></span>

[!code-csharp[csRefOperators#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#19)]

<span data-ttu-id="aacb9-110">O ponto é usado também para formar nomes qualificados, que são nomes que especificam o namespace ou interface, por exemplo, à qual eles pertencem.</span><span class="sxs-lookup"><span data-stu-id="aacb9-110">The dot is also used to form qualified names, which are names that specify the namespace or interface, for example, to which they belong.</span></span>

[!code-csharp[csRefOperators#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#20)]

<span data-ttu-id="aacb9-111">A diretiva using torna algumas qualificações de nome opcionais:</span><span class="sxs-lookup"><span data-stu-id="aacb9-111">The using directive makes some name qualification optional:</span></span>

[!code-csharp[csRefOperators#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#21)]

<span data-ttu-id="aacb9-112">Mas quando um identificador é ambíguo, ele deve ser qualificado:</span><span class="sxs-lookup"><span data-stu-id="aacb9-112">But when an identifier is ambiguous, it must be qualified:</span></span>

[!code-csharp[csRefOperators#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#22)]

## <a name="c-language-specification"></a><span data-ttu-id="aacb9-113">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="aacb9-113">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="aacb9-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aacb9-114">See also</span></span>

- [<span data-ttu-id="aacb9-115">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="aacb9-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="aacb9-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="aacb9-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="aacb9-117">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="aacb9-117">C# Operators</span></span>](index.md)
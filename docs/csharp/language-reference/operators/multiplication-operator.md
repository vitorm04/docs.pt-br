---
title: '* Operador – referência do C#'
ms.custom: seodec18
ms.date: 04/04/2018
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: f4490c4632d9344eb879ea55c20787b838781d91
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333727"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="aff57-102">Operador \* (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="aff57-102">\* operator (C# Reference)</span></span>

<span data-ttu-id="aff57-103">O operador de multiplicação (`*`) calcula o produto dos operandos.</span><span class="sxs-lookup"><span data-stu-id="aff57-103">The multiplication operator (`*`) computes the product of its operands.</span></span> <span data-ttu-id="aff57-104">Todos os tipos numéricos têm operadores de multiplicação predefinidos.</span><span class="sxs-lookup"><span data-stu-id="aff57-104">All numeric types have predefined multiplication operators.</span></span>

<span data-ttu-id="aff57-105">`*` também atua como o operador de desreferenciamento, que permite a leitura e a gravação em um ponteiro.</span><span class="sxs-lookup"><span data-stu-id="aff57-105">`*` also serves as the dereference operator, which allows reading and writing to a pointer.</span></span>

## <a name="remarks"></a><span data-ttu-id="aff57-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="aff57-106">Remarks</span></span>

<span data-ttu-id="aff57-107">O operador `*` também é usado para declarar tipos de ponteiro e para desreferenciar ponteiros.</span><span class="sxs-lookup"><span data-stu-id="aff57-107">The `*` operator is also used to declare pointer types and to dereference pointers.</span></span> <span data-ttu-id="aff57-108">Esse operador pode ser usado somente em contextos não seguros, indicado pelo uso da palavra-chave [unsafe](../keywords/unsafe.md) e exigindo a opção do compilador [/unsafe](../compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="aff57-108">This operator can only be used in unsafe contexts, denoted by the use of the [unsafe](../keywords/unsafe.md) keyword, and requiring the [/unsafe](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span>  <span data-ttu-id="aff57-109">O operador de desreferenciamento é também conhecido como operador de indireção.</span><span class="sxs-lookup"><span data-stu-id="aff57-109">The dereference operator is also known as the indirection operator.</span></span>

<span data-ttu-id="aff57-110">Tipos definidos pelo usuário podem sobrecarregar o operador binário `*` (consulte [operador](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="aff57-110">User-defined types can overload the binary `*` operator (see [operator](../keywords/operator.md)).</span></span> <span data-ttu-id="aff57-111">Quando um operador binário está sobrecarregado, o operador de atribuição correspondente, se houver, também estará implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="aff57-111">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>

## <a name="example"></a><span data-ttu-id="aff57-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aff57-112">Example</span></span>

[!code-csharp-interactive[csRefOperators#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#50)]

## <a name="example"></a><span data-ttu-id="aff57-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aff57-113">Example</span></span>

[!code-csharp[csRefOperators#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#51)]

## <a name="see-also"></a><span data-ttu-id="aff57-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aff57-114">See also</span></span>

- [<span data-ttu-id="aff57-115">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="aff57-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="aff57-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="aff57-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="aff57-117">Código não seguro e ponteiros</span><span class="sxs-lookup"><span data-stu-id="aff57-117">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="aff57-118">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="aff57-118">C# Operators</span></span>](index.md)
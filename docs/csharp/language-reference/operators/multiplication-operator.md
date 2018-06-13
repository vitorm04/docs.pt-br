---
title: '* Operador (Referência de C#)'
ms.date: 04/04/2018
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: 6c5d4de587b67e5ade158c163a87e8dea6bece5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275835"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="7af06-102">Operador \* (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="7af06-102">\* Operator (C# Reference)</span></span>
<span data-ttu-id="7af06-103">O operador de multiplicação (`*`) calcula o produto dos operandos.</span><span class="sxs-lookup"><span data-stu-id="7af06-103">The multiplication operator (`*`) computes the product of its operands.</span></span> <span data-ttu-id="7af06-104">Todos os tipos numéricos têm operadores de multiplicação predefinidos.</span><span class="sxs-lookup"><span data-stu-id="7af06-104">All numeric types have predefined multiplication operators.</span></span>  

<span data-ttu-id="7af06-105">`*` também atua como o operador de desreferenciamento, que permite a leitura e a gravação em um ponteiro.</span><span class="sxs-lookup"><span data-stu-id="7af06-105">`*` also serves as the dereference operator, which allows reading and writing to a pointer.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="7af06-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="7af06-106">Remarks</span></span>  
 <span data-ttu-id="7af06-107">O operador `*` também é usado para declarar tipos de ponteiro e para desreferenciar ponteiros.</span><span class="sxs-lookup"><span data-stu-id="7af06-107">The `*` operator is also used to declare pointer types and to dereference pointers.</span></span> <span data-ttu-id="7af06-108">Esse operador pode ser usado somente em contextos não seguros, indicado pelo uso da palavra-chave [unsafe](../../../csharp/language-reference/keywords/unsafe.md) e exigindo a opção do compilador [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="7af06-108">This operator can only be used in unsafe contexts, denoted by the use of the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, and requiring the [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>  <span data-ttu-id="7af06-109">O operador de desreferenciamento é também conhecido como operador de indireção.</span><span class="sxs-lookup"><span data-stu-id="7af06-109">The dereference operator is also known as the indirection operator.</span></span>  
  
 <span data-ttu-id="7af06-110">Tipos definidos pelo usuário podem sobrecarregar o operador binário `*` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="7af06-110">User-defined types can overload the binary `*` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="7af06-111">Quando um operador binário está sobrecarregado, o operador de atribuição correspondente, se houver, também estará implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="7af06-111">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7af06-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7af06-112">Example</span></span>  
 [!code-csharp[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="7af06-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7af06-113">Example</span></span>  
 [!code-csharp[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="7af06-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7af06-114">See Also</span></span>  
 [<span data-ttu-id="7af06-115">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="7af06-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="7af06-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="7af06-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7af06-117">Código não seguro e ponteiros</span><span class="sxs-lookup"><span data-stu-id="7af06-117">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="7af06-118">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="7af06-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

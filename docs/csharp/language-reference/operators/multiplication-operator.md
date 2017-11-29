---
title: "* Operador (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 64c32def0935f4347f9aaccc2865b9cd33dd8a70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="0f53d-102">Operador * (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="0f53d-102">* Operator (C# Reference)</span></span>
<span data-ttu-id="0f53d-103">O operador de multiplicação (`*`), que calcula o produto dos operandos.</span><span class="sxs-lookup"><span data-stu-id="0f53d-103">The multiplication operator (`*`), which computes the product of its operands.</span></span>  <span data-ttu-id="0f53d-104">Além disso, o operador de desreferenciamento, que permite a leitura e gravação em um ponteiro.</span><span class="sxs-lookup"><span data-stu-id="0f53d-104">Also, the dereference operator, which allows reading and writing to a pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f53d-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="0f53d-105">Remarks</span></span>  
 <span data-ttu-id="0f53d-106">Todos os tipos numéricos têm operadores de multiplicação predefinidos.</span><span class="sxs-lookup"><span data-stu-id="0f53d-106">All numeric types have predefined multiplication operators.</span></span>  
  
 <span data-ttu-id="0f53d-107">O operador `*` também é usado para declarar tipos de ponteiro e para desreferenciar ponteiros.</span><span class="sxs-lookup"><span data-stu-id="0f53d-107">The `*` operator is also used to declare pointer types and to dereference pointers.</span></span> <span data-ttu-id="0f53d-108">Esse operador pode ser usado somente em contextos não seguros, indicado pelo uso da palavra-chave [unsafe](../../../csharp/language-reference/keywords/unsafe.md) e exigindo a opção do compilador [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="0f53d-108">This operator can only be used in unsafe contexts, denoted by the use of the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, and requiring the [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>  <span data-ttu-id="0f53d-109">O operador de desreferenciamento é também conhecido como operador de indireção.</span><span class="sxs-lookup"><span data-stu-id="0f53d-109">The dereference operator is also known as the indirection operator.</span></span>  
  
 <span data-ttu-id="0f53d-110">Tipos definidos pelo usuário podem sobrecarregar o operador binário `*` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="0f53d-110">User-defined types can overload the binary `*` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="0f53d-111">Quando um operador binário está sobrecarregado, o operador de atribuição correspondente, se houver, também estará implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="0f53d-111">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f53d-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0f53d-112">Example</span></span>  
 [!code-csharp[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="0f53d-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0f53d-113">Example</span></span>  
 [!code-csharp[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="0f53d-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f53d-114">See Also</span></span>  
 [<span data-ttu-id="0f53d-115">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="0f53d-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0f53d-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="0f53d-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0f53d-117">Código não seguro e ponteiros</span><span class="sxs-lookup"><span data-stu-id="0f53d-117">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="0f53d-118">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="0f53d-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

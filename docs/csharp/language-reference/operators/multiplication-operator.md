---
title: "* Operador (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '*_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
caps.latest.revision: 14
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
ms.openlocfilehash: 165ca8f797eb8d03ae1dec8c0ec5e1f4b31cb050
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="cde69-102">Operador * (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="cde69-102">* Operator (C# Reference)</span></span>
<span data-ttu-id="cde69-103">O operador de multiplicação (`*`), que calcula o produto dos operandos.</span><span class="sxs-lookup"><span data-stu-id="cde69-103">The multiplication operator (`*`), which computes the product of its operands.</span></span>  <span data-ttu-id="cde69-104">Além disso, o operador de desreferenciamento, que permite a leitura e gravação em um ponteiro.</span><span class="sxs-lookup"><span data-stu-id="cde69-104">Also, the dereference operator, which allows reading and writing to a pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cde69-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="cde69-105">Remarks</span></span>  
 <span data-ttu-id="cde69-106">Todos os tipos numéricos têm operadores de multiplicação predefinidos.</span><span class="sxs-lookup"><span data-stu-id="cde69-106">All numeric types have predefined multiplication operators.</span></span>  
  
 <span data-ttu-id="cde69-107">O operador `*` também é usado para declarar tipos de ponteiro e para desreferenciar ponteiros.</span><span class="sxs-lookup"><span data-stu-id="cde69-107">The `*` operator is also used to declare pointer types and to dereference pointers.</span></span> <span data-ttu-id="cde69-108">Esse operador pode ser usado somente em contextos não seguros, indicado pelo uso da palavra-chave [unsafe](../../../csharp/language-reference/keywords/unsafe.md) e exigindo a opção do compilador [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="cde69-108">This operator can only be used in unsafe contexts, denoted by the use of the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, and requiring the [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>  <span data-ttu-id="cde69-109">O operador de desreferenciamento é também conhecido como operador de indireção.</span><span class="sxs-lookup"><span data-stu-id="cde69-109">The dereference operator is also known as the indirection operator.</span></span>  
  
 <span data-ttu-id="cde69-110">Tipos definidos pelo usuário podem sobrecarregar o operador binário `*` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="cde69-110">User-defined types can overload the binary `*` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="cde69-111">Quando um operador binário está sobrecarregado, o operador de atribuição correspondente, se houver, também estará implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="cde69-111">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cde69-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cde69-112">Example</span></span>  
 <span data-ttu-id="cde69-113">[!code-cs[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="cde69-113">[!code-cs[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="cde69-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cde69-114">Example</span></span>  
 <span data-ttu-id="cde69-115">[!code-cs[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="cde69-115">[!code-cs[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cde69-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cde69-116">See Also</span></span>  
 <span data-ttu-id="cde69-117">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="cde69-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="cde69-118">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="cde69-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="cde69-119">[Código Não Seguro e Ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span><span class="sxs-lookup"><span data-stu-id="cde69-119">[Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span></span>  
 [<span data-ttu-id="cde69-120">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="cde69-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)


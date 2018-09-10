---
title: Operador -&gt; (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: fb95e508ce1339868723bcc3178851e8c1355c1f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44190222"
---
# <a name="-gt-operator-c-reference"></a><span data-ttu-id="7b466-102">Operador -&gt; (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="7b466-102">-&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="7b466-103">O operador `->` combina a desreferência de ponteiro e o acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="7b466-103">The `->` operator combines pointer dereferencing and member access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b466-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="7b466-104">Remarks</span></span>  
 <span data-ttu-id="7b466-105">Uma expressão da forma,</span><span class="sxs-lookup"><span data-stu-id="7b466-105">An expression of the form,</span></span>  
  
```csharp  
x->y  
```  
  
 <span data-ttu-id="7b466-106">(em que `x` é um ponteiro de tipo `T*` e `y` é um membro de `T`) é equivalente a,</span><span class="sxs-lookup"><span data-stu-id="7b466-106">(where `x` is a pointer of type `T*` and `y` is a member of `T`) is equivalent to,</span></span>  
  
```csharp  
(*x).y  
```  
  
 <span data-ttu-id="7b466-107">O operador `->` pode ser usado apenas no código que está marcado como [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="7b466-107">The `->` operator can be used only in code that is marked as [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span></span>  
  
 <span data-ttu-id="7b466-108">O operador `->` não pode ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="7b466-108">The `->` operator cannot be overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b466-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7b466-109">Example</span></span>  
 [!code-csharp[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/CSharp/dereference-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="7b466-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b466-110">See Also</span></span>

- [<span data-ttu-id="7b466-111">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="7b466-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="7b466-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="7b466-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="7b466-113">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="7b466-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

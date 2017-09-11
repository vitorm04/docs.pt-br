---
title: "Operador -&gt; (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ->_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
caps.latest.revision: 19
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
ms.openlocfilehash: f42135e43bdfc58ee64fd3465074b3f8791f8ada
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="-gt-operator-c-reference"></a><span data-ttu-id="a01ea-102">Operador -&gt; (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="a01ea-102">-&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="a01ea-103">O operador `->` combina a desreferência de ponteiro e o acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="a01ea-103">The `->` operator combines pointer dereferencing and member access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a01ea-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="a01ea-104">Remarks</span></span>  
 <span data-ttu-id="a01ea-105">Uma expressão da forma,</span><span class="sxs-lookup"><span data-stu-id="a01ea-105">An expression of the form,</span></span>  
  
```  
x->y  
```  
  
 <span data-ttu-id="a01ea-106">(em que `x` é um ponteiro de tipo `T*` e `y` é um membro de `T`) é equivalente a,</span><span class="sxs-lookup"><span data-stu-id="a01ea-106">(where `x` is a pointer of type `T*` and `y` is a member of `T`) is equivalent to,</span></span>  
  
```  
(*x).y  
```  
  
 <span data-ttu-id="a01ea-107">O operador `->` pode ser usado apenas no código que está marcado como [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="a01ea-107">The `->` operator can be used only in code that is marked as [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span></span>  
  
 <span data-ttu-id="a01ea-108">O operador `->` não pode ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="a01ea-108">The `->` operator cannot be overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a01ea-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a01ea-109">Example</span></span>  
 <span data-ttu-id="a01ea-110">[!code-cs[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/CSharp/dereference-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="a01ea-110">[!code-cs[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/CSharp/dereference-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a01ea-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a01ea-111">See Also</span></span>  
 <span data-ttu-id="a01ea-112">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="a01ea-112">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="a01ea-113">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="a01ea-113">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="a01ea-114">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="a01ea-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)


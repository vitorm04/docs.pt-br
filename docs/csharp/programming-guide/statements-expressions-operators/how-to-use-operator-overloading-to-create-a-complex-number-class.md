---
title: "Como usar sobrecarga de operador para criar uma classe de número complexo (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- complex numbers [C#]
- classes [C#], operator overloading
- operator overloading [C#], complex numbers
- operator overloading [C#], using to create classes
- operators [C#], overloading to create a complex number class
ms.assetid: c9b8d982-5112-413f-bae3-b42ae3248ddf
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e851b9d8a46f9cab73883a7b38761fed749c4f93
ms.sourcegitcommit: 22a48b64a0150a60b00b4fc4d8c62cde7f1670c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2018
---
# <a name="how-to-use-operator-overloading-to-create-a-complex-number-class-c-programming-guide"></a><span data-ttu-id="dcfa2-102">Como usar sobrecarga de operador para criar uma classe de número complexo (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="dcfa2-102">How to: Use Operator Overloading to Create a Complex Number Class (C# Programming Guide)</span></span>
<span data-ttu-id="dcfa2-103">Este exemplo mostra como é possível usar a sobrecarga de operador para criar uma classe de número complexo `Complex` que define a adição de complexa.</span><span class="sxs-lookup"><span data-stu-id="dcfa2-103">This example shows how you can use operator overloading to create a complex number class `Complex` that defines complex addition.</span></span> <span data-ttu-id="dcfa2-104">O programa exibe as partes imaginárias e reais dos números e o resultado da adição usando uma substituição do método `ToString`.</span><span class="sxs-lookup"><span data-stu-id="dcfa2-104">The program displays the imaginary and the real parts of the numbers and the addition result using an override of the `ToString` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dcfa2-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dcfa2-105">Example</span></span>  
 [!code-csharp[csProgGuideStatements#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-operator-overloading-to-create-a-complex-number-class_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="dcfa2-106">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dcfa2-106">See Also</span></span>  
 [<span data-ttu-id="dcfa2-107">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="dcfa2-107">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="dcfa2-108">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="dcfa2-108">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="dcfa2-109">operator (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="dcfa2-109">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)  
 [<span data-ttu-id="dcfa2-110">Por que os operadores sobrecarregados sempre são estáticos em C#?</span><span class="sxs-lookup"><span data-stu-id="dcfa2-110">Why are overloaded operators always static in C#?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/)

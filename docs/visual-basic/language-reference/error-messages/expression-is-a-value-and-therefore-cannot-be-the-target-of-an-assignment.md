---
title: "Expressão é um valor e, portanto, não pode ser o destino de uma atribuição | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30068
- vbc30068
dev_langs:
- VB
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 734e46a6fab781e1ff9a421625b952e2cfd3a8f1
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a><span data-ttu-id="8f9d5-102">Expressão é um valor e, por isso, não pode ser o destino de uma atribuição</span><span class="sxs-lookup"><span data-stu-id="8f9d5-102">Expression is a value and therefore cannot be the target of an assignment</span></span>
<span data-ttu-id="8f9d5-103">Uma declaração tenta atribuir um valor a uma expressão.</span><span class="sxs-lookup"><span data-stu-id="8f9d5-103">A statement attempts to assign a value to an expression.</span></span> <span data-ttu-id="8f9d5-104">Você pode atribuir um valor apenas para uma variável gravável, uma propriedade ou um elemento da matriz em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8f9d5-104">You can assign a value only to a writable variable, property, or array element at run time.</span></span> <span data-ttu-id="8f9d5-105">O exemplo a seguir ilustra como esse erro pode ocorrer.</span><span class="sxs-lookup"><span data-stu-id="8f9d5-105">The following example illustrates how this error can occur.</span></span>  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 <span data-ttu-id="8f9d5-106">Exemplos semelhantes pode aplicar propriedades e elementos de matriz.</span><span class="sxs-lookup"><span data-stu-id="8f9d5-106">Similar examples could apply to properties and array elements.</span></span>  
  
 <span data-ttu-id="8f9d5-107">**Acesso indireto.**</span><span class="sxs-lookup"><span data-stu-id="8f9d5-107">**Indirect Access.**</span></span> <span data-ttu-id="8f9d5-108">Acesso indireto através de um tipo de valor também pode gerar esse erro.</span><span class="sxs-lookup"><span data-stu-id="8f9d5-108">Indirect access through a value type can also generate this error.</span></span> <span data-ttu-id="8f9d5-109">Considere o seguinte exemplo de código, que tenta definir o valor de <xref:System.Drawing.Point>Acessando indiretamente por meio de <xref:System.Windows.Forms.Control.Location%2A>.</xref:System.Windows.Forms.Control.Location%2A> </xref:System.Drawing.Point></span><span class="sxs-lookup"><span data-stu-id="8f9d5-109">Consider the following code example, which attempts to set the value of <xref:System.Drawing.Point> by accessing it indirectly through <xref:System.Windows.Forms.Control.Location%2A>.</span></span>  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 <span data-ttu-id="8f9d5-110">A última instrução do exemplo anterior falhará porque ela cria somente uma alocação temporária para o <xref:System.Drawing.Point>estrutura retornada pelo <xref:System.Windows.Forms.Control.Location%2A>propriedade.</xref:System.Windows.Forms.Control.Location%2A> </xref:System.Drawing.Point></span><span class="sxs-lookup"><span data-stu-id="8f9d5-110">The last statement of the preceding example fails because it creates only a temporary allocation for the <xref:System.Drawing.Point> structure returned by the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span> <span data-ttu-id="8f9d5-111">Uma estrutura é um tipo de valor e a estrutura temporária não é mantida após a instrução é executada.</span><span class="sxs-lookup"><span data-stu-id="8f9d5-111">A structure is a value type, and the temporary structure is not retained after the statement runs.</span></span> <span data-ttu-id="8f9d5-112">O problema é resolvido ao declarar e usar uma variável para <xref:System.Windows.Forms.Control.Location%2A>, que cria uma alocação mais permanente para o <xref:System.Drawing.Point>estrutura.</xref:System.Drawing.Point> </xref:System.Windows.Forms.Control.Location%2A></span><span class="sxs-lookup"><span data-stu-id="8f9d5-112">The problem is resolved by declaring and using a variable for <xref:System.Windows.Forms.Control.Location%2A>, which creates a more permanent allocation for the <xref:System.Drawing.Point> structure.</span></span> <span data-ttu-id="8f9d5-113">O exemplo a seguir mostra o código que pode substituir a última instrução do exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="8f9d5-113">The following example shows code that can replace the last statement of the preceding example.</span></span>  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 <span data-ttu-id="8f9d5-114">**ID do erro:** BC30068</span><span class="sxs-lookup"><span data-stu-id="8f9d5-114">**Error ID:** BC30068</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8f9d5-115">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="8f9d5-115">To correct this error</span></span>  
  
-   <span data-ttu-id="8f9d5-116">Se a instrução atribui um valor a uma expressão, substitua a expressão com uma única variável gravável, uma propriedade ou um elemento de matriz.</span><span class="sxs-lookup"><span data-stu-id="8f9d5-116">If the statement assigns a value to an expression, replace the expression with a single writable variable, property, or array element.</span></span>  
  
-   <span data-ttu-id="8f9d5-117">Se a instrução faz acesso indireto através de um tipo de valor (geralmente uma estrutura), crie uma variável para conter o tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="8f9d5-117">If the statement makes indirect access through a value type (usually a structure), create a variable to hold the value type.</span></span>  
  
-   <span data-ttu-id="8f9d5-118">Atribua a estrutura apropriada (ou outro tipo de valor) à variável.</span><span class="sxs-lookup"><span data-stu-id="8f9d5-118">Assign the appropriate structure (or other value type) to the variable.</span></span>  
  
-   <span data-ttu-id="8f9d5-119">Use a variável para acessar a propriedade para atribuir um valor ela.</span><span class="sxs-lookup"><span data-stu-id="8f9d5-119">Use the variable to access the property to assign it a value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f9d5-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f9d5-120">See Also</span></span>  
 <span data-ttu-id="8f9d5-121">[Operadores e expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="8f9d5-121">[Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md) </span></span>  
<span data-ttu-id="8f9d5-122"> [Instruções](../../../visual-basic/programming-guide/language-features/statements.md) </span><span class="sxs-lookup"><span data-stu-id="8f9d5-122"> [Statements](../../../visual-basic/programming-guide/language-features/statements.md) </span></span>  
<span data-ttu-id="8f9d5-123"> [Solução de problemas de Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)</span><span class="sxs-lookup"><span data-stu-id="8f9d5-123"> [Troubleshooting Procedures](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)</span></span>

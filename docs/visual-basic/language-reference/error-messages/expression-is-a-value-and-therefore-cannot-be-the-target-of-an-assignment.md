---
title: Expressão é um valor e, por isso, não pode ser o destino de uma atribuição
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: dd5618bd0533f885a6aef8229b2d8cb1bc34c237
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590232"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a><span data-ttu-id="76384-102">Expressão é um valor e, por isso, não pode ser o destino de uma atribuição</span><span class="sxs-lookup"><span data-stu-id="76384-102">Expression is a value and therefore cannot be the target of an assignment</span></span>
<span data-ttu-id="76384-103">Uma instrução tenta atribuir um valor a uma expressão.</span><span class="sxs-lookup"><span data-stu-id="76384-103">A statement attempts to assign a value to an expression.</span></span> <span data-ttu-id="76384-104">Você pode atribuir um valor apenas para uma variável gravável, propriedade ou elemento de matriz em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="76384-104">You can assign a value only to a writable variable, property, or array element at run time.</span></span> <span data-ttu-id="76384-105">O exemplo a seguir ilustra como esse erro pode ocorrer.</span><span class="sxs-lookup"><span data-stu-id="76384-105">The following example illustrates how this error can occur.</span></span>  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 <span data-ttu-id="76384-106">Exemplos semelhantes podem aplicar a propriedades e os elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="76384-106">Similar examples could apply to properties and array elements.</span></span>  
  
 <span data-ttu-id="76384-107">**Acesso indireto.**</span><span class="sxs-lookup"><span data-stu-id="76384-107">**Indirect Access.**</span></span> <span data-ttu-id="76384-108">Acesso indireto por meio de um tipo de valor também pode gerar esse erro.</span><span class="sxs-lookup"><span data-stu-id="76384-108">Indirect access through a value type can also generate this error.</span></span> <span data-ttu-id="76384-109">Considere o seguinte exemplo de código, que tenta definir o valor de <xref:System.Drawing.Point> acessando indiretamente por meio <xref:System.Windows.Forms.Control.Location%2A>.</span><span class="sxs-lookup"><span data-stu-id="76384-109">Consider the following code example, which attempts to set the value of <xref:System.Drawing.Point> by accessing it indirectly through <xref:System.Windows.Forms.Control.Location%2A>.</span></span>  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 <span data-ttu-id="76384-110">A última instrução do exemplo anterior falhará porque ela cria somente uma alocação temporária para o <xref:System.Drawing.Point> estrutura retornada pelo <xref:System.Windows.Forms.Control.Location%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="76384-110">The last statement of the preceding example fails because it creates only a temporary allocation for the <xref:System.Drawing.Point> structure returned by the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span> <span data-ttu-id="76384-111">Uma estrutura é um tipo de valor e a estrutura temporária não é retida depois que a instrução é executada.</span><span class="sxs-lookup"><span data-stu-id="76384-111">A structure is a value type, and the temporary structure is not retained after the statement runs.</span></span> <span data-ttu-id="76384-112">O problema seja resolvido declarando e usando uma variável para <xref:System.Windows.Forms.Control.Location%2A>, que cria uma alocação mais permanente para o <xref:System.Drawing.Point> estrutura.</span><span class="sxs-lookup"><span data-stu-id="76384-112">The problem is resolved by declaring and using a variable for <xref:System.Windows.Forms.Control.Location%2A>, which creates a more permanent allocation for the <xref:System.Drawing.Point> structure.</span></span> <span data-ttu-id="76384-113">O exemplo a seguir mostra o código que pode substituir a última instrução do exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="76384-113">The following example shows code that can replace the last statement of the preceding example.</span></span>  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 <span data-ttu-id="76384-114">**ID do erro:** BC30068</span><span class="sxs-lookup"><span data-stu-id="76384-114">**Error ID:** BC30068</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="76384-115">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="76384-115">To correct this error</span></span>  
  
-   <span data-ttu-id="76384-116">Se a instrução atribui um valor a uma expressão, substitua a expressão com uma única variável gravável, propriedade ou elemento de matriz.</span><span class="sxs-lookup"><span data-stu-id="76384-116">If the statement assigns a value to an expression, replace the expression with a single writable variable, property, or array element.</span></span>  
  
-   <span data-ttu-id="76384-117">Se a instrução faz acesso indireto por meio de um tipo de valor (normalmente uma estrutura), crie uma variável para manter o tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="76384-117">If the statement makes indirect access through a value type (usually a structure), create a variable to hold the value type.</span></span>  
  
-   <span data-ttu-id="76384-118">Atribua a estrutura apropriada (ou outro tipo de valor) à variável.</span><span class="sxs-lookup"><span data-stu-id="76384-118">Assign the appropriate structure (or other value type) to the variable.</span></span>  
  
-   <span data-ttu-id="76384-119">Use a variável para acessar a propriedade para atribuir a ela um valor.</span><span class="sxs-lookup"><span data-stu-id="76384-119">Use the variable to access the property to assign it a value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76384-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76384-120">See Also</span></span>  
 [<span data-ttu-id="76384-121">Operadores e Expressões</span><span class="sxs-lookup"><span data-stu-id="76384-121">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="76384-122">Instruções</span><span class="sxs-lookup"><span data-stu-id="76384-122">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="76384-123">Solução de problemas de Procedimentos</span><span class="sxs-lookup"><span data-stu-id="76384-123">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
